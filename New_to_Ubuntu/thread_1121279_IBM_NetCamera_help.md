---
title: "IBM NetCamera help"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by LostMagix on 2009-04-09
Well a few days ago my friend gave me this really cool old school IBM Netcam and i have been trying to get it to work right...

I have hit a few dead ends so I came here in hopes that someone might be able to help out.


```

:~$lsusb
Bus 005 Device 005: ID 0545:8002 Xirlink, Inc. IBM NetCamera

:~$ sudo modprobe ibmcam
:~$ sudo lsmod | grep ibm
ibmcam                 55504  0 
usbvideo               32900  1 ibmcam
usbcore               149488  8 ibmcam,usbvideo,usb_storage,libusual,usbhid,ehci_hcd,uhci_hcd


:~$ ls /dev/video
ls: cannot access /dev/video: No such file or directory

:~$ dmesg
[ 5229.616844] Linux video capture interface: v2.00
[ 5229.636103] ibmcam: IBM NetCamera USB camera found (model 4, rev. 0x030a)
[ 5229.637024] videodev: "ibmcam USB Camera" has no release callback. Please fix your driver for proper sysfs support, see http://lwn.net/Articles/36850/
[ 5229.637029] usbvideo: ibmcam on /dev/video0: canvas=352x288 videosize=352x288
[ 5229.638685] usbcore: registered new interface driver ibmcam


```

