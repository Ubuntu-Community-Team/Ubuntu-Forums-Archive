---
title: "Webcam driver for Ubuntu"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by TomErwin on 2009-01-30
Hello everybody..
I have a problem with my USB webcam. 
My webcam is "sw1000" (I have no more details, not even a brand name), I have the webcam CD with the windows driver. it works perfectly on Windows. 
But when I connect it on Skype. nothing happens at all... 
and when I open System>Administration>Hardware Drivers, it says NO PROPRIETARY DRIVERS ARE IN USE ON THIS SYSTEM if this means something.
I am on Ubuntu 8.04...
Thank you for taking the time to read... :)

---

### Post by sumit.kalra999 on 2009-01-30
Hi,

install "cheese" package for webcam  and get it run. It works on Ubuntu8.04. I'm using it.

---

### Post by ratmandall on 2009-01-31
If you don't know how to install cheese, then open up a terminal

Applcations-->Accessories-->Terminal.
And type
```

sudo apt-get install cheese
```

---

### Post by Crafty Kisses on 2009-01-31
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2) To test your webcam you can do this:

There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly. If Ekiga doesn't work post the results of the following command:```
lsusb
```

---

### Post by TomErwin on 2009-01-31
Thank you very much. I did not know about Cheese, but this seems like a very nice program. when my Camera works I'll give it a try. :)

---

### Post by TomErwin on 2009-01-31
Well. Thank you very much for understanding my problem. I have tried Ekiga and I can see the bouncing logo. and in the preferences, the video device is not detected.

I have tried the command you have given me. and here is the result:

Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 06a2:6810 Topro Technology, Inc. 
Bus 001 Device 001: ID 0000:0000  

Thank you so much for your time  :)

---

### Post by waldir on 2009-05-21
I have the same camera, and coudln't manage to get it working either. Also, [post 861851]("http://ubuntuforums.org/showthread.php?t=861851") points to [http://www.qbik.ch/usb/devices/showdev.php?id=4378](http://www.qbik.ch/usb/devices/showdev.php?id=4378)
Unfortunately, that page says there's no driver available...

Plus, a [google search for "06a2:6810"]("http://www.google.com/search?q=06a2:6810") returns some interesting results (including this thread), even though I found none of them to be of practical use if you just want to get the camera working. But most probably if there ever happens to be a driver developed for this camera, that query should reveal it.

---

### Post by souptafied on 2010-02-01
try here
[http://stemp.wordpress.com/2009/11/03/karmic-get-the-latest-drivers-for-gspca-uvc-usbvideo-and-other/](http://stemp.wordpress.com/2009/11/03/karmic-get-the-latest-drivers-for-gspca-uvc-usbvideo-and-other/)

---

### Post by J V on 2010-02-01
ok, lets start with cheese: All cheese does is show you your camera, thats all. No drivers or whatnot...

Second, windows drivers won't work on linux

Third, webcams work out of the box on linux (yes all of them, there are standards for webcams and usb...)

Fourth: Check your skype settings

---

### Post by no2498 on 2010-02-01
do  this open a terminal type (gstreamer-properties) click enter
try v4l1 or v4l2
click the bottom test button

---

### Post by niffcreature on 2010-02-01
> **J V said:**
> ok, lets start with cheese: All cheese does is show you your camera, thats all. No drivers or whatnot...

Second, windows drivers won't work on linux

Third, webcams work out of the box on linux (yes all of them, there are standards for webcams and usb...)

Fourth: Check your skype settings

the only reason they work out of the box is because they are built in kernel modules and v4l is installed, right? 
so if a user has installed new kernel modules or v4l is not functioning correctly, then it wont work. 
i love and hate how everything is so connected in linux. im trying to learn because no one understands my specific issue. can i ask here if v4l and v4l2 ONLY exist for webcams??

---

### Post by sbelz79 on 2010-05-18
OK, so I've been having problems with my new webcam in Skype.  It's a Creative Live! Socialize HD.  I tried this:

> **no2498 said:**
> do  this open a terminal type (gstreamer-properties) click enter
try v4l1 or v4l2
click the bottom test button

And the test worked fine.  Cheese works fine.  In chatroulette I can see my video, but due to Flash problems I can't actually connect with anyone.  I can take pictures and videos with my Webcam in Facebook and upload them.  However, when I try to run a test of my camera in Skype (by going to Options>Video Devices and clicking "Test."  The correct webcam is listed), I get the following output:

```
X Error, request 133, minor 18, error code 8 BadMatch (invalid parameter attributes) 
X Error, request 133, minor 18, error code 8 BadMatch (invalid parameter attributes) 
X Error, request 133, minor 18, error code 8 BadMatch (invalid parameter attributes) 
X Error, request 133, minor 18, error code 8 BadMatch (invalid parameter attributes) 
X Error, request 133, minor 18, error code 8 BadMatch (invalid parameter attributes) 
X Error, request 133, minor 18, error code 8 BadMatch (invalid parameter attributes) 
X Error, request 133, minor 18, error code 8 BadMatch (invalid parameter attributes) 
X Error, request 133, minor 18, error code 8 BadMatch (invalid parameter attributes) 
X Error, request 133, minor 18, error code 8 BadMatch (invalid parameter attributes) 
X Error, request 133, minor 18, error code 8 BadMatch (invalid parameter attributes) 
X Error, request 133, minor 18, error code 8 BadMatch (invalid parameter attributes) 
X Error, request 133, minor 18, error code 8 BadMatch (invalid parameter attributes) 
X Error, request 133, minor 18, error code 8 BadMatch (invalid parameter attributes) 
```

Under the advice of another thread, I opened Skype using the following command:
```
bash -c 'LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype'

