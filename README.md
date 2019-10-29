FFmpeg README
=============
交叉编译ffmpeg指令
./configure --prefix=/d/opencv3/opencv_contrib/opencv_contrib-3.1.0/zk/ffmpeg-2.7.7//install 
--enable-shared --disable-static --enable-gpl --enable-memalign-hack 
--enable-cross-compile --arch=arm --disable-stripping --target-os=qnx --enable-libx264 --enable-libxvid --cc=arm-unknown-nto-qnx6.6.0eabi-gcc.exe --enable-swscale 
--extra-ldflags=-L/d/opencv3/opencv_contrib/opencv_contrib-3.1.0/zk/ffmpeg-2.7.7/install/lib 
--extra-cflags=-I/d/opencv3/opencv_contrib/opencv_contrib-3.1.0/zk/ffmpeg-2.7.7/install/include
将编译好的x264和libxvid中的lib和include分别放入到ffmpeg中的./install/lib 和./install/include

编译完成之后调用ffmpeg库编译ffmpeg_test.cpp
 arm-unknown-nto-qnx6.6.0eabi-g++.exe ffmpeg_test.cpp -o FFDemo -I D:\opencv3\opencv_contrib\opencv_contrib\zk\ffmpeg_2_7_7\install\include  -L D:\opencv3\opencv_contrib\opencv_contrib\zk\ffmpeg_2_7_7\install\lib -lavformat -lavcodec -lswscale -lx264 -lxvidcore -lswresample -lavutil -lm -lz 
-std=c++11

上面比如-lavformat是include中libavformat。
在ffmpeg_test.cpp中的头文件中添加#undef  __cplusplus
头文件如下：
#include <libavformat/avformat.h>
#include <libavcodec/avcodec.h>
#include <libswscale/swscale.h>
