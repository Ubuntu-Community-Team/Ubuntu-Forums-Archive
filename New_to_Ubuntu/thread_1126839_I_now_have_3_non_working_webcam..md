---
title: "I now have 3 non working webcam."
date: 2009-04-15
forum: New to Ubuntu
---

### Post by LostMagix on 2009-04-15
```
:~$ lsusb
Bus 001 Device 007: ID 0ad2:9314 Service & Quality Technology Co., Ltd 
Bus 001 Device 006: ID 0545:8002 Xirlink, Inc. IBM NetCamera
Bus 001 Device 004: ID 046d:0870 Logitech, Inc. QuickCam Express
```

I have been trying to get a MI web cam working in 8.10 for months, never even got close so I gave up on that.  Tried for a about week to get a IBM Netcam working but failed once more.  After I cooled down for a day and forgot about the whole ordeal I was given a quickcam which shown promise as first but ended up even more of a failure!!

So I updated to 9.04.....lo and behold, it didn't help one bit.  I have never been so frustrated in my life!!

Do other people have these problems or is it just that the Linux gods hate me?

---

### Post by spiderbatdad on 2009-04-15
well not totally normal. What applications are you trying to use webcam with? skype, cheese?

---

### Post by LostMagix on 2009-04-15
everyone I could find

cheese
camstream
luvcview
ekiga
camorama
xawtv
gqcam
the list goes on and on

---

### Post by spiderbatdad on 2009-04-15
2 of your cams are clearly recognized.
can you post:
```
lsmod
```we'll see what modules you have loaded for driving the cams.

---

### Post by LostMagix on 2009-04-15
```
:~$ lsmod
Module                  Size  Used by
snd_usb_audio          90400  0 
snd_usb_lib            24320  1 snd_usb_audio
snd_hwdep              15108  1 snd_usb_audio
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    58144  1 vfat
ibmcam                 55760  0 
usbvideo               33924  1 ibmcam
binfmt_misc            16776  1 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
video                  25360  0 
output                 11008  1 video
coretemp               13952  0 
w83627ehf              26888  0 
hwmon_vid              11264  1 w83627ehf
lp                     17156  0 
snd_hda_intel         435508  5 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82820  4 snd_usb_audio,snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
quickcam               78628  0 
videodev               41600  2 usbvideo,quickcam
v4l1_compat            21764  1 videodev
pcspkr                 10496  0 
snd                    62628  20 snd_usb_audio,snd_hwdep,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i82975x_edac           12292  0 
nvidia               7233756  36 
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
edac_core              47404  1 i82975x_edac
agpgart                42696  1 nvidia
usbhid                 42336  0 
ppdev                  15492  0 
parport_pc             40100  1 
parport                42220  3 lp,ppdev,parport_pc
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
e1000e                121136  0 
floppy                 64324  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
```

---

### Post by spiderbatdad on 2009-04-15
lets try this:
```
sudo modprobe uvcvideo
```unplug cam and plug in again.

try to launch cheese like this:
```
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so cheese
```

---

### Post by tom66 on 2009-04-15
Can you find anything in dmesg about webcams and sensors or video4linux (v4l or v4l2)?

---

### Post by LostMagix on 2009-04-15
the IBM and logitech both get

```
:~$ LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so cheese
cheese: ../../src/xcb_io.c:176: process_responses: Assertion `!(req && current_request && !(((long) (req->sequence) - (long) (current_request)) <= 0))' failed.
Aborted (core dumped)

