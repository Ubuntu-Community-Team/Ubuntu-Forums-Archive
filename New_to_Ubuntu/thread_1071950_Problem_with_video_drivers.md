---
title: "Problem with video drivers"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by itsvan on 2009-02-16
HI there im new to kubuntu,,but ive noticed everything is very laggy when i move windows and the sort,things tend to freeze when to much is going on,i checked the hardware drivers and i try to enable it but it wont let me..and this wont let me kick in my 3d effects and the such,,wich is my second question how do i install that?

---

### Post by itsvan on 2009-02-16
I tried installing the drivers that are inthe Hardware drivers section and i get this before it finishes 

A Fatal Error Occurred
The application KMix (kmix) crashed and caused the signal 6 (SIGABRT).


By the way im running a NVIDA GEFORCE 7 series video card,,and im the list i get these three....

NVIDIA ACCELERATED GRAPHICS DRIVER VERSION 173
"          "         "         "    "      177 (recomended)
"          "         "         "    "      96

no matter which one i try they all mess up,,,was eh a going on?

---

### Post by avsilesh on 2009-02-16
I use GNome Ubuntu 8.10. I had the same problem with my Geforce 7300 nvidia drivers.I could resolve it and my 3D are workin fine now.
Post the method of installation u tried, i'm not sure of KDE, but will try to help.

---

### Post by itsvan on 2009-02-16
i installed KDE through the basic live disc,,it installed without any questions to my videocard...i managed to get one of the drivers isntalled but it is still laggy, and it is clear that it isnt working properly,,also my resolution keeps being low,,and i cant raise it..how can i fix this?

---

### Post by itsvan on 2009-02-18
any ideas please????:o

---

### Post by HavocXphere on 2009-02-19
Well the driver clearly isn't working. Boht the low performance and the low resolution are a result of this.

What happens when you type this into a konsole:
> glxinfo | grep render
It should give you something like this:
> Havoc@Sphere:~$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: ATI Radeon HD 3850
Havoc@Sphere:~$
Except you'll have a different video card.

The kmix error suggests to me that the systen isn't up-to-date. The last time I've seen a kmix error was about 2 months ago and on a system thats pretty close to the 8.10 standard install without updates.

Before installing drivers, the system should be up-to-date.

I'm running ati gear so I can't help you fix the nvidia setup directly, but I can give you some commands to check whether everything is set up OK.

Another way to check whether the driver is installed correctly is to run:
> glxgears
and wait till you get a fps read-out in the konsole. That should be sky-high. On my system its ~6000fps. Not sure how powerful a Geforce7 is...but the count should be in the thousands at least. If glxgears does show you 3 colourful gears spinning or the fps count is <1000 then something is wrong with the setup.

Once the driver is sorted out, the resolution should also be available. If its not then you can try to force it....but I would recommend rather sorting out the driver first because if it runs slowly current on low res, then a higher res is going to be even worse.

