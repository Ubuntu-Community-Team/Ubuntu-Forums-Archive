---
title: "Working webcam"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by mmichielin on 2009-08-17
Hi,
I'm looking for a webcam COMPLETELY working with ubuntu 9.04.
Completely means:
- skype (first of all)
- camorama
- cheese
- ekiga

I've seen a lot of confusion about webcams and since I have 3 (three) different webcams none of which is completely working with ubuntu 9.04, I'm asking is somebody out there HAVE and USE a webcam with all that applications.

The webcams I have are:
- philips spc200nc (0471:0325)
- Creative Technology, Ltd Live! Cam Video IM Pro (041e:4055)
- Logitech XXX (I cannot check the ID since I gave it to a friend)

Please, does anyone HAVE a webcam that really works with ubuntu 9.04?

Thanks in advance

---

### Post by Nate Shoffner on 2009-08-17
I've heard the Logitech Quickcam Pro 9000 is really good.  I currently have a Microsoft Lifecam VX-1000 and have had no luck with it.  Don't really have the money to buy a new one right now..kinda bummed.  So I have to switch back to Windows just to use my web cam.

---

### Post by mmichielin on 2009-08-17
Thanks for the answer.
But I don't want to buy the fourth useless webcam so I'll wait until somebody answer me:

"I have this webcam and it works perfectly".

Thanks

---

### Post by zerhacke on 2009-08-17
> **mmichielin said:**
> Hi,

- philips spc200nc (0471:0325)