```

The MI get no outputs

---

### Post by spiderbatdad on 2009-04-15
did modprobe work?
do you now have uvcvideo listed in lsmod?
also check package manager for v4l-0 v4l-dev

---

### Post by Twitch6000 on 2009-04-15
That quickcam should work I have one myself and it works just fine.

You are probably missing a file to read the camera/s correctly.

---

### Post by LostMagix on 2009-04-15
> **tom66 said:**
> Can you find anything in dmesg about webcams and sensors or video4linux (v4l or v4l2)?

Not really...

```
[  259.593984] usb 1-2.2: USB disconnect, address 4
[  259.594344] usb 1-2.3: USB disconnect, address 5
[  259.594716] usb 1-2.4: USB disconnect, address 6
[  264.344020] usb 1-2: new high speed USB device using ehci_hcd and address 7
[  264.477333] usb 1-2: configuration #1 chosen from 1 choice
[  264.477675] hub 1-2:1.0: USB hub found
[  264.478003] hub 1-2:1.0: 4 ports detected
[  264.748283] usb 1-2.2: new full speed USB device using ehci_hcd and address 8
[  264.840939] usb 1-2.2: configuration #1 chosen from 1 choice
[  264.841164] quickcam: QuickCam USB camera found (driver version QuickCam USB 0.6.6 $Date: 2006/11/04 08:38:14 $)
[  264.841168] quickcam: Kernel:2.6.28-11-generic bus:1 class:FF subclass:FF vendor:046D product:0870
[  264.842989] quickcam: Sensor HDCS-1020 detected
[  264.843275] quickcam: Registered device: /dev/video0
[  264.916349] usb 1-2.3: new full speed USB device using ehci_hcd and address 9
[  265.009000] usb 1-2.3: configuration #1 chosen from 1 choice
[  265.080280] usb 1-2.4: new high speed USB device using ehci_hcd and address 10
[  265.184695] usb 1-2.4: configuration #1 chosen from 1 choice

```


After I

```
:~$ sudo modprobe uvcvideo
:~$ sudo modprobe ibmcam

``` 

this come out of dmesg

```
[  578.394083] usbcore: registered new interface driver uvcvideo
[  578.394088] USB Video Class driver (v0.1.0)
[  587.747647] usb 1-2.3: IBM NetCamera USB camera found (model 4, rev. 0x030a)
[  587.747712] usb 1-2.3: ibmcam on /dev/video1: canvas=352x288 videosize=352x288
[  587.747739] usbcore: registered new interface driver ibmcam
[  587.770952] usbvideo: usbvideo_StartDataPump: usb_submit_isoc(0) ret -28
[  587.770973] usbvideo: usbvideo_StartDataPump: usb_submit_isoc(1) ret -28

```

---

### Post by LostMagix on 2009-04-15
> **spiderbatdad said:**
> did modprobe work?
do you now have uvcvideo listed in lsmod?
also check package manager for v4l-0 v4l-dev

```
:~$ lsmod
Module                  Size  Used by
ibmcam                 55760  0 
usbvideo               33924  1 ibmcam
uvcvideo               63240  0 
compat_ioctl32          9344  1 uvcvideo
binfmt_misc            16776  1 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
video                  25360  0 
output                 11008  1 video
coretemp               13952  0 
w83627ehf              26888  0 
hwmon_vid              11264  1 w83627ehf
lp                     17156  0 
snd_usb_audio          90400  0 
snd_usb_lib            24320  1 snd_usb_audio
snd_hwdep              15108  1 snd_usb_audio
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_hda_intel         435508  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
nvidia               7233756  36 
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_pcm                82820  3 snd_usb_audio,snd_hda_intel,snd_pcm_oss
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_timer              29704  2 snd_seq,snd_pcm
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
i82975x_edac           12292  0 
ppdev                  15492  0 
parport_pc             40100  1 
parport                42220  3 lp,ppdev,parport_pc
usbhid                 42336  0 
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
edac_core              47404  1 i82975x_edac
agpgart                42696  1 nvidia
snd                    62628  17 snd_usb_audio,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_seq,snd_pcm,snd_seq_device,snd_timer
soundcore              15200  1 snd
quickcam               78628  0 
videodev               41600  3 usbvideo,uvcvideo,quickcam
v4l1_compat            21764  2 uvcvideo,videodev
pcspkr                 10496  0 
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
e1000e                121136  0 
floppy                 64324  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

```

synaptic has v4l-0 or v4l-dev listed as installed.. kinda

A Qsearch in synaptic has libpt-1.10.10-plugins-v4l2, libpt2.4.2-plugins-v4l2, libv4l-0, v4l-conf, xserver-xorg-video-v4l as install


```
:~$ v4l-conf
v4l-conf: using X11 display :0.0
dga: version 2.0
WARNING: No DGA direct video mode for this display.
mode: 1024x768, depth=24, bpp=32, bpl=4096, base=unknown
/dev/video0 [v4l2]: ioctl VIDIOC_QUERYCAP: Unknown error 515
/dev/video0 [v4l]: no overlay support


