# assault-rifle-detection

git clone https://github.com/sofwerx/assault-rifle-detection.git $HOME/Documents/assault-rifle-detection

cd $HOME/Documents/assault-rifle-detection

docker build -t gpu_tf .


nvidia-docker run --rm --network host --privileged -it -v ~/.Xauthority:/root/.Xauthority -v /tmp/.X11-unix:/tmp/.X11-unix -e DISPLAY=$DISPLAY --env="QT_X11_NO_MITSHM=1" -v /dev/video0:/dev/video0  -v $HOME/Documents/assault-rifle-detection/tf_files:/tf_files  --device /dev/snd gpu_tf bash


cd object_detection


cp /tf_files/longgun-detection.py .


wget http://download.tensorflow.org/models/object_detection/faster_rcnn_resnet101_coco_2017_11_08.tar.gz


tar -xvf faster_rcnn_resnet101_coco_2017_11_08.tar.gz

python longgun-detection.py




