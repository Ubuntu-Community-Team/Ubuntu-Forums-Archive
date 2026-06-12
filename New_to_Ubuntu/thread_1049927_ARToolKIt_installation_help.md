---
title: "ARToolKIt installation help"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by glennlad on 2009-01-25
Im trying to install artoolkit, i have read tuts on how to do it but its confusing me and most of it doesnt help on the slightest, hoping someone here can help please...

I have artoolkit on the desktop in .tgz folder, what do i do?

or if anyone knows the sudo apt-get command for this program then could you please share?

thanks in advance

---

### Post by Michael.Godawski on 2009-01-25
hi, 
have a  read here:

[http://ubuntuforums.org/showthread.php?t=343529](http://ubuntuforums.org/showthread.php?t=343529)

---

### Post by glennlad on 2009-01-25
IM having a slight problem with

./configure

bash: ./configure: No such file or directory

---

### Post by Michael.Godawski on 2009-01-25
The ./configure command must be executed in the correct directory.

Make sure you navigate with the cd command to the extracted folder in Terminal.

---

### Post by glennlad on 2009-01-25
how do i do that?

im new to this

---

### Post by Michael.Godawski on 2009-01-25
When you open the [terminal]("http://ubunturesources.ub.ohost.de/terminal.html"), you can use the 
```

ls
```

command to show all folders and files which are in the directory in which you are.
So when you just open the terminal and run ls you will see the content of your /home folder.

To navigate in terminal we use the cd command ( **c**hange **d**irectory ).
So for instance we wanna go to the Desktop we run

```
cd ~/Desktop
```The ~ is the abbreviation for /home/username. 
A nice feature is the TAB- Button which auto-completes directory names when you enter only the first few letters. If there is clear aut-complete options you will hear a system beep.

---

### Post by glennlad on 2009-01-25
ok well i've got into the directory of artoolkit, which is on my desktop, i try the ./configure and its still presenting me with the same problem bash: ./configure: No such file or directory
altho i can clearly see a Configure file in the folder.

---

### Post by Michael.Godawski on 2009-01-25
lol I got it:D

it has to be 
```
./Configure
```
with a capital C

---

### Post by glennlad on 2009-01-25
Ok i done the configure and ive done the make then i do sudo make install and i get errors at the bottom of this:

ste@PC:~/ARToolKit$ make
(cd lib/SRC;    make -f Makefile)
make[1]: Entering directory `/home/ste/ARToolKit/lib/SRC'
(cd AR;         make -f Makefile)
make[2]: Entering directory `/home/ste/ARToolKit/lib/SRC/AR'
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include mAlloc.c
ar rs ../../libAR.a mAlloc.o
rm -f mAlloc.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include mFree.c
ar rs ../../libAR.a mFree.o
rm -f mFree.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include mAllocDup.c
ar rs ../../libAR.a mAllocDup.o
rm -f mAllocDup.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include mDup.c
ar rs ../../libAR.a mDup.o
rm -f mDup.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include mAllocTrans.c
ar rs ../../libAR.a mAllocTrans.o
rm -f mAllocTrans.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include mTrans.c
ar rs ../../libAR.a mTrans.o
rm -f mTrans.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include mAllocMul.c
ar rs ../../libAR.a mAllocMul.o
rm -f mAllocMul.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include mMul.c
ar rs ../../libAR.a mMul.o
rm -f mMul.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include mAllocInv.c
ar rs ../../libAR.a mAllocInv.o
rm -f mAllocInv.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include mInv.c
ar rs ../../libAR.a mInv.o
rm -f mInv.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include mSelfInv.c
ar rs ../../libAR.a mSelfInv.o
rm -f mSelfInv.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include mAllocUnit.c
ar rs ../../libAR.a mAllocUnit.o
rm -f mAllocUnit.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include mUnit.c
ar rs ../../libAR.a mUnit.o
rm -f mUnit.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include mDisp.c
ar rs ../../libAR.a mDisp.o
rm -f mDisp.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include mDet.c
ar rs ../../libAR.a mDet.o
rm -f mDet.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include mPCA.c
ar rs ../../libAR.a mPCA.o
rm -f mPCA.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include vAlloc.c
ar rs ../../libAR.a vAlloc.o
rm -f vAlloc.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include vDisp.c
ar rs ../../libAR.a vDisp.o
rm -f vDisp.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include vFree.c
ar rs ../../libAR.a vFree.o
rm -f vFree.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include vHouse.c
ar rs ../../libAR.a vHouse.o
rm -f vHouse.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include vInnerP.c
ar rs ../../libAR.a vInnerP.o
rm -f vInnerP.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include vTridiag.c
ar rs ../../libAR.a vTridiag.o
rm -f vTridiag.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include paramGet.c
ar rs ../../libAR.a paramGet.o
rm -f paramGet.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include paramDecomp.c
ar rs ../../libAR.a paramDecomp.o
rm -f paramDecomp.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include paramDistortion.c
ar rs ../../libAR.a paramDistortion.o
rm -f paramDistortion.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include paramChangeSize.c
ar rs ../../libAR.a paramChangeSize.o
rm -f paramChangeSize.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include paramFile.c
ar rs ../../libAR.a paramFile.o
rm -f paramFile.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include paramDisp.c
ar rs ../../libAR.a paramDisp.o
rm -f paramDisp.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include arDetectMarker.c
ar rs ../../libAR.a arDetectMarker.o
rm -f arDetectMarker.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include arGetTransMat.c
ar rs ../../libAR.a arGetTransMat.o
rm -f arGetTransMat.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include arGetTransMat2.c
ar rs ../../libAR.a arGetTransMat2.o
rm -f arGetTransMat2.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include arGetTransMat3.c
ar rs ../../libAR.a arGetTransMat3.o
rm -f arGetTransMat3.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include arGetTransMatCont.c
ar rs ../../libAR.a arGetTransMatCont.o
rm -f arGetTransMatCont.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include arLabeling.c
ar rs ../../libAR.a arLabeling.o
rm -f arLabeling.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include arDetectMarker2.c
ar rs ../../libAR.a arDetectMarker2.o
rm -f arDetectMarker2.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include arGetMarkerInfo.c
ar rs ../../libAR.a arGetMarkerInfo.o
rm -f arGetMarkerInfo.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include arGetCode.c
ar rs ../../libAR.a arGetCode.o
rm -f arGetCode.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include arUtil.c
arUtil.c: In function ‘arGetVersion’:
arUtil.c:46: warning: incompatible implicit declaration of built-in function ‘exit’
ar rs ../../libAR.a arUtil.o
rm -f arUtil.o
make[2]: Leaving directory `/home/ste/ARToolKit/lib/SRC/AR'
(cd ARMulti;    make -f Makefile)
make[2]: Entering directory `/home/ste/ARToolKit/lib/SRC/ARMulti'
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include arMultiReadConfigFile.c
ar rs ../../libARMulti.a arMultiReadConfigFile.o
rm -f arMultiReadConfigFile.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include arMultiGetTransMat.c
ar rs ../../libARMulti.a arMultiGetTransMat.o
rm -f arMultiGetTransMat.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include arMultiActivate.c
ar rs ../../libARMulti.a arMultiActivate.o
rm -f arMultiActivate.o
make[2]: Leaving directory `/home/ste/ARToolKit/lib/SRC/ARMulti'
(cd Gl;         make -f Makefile)
make[2]: Entering directory `/home/ste/ARToolKit/lib/SRC/Gl'
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include gsub.c
ar rs ../../libARgsub.a gsub.o
rm -f gsub.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include gsubUtil.c
ar rs ../../libARgsubUtil.a gsubUtil.o
rm -f gsubUtil.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include gsub_lite.c
gsub_lite.c: In function ‘arglCameraFrustum’:
gsub_lite.c:659: warning: passing argument 1 of ‘arParamDecompMat’ from incompatible pointer type
gsub_lite.c: In function ‘arglCameraFrustumRH’:
gsub_lite.c:718: warning: passing argument 1 of ‘arParamDecompMat’ from incompatible pointer type
ar rs ../../libARgsub_lite.a gsub_lite.o
rm -f gsub_lite.o
make[2]: Leaving directory `/home/ste/ARToolKit/lib/SRC/Gl'
(cd VideoLinuxV4L; make -f Makefile)
make[2]: Entering directory `/home/ste/ARToolKit/lib/SRC/VideoLinuxV4L'
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include ccvt_i386.S
ccvt_i386.S:32:27: error: linux/linkage.h: No such file or directory
make[2]: *** [../../libARvideo.a(ccvt_i386.o)] Error 1
make[2]: Leaving directory `/home/ste/ARToolKit/lib/SRC/VideoLinuxV4L'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/ste/ARToolKit/lib/SRC'
make: *** [all] Error 2

---

### Post by dersteps on 2009-10-10
Hi there!

I've got exactly the same error(s). Maybe you solved that issue by now and are able to help me?

Here's what I did:

1. Downloaded [http://sourceforge.net/projects/artoolkit/files/artoolkit/2.72.1/ARToolKit-2.72.1.tgz/download](http://sourceforge.net/projects/artoolkit/files/artoolkit/2.72.1/ARToolKit-2.72.1.tgz/download)
(to my Desktop)
2. Terminal -> cd Desktop
3. tar zxvf ARToolKit-2.72.1.tgz
4. cd ARToolKit/
5. ./Configure
  5a. Chose EYETOY Option (2)
  5b. "Color conversion should use x86 assembly (not working for 64bit)?" (answer: y)
  5c. Debug Symbols: y
  5d. Texture Rectangle Support: y
6. make

Here are my make errors:

```
arUtil.c: In function ‘arGetVersion’:
arUtil.c:46: warning: incompatible implicit declaration of built-in function ‘exit’
gsub_lite.c: In function ‘arglCameraFrustum’:
gsub_lite.c:659: warning: passing argument 1 of ‘arParamDecompMat’ from incompatible pointer type
gsub_lite.c: In function ‘arglCameraFrustumRH’:
gsub_lite.c:718: warning: passing argument 1 of ‘arParamDecompMat’ from incompatible pointer type
ccvt_i386.S:32:27: error: linux/linkage.h: No such file or directory
make[2]: *** [../../libARvideo.a(ccvt_i386.o)] Error 1
make[1]: *** [all] Error 2
make: *** [all] Error 2

```I am using Ubuntu 9.04 Jaunty 64 Bit - guess that could be a problem?

Well...any help would do...so if someone knows how to make ARToolkit in Jauntyx64...please tell me!

Greets

---

### Post by RyanLu on 2009-11-20
I'm new and i'm doing some project on AR. I'm facing some problem while i am installing visual C++ 2005 and ARToolkit. 

I've reach step 7 while installing AR. I cant completely build the toolkit.

Error shows :
> 1>------ Build started: Project: libAR, Configuration: Debug Win32 ------
1>Compiling...
1>arUtil.c
1>c:\documents and settings\administrator\my documents\downloads\artoolkit\lib\src\ar\arutil.c(17) : fatal error C1083: Cannot open include file: 'windows.h': No such file or directory
1>arLabeling.c
1>c:\documents and settings\administrator\my documents\downloads\artoolkit\lib\src\ar\arlabeling.c(19) : fatal error C1083: Cannot open include file: 'windows.h': No such file or directory
1>Generating Code...
1>Creating browse information file...
1>Microsoft Browse Information Maintenance Utility Version 8.00.50727
1>Copyright (C) Microsoft Corporation. All rights reserved.
1>BSCMAKE: error BK1506 : cannot open file '.\Debug\arLabeling.sbr': No such file or directory
1>Build log was saved at "file://c:\Documents and Settings\Administrator\My Documents\Downloads\ARToolKit\lib\SRC\AR\Debug\BuildLog.htm"
1>libAR - 3 error(s), 0 warning(s)
========== Build: 0 succeeded, 1 failed, 0 up-to-date, 0 skipped ==========

Help me please.

---

### Post by mcguinnessdr on 2009-11-21
I am having the same problem "linkage.h: no such file or directory". I used search and there are 22 linkage.h files, but none of them where artoolkit tries to find it. How can i get it to work?

---

### Post by sazawal on 2010-02-12
I tried to install ARToolkit on Ubuntu 9.10. ./Configure worked fine but I am stuck at make, I am getting errors, here is the output

```

root@saz:/home/saz/Desktop/Downloads/ARToolKit# make
(cd lib/SRC;    make -f Makefile)
make[1]: Entering directory `/home/saz/Downloads/ARToolKit/lib/SRC'
(cd AR;         make -f Makefile)
make[2]: Entering directory `/home/saz/Downloads/ARToolKit/lib/SRC/AR'
cc -c -O -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/X11R6/include -I../../../include mAlloc.c
ar rs ../../libAR.a mAlloc.o
rm -f mAlloc.o
cc -c -O -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/X11R6/include -I../../../include mFree.c
ar rs ../../libAR.a mFree.o
rm -f mFree.o
cc -c -O -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/X11R6/include -I../../../include mAllocDup.c
ar rs ../../libAR.a mAllocDup.o
rm -f mAllocDup.o
cc -c -O -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/X11R6/include -I../../../include mDup.c
ar rs ../../libAR.a mDup.o
rm -f mDup.o
cc -c -O -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/X11R6/include -I../../../include mAllocTrans.c
ar rs ../../libAR.a mAllocTrans.o
rm -f mAllocTrans.o
cc -c -O -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/X11R6/include -I../../../include mTrans.c
ar rs ../../libAR.a mTrans.o
rm -f mTrans.o
cc -c -O -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/X11R6/include -I../../../include mAllocMul.c
ar rs ../../libAR.a mAllocMul.o
rm -f mAllocMul.o
cc -c -O -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/X11R6/include -I../../../include mMul.c
ar rs ../../libAR.a mMul.o
rm -f mMul.o
cc -c -O -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/X11R6/include -I../../../include mAllocInv.c
ar rs ../../libAR.a mAllocInv.o
rm -f mAllocInv.o
cc -c -O -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/X11R6/include -I../../../include mInv.c
ar rs ../../libAR.a mInv.o
rm -f mInv.o
cc -c -O -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/X11R6/include -I../../../include mSelfInv.c
ar rs ../../libAR.a mSelfInv.o
rm -f mSelfInv.o
cc -c -O -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/X11R6/include -I../../../include mAllocUnit.c
ar rs ../../libAR.a mAllocUnit.o
rm -f mAllocUnit.o
cc -c -O -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/X11R6/include -I../../../include mUnit.c
ar rs ../../libAR.a mUnit.o
rm -f mUnit.o
cc -c -O -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/X11R6/include -I../../../include mDisp.c
ar rs ../../libAR.a mDisp.o
rm -f mDisp.o
cc -c -O -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/X11R6/include -I../../../include mDet.c
ar rs ../../libAR.a mDet.o
rm -f mDet.o
cc -c -O -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/X11R6/include -I../../../include mPCA.c
ar rs ../../libAR.a mPCA.o
rm -f mPCA.o
cc -c -O -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/X11R6/include -I../../../include vAlloc.c
ar rs ../../libAR.a vAlloc.o
rm -f vAlloc.o
cc -c -O -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/X11R6/include -I../../../include vDisp.c
ar rs ../../libAR.a vDisp.o
rm -f vDisp.o
cc -c -O -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/X11R6/include -I../../../include vFree.c
ar rs ../../libAR.a vFree.o
rm -f vFree.o
cc -c -O -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/X11R6/include -I../../../include vHouse.c
ar rs ../../libAR.a vHouse.o
rm -f vHouse.o
cc -c -O -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/X11R6/include -I../../../include vInnerP.c
ar rs ../../libAR.a vInnerP.o
rm -f vInnerP.o
cc -c -O -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/X11R6/include -I../../../include vTridiag.c
ar rs ../../libAR.a vTridiag.o
rm -f vTridiag.o
cc -c -O -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/X11R6/include -I../../../include paramGet.c
ar rs ../../libAR.a paramGet.o
rm -f paramGet.o
cc -c -O -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/X11R6/include -I../../../include paramDecomp.c
ar rs ../../libAR.a paramDecomp.o
rm -f paramDecomp.o
cc -c -O -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/X11R6/include -I../../../include paramDistortion.c
ar rs ../../libAR.a paramDistortion.o
rm -f paramDistortion.o
cc -c -O -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/X11R6/include -I../../../include paramChangeSize.c
ar rs ../../libAR.a paramChangeSize.o
rm -f paramChangeSize.o
cc -c -O -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/X11R6/include -I../../../include paramFile.c
ar rs ../../libAR.a paramFile.o
rm -f paramFile.o
cc -c -O -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/X11R6/include -I../../../include paramDisp.c
ar rs ../../libAR.a paramDisp.o
rm -f paramDisp.o
cc -c -O -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/X11R6/include -I../../../include arDetectMarker.c
ar rs ../../libAR.a arDetectMarker.o
rm -f arDetectMarker.o
cc -c -O -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/X11R6/include -I../../../include arGetTransMat.c
ar rs ../../libAR.a arGetTransMat.o
rm -f arGetTransMat.o
cc -c -O -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/X11R6/include -I../../../include arGetTransMat2.c
ar rs ../../libAR.a arGetTransMat2.o
rm -f arGetTransMat2.o
cc -c -O -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/X11R6/include -I../../../include arGetTransMat3.c
ar rs ../../libAR.a arGetTransMat3.o
rm -f arGetTransMat3.o
cc -c -O -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/X11R6/include -I../../../include arGetTransMatCont.c
ar rs ../../libAR.a arGetTransMatCont.o
rm -f arGetTransMatCont.o
cc -c -O -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/X11R6/include -I../../../include arLabeling.c
ar rs ../../libAR.a arLabeling.o
rm -f arLabeling.o
cc -c -O -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/X11R6/include -I../../../include arDetectMarker2.c
ar rs ../../libAR.a arDetectMarker2.o
rm -f arDetectMarker2.o
cc -c -O -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/X11R6/include -I../../../include arGetMarkerInfo.c
ar rs ../../libAR.a arGetMarkerInfo.o
rm -f arGetMarkerInfo.o
cc -c -O -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/X11R6/include -I../../../include arGetCode.c
ar rs ../../libAR.a arGetCode.o
rm -f arGetCode.o
cc -c -O -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/X11R6/include -I../../../include arUtil.c
arUtil.c: In function ‘arGetVersion’:
arUtil.c:46: warning: incompatible implicit declaration of built-in function ‘exit’
ar rs ../../libAR.a arUtil.o
rm -f arUtil.o
make[2]: Leaving directory `/home/saz/Downloads/ARToolKit/lib/SRC/AR'
(cd ARMulti;    make -f Makefile)
make[2]: Entering directory `/home/saz/Downloads/ARToolKit/lib/SRC/ARMulti'
cc -c -O -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/X11R6/include -I../../../include arMultiReadConfigFile.c
ar rs ../../libARMulti.a arMultiReadConfigFile.o
rm -f arMultiReadConfigFile.o
cc -c -O -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/X11R6/include -I../../../include arMultiGetTransMat.c
ar rs ../../libARMulti.a arMultiGetTransMat.o
rm -f arMultiGetTransMat.o
cc -c -O -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/X11R6/include -I../../../include arMultiActivate.c
ar rs ../../libARMulti.a arMultiActivate.o
rm -f arMultiActivate.o
make[2]: Leaving directory `/home/saz/Downloads/ARToolKit/lib/SRC/ARMulti'
(cd Gl;         make -f Makefile)
make[2]: Entering directory `/home/saz/Downloads/ARToolKit/lib/SRC/Gl'
cc -c -O -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/X11R6/include -I../../../include gsub.c
ar rs ../../libARgsub.a gsub.o
rm -f gsub.o
cc -c -O -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/X11R6/include -I../../../include gsubUtil.c
ar rs ../../libARgsubUtil.a gsubUtil.o
rm -f gsubUtil.o
cc -c -O -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/X11R6/include -I../../../include gsub_lite.c
gsub_lite.c:102:1: warning: "GL_TEXTURE_RECTANGLE" redefined
In file included from /usr/include/GL/gl.h:2089,
                 from ../../../include/AR/gsub_lite.h:133,
                 from gsub_lite.c:48:
/usr/include/GL/glext.h:756:1: warning: this is the location of the previous definition
gsub_lite.c:103:1: warning: "GL_PROXY_TEXTURE_RECTANGLE" redefined
/usr/include/GL/glext.h:758:1: warning: this is the location of the previous definition
gsub_lite.c:104:1: warning: "GL_MAX_RECTANGLE_TEXTURE_SIZE" redefined
/usr/include/GL/glext.h:759:1: warning: this is the location of the previous definition
gsub_lite.c: In function ‘arglCameraFrustum’:
gsub_lite.c:659: warning: passing argument 1 of ‘arParamDecompMat’ from incompatible pointer type
../../../include/AR/param.h:123: note: expected ‘double (*)[4]’ but argument is of type ‘const double (*)[4]’
gsub_lite.c: In function ‘arglCameraFrustumRH’:
gsub_lite.c:718: warning: passing argument 1 of ‘arParamDecompMat’ from incompatible pointer type
../../../include/AR/param.h:123: note: expected ‘double (*)[4]’ but argument is of type ‘const double (*)[4]’
ar rs ../../libARgsub_lite.a gsub_lite.o
rm -f gsub_lite.o
make[2]: Leaving directory `/home/saz/Downloads/ARToolKit/lib/SRC/Gl'
(cd VideoGStreamer; make -f Makefile)
make[2]: Entering directory `/home/saz/Downloads/ARToolKit/lib/SRC/VideoGStreamer'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/saz/Downloads/ARToolKit/lib/SRC/VideoGStreamer'
make[1]: Leaving directory `/home/saz/Downloads/ARToolKit/lib/SRC'
(cd util;       make -f Makefile)
make[1]: Entering directory `/home/saz/Downloads/ARToolKit/util'
(cd graphicsTest;     make -f Makefile)
make[2]: Entering directory `/home/saz/Downloads/ARToolKit/util/graphicsTest'
cc -o ../../bin/graphicsTest graphicsTest.o  -pthread -lgstreamer-0.10 -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lrt -lxml2 -lglib-2.0 -L/usr/X11R6/lib -L/usr/local/lib -L../../lib -lARgsub -lARvideo -lAR -lpthread -lglut -lGLU -lGL -lXi -lX11 -lm
/usr/bin/ld: cannot find -lXi
collect2: ld returned 1 exit status
make[2]: *** [../../bin/graphicsTest] Error 1
make[2]: Leaving directory `/home/saz/Downloads/ARToolKit/util/graphicsTest'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/saz/Downloads/ARToolKit/util'
make: *** [all] Error 2


```

I am not able to recognise these errors, somebody please help me out

---

### Post by sazawal on 2010-02-12
I got the solution for my problem here 

[http://ubuntuforums.org/showthread.php?p=8816386#post8816386](http://ubuntuforums.org/showthread.php?p=8816386#post8816386)

---