:~$ sudo v4l-info /dev/video0

### video4linux device info [/dev/video0] ###
general info
    VIDIOCGCAP
	name                    : "Logitech QuickCam USB"
	type                    : 0x201 [CAPTURE,SUBCAPTURE]
	channels                : 1
	audios                  : 0
	maxwidth                : 352
	maxheight               : 292
	minwidth                : 32
	minheight               : 32

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
	whiteness               : 32768
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
	height                  : 292
	chromakey               : 0
	flags                   : 524288

:~$ sudo v4l-info /dev/video1

### video4linux device info [/dev/video1] ###
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
	contrast                : 49152
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

### Post by LostMagix on 2009-04-15
> **Twitch6000 said:**
> That quickcam should work I have one myself and it works just fine.

You are probably missing a file to read the camera/s correctly.

Is it the same model?

```
:~$ lsusb
Bus 001 Device 010: ID 0ad2:9314 Service & Quality Technology Co., Ltd 
Bus 001 Device 009: ID 0545:8002 Xirlink, Inc. IBM NetCamera
Bus 001 Device 008: ID 046d:0870 Logitech, Inc. QuickCam Express
```

I am on a fresh install of 9.04 as of right now.

I tried all 3 on 8.10 also, same box, with no luck.

---

### Post by Twitch6000 on 2009-04-15
> **LostMagix said:**
> Is it the same model?

```
:~$ lsusb
Bus 001 Device 010: ID 0ad2:9314 Service & Quality Technology Co., Ltd 
Bus 001 Device 009: ID 0545:8002 Xirlink, Inc. IBM NetCamera
Bus 001 Device 008: ID 046d:0870 Logitech, Inc. QuickCam Express
```

I am on a fresh install of 9.04 as of right now.

I tried all 3 on 8.10 also, same box, with no luck.

Yes infact it is.

I would suggest reinstalling the v4l-0 v4l-dev files and then using cheese.

That same webcam worked for me on Ubuntu 9.04,Mint 6 ,PClinuxOS2009,and Siltaz so I am sure it should work for you.

---

### Post by spiderbatdad on 2009-04-15
still not sure. would have expected to see a driver listed from v4l-info like:
```
### v4l2 device info [/dev/video0] ###
general info
    VIDIOC_QUERYCAP
	driver                  : "uvcvideo"
	card                    : "USB 2.0 Camera"
	bus_info                : "0000:00:1d.1"
	version                 : 0.1.0
	capabilities            : 0x4000001 [VIDEO_CAPTURE,STREAMING]


```

Try restarting with just one camera plugged in?

---

### Post by LostMagix on 2009-04-15
> **Twitch6000 said:**
> Yes infact it is.

I would suggest reinstalling the v4l-0 v4l-dev files and then using cheese.

That same webcam worked for me on Ubuntu 9.04,Mint 6 ,PClinuxOS2009,and Siltaz so I am sure it should work for you.

reinstall did nothing, cheese sees the quickcam but not the IBM, no output in terminal.

