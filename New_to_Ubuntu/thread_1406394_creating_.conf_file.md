---
title: "creating .conf file"
date: 2010-02-13
forum: New to Ubuntu
---

### Post by ionray on 2010-02-13
Hi,
I'm trying to install OpenCV but I have a really basic problem.  I cant understand one of the instructions in the guide to installing it. It's under the path configuration it says;

"In order to use the libraries in Linux, thier path should be specified. Library path can be specified in /etc/ld.so.conf.d/ by creating a file called 'opencv.conf' which contains the opencv library path (Default configuration is /usr/local/lib). Once the file is created, execute 

sudo ldconfig -v

to make new set library pathes effective. Or you can also add the path to LD_LIBRARY_PATH: 

export LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH     "


I cant find any information on creating a file (.conf) that contains the 
path so im assuming its something really simple.  Any help is appreciated.

Thanks,

---

### Post by rCXer on 2010-02-14
Hey ionray, the OpenCV 1.0 libraries are in the repositories.  You don't have to install it manually unless you need the newer OpenCV 2.0.  You can install it using:

```

sudo apt-get install libavutil49 libavutil-dev libavcodec-dev libcv1 libcvaux1 libcvaux-dev libcv-dev libhighgui1 libhighgui-dev opencv-doc

```

If you want to build with cmake, [my guide]("http://ubuntuforums.org/showpost.php?p=8760983&postcount=2") may be helpful.

---

### Post by ionray on 2010-02-14
I don't know the difference between OpenCV 1.0 and 2.0 but I've only used 2.0 so that's why I want it to work.  

I'm still new to linux so hope you don't mind dumb questions i guess. but what's repositories? 

