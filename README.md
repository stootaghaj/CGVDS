# CGVDS
Cloud Gaming Video Dataset
 

Due to review process of the paper, we only provide the dataset for two video sequences out fifteen. The encoded videos together with raw recorded sequences are included in the dataset. 
Link: https://drive.google.com/open?id=1wfiuShlLcbpjMkQ3ZkIlJAYcZeEwlifl 

The dataset has four folders as follows:

•	Subject Ratings: subjective ratings together with additional pre/post-game ratings. Raw subjective rating will be realized upon acceptance of the paper. 

•	MOS information: The Mean Opinion Score (MOS) information is provided together with some plots lined to MOS ratings. 

•	Plots and Metrics: the results of objective metrics are provided in frame level as well video level together with some scatter plots of each metric and subjective results.

•	Materials: the raw reference sequence in YUV format together with encoded videos in mp4 format at spatial resolutions are provided in this folder.

In order to encode the video we used the following command on ffmpeg:

ffmpeg -y -r ${framerate} -s:v 1920x1080 -i ${file} -r ${framerate} -c:v h264_nvenc -rc cbr_ld_hq -preset llhq -zerolatency 1 -forced-idr 1 -pixel_format yuv420p -b:v $bitrate$'k' -minrate $bitrate$'k' -maxrate $bitrate$'k' -bufsize $bitrate$'k' ${file%.*}_${encodingresolution}_${framerate}_${bitrate}_${codec}.mp4

In order to rescale the videos to 1080p we used bilinear method tas follows:

ffmpeg -y -i ${file%.*}.mp4 -filter:v scale=1920:1080 -sws_flags "bilinear" -vcodec rawvideo -pix_fmt yuv420p -f rawvideo PATH/${file%.*}.yuv

Dataset will be completely published upon acceptance of the paper!