camstream sees both the quickcam and the IBM but still no video, output here, quickcam first:

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
D: >> CVideoDevice::CVideoDevice()
D: << CVideoDevice::CVideoDevice()
D: >> CVideoDeviceLinux::CVideoDeviceLinux(/dev/video1)
D: << CVideoDeviceLinux::CVideoDeviceLinux()
>> CCamWindow::CCamWindow(QWidget*, const char*)
<< CCamWindow::CCamWindow(QWidget*, const char*)
>> CWebCamViewer::CWebCamViewer(CVideoDevice*, QWidget*, const char*)
  >> QDomNode CCamStreamApp::FindVideoDeviceConfig(const QString&, const QString&, bool)
    Trying to find video options for Logitech QuickCam USB@/dev/video0
    D: Creating new node for Logitech QuickCam USB@/dev/video0
  << QDomNode CCamStreamApp::FindVideoDeviceConfig(const QString&, const QString&, bool)
  >> CVideoOptions::CVideoOptions()
    >> virtual void CVideoOptions::DeclareVariables()
    << virtual void CVideoOptions::DeclareVariables()
  << CVideoOptions::CVideoOptions()
  D: CSnapshotSettingsDlg::CSnapshotSettingsDlg(...)
  W: QFont::setWeight: Value out of range (100)
  D: >> CVideoDeviceLinux::Init()
  W: Cannot query audio capabilities of video device.
  D: Using mmap(), size = 426240
  D: mmap()ed 1 buffers.
  D: Initial image size = (176, 144)
  D: << CVideoDeviceLinux::Init()
  D: CVideoSettingsDlg::SizeChanged(176x144)
  D: CVideoSettingsDlg::FramerateChanged(10)
  D: No Philips webcam detected, removing extension tab
  D: CCamPanel::SetSize(176x144)
  D: CCamPanel::SetImageSize(176x144)
  D: CCamPanel::SetVisibleSize(176x144)
  D: CCamPanel::SetSize(176x144)
  D: CCamPanel::SetImageSize(176x144)
  D: CCamPanel::SetVisibleSize(176x144)
  >> void CWebCamViewer::RecalcTotalViewSize()
  << void CWebCamViewer::RecalcTotalViewSize()
<< CWebCamViewer::CWebCamViewer(CVideoDevice*, QWidget*, const char*)
D: >> CVideoDevice::IncrementPalette(0)
D: >> CVideoDeviceLinux::StartCapture()
D: CVideoDeviceLinux::SetPalette picked palette 5 [rgb32]
D: >> CVideoDeviceLinux::CreateImagesRGB()
D: << CVideoDeviceLinux::CreateImagesRGB()
D: >> CVideoDeviceLinux::run()...
D: << CVideoDeviceLinux::StartCapture()
D: << CVideoDevice::IncrementPalette()

```

now the IBM

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
D: >> CVideoDevice::CVideoDevice()
D: << CVideoDevice::CVideoDevice()
D: >> CVideoDeviceLinux::CVideoDeviceLinux(/dev/video1)
D: << CVideoDeviceLinux::CVideoDeviceLinux()
>> CCamWindow::CCamWindow(QWidget*, const char*)
<< CCamWindow::CCamWindow(QWidget*, const char*)
>> CWebCamViewer::CWebCamViewer(CVideoDevice*, QWidget*, const char*)
  >> QDomNode CCamStreamApp::FindVideoDeviceConfig(const QString&, const QString&, bool)
    Trying to find video options for IBM USB Camera@/dev/video1
    D: Creating new node for IBM USB Camera@/dev/video1
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

### Post by LostMagix on 2009-04-15
> **spiderbatdad said:**
> 
Try restarting with just one camera plugged in?

tried that, it didn't do any good.

---

### Post by spiderbatdad on 2009-04-15
lets try cheese once more like this

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese
```

---

### Post by LostMagix on 2009-04-15
this is right, isnt it?

[IMG]http://i105.photobucket.com/albums/m231/crazy_monkey_ninja/Screenshot-9.png[/IMG]

---

### Post by LostMagix on 2009-04-15
> **spiderbatdad said:**
> lets try cheese once more like this

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese
```

my system halted, after reboot i tried again and got nothing accept this output after i closed cheese:

```
:~$ LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so cheese

(cheese:3776): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(cheese:3776): GStreamer-CRITICAL **: gst_object_unref: assertion `object != NULL' failed

(cheese:3776): GStreamer-CRITICAL **: gst_object_unref: assertion `object != NULL' failed

```

---

### Post by spiderbatdad on 2009-04-15
i have the libpt plugins installed

---

### Post by spiderbatdad on 2009-04-15
> **LostMagix said:**
> my system halted, after reboot i tried again and got nothing accept this output after i closed cheese:

```
:~$ LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so cheese

(cheese:3776): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(cheese:3776): GStreamer-CRITICAL **: gst_object_unref: assertion `object != NULL' failed

(cheese:3776): GStreamer-CRITICAL **: gst_object_unref: assertion `object != NULL' failed