```
getting the same result and output.

Help, please.

---

### Post by Stemp on 2010-06-19
> **sbelz79 said:**
> 
```
bash -c 'LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype'

```

```
LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so skype
```

---

### Post by Karyzma on 2010-08-15
> **J V said:**
> ok, lets start with cheese: All cheese does is show you your camera, thats all. No drivers or whatnot...

Second, windows drivers won't work on linux

Third, webcams work out of the box on linux (yes all of them, there are standards for webcams and usb...)

Fourth: Check your skype settings

Can you help me as I am unable to get my webcam to work.  I am using a Gear Head USB Motor Track 2.0 webcam.  I tried getting the windows drivers for it. [**_Here_**]("http://pcgearheadsupport.com/ghs/detail.php?item_id=25")
They didn't work.  I am kinda newb still to Linux so I was wondering if I could get some help.  I really like this webcam.   I am running Lucid.

---

### Post by Gudkisser79 on 2010-08-19
> **no2498 said:**
> do  this open a terminal type (gstreamer-properties) click enter
try v4l1 or v4l2
click the bottom test button

this one comes out on the terminal....

don@don-desktop:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Device "/dev/video0" does not exist. [v4l_calls.c(16: gst_v4l_open (): /GstPipelineipeline0/GstV4lSrc:v4lsrc1]
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Cannot identify device '/dev/video0'. [v4l2_calls.c(48: gst_v4l2_open (): /GstPipelineipeline1/GstV4l2Src:v4l2src1:
system error: No such file or directory]
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Cannot identify device '/dev/video0'. [v4l2_calls.c(48: gst_v4l2_open (): /GstPipelineipeline2/GstV4l2Src:v4l2src2:
system error: No such file or directory]
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Device "/dev/video0" does not exist. [v4l_calls.c(16: gst_v4l_open (): /GstPipelineipeline3/GstV4lSrc:v4lsrc2]
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Cannot identify device '/dev/video0'. [v4l2_calls.c(48: gst_v4l2_open (): /GstPipelineipeline4/GstV4l2Src:v4l2src3:
system error: No such file or directory]
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Cannot identify device '/dev/video0'. [v4l2_calls.c(48: gst_v4l2_open (): /GstPipelineipeline7/GstV4l2Src:v4l2src4:
system error: No such file or directory]

(gstreamer-properties:258: GLib-GObject-WARNING **: invalid cast from `GtkBuilder' to `GtkWidget'

