---
title: "Clique HUE HD Webcam"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by Sirchristopher on 2008-12-20
So I bought this Clique HUE HD Webcam from [www.woot.com](www.woot.com) and I don't know how to get it to work.  When I type 'lsusb' I get 

Bus 005 Device 003: ID 0c45:6282 Microdia Audio (Microphone)
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

If I unplug it the 'Bus 005 Device 003: ID 0c45:6282 Microdia Audio (Microphone)' goes away so I know that is the camera but I can't make it work.  Any help is greatly appreciated.

---

### Post by anderlan on 2008-12-22
I'm in the same boat as you, gah.  Same camera, same website.  So anyway, I'll apply my bowstaff-camera skills and let you know if I have any success with it.

---

### Post by gcvisel on 2008-12-24
> **anderlan said:**
> I'm in the same boat as you, gah.  Same camera, same website.  So anyway, I'll apply my bowstaff-camera skills and let you know if I have any success with it.

   I got wooted too.  Any assistance would be appreciated!  I can see its audio side, but not the video.

Thanx!

(Don't work over Christmas though!)

Spook

---

### Post by go_beep_yourself on 2009-01-02
Try this. I read it worked for someone with a Hue in Inteprid.

[http://groups.google.com/group/microdia/web/testing-microdia-driver-draft?pli=1](http://groups.google.com/group/microdia/web/testing-microdia-driver-draft?pli=1)

---

### Post by go_beep_yourself on 2009-01-02
I managed to get mine working, but it doesn't display right. I'm posting a screenshot. The module I got from compiling is sn9c20x.ko not microdia.ko, and I had to take a few extra steps to get it working in 64-bit 8.10.

---

### Post by go_beep_yourself on 2009-01-06
Has anyone else managed to get theirs working? I finally was able to get the built-in microphone working with Skype.

---

### Post by wangrui on 2009-01-06
By the following link

[http://groups.google.com/group/microdia/web/testing-microdia-driver-draft?pli=1](http://groups.google.com/group/microdia/web/testing-microdia-driver-draft?pli=1)

I almost got it work in both i386 hardy and AMD64 hardy.

I compile the source code and insert the module. No problem in i386 and AMD64.
But when I start the camera with the code

```
	fmt.type = V4L2_BUF_TYPE_VIDEO_CAPTURE;
	fmt.fmt.pix.width = width;
	fmt.fmt.pix.height = height;
	fmt.fmt.pix.pixelformat = pixelformat; //V4L2_PIX_FMT_MJPEG; //V4L2_PIX_FMT_YUYV;
	fmt.fmt.pix.field = V4L2_FIELD_NONE; //V4L2_FIELD_INTERLACED;

```

I always got an 640x480 picture no matter what the width and height is. And about pixelformat, the driver report the following supported formats

```
Bayer 8bit (BGGR)
I420 (YUV 4:2:0)
YUYV (YUV 4:2:0)
JPEG (YUV 4:2:2)

```

I got the following two formats working
```
V4L2_PIX_FMT_JPEG
V4L2_PIX_FMT_YUYV
```

For V4L2_PIX_FMT_JPEG format, the driver returns a gray JPEG picture with a fixed exposure. So it's impossible to see anything in the night because the exposure is not enough. I guess it's because the driver hasn't be able to adjust the exposure settings yet. And the driver also can't change the camera mode to show colored picture.

For V4L2_PIX_FMT_YUYV format, the driver return an 614400 bytes data for each frame. But the data is definitely not a YUV4:2:2 format. I haven't figure out how to decode it yet. There is no libv4l in hardy repository which may able to decode the frame.

The driver is still in the developing stage. I guess someone will keep improving the driver. These people are so nice.

---

### Post by wangrui on 2009-01-07
> **go_beep_yourself said:**
> I managed to get mine working, but it doesn't display right. I'm posting a screenshot. The module I got from compiling is sn9c20x.ko not microdia.ko, and I had to take a few extra steps to get it working in 64-bit 8.10.

Actually the name is correct. I opened the camera body today. The circuit said SN9C202AFC.

---

### Post by Veenified on 2009-01-26
Has there been any progress on getting this driver improved? What can I do to help?

I'm trying to get it to work with skype. Currently, my video looks bad. Attached is a screen capture of how my video looks when I run:
```
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so mplayer tv://     -tv driver=v4l2:width=640:height=480:fps=25:device=/dev/video0 -vo x11
```

---

### Post by Veenified on 2009-02-04
I ran:
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so camorama
```

... and I am getting video that looks like the attached.

If it helps I am getting only this relevant entry when I run lsusb:
```
Bus 002 Device 005: ID 0c45:6282 Microdia Audio (Microphone)
```

Can someone please help?

---

### Post by go_beep_yourself on 2009-03-06
I read there is a patch you can apply to the driver on one of the alsa mailing lists. You many have to search the mailing list archives.

---

### Post by rustutzman on 2009-03-06
The Hue camera is now working great for me. You need to get the driver from [http://groups.google.com/group/microdia](http://groups.google.com/group/microdia) Use git to download the files then build the driver, and install it. It really is easy to do.

I have it working in Cheese, aMSN, and mplayer. Just follow their instructions and read the readme files and you'll have it working in no time.

Russ

---

### Post by go_beep_yourself on 2009-03-13
> **rustutzman said:**
> The Hue camera is now working great for me. You need to get the driver from [http://groups.google.com/group/microdia](http://groups.google.com/group/microdia) Use git to download the files then build the driver, and install it. It really is easy to do.

I have it working in Cheese, aMSN, and mplayer. Just follow their instructions and read the readme files and you'll have it working in no time.

Russ

For me, it works for aMSN, mplayer, and Skype. I'll try it with motion soon. It does not work with cheese or camorama. Could someone help me get it working for those?

---

### Post by juny20 on 2009-05-20
I just got a new HUE HD WEBCAM, green color (only color for the price from tigerdirect.com). I was able to get it to work by following the instructions listed here:
[http://www.linuxquestions.org/questions/linux-software-2/hue-hd-web-cam-driver-installation-700724/](http://www.linuxquestions.org/questions/linux-software-2/hue-hd-web-cam-driver-installation-700724/)

I tried Cheese and it worked. I need to figure out sound? I will try Skype next.

One thing; when I use the based, the camera does not work in Cheese. However, when I plug it directly on the USB port, it works...

---

### Post by anderlan on 2010-07-24
With 10.04 Lucid Lynx, HUE Clique HD webcam works.  lsusb shows 
Bus 00X Device 00X: ID 0c45:6282 Microdia PC Camera with Microphone (SN9C202 + MI1310)
Skype tests video successfully.  Resolution may not be maximum native of the camera, but it is close.

---

### Post by UltraAnders on 2010-07-29
Nice one, looking to get a webcam and this is on the list. What sort of resolution do you get? Do you think the cam is any good?

---

### Post by juny20 on 2010-12-04
Just following up on this issue...
**With Ubuntu 10.10**, the camera was recognized instantly with absolutely no issues!

It works on Cheese and Skype perfectly fine.
The resolution is good. I use Skype in full screen mode on a 19" lcd and the image is good. 

It is a very inexpensive camera and works very good. The one thing is that I thought there was an integrated microphone (it looks like there is), but for Skype, I had to connect my external microphone, which is not a big deal. Just sharing this in case someone is still thinking about getting one of this Clique HUE webcam.

---

### Post by manche on 2011-01-31
juny20, or anyone else with this camera working out of the box with 10.10, could you please tell us which module is loaded for it and what the dmesg looks like when you plug it in?

In my case, the audio seems to work fine, but I don't get video. I have gotten it to work in the past on another machine with the Microdia driver mentioned earlier in this thread. I'm wondering if the Ubuntu driver is the same one or a better one.

---