```
 HMMM. you didnt use the same command ie, v4l2convert.so vs. v4l1compat.so

---

### Post by LostMagix on 2009-04-15
> **spiderbatdad said:**
> HMMM. you didnt use the same command ie, v4l2convert.so vs. v4l1compat.so

still no good

---

### Post by LostMagix on 2009-04-15
> **spiderbatdad said:**
> i have the libpt plugins installed

i'm gonna try and match yours and see what come of it

---

### Post by LostMagix on 2009-04-15
> **LostMagix said:**
> i'm gonna try and match yours and see what come of it

no good and my system is becoming unstable

---

### Post by LostMagix on 2009-04-15
I'm gonna go take a breather, clear my head a little bit.

---

### Post by spiderbatdad on 2009-04-15
If all else fails you can try compiling a patched gspca driver for the quickcam. I used the following guide several months ago and got mine working...since then, I have changed cams and got another laptop (acer aspire) with built in cam...both worked "out of the box."

Anyway this is the guide by actionshrimp...its a bit of a moderate to advanced user guide...and I actually ended up using comments posted by sweeper November 14th, 2008 at 1:19 pm (second comment he/she makes)
[http://www.actionshrimp.com/2008/08/logitech-quickcam-e2500-on-ubuntu-skype/#comment-1317](http://www.actionshrimp.com/2008/08/logitech-quickcam-e2500-on-ubuntu-skype/#comment-1317)

sorry this is giving you such a problem.

---

### Post by LostMagix on 2009-04-15
> **spiderbatdad said:**
> If all else fails you can try compiling a patched gspca driver for the quickcam. I used the following guide several months ago and got mine working...since then, I have changed cams and got another laptop (acer aspire) with built in cam...both worked "out of the box."

Anyway this is the guide by actionshrimp...its a bit of a moderate to advanced user guide...and I actually ended up using comments posted by sweeper November 14th, 2008 at 1:19 pm (second comment he/she makes)
[http://www.actionshrimp.com/2008/08/logitech-quickcam-e2500-on-ubuntu-skype/#comment-1317](http://www.actionshrimp.com/2008/08/logitech-quickcam-e2500-on-ubuntu-skype/#comment-1317)

sorry this is giving you such a problem.

Ill give it a shot but i don't think its the driver, [THIS PAGE]("http://www.linux-usb.org/ibmcam/") claims the driver for the IBM Netcam I have is build into the kernel and we know from twitches post that the Logitech Quickcam i have is compatible also.  To think that two cams, both known to work in Linux, would have the same problem with different drivers is hard to believe. The MI ZOOM im not that worried about, I never expected it to be supported in the first place.

As of right now it seems like v4l is the issue here, but I could be wrong.

---

### Post by spiderbatdad on 2009-04-15
yeah I saw that page on the ibm cam and followed to sourceforge to look for a driver...the project has not actually released one yet...and apparently many of the ibm net cams do not work on linux. As for the quickcam...again there are several models that use the name quick cam...you would need to know if he is using ID 046d:0870 Logitech, Inc. QuickCam Express  by ID #.
Best of luck. I hope you get it working soon. I know its a drag right now. Sure you'll get one working soon.

---

### Post by spiderbatdad on 2009-04-15
Some IBM NetCameras are not supported. They simply do not work. They share the same USB identification (0545:8002:030A)

---

### Post by LostMagix on 2009-04-15
grr, what cant everyone just use UVC, this is some BS!!

---

### Post by Twitch6000 on 2009-04-15
Okay you say cheese picks up the logitech?

By picks it up you mean your face shows up on the screen or the camera just lights up?

Anyways this is seeming more like a distro problem then anything else.

If you can try a livecd of a more up to date distro like opensuse and see if your cam works on it.

If it does then we can then report the problem.

If it doesn't then it is something else.

---

### Post by LostMagix on 2009-04-15
> **Twitch6000 said:**
> Okay you say cheese picks up the logitech?

By picks it up you mean your face shows up on the screen or the camera just lights up?

Anyways this is seeming more like a distro problem then anything else.

If you can try a livecd of a more up to date distro like opensuse and see if your cam works on it.

If it does then we can then report the problem.

If it doesn't then it is something else.

It will show up in the menu but i get no video:

[IMG]http://i105.photobucket.com/albums/m231/crazy_monkey_ninja/Screenshot-1-2.png[/IMG]

Ill go get a copy of opensuse and see if it works

---

### Post by Twitch6000 on 2009-04-15
while you are download opensuse try running cheese like this.

I was looking on the help files and google and found this.

run cheese through the terminal as  cheese qcset /dev/video0 compat=dblbuf

or qcset /dev/video0 compat=dblbuf cheese

I am not sure which way to put that in the terminal,but it might fix your problem.

Edit: also since it is being detected try this, in the terminal type gstreamer-properties

Then go to video settings and fiddle with them and see if that helps at all.

---

### Post by LostMagix on 2009-04-15
cheese qcset /dev/video0 compat=dblbuf fails to grab a image

and the other i get this:

```
:~$ qcset /dev/video0 compat=dblbuf cheese
2
qcset: invalid configuration name

