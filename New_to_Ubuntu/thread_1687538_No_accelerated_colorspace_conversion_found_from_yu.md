---
title: "No accelerated colorspace conversion found from yuv420p to bgr24."
date: 2011-02-14
forum: New to Ubuntu
---

### Post by raja2k9 on 2011-02-14
hello..i am new to ubuntu ..i was trying to compile a c program and i got this error...."No accelerated colorspace conversion found from yuv420p to bgr24."....i find out tht recompiling ffmpeg and opencv will rectify this error...but evn after tht done i am getting the same error......
when i type FFMPEG in terminal i get following output as expected..

raja@raja-VirtualBox:~$ ffmpeg
FFmpeg version SVN-r26402, Copyright (c) 2000-2011 the FFmpeg developers
  built on Feb 14 2011 11:12:12 with gcc 4.4.5
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-x11grab --enable-swscale
  libavutil     50.36. 0 / 50.36. 0
  libavcore      0.16. 1 /  0.16. 1
  libavcodec    52.108. 0 / 52.108. 0
  libavformat   52.93. 0 / 52.93. 0
  libavdevice   52. 2. 3 / 52. 2. 3
  libavfilter    1.74. 0 /  1.74. 0
  libswscale     0.12. 0 /  0.12. 0
  libpostproc   51. 2. 0 / 51. 2. 0
Hyper fast Audio and Video encoder
usage: ffmpeg [options] [[infile options] -i infile]... {[outfile options] outfile}...

Use -h to get full help or, even better, run 'man ffmpeg'


can anyone help me out in getting out of this error....i am struggling for two days.....i have tried recompiling ffmpeg and opencv many times.....

---

### Post by obiwang on 2011-06-30
I have the same problem on my Mac, but it is OK now.
(I do not know why, but here is what I did.)