(gstreamer-properties:258: Gtk-CRITICAL **: gtk_widget_get_screen: assertion `GTK_IS_WIDGET (widget)' failed





I've already tried this one...and i have cheese on my ubuntu 10.04 but still my USB WEBCAM is not functioning. CAT is the name of my webcam ( i guess that's generic?) . can somebody help me?

---

### Post by Stemp on 2010-08-19
> **Gudkisser79 said:**
> I've already tried this one...and i have cheese on my ubuntu 10.04 but still my USB WEBCAM is not functioning. CAT is the name of my webcam ( i guess that's generic?) . can somebody help me?

The name of your webcam is not really helpfull, you need to show us the result of 2 commands :

```
lsusb
```
To get the id of your cam

```
lsmod | grep video
```
To see if there is a webcam module.

---

### Post by Karyzma on 2010-08-19
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 006: ID 2770:930b NHJ, Ltd CCD Webcam(PC370R)
Bus 002 Device 005: ID 04d9:2013 Holtek Semiconductor, Inc. 
Bus 002 Device 004: ID 1532:000c Razer USA, Ltd 
Bus 002 Device 003: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 002 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



video                  17375  1 i915
output                  1871  1 video

---

### Post by Stemp on 2010-08-19
Ok, this webcam is now supported by the gspca sq930x driver.
It's a bit new so it's not in Ubuntu 10.04.
In order to get it, you need to compile a new gspca version.
You may try with this post : [Gspca Snapshot]("http://stemp.wordpress.com/2010/05/17/gspca-snapshot/")
Good luck ;)

---

### Post by Karyzma on 2010-08-19
I went to that link.  Did all of the commands.  When he started talking about replacing spaces with M's I got lost.  Also all of the screenshots looked nothing like what I was working with.

---

### Post by Stemp on 2010-08-19
Can you provide a screenshot of what you have ?
Because the screenshots in the post are clearly .config Linux Kernel Configuration ;)

---

### Post by primitivling on 2010-09-04
Hey Stemp, I also have a webcam that I can't get to work. I got the webcam as a gift from siemens about 2 years ago and it says skype, intel and broadxent sw 1000 on it. I am a complete Ubuntu Beginner and have barely ever worked with the terminal. In Ekiga I only get the bouncing icon. Both skype and Ekiga don't seem to know that there's a webcam plugged into my USB..

my results to lsub are:

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 06a2:6810 Topro Technology, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

and for lsmod | grep video:

video                  17375  1 i915
output                  1871  1 video

would be great if you could help me get this work so i can chat with my girlfriend..

---

### Post by Stemp on 2010-09-04
Hi primitivling,

```
Bus 003 Device 003: ID 06a2:6810 Topro Technology, Inc. 
```

AFAIK there is NO working drivers for topro webcams :(

There is an untested and unusable driver at [http://code.google.com/p/tp68xx-webcam-drv/](http://code.google.com/p/tp68xx-webcam-drv/) (and it's not even for your cam)

Sorry.

---

### Post by mikilion on 2010-09-28
> **Karyzma said:**
> I went to that link.  Did all of the commands.  When he started talking about replacing spaces with M's I got lost.  Also all of the screenshots looked nothing like what I was working with.

Hi,
try the latest GSPCA test drivers by [Jean-François Moine]("http://moinejf.free.fr/").

Download and unpack this [gspca-2.10.18.tar.gz]("http://moinejf.free.fr/gspca-2.10.18.tar.gz")
From console move in dir and type:
```
make
sudo make install
```

Reboot and use your cam.

---

### Post by Stemp on 2010-12-24
The webcam 06a2:6810 was just added to the gspca tp6800 driver in [gspca-2.11.11]("http://moinejf.free.fr/gspca-2.11.11.tar.gz") !

---

### Post by nsrikant on 2011-07-24
Hi Everybody

I have Ubuntu 11.04 installed. My Quantum webcam ZC0301 does not work in ubuntu though it works perfectly on Windows XP and Windows 7 out of the box without having to install any drivers from the accompanying CD.
The accompanying CD of this WEBCAM includes an old Linux driver for Kernel 2.4.. . 
Can this be adopted to work on Ubuntu 11.04?

Would appreciate any advise.

---

### Post by no2498 on 2011-07-24
open a terminal type lsusb click enter
type lsmod | grep video click enter
type dmesg click enter
close the terminal
look in your package manager for xawtv install it
try the cam in xawtv first

---

### Post by redwheelbarrow on 2011-09-19
```
modprobe gspca_sq930x 
```

If it doesn't work right out of the box.

---

### Post by jockyburns on 2011-09-20
Sorry if I appear to be hijacking this thread, but,,, I have a problem with skype. I can't start my webcam. It works with Cheese,however. Last night on a Skype call to my dad, the only way I could get the video to work was to open Cheese webcam booth and then share my screen with my dad. Surely this can't be right though?
I'm running ubuntu 11.04 and have Skype installed I do receive video from my dad and other callers though.

Thanks

JB

PS I have already posted about this problem , but haven't had any replies so far .

---

### Post by no2498 on 2011-09-20
look in your system start up programs
look for any webcam programs that come on as you restart the computer
turn them off and restart the computer

---

### Post by madjr on 2011-09-20
> **jockyburns said:**
> Sorry if I appear to be hijacking this thread, but,,, I have a problem with skype. I can't start my webcam. It works with Cheese,however. Last night on a Skype call to my dad, the only way I could get the video to work was to open Cheese webcam booth and then share my screen with my dad. Surely this can't be right though?
I'm running ubuntu 11.04 and have Skype installed I do receive video from my dad and other callers though.

Thanks

JB

PS I have already posted about this problem , but haven't had any replies so far .

is not very good to hijack threads.

you should at least post a link to yours.

anyway, there are many quick fixes on the net about your issue, it has nothing to do with drivers (because other apps already recognize it).

is a skype bug. You should file a bug report on the skype website or add yourself to one of the reports, so they can finally fix the issue for you.

if you want a temporary quick fix, google something like: *skype not recognizing webcam on ubuntu*

---

### Post by nothingspecial on 2011-09-20
You have a thread here

[http://ubuntuforums.org/showthread.php?t=1846894](http://ubuntuforums.org/showthread.php?t=1846894)

Closed

---