using cmake looks a bit complex for me to use being I'm having trouble using codeblocks.  which I know how to set up opencv in codeblocks but for some reason when I add the library files it doesn't note they are there.  only explanation I could think of was that I hadn't done the path configuration from the guide:
[http://opencv.willowgarage.com/wiki/InstallGuide_Linux](http://opencv.willowgarage.com/wiki/InstallGuide_Linux) 

which I assume its easy to put the library path on a .conf file, am I correct? 

thanks for your help.

---

### Post by rCXer on 2010-02-14
> **ionray said:**
> I don't know the difference between OpenCV 1.0 and 2.0 but I've only used 2.0 so that's why I want it to work.  


I don't know the difference either but 1.0 has most of the features that 2.0 has :p

> 
I'm still new to linux so hope you don't mind dumb questions i guess. but what's repositories? 


No such thing as a dumb question. It's software available to Ubuntu users that can be downloaded using apt-get or the package manager.

> 
using cmake looks a bit complex for me to use being I'm having trouble using codeblocks. which I know how to set up opencv in codeblocks but for some reason when I add the library files it doesn't note they are there.  only explanation I could think of was that I hadn't done the path configuration from the guide:
[http://opencv.willowgarage.com/wiki/InstallGuide_Linux](http://opencv.willowgarage.com/wiki/InstallGuide_Linux) 

which I assume its easy to put the library path on a .conf file, am I correct? 

thanks for your help.


Unfortunately, I'm not familiar with .conf files but I also codeblocks. If you install opencv 1.0 as described above and follow [my guide]("http://ubuntuforums.org/showpost.php?p=8760983&postcount=2"), selecting "CodeBlocks - Unix Makefiles"  instead of "Unix Makefiles" it should work.  That's the magic of CMake :) Although it seems difficult at first it's worth giving it a try.

The people at the [opencv mailing list]("http://tech.groups.yahoo.com/group/OpenCV/messages") might be able help you as well.

---

### Post by ionray on 2010-02-14
awesome thanks for that. 

I now understand how to use cmake and have gotten it to work without opencv.  But when I do try to use opencv it cant find anything from it. for example at the top when building it says:

"CMakeFiles/image.dir/image.c.o: In function `cvRound':
image.c:(.text+0x19): undefined reference to `lrint'"

happen to know what I'm doing wrong?

---

### Post by rCXer on 2010-02-14
Could you post your source code and your CMakeLists.txt if possible.  I'll try it on my computer?

Are you using the OpenCV from the repositories?

---

### Post by rCXer on 2010-02-14
Also could you post the output of...
```

whereis libcv

```
...and...
```

whereis libcvaux

```

---

### Post by ionray on 2010-02-15
I used the apt code you supplied before. Was that the opencv 1.0 in the repositories?  The source code worked when I made it on windows so there shouldn't be any errors.
 

 Source code:
 // Convert a video to grayscale 
 // argv[1]: input video file 
 // argv[2]: name of new output file 
  
 #include "cv.h" 
 #include "highgui.h" 
 #include <stdio.h> 
  
 main( int argc, char* argv[] ) 
 { 
     char c; 
  
     CvCapture* capture = NULL; 
     if( argc==1 ) 
     { 
         capture = cvCreateCameraCapture(0); 
     } 
     else 
     { 
         capture = cvCreateFileCapture( argv[1] ); 
     } 
     assert( capture != NULL ); 
  
     int fps = 25; 
     int frameW  = 744; 
     int frameH  = 480; 
  
     CvVideoWriter* writer = cvCreateVideoWriter("output.avi",CV_FOURCC('P','I','M','1'),fps,cvSize(frameW,frameH),1); 
     cvNamedWindow( "display", CV_WINDOW_AUTOSIZE ); 
     IplImage* frame; 
  
     while(1) 
     { 
         /*save video*/ 
         cvGrabFrame(capture);             // capture a frame 
         frame = cvRetrieveFrame(capture,1); // retrieve the captured frame 
  
         printf("\n1\n"); 
         cvWriteFrame(writer, frame);      // add the frame to the file 
         printf("\n2\n"); 
  
         /*break when out of frames*/ 
         if(!frame) break; 
         cvShowImage("display", frame); 
         /*ASCII 27 = esc*/ 
         c = cvWaitKey(20); 
         if( c == 27 ) break; 
         /*ASCII 114 = r*/ 
         /*if(c == 114) 
         { 
  
         }*/ 
     } 
  
     cvReleaseVideoWriter(&writer); 
     cvReleaseCapture(&capture); 
     cvDestroyWindow("display"); 
  
     return(0); 
 }
 

 cmake code:
 CMAKE_MINIMUM_REQUIRED(VERSION 2.6)  
  
 PROJECT(show)  
 FIND_Package(OpenCV REQUIRED)  
 INCLUDE_DIRECTORIES( ${OPENCV_INCLUDE_DIR} )  
 ADD_EXECUTABLE(image image.c)  
 TARGET_LINK_LIBRARIES(image ${OPENCV_LIBRARIES})  
 

 where is libcv:
 libcv: /usr/lib/libcv.la /usr/lib/libcv.so /usr/lib/libcv.a /usr/local/lib/libcv.so 
 

 where is libcvaux:
 libcvaux: /usr/lib/libcvaux.a /usr/lib/libcvaux.la /usr/lib/libcvaux.so /usr/local/lib/libcvaux.so 
 

 hope that's enough information for you to help me.

---

### Post by rCXer on 2010-02-15
Thanks for posting this. The outputs of the whereis looks fine. I tried the example code you gave me, and I got this error...
```

./show/image.c:36: error: too many arguments to function &#8216;cvRetrieveFrame&#8217;

```
Changing line 36...
```

frame = cvRetrieveFrame(capture,1);

```
...to...
```

frame = cvRetrieveFrame(capture);

```
Builds without any errors.  Apparently cvRetrieveFrame only takes one argument as indicated [ in the documentation]("http://opencv.willowgarage.com/documentation/reading_and_writing_images_and_video.html?highlight=cvretrieveframe#cvRetrieveFrame").  I could not reproduce the error with cvRound and I don't see cvRound in the code you gave me ;)

---

### Post by ionray on 2010-02-15
This is weird because when I try and build the code by changing the function “cvRetrieveFrame(capture,1)” to “cvRetrieveFrame(capture)” it tells me “error: too few arguments to function 'cvRetrieveFrame'” and that is the only error. But when I change it back to what I had before then it gives me 50 errors of functions that I haven't even used(like the cvRound).   
 

 I made that program on opencv 2.0 which “cvRetrieveFrame(capture,1)” was what was needed then mabe :S.
 

 linux could be having trouble because I started with opencv 2.0 installing then I followed getting opencv 1.0 could this be codeblocks using the opencv2.0 libraries but opencv1.0 building, or something around that. This would explain  the other 50 errors that I'm randomly getting even though they ain't in my code.


either way I'm confused :S.


Thanks heaps for your help.

---

### Post by rCXer on 2010-02-15
I think you are right.  I looked at the [instructions on the opencv site](http://opencv.willowgarage.com/wiki/InstallGuide_Linux#Compilation) and apparently it tells you to install opencv "/usr/local/lib/" while the ubuntu installs opnecv to "/usr/lib/".  Just to check it this is true.  Can you start cmake, make sure the source and binary paths are correct and use the drop down menu to change from the "Simple View" to the "Advanced View"? Next scroll down to the bottom.  My screenshot is attached below.  Could you take a screenshot of this as well? I think your setup will probably have paths with "/usr/local/lib/" insted of "/usr/lib/"

What is done next depends on which version of opencv you want.  Do you want OpenCV 1.0 or 2.0?

---

### Post by ionray on 2010-02-16
hmm maybe I didn't install in properly I've got pretty much no OpenCV taps in the screen shot.... if I still have to choose between OpenCV 1 and 2 then ill choose 2 being that's the one I've made all my programs in.

---