no video at all :(

---

### Post by LostMagix on 2009-04-10
*bump

---

### Post by LostMagix on 2009-04-10
*bump

---

### Post by LostMagix on 2009-04-10
Whats this?

```
:~$  cat < /dev/video0 > foo.dat
bash: /dev/video0: Cannot allocate memory

```


also I noticed that /var/log/syslog is coming back with a lot or errors like this

```
Apr 10 14:13:15 lost-desktop kernel: [64951.904659] Write-error on swap-device (254:0:405880)
Apr 10 14:13:15 lost-desktop kernel: [64951.904700] compcache: Error allocating memory for compressed page: 50599, size=578
```

Whats happening, Im know something is wrong but im over my head with this.

---

### Post by LostMagix on 2009-04-10
FYI I am using this:

[http://conshell.net/wiki/index.php/User:Fostermarkd/IBM_PC_Camera]("http://conshell.net/wiki/index.php/User:Fostermarkd/IBM_PC_Camera")

---

### Post by LostMagix on 2009-04-11
*bump

---

### Post by LostMagix on 2009-04-12
*bump


I have seen thread where people have got it working but none of them have given a link or said how it was done.

From what i have read the driver is built into the kernel, I don't know why its not working.

---

### Post by LostMagix on 2009-04-12
Whats going on here?

```
:~$ cat < /dev/video0 > foo.dat
bash: /dev/video0: Cannot allocate memory
```


/var/log/syslog

Apr 10 14:13:15 lost-desktop kernel: [64951.904659] Write-error on swap-device (254:0:405880)
Apr 10 14:13:15 lost-desktop kernel: [64951.904700] compcache: Error allocating memory for compressed page: 50599, size=578

---

### Post by LostMagix on 2009-04-12
I got the cam to be seen under camstream but still no video

Output:

```
:~$ camstream
W: CamStream version 0.27 starting.
>> void CCamStreamApp::ReadConfigFile()
<< void CCamStreamApp::ReadConfigFile()
D: CVideoCollector::VideoCollector()
D: >> CVideoDevice::CVideoDevice()
D: << CVideoDevice::CVideoDevice()
D: >> CVideoDeviceLinux::CVideoDeviceLinux(/dev/video0)
D: << CVideoDeviceLinux::CVideoDeviceLinux()
>> CCamWindow::CCamWindow(QWidget*, const char*)
<< CCamWindow::CCamWindow(QWidget*, const char*)
>> CWebCamViewer::CWebCamViewer(CVideoDevice*, QWidget*, const char*)
  >> QDomNode CCamStreamApp::FindVideoDeviceConfig(const QString&, const QString&, bool)
    Trying to find video options for IBM USB Camera@/dev/video0
    D: Creating new node for IBM USB Camera@/dev/video0
  << QDomNode CCamStreamApp::FindVideoDeviceConfig(const QString&, const QString&, bool)
  >> CVideoOptions::CVideoOptions()
    >> virtual void CVideoOptions::DeclareVariables()
    << virtual void CVideoOptions::DeclareVariables()
  << CVideoOptions::CVideoOptions()
  D: CSnapshotSettingsDlg::CSnapshotSettingsDlg(...)
  W: QFont::setWeight: Value out of range (100)
  D: >> CVideoDeviceLinux::Init()
  W: Cannot query audio capabilities of video device.
  D: Using mmap(), size = 608256
  D: mmap()ed 2 buffers.
  W: Failed to restore image size (176, 144)
  D: Initial image size = (352, 288)
  D: << CVideoDeviceLinux::Init()
  D: CVideoSettingsDlg::SizeChanged(352x288)
  D: CVideoSettingsDlg::FramerateChanged(10)
  D: No Philips webcam detected, removing extension tab
  D: CCamPanel::SetSize(352x288)
  D: CCamPanel::SetImageSize(352x288)
  D: CCamPanel::SetVisibleSize(352x288)
  D: CCamPanel::SetSize(352x288)
  D: CCamPanel::SetImageSize(352x288)
  D: CCamPanel::SetVisibleSize(352x288)
  >> void CWebCamViewer::RecalcTotalViewSize()
  << void CWebCamViewer::RecalcTotalViewSize()
<< CWebCamViewer::CWebCamViewer(CVideoDevice*, QWidget*, const char*)
D: >> CVideoDevice::IncrementPalette(0)
D: >> CVideoDeviceLinux::StartCapture()
D: CVideoDeviceLinux::SetPalette picked palette 4 [rgb24]
D: >> CVideoDeviceLinux::CreateImagesRGB()
D: << CVideoDeviceLinux::CreateImagesRGB()
D: >> CVideoDeviceLinux::run()...
D: << CVideoDeviceLinux::StartCapture()
D: << CVideoDevice::IncrementPalette()


```

---

### Post by LostMagix on 2009-04-12
```

:~$ ls /dev/video
ls: cannot access /dev/video: No such file or directory
:~$ ls /dev/video0
/dev/video0

```

---

### Post by LostMagix on 2009-04-12
cat /dev/video0 foo.dat

its not giving me an output for some reason.

---

### Post by LostMagix on 2009-04-12
gqcam recognizes the camera also, but no video

the status bar is on "speed-calculating"

---

### Post by LostMagix on 2009-04-13
Any input at all would be greatly appreciated.

My brain is turning into mush and I feel no closer to solving this

---

### Post by LostMagix on 2009-04-13
*bump

---

### Post by LostMagix on 2009-04-13
I been talking to myself for 3 days in here, I need some help here!!



I can see the camera fine now. but I am not getting a stream.

---

### Post by LostMagix on 2009-04-13
other linux forums tell me to check "/proc/bus/usb/devices" but it does not exist on my system, where else might it be?

---

### Post by LostMagix on 2009-04-13
I thinking its a problem with v4l, so here is a few outputs for it:

```
:~$ v4l-conf
v4l-conf: using X11 display :0.0
dga: version 2.0
WARNING: No DGA direct video mode for this display.
mode: 1024x768, depth=24, bpp=32, bpl=4096, base=unknown
/dev/video0 [v4l2]: ioctl VIDIOC_QUERYCAP: Invalid argument
/dev/video0 [v4l]: no overlay support

:~$ v4l-info

### video4linux device info [/dev/video0] ###
general info
    VIDIOCGCAP
	name                    : "IBM USB Camera"
	type                    : 0x1 [CAPTURE]
	channels                : 1
	audios                  : 0
	maxwidth                : 352
	maxheight               : 288
	minwidth                : 8
	minheight               : 4

channels
    VIDIOCGCHAN(0)
	channel                 : 0
	name                    : "Camera"
	tuners                  : 0
	flags                   : 0x0 []
	type                    : CAMERA
	norm                    : 0

tuner
ioctl VIDIOCGTUNER: Invalid argument

audio
ioctl VIDIOCGAUDIO: Invalid argument

picture
    VIDIOCGPICT
	brightness              : 32768
	hue                     : 32768
	colour                  : 32768
	contrast                : 32768
	whiteness               : 26880
	depth                   : 24
	palette                 : RGB24

buffer
    VIDIOCGFBUF
	base                    : (nil)
	height                  : 0
	width                   : 0
	depth                   : 0
	bytesperline            : 0

window
    VIDIOCGWIN
	x                       : 0
	y                       : 0
	width                   : 352
	height                  : 288
	chromakey               : 0
	flags                   : 4294967295
```

---

### Post by LostMagix on 2009-04-13
I give up.

/thread

---

### Post by LostMagix on 2009-04-14
One more try!!


I found [this]("https://help.ubuntu.com/community/Webcam") page which suggested I try a programs called luvcview to check the cam, here is the output.

:~$ luvcview
luvcview 0.2.4

SDL information:
  Video driver: x11
  A window manager is available
Device information:
  Device path:  /dev/video0
Error opening device /dev/video0: unable to query device.
 Init v4L2 failed !! exit fatal

---

### Post by LostMagix on 2009-04-15
Thats kinda cold, I have been talking to myself in this thread for 5 days...

---

### Post by LostMagix on 2009-04-15
How about this, what webcam can I get for under $30 that WILL work with 9.04

---

### Post by kokapui on 2009-06-08
I has the same issue on this webcam - (lsusb)

   Bus 002 Device 006: ID 0545:8080 Xirlink, Inc. IBM C-It WebCam

and I noticed the following message in syslog -

   usbvideo: usbvideo_StartDataPump: usb_submit_isoc(0) ret -28

does this sound like an issue from ibmcam.ko?

kko

---

### Post by kokapui on 2009-06-08
I have the same issue on this webcam - (lsusb)

   Bus 002 Device 006: ID 0545:8080 Xirlink, Inc. IBM C-It WebCam

and I noticed the following message in syslog -

   usbvideo: usbvideo_StartDataPump: usb_submit_isoc(0) ret -28

does this sound like an issue from ibmcam.ko?

kko

---