```

---

### Post by Twitch6000 on 2009-04-15
> **LostMagix said:**
> cheese qcset /dev/video0 compat=dblbuf fails to grab a image

and the other i get this:

```
:~$ qcset /dev/video0 compat=dblbuf cheese
2
qcset: invalid configuration name

```

Well only one of those were the correct way to put it in the terminal :P.

Anyways try the gstreamer thing that might fix your problem. I know it has been known to fix slowness with others.

---

### Post by LostMagix on 2009-04-15
well this isnt right

```
:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'

```

so its not v4l, its gstreamer!!

we are getting closer, I can almost taste it!!

---

### Post by LostMagix on 2009-04-15
enabling jaunty-backport and jaunty-proposed is a bust

[http://ubuntuforums.org/showthread.php?t=1025992]("http://ubuntuforums.org/showthread.php?t=1025992")

---

### Post by Twitch6000 on 2009-04-15
> **LostMagix said:**
> well this isnt right

```
:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'

```

so its not v4l, its gstreamer!!

we are getting closer, I can almost taste it!!


Yes it does that to me aswell that is no shocker(ofcourse right now I wish it was...).

However after these messages does a menu come up with the gstreamer prefrences?

If so click video then plugin then choose x11/xshm/xv

This might fix your problem.

---

### Post by LostMagix on 2009-04-15
> **Twitch6000 said:**
> Yes it does that to me aswell that is no shocker(ofcourse right now I wish it was...).

However after these messages does a menu come up with the gstreamer prefrences?

If so click video then plugin then choose x11/xshm/xv

This might fix your problem.

No menu but I am reinstalling everything to do with gstreaming via synaptic and then i will run it again and see what comes out.

---

### Post by LostMagix on 2009-04-15
no menu :(

---

### Post by Twitch6000 on 2009-04-15
> **LostMagix said:**
> no menu :(

Humm then it just might be a distro problem.

Atleast this is what it seems like.

Once you get OpenSuse downloaded tryout the livecd or try it out on a virtual machine and if it works on OpenSuse problem solved.

If not ... then I have no idea what to do lol...

Edit: if anyone else wants to step in and help out go ahead I am running out of ideas here.

---

### Post by LostMagix on 2009-04-15
Alright i got the menu after a nether reboot!!


It wont let me test, it just locks up.

I took a look in dmesg and found something unsettiling

```
[  132.721771] Modules linked in: binfmt_misc bridge stp bnep input_polldev video output coretemp w83627ehf hwmon_vid lp snd_usb_audio snd_hda_intel snd_usb_lib snd_pcm_oss snd_mixer_oss snd_hwdep snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device i82975x_edac iTCO_wdt snd nvidia(P) quickcam ppdev iTCO_vendor_support snd_page_alloc soundcore edac_core agpgart videodev v4l1_compat pcspkr parport_pc parport usbhid ohci1394 ieee1394 e1000e floppy fbcon tileblit font bitblit softcursor
[  132.721820] 
[  132.721824] Pid: 3936, comm: gstreamer-prope Tainted: P           (2.6.28-11-generic #37-Ubuntu) MS-7246
[  132.721827] EIP: 0060:[<c02c7f26>] EFLAGS: 00210002 CPU: 1
[  132.721831] EIP is at kref_get+0x6/0x30
[  132.721833] EAX: 0000022c EBX: 0000022c ECX: 00000002 EDX: 00000198
[  132.721835] ESI: ea67e400 EDI: fffffffe EBP: ea7a9d94 ESP: ea7a9d90
[  132.721838]  DS: 007b ES: 007b FS: 00d8 GS: 0000 SS: 0068
[  132.721841] Process gstreamer-prope (pid: 3936, ti=ea7a8000 task=ea411920 task.ti=ea7a8000)
[  132.721843] Stack:
[  132.721845]  00000210 ea7a9da0 c02c71d2 0000013c ea7a9da8 c034c0f3 ea7a9db4 c03b19f2
[  132.721853]  00200296 ea7a9dc8 c03b7560 ea67e400 e181a000 c08777e0 ea7a9df0 c03b875f
[  132.721861]  00000000 00000000 00001388 f5d25400 f61216c8 f5e1c000 e181a000 f6abbaa0
[  132.721869] Call Trace:
[  132.721871]  [<c02c71d2>] ? kobject_get+0x12/0x20
[  132.721875]  [<c034c0f3>] ? get_device+0x13/0x20
[  132.721881]  [<c03b19f2>] ? usb_get_dev+0x12/0x20
[  132.721886]  [<c03b7560>] ? usb_hcd_unlink_urb+0x30/0x90
[  132.721889]  [<c03b875f>] ? usb_kill_urb+0x5f/0xf0
[  132.721895]  [<f7e3094f>] ? qc_isoc_stop+0x2f/0x100 [quickcam]
[  132.721902]  [<c015385c>] ? down+0x2c/0x40
[  132.721907]  [<f7e30aef>] ? qc_v4l_close+0x4f/0xa0 [quickcam]
[  132.721913]  [<c01be904>] ? __fput+0xb4/0x1c0
[  132.721918]  [<c01bea2f>] ? fput+0x1f/0x30
[  132.721922]  [<c01bb429>] ? filp_close+0x49/0x70
[  132.721926]  [<c027c280>] ? exit_sem+0x180/0x1d0
[  132.721932]  [<c013bd96>] ? put_files_struct+0x66/0xb0
[  132.721937]  [<c013be23>] ? exit_files+0x43/0x60
[  132.721940]  [<c013d8e0>] ? do_exit+0x160/0x330
[  132.721944]  [<c013dae0>] ? do_group_exit+0x30/0xa0
[  132.721948]  [<c0147a7b>] ? get_signal_to_deliver+0x17b/0x390
[  132.721952]  [<c01a42ac>] ? vma_link+0x7c/0x90
[  132.721957]  [<c0103d81>] ? do_notify_resume+0x91/0x190
[  132.721966]  [<c0503008>] ? unlock_kernel+0x28/0x2f
[  132.721971]  [<c01ca080>] ? vfs_ioctl+0x80/0x90
[  132.721976]  [<c01ca50e>] ? do_vfs_ioctl+0x5e/0x200
[  132.721980]  [<c01ca6f7>] ? sys_ioctl+0x47/0x70
[  132.721983]  [<c0104130>] ? work_notifysig+0x13/0x23
[  132.721987] Code: 1b e7 ff eb cd ba 40 00 00 00 b8 b0 0b 62 c0 e8 71 1b e7 ff eb bc eb 0d 90 90 90 90 90 90 90 90 90 90 90 90 90 55 89 e5 53 89 c3 <8b> 00 85 c0 74 06 f0 ff 03 5b 5d c3 ba 2b 00 00 00 b8 b0 0b 62 
[  132.722032] EIP: [<c02c7f26>] kref_get+0x6/0x30 SS:ESP 0068:ea7a9d90
[  132.722039] ---[ end trace fc71b2f176b84794 ]---
[  132.722041] Fixing recursive fault but reboot is needed!

```

the system now locks up when i try to reboot

---

### Post by LostMagix on 2009-04-16
I am done for the night..

Thanks for all your help so far!

---

### Post by iponeverything on 2009-04-16
LostMagix -- I reading though this thread, I have to give you an A+ for tenacity.

---

### Post by LostMagix on 2009-04-16
> **iponeverything said:**
> LostMagix -- I reading though this thread, I have to give you an A+ for tenacity.

Thanks you!

I appreciate the complement.

---

### Post by LostMagix on 2009-04-16
The opensuse live boot didnt see the cams, i didnt play around with it that much however.

So im trying 

```
gstreamer-properties

```

the menu came up

changing the output to X11/XShm/Xv did nothing, none of the other setting for output are doing anything ether

I get a test scraneteactedeen for "test input" (go figure) but with vl4 and v4l2 the cam is seen as unknown, This seems to be fixed with 

```
sudo modprobe uvcvideo
sudo modprobe uvcvideo
```

I can now see both cams in the menu but the test locks up as soon as it is started.

I try to close the gstreamer-properties windows and my system crashes

---

### Post by Twitch6000 on 2009-04-16
Humm and you did this on Ubuntu 9.04 correct?

I think for now you should downgrade to 8.10 or use OpenSuse.

Only reason why I am saying this is so we know you have a stable system.

As you have already said you are starting to crash alot.

---

### Post by LostMagix on 2009-04-16
> **Twitch6000 said:**
> Humm and you did this on Ubuntu 9.04 correct?

I think for now you should downgrade to 8.10 or use OpenSuse.

Only reason why I am saying this is so we know you have a stable system.

As you have already said you are starting to crash alot.

well I started this whole ordeal in 8.10, I just upgraded a few days ago.

Its only crashing when I modprobe and try to use the cams, my system is 100% stable other wise.

---

### Post by Twitch6000 on 2009-04-16
> **LostMagix said:**
> well I started this whole ordeal in 8.10, I just upgraded a few days ago.

Its only crashing when I modprobe and try to use the cams, my system is 100% stable other wise.

My bad I misunderstood then.

Back to step one then...

Well since you have been trying cheese the most try camstudio it works a bit different then cheese so it might work.

Also try engima or whatever that calling program is called.

If one of those work say which.

If none of those work then I am out of ideas =[.

---

### Post by LostMagix on 2009-04-16
I cant seem to find anything but .exe for camstudio

---

### Post by Twitch6000 on 2009-04-16
> **LostMagix said:**
> I cant seem to find anything but .exe for camstudio

shoot did I say camstudio... I meant camorama lol.

Sorry my head goes off into different worlds sometimes lol.

---

### Post by LostMagix on 2009-04-16
camorama sees the cam but no video and i couldn't find the other program.

---

### Post by LostMagix on 2009-04-16
Im out of ideas so im gonna go see if any of my micro$oft buddys want to trade cams, hopefully i can get a working one.

---

### Post by Twitch6000 on 2009-04-16
> **LostMagix said:**
> camorama sees the cam but no video and i couldn't find the other program.

I didn't type the other name correctly,it is installed on ubuntu by default.

It should be in the internet apps or something.

Its a program like skype.

---

### Post by LostMagix on 2009-04-16
ekiga?

tried that allready

---

### Post by LostMagix on 2009-04-16
lol, I just drive 20 miles to pick up a diffrent cam..

```
Bus 001 Device 024: ID 046d:0870 Logitech, Inc. QuickCam Express
Bus 001 Device 023: ID 046d:0870 Logitech, Inc. QuickCam Express

```

god must not want me to have a webcam

---

### Post by Twitch6000 on 2009-04-17
*bumping thread*

Okay it seems your camera is detected its just being used incorrectly somehow.

You could try a reinstall to see if this fixes the problem.(not likely)

Or you could look for a newer version of gstreamer then what is in the repos.

---

### Post by LostMagix on 2009-04-17
I guess this quickcam used to work fine in damper, but something made the driver unusable, I am looking for more documentation on it right now.

---

### Post by LostMagix on 2009-04-18
*bump

---