I download x264 directly from (instead of using git)
----> [http://www.videolan.org/developers/x264.html](http://www.videolan.org/developers/x264.html)
----> my version is "x264-snapshot-20110603-2245"

I [COLOR="Blue"]recompiler x264 with[/COLOR]

----> [COLOR="Red"]./configure --enable-shared[/COLOR]
(This might be the key step ??)
instead of ./configure --enable-static  (ref. [http://ubuntuforums.org/showpost.php?p=9868359&postcount=1289](http://ubuntuforums.org/showpost.php?p=9868359&postcount=1289))

[COLOR="Blue"]After recompiled x264, I recompiled ffmpeg[/COLOR]

and my ffmpeg configure is 

./configure --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libmp3lame --enable-libx264 --enable-libxvid --enable-x11grab --enable-shared --enable-mmx --arch=x86_64 --enable-swscale

The only different between yours and mine is "--enable-mmx", but I don't think it is the key step for solving this problem.

--------------------------
Following is the additional information about the ffmpeg I use.
The ffmpeg is downloaded from [http://www.ffmpeg.org](http://www.ffmpeg.org) with Git. 
--------------------------

ffmpeg version git-N-30512-ge4e2db9, Copyright (c) 2000-2011 the FFmpeg developers  built on Jun 30 2011 23:10:10 with gcc 4.2.1 (Apple Inc. build 5666) (dot 3)
 
configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libmp3lame --enable-libx264 --enable-libxvid --enable-x11grab --enable-shared --enable-mmx --arch=x86_64 --enable-swscale

  libavutil    51.  4. 0 / 51.  4. 0
  libavcodec   53.  6. 1 / 53.  6. 1
  libavformat  53.  2. 0 / 53.  2. 0
  libavdevice  53.  1. 0 / 53.  1. 0
  libavfilter   2. 12. 0 /  2. 12. 0
  libswscale    0. 14. 1 /  0. 14. 1
  libpostproc  51.  2. 0 / 51.  2. 0

---

### Post by obiwang on 2011-06-30
I think ...This problem has nothing to do with OpenCV.

Because I do not use OpenCV in my program. 

And I suggest you [COLOR="Red"]compiler OpenCV first then ffmpeg[/COLOR].
If you do not want to use the ffmpeg carried by OpenCV.
ffmpeg in OpenCV is an older version. 

If you install lastest ffmpeg download from [http://www.ffmpeg.org/](http://www.ffmpeg.org/) [COLOR="red"]first[/COLOR], and
install OpenCV after it.

OpenCV will use the lastest ffmpeg under /usr/local instead of its own ffmpeg at /3rdparty
It sometimes causes error, such as the changes mentioned below.
OpenCV will stop at something like 

[80%] undefined symbols "CODEC_TYPE_VIDEO" at XXXX.c

The solution ?? is to install OpenCV without NEW ffmpeg installed first, after OpenCV installed with its ffmpeg 
then install NEW ffmpeg.?
or pls check [[COLOR="Blue"]here[/COLOR]]("https://code.ros.org/trac/opencv/ticket/1020").

Anyway, this is not the topic of this forum, so we should stop and come back.

====================================

In case you want to try the code I used.
....actually it is the first program at
 
[http://dranger.com/ffmpeg/](http://dranger.com/ffmpeg/)

But the original [COLOR="blue"][tutorial01.c]("http://dranger.com/ffmpeg/tutorial01.c")[/COLOR] at [http://dranger.com/ffmpeg](http://dranger.com/ffmpeg) can't be compiled anymore
because some definitions and functions no longer available in new ffmpeg.
you have to make the following changes...

------------------
replace list
------------------
1) about line 127:

     avcodec_decode_video(pCodecCtx, pFrame, &frameFinished,[COLOR="Blue"]packet.data, packet.size[/COLOR]);

--->  avcodec_decode_video[COLOR="red"]2[/COLOR](pCodecCtx, pFrame, &frameFinished,[COLOR="red"]&packet[/COLOR]);

2) about line 133:

   img_convert() is nolonger avaliable...

   [COLOR="Blue"] img_convert((AVPicture *)pFrameRGB, PIX_FMT_RGB24, 
                    (AVPicture*)pFrame, pCodecCtx->pix_fmt, pCodecCtx->width, 
                    pCodecCtx->height);[/COLOR]

--->
         declare this first...    [COLOR="Red"]static struct SwsContext *img_convert_ctx;[/COLOR]

 [COLOR="Red"] img_convert_ctx = sws_getContext(pCodecCtx->width, pCodecCtx->height,
                    pCodecCtx->pix_fmt, pCodecCtx->width, pCodecCtx->height,
                    PIX_FMT_RGB24, SWS_BICUBIC, NULL, NULL, NULL);

         sws_scale(img_convert_ctx, (const uint8_t* const*)pFrame->data, pFrame->linesize,
                    0, pCodecCtx->height, pFrameRGB->data, pFrameRGB->linesize);[/COLOR]

3) about line 82:

     if(pFormatCtx->streams[i]->codec->codec_type==[COLOR="Blue"]CODEC_TYPE_VIDEO[/COLOR])

---> if( pFormatCtx->streams[i]->codec->codec_type==[COLOR="red"]AVMEDIA_TYPE_VIDEO[/COLOR])

I found these solutions at 

1) [http://trac.perian.org/changeset/1056](http://trac.perian.org/changeset/1056)
2) [http://witmax.cn/ffmpeg-img-convert.html](http://witmax.cn/ffmpeg-img-convert.html)
3) [http://ffmpeg.org/doxygen/0.6/avutil_8h.html#9a84bba4713dfced21a1a56163be1f48](http://ffmpeg.org/doxygen/0.6/avutil_8h.html#9a84bba4713dfced21a1a56163be1f48)

-------------------
compiler setting
-------------------
INCLUDEPATH:

----> /usr/local/include/libavcodec
           /usr/local/include/libavformat
           /usr/local/include/libswscale

LIBs:
----> -L/usr/local/lib
----> -lswscale -lavformat -lavcodec -lz -lavutil -lm


with these INCLUDEPATH setting, your include files are

    #include <avcodec.h>
    #include <avformat.h>
    #include <swscale.h>



-----------------
keywords for google, not for reader
-----------------
'CODEC_TYPE_VIDEO' was not declared in this scope
'img_convert' was not declared in this scope
'avcodec_decode_video' was not declared in this scope

---