Use at own risk:
[http://kubuntuforums.net/forums/index.php?topic=3100136.msg161401#msg161401](http://kubuntuforums.net/forums/index.php?topic=3100136.msg161401#msg161401)

---

### Post by itsvan on 2009-02-19
this is what i get

direct rendering: Yes
OpenGL renderer string: GeForce 7800 GT/PCI/SSE2
    GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod,



and yes gears do show up spinning

---

### Post by itsvan on 2009-02-19
17626 frames in 5.0 seconds = 3494.940 FPS
24540 frames in 5.0 seconds = 4907.991 FPS
24156 frames in 5.0 seconds = 4831.030 FPS
24692 frames in 5.0 seconds = 4938.371 FPS
XIO:  fatal IO error 22 (Invalid argument) on X server ":0.0"
      after 1384 requests (1384 known processed) with 0 events remaining.

and ya i do get the colorful gears spinning

how can i fix the drivers?

---

### Post by itsvan on 2009-02-19
this happens everytime i try to isntall a driver

Application: KMix (kmix), signal SIGABRT
0x00007f62406e06b0 in nanosleep () from /lib/libc.so.6

Thread 1 (Thread 0x7f6240df76f0 (LWP 5642)):
[KCrash Handler]
#5  0x00007f624066b015 in raise () from /lib/libc.so.6
#6  0x00007f624066cb83 in abort () from /lib/libc.so.6
#7  0x00007f623f3396b5 in qt_message_output () from /usr/lib/libQtCore.so.4
#8  0x00007f623f3397fd in qFatal () from /usr/lib/libQtCore.so.4
#9  0x00007f623fb93323 in ?? () from /usr/lib/libsolid.so.4
#10 0x00007f623fb93637 in ?? () from /usr/lib/libsolid.so.4
#11 0x00007f623f43e134 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#12 0x00007f623fba2cc2 in ?? () from /usr/lib/libsolid.so.4
#13 0x00007f623fbc592c in ?? () from /usr/lib/libsolid.so.4
#14 0x00007f623f089ea3 in ?? () from /usr/lib/libQtDBus.so.4
#15 0x00007f623f090eef in ?? () from /usr/lib/libQtDBus.so.4
#16 0x00007f623f438da5 in QObject::event () from /usr/lib/libQtCore.so.4
#17 0x00007f623e494c3d in QApplicationPrivate::notify_helper () from /usr/lib/libQtGui.so.4
#18 0x00007f623e49c9ba in QApplication::notify () from /usr/lib/libQtGui.so.4
#19 0x00007f624025f13b in KApplication::notify () from /usr/lib/libkdeui.so.5
#20 0x00007f623f429d61 in QCoreApplication::notifyInternal () from /usr/lib/libQtCore.so.4
#21 0x00007f623f42a9fa in QCoreApplicationPrivate::sendPostedEvents () from /usr/lib/libQtCore.so.4
#22 0x00007f623f4524d3 in ?? () from /usr/lib/libQtCore.so.4
#23 0x00007f623baf0d3b in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#24 0x00007f623baf450d in ?? () from /usr/lib/libglib-2.0.so.0
#25 0x00007f623baf46cb in g_main_context_iteration () from /usr/lib/libglib-2.0.so.0
#26 0x00007f623f45215f in QEventDispatcherGlib::processEvents () from /usr/lib/libQtCore.so.4
#27 0x00007f623e526a6f in ?? () from /usr/lib/libQtGui.so.4
#28 0x00007f623f428682 in QEventLoop::processEvents () from /usr/lib/libQtCore.so.4
#29 0x00007f623f42880d in QEventLoop::exec () from /usr/lib/libQtCore.so.4
#30 0x00007f623f42acbd in QCoreApplication::exec () from /usr/lib/libQtCore.so.4
#31 0x00007f62409c652a in kdemain () from /usr/lib/libkdeinit4_kmix.so
#32 0x00007f6240656466 in __libc_start_main () from /lib/libc.so.6
#33 0x0000000000400659 in _start ()

---

### Post by HavocXphere on 2009-02-20
Well the driver appears to be installed OK.

Check under System-settings->Desktop->advanced settings->compositing type. Make sure this is set to Opengl and a bit below that:
Texture from pixmap
bilineral
direct rendering=ON

> XIO: fatal IO error 22 (Invalid argument) on X server ":0.0"
No too sure what that means....but its not ideal.

On the whole, I'd say that its not necessarily a video issue.

I'd say start by updating the system to the newest available updates...they KDE code was very buggy in the beginning and they've fixed a lot of stuff since the original 8.10 cd was released.

Unfortunately, if its not a video issue then it could be a lot of things. I'd start by running memtest for half a day or so to make sure that the system as a whole is stable. This will also show if something is overheating...which could cause lagging too.

The laggy behaviour and freezes could also be a bad harddrive.

---

### Post by Ben Page on 2009-02-20
Why not try Kubuntu 9.04 Jaunty instead? Kubuntu 8.10 is a very buggy OS, at least with 173 - 177 nvidia drivers. Search for how to install 180 drivers in 8.10, or just download 9.04 and the "hardware drivers" thingy will install them by default (180.29) and KDE4.2 witch is mutch better and faster than KDE 4.1 on 177 drivers in Kubuntu 8.10

---

### Post by 3rdalbum on 2009-02-20
Kubuntu 9.04 is months away from being ready; give it a miss for the moment.

I'd recommend installing the latest Nvidia driver from Nvidia.com. There are known issues with the stock Ubuntu Nvidia driver and KDE 4.

---

### Post by itsvan on 2009-02-21
al off those tabs where already set to the exact specifics that you said,,its weird cuse it seems like it is fine but the resoultion is just ridiclous,,,its way to low,,and it wont give me options to set higher ones,,could this have anything to do with the detection of my monitor? or what i dont get what is going on? ive pretty much tried everything so far..shucks.....

---

### Post by itsvan on 2009-02-21
how do i install the new drivers,,im really new at all of that...because i know in windows you just download it and install it,,here it has to be done differently right?

---