[http://ubuntuforums.org/showpost.php?p=789821&postcount=10](http://ubuntuforums.org/showpost.php?p=789821&postcount=10)

---

### Post by mmichielin on 2009-08-18
SPC200NC works out of the box with cheese but not with Skype in Ubuntu 9.04.
I need a webcam working with cheese AND with skype.
Thanks

---

### Post by acron1 on 2009-08-18
> **mmichielin said:**
> SPC200NC works out of the box with cheese but not with Skype in Ubuntu 9.04.
I need a webcam working with cheese AND with skype.
Thanks

I too would like to know of a web cam that's fully compatible with Ubuntu 9.04. Anyone?

---

### Post by whitethorn on 2009-08-18
I have a quickcam pro 9000.  

Skype, cheese, luvcview work.  Ekiga worked on 8.10 haven't tried it on 9.04.  As for camorama I haven't tried it.  If you give me till tomorrow, I'll let you know.

---

### Post by acron1 on 2009-08-18
> **whitethorn said:**
> I have a quickcam pro 9000.  

Skype, cheese, luvcview work.  Ekiga worked on 8.10 haven't tried it on 9.04.  As for camorama I haven't tried it.  If you give me till tomorrow, I'll let you know.

That's great! Does it have a built-in mic?

---

### Post by whitethorn on 2009-08-18
> **acron1 said:**
> That's great! Does it have a built-in mic?

Yes it does have a mic (I use it as a mic and webcam in skype), I tried out camorama it didn't work for me.  So pretty much everything else works except for camorama.  I'm really satisfied with the webcam, only thing I wish it had was the same logitech program as in windows with the cool avatars and stuff.  Maybe someday...

---

### Post by mmichielin on 2009-08-19
> **whitethorn said:**
> I have a quickcam pro 9000.  

Skype, cheese, luvcview work.  Ekiga worked on 8.10 haven't tried it on 9.04.  As for camorama I haven't tried it.  If you give me till tomorrow, I'll let you know.

Thanks.
Can you post "lsusb" output?

I post the same question in the italian forum and I discovered that these webcams are told to work very well:
- 046d:08da Logitech, Inc. QuickCam Messanger
- Logitech Quickcam Sphere
- Keyteck WCAM-630

PS: I have a "046d:08f6 Logitech Quickcam Messenger Plus" and it dows NOT work

---

### Post by 3rdalbum on 2009-08-19
I'd be interested too, in one that works in Flash Player (as well as Skype).

---

### Post by whitethorn on 2009-08-19
> **mmichielin said:**
> Thanks.
Can you post "lsusb" output?

I post the same question in the italian forum and I discovered that these webcams are told to work very well:
- 046d:08da Logitech, Inc. QuickCam Messanger
- Logitech Quickcam Sphere
- Keyteck WCAM-630

PS: I have a "046d:08f6 Logitech Quickcam Messenger Plus" and it dows NOT work

```

john:~$ lsusb
Bus 002 Device 011: ID 046d:0990 Logitech, Inc. QuickCam Pro 9000
Bus 002 Device 010: ID 03f0:2e24 Hewlett-Packard 
Bus 002 Device 005: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 005: ID 1532:0007 Razer USA, Ltd DeathAdder Mouse
Bus 006 Device 004: ID 046d:c316 Logitech, Inc. HID-Compliant Keyboard
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by callan79 on 2009-08-19
> **mmichielin said:**
> Hi,
Please, does anyone HAVE a webcam that really works with ubuntu 9.04?



Hi mmichielin,

I have a Logitech E3500. Works fine in Skype and Cheese. Not with Camorama though.

Output from lsusb is 'Bus 001 Device 002: ID 046d:09a4 Logitech, Inc."

Cheers
Callan

---

### Post by whitethorn on 2009-08-19
> **3rdalbum said:**
> I'd be interested too, in one that works in Flash Player (as well as Skype).

Have a look at this, especially the last post.  I'm gonna give it a try tomorrow and post results.

[http://ubuntuforums.org/showthread.php?t=637595](http://ubuntuforums.org/showthread.php?t=637595)

---

### Post by mangurt on 2009-08-19
I know the webcam that came with my laptop (dell inspiron) works perfectly with 9.04.  If I could figure out how to bring up what type of web cam it is, I would post it.

---

### Post by mmichielin on 2009-08-20
> If I could figure out how to bring up what type of web cam it is, I would post it.

- open a terminal
- enter the command:
```
lsusb
```
- post here the output

thanks a lot

(but if it's an embedded webcam I don't think I can but it)

---

### Post by 3rdalbum on 2009-08-20
> **whitethorn said:**
> Have a look at this, especially the last post.  I'm gonna give it a try tomorrow and post results.

[http://ubuntuforums.org/showthread.php?t=637595](http://ubuntuforums.org/showthread.php?t=637595)

I tried it about 6 months ago and nada. Maybe I'll give it another go one of these days.

---

### Post by mangurt on 2009-08-20
My web cam is embedded :(

---

### Post by Keith_Beef on 2009-08-23
I have a Logitech webcam.
```
$ lsusb
Bus 001 Device 006: ID 046d:0991 Logitech, Inc. QuickCam Pro for Notebooks

```
No luck with camorama...
"Could not connect to video device (/dev/video0).
However,
```
$ ls -al /dev/video0 
crw-rw----+ 1 root video 81, 0 2009-08-22 23:58 /dev/video0
```

I set up an Ekiga account, and it worked. Until I changed the size of the capture image, then Ekiga complained that "[my] driver doesn't seem to support any of the color formats supported by Ekiga".
```
$ ekiga
libv4l2: error setting pixformat: Input/output error
libv4l2: error setting pixformat: Input/output error
libv4l2: error setting pixformat: Input/output error
libv4l2: error setting pixformat: Input/output error
```

The cure seems to be:
[LIST=1]
[*]quit Ekiga,
[*]unplug the webcam,
[*]plug the webcam in again,
[*]restart Ekiga.
[/LIST]

I can't get camorama working though, yet.

From the error that Ekiga was reporting, I thought I might have better luck if I pointed camorama at a v4l device... but that is just a link back to /dev/video0 anyway.

```
$ ls -al /dev/v4l/by-id/
total 0
drwxr-xr-x 2 root root 60 2009-08-23 00:26 .
drwxr-xr-x 4 root root 80 2009-08-23 00:26 ..
lrwxrwxrwx 1 root root 12 2009-08-23 00:26 usb-046d_0991_1CE82929-video-index0 -> ../../video0
```

```
$ camorama -D

VIDIOCGCAP
device name = UVC Camera (046d:0991)
device type = 1
can use mmap()
# of channels = 1
# of audio devices = 0
max width = 960
max height = 720
min width = 48
min height = 32

VIDIOCGWIN
x = 0
y = 0
width = 176
height = 144
chromakey = 0
flags = 0

VIDIOCGWIN
x = 0
y = 0
width = 352
height = 288
chromakey = 0
flags = 0

VIDIOCGPICT:
bright = 32896
hue = 0
colour = 8224
contrast = 8224
whiteness = 0
colour depth = 16
YUYV
VIDIOCGMBF  --  could not set buffer info, exiting...
```

So, camorama does indeed detect the device, 
```
VIDIOCGCAP
device name = UVC Camera (046d:0991)
```

But, from reading another thread...

[http://ubuntuforums.org/showpost.php?p=4299269&postcount=22](http://ubuntuforums.org/showpost.php?p=4299269&postcount=22)

it looks like camorama will no longer work, since the camorama app doesn't work with v4l2, which is what is grabbing the webcam stream.

However, from reading the reviews that Talon linked to, below, it looks like there *is* a way to get v4l apps working.
> uvcvideo support under linux is v4l2, doesn't work natively with v4l apps (camstream, Flash <=10, vlc) unless you redirect it through videoloop loopback device (this is not really the cameras fault I suppose, but choices made by the linux developers).

Not sure how you'd do this, though... I've not heard of a videoloop device, though from its name I imaging you'd use it in a similar way to the way you can use a loopback device to mount an ISO960 image file as if it were a CD in the drive... so mount the v4l2 uvcvideo device as a v4l device.

More info is here:
[http://www.lavrsen.dk/foswiki/bin/view/Motion/VideoFourLinuxLoopbackDevice](http://www.lavrsen.dk/foswiki/bin/view/Motion/VideoFourLinuxLoopbackDevice)
but I've not read and digested it, yet.

Good news: cheese works just fine!

K.

---

### Post by Talon2 on 2009-08-23
> **acron1 said:**
> I too would like to know of a web cam that's fully compatible with Ubuntu 9.04. Anyone?

I have one like [this]("http://www.newegg.com/Product/ProductReview.aspx?Item=N82E16826104252").

---

### Post by mmichielin on 2009-08-24
> **callan79 said:**
> Hi mmichielin,

I have a Logitech E3500. Works fine in Skype and Cheese. Not with Camorama though.

Output from lsusb is 'Bus 001 Device 002: ID 046d:09a4 Logitech, Inc."

Cheers
Callan

Thanks to callan79 now I have a working webcam with ubuntu 9.04 (works very good with cheese, skype, ekiga).
I'm very happy.
Thanks everybody

---

