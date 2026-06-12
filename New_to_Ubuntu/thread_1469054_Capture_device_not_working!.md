---
title: "Capture device not working!"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by racie on 2010-05-01
Hello, I followed the instructions to install this driver: [http://sourceforge.net/projects/easycapdc60/](http://sourceforge.net/projects/easycapdc60/)
I did not receive any error messages during the install.

However, the device is still not recognized in Camorama (could not connect to /dev/video0) and Pitivi Video Editor.  How do I fix this?

---

### Post by anewguy on 2010-05-02
With the adapter plugged into a USB port, do this in a terminal and post back here:

- lsusb -v <press enter> -> post the output back here

- lsmod <press enter> -> post the output back here


I don't know a thing about this adapter, but took a quick look at the link you provided and determined this is a specific USB video adapter with sound.  If the driver from sourceforge did indeed install, we should see it in the output from lsmod.  I want the lsusb -v (verbose, more information) to be sure we're dealing with the correct device, the device is getting mounted properly, etc.

I will try help the best I can after that information.

Dave ;)

---

### Post by racie on 2010-05-02
Thanks for replying.  My results:

lsusb -v
```
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
can't get hub descriptor: Operation not permitted
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 001 Device 002: ID 05e1:0408 Syntek Semiconductor Co., Ltd 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x05e1 Syntek Semiconductor Co., Ltd
  idProduct          0x0408 
  bcdDevice            0.05
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          251
    bNumInterfaces          3
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               5
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval               5
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0300  1x 768 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       2
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval               5
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x03fc  1x 1020 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       3
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval               5
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0400  1x 1024 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       4
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval               5
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0c00  2x 1024 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       5
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval               5
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x1400  3x 1024 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass         1 Audio
      bInterfaceSubClass      1 Control Device
      bInterfaceProtocol      0 
      iInterface             11 
      AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      1 (HEADER)
        bcdADC               1.00
        wTotalLength           38
        bInCollection           1
        baInterfaceNr( 0)       2
      AudioControl Interface Descriptor:
        bLength                12
        bDescriptorType        36
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        bTerminalID             1
        wTerminalType      0x0201 Microphone
        bAssocTerminal          0
        bNrChannels             1
        wChannelConfig     0x0000
        iChannelNames           0 
        iTerminal               0 
      AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      3 (OUTPUT_TERMINAL)
        bTerminalID             2
        wTerminalType      0x0101 USB Streaming
        bAssocTerminal          0
        bSourceID               3
        iTerminal               0 
      AudioControl Interface Descriptor:
        bLength                 8
        bDescriptorType        36
        bDescriptorSubtype      6 (FEATURE_UNIT)
        bUnitID                 3
        bSourceID               1
        bControlSize            1
        bmaControls( 0)      0x01
          Mute
        iFeature                0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface             11 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface             11 
      AudioStreaming Interface Descriptor:
        bLength                 7
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink           2
        bDelay                  1 frames
        wFormatTag              2 PCM8
      AudioStreaming Interface Descriptor:
        bLength                11
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             1
        bSubframeSize           1
        bBitResolution          8
        bSamFreqType            1 Discrete
        tSamFreq[ 0]         8000
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0009  1x 9 bytes
        bInterval               4
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x00
          bLockDelayUnits         0 Undefined
          wLockDelay              0 Undefined
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
can't get hub descriptor: Operation not permitted
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
```

lsmod
```
Module                  Size  Used by
easycap               328096  0 
aes_i586                7268  1 
aes_generic            26863  1 aes_i586
binfmt_misc             6587  1 
ppdev                   5259  0 
joydev                  8708  0 
snd_hda_codec_conexant    22577  1 
arc4                    1153  2 
nvidia               9932176  40 
snd_hda_intel          21877  4 
snd_hda_codec          74201  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ath5k                 121792  0 
mac80211              204922  1 ath5k
ath                     7611  1 ath5k
snd                    54148  19 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              126485  3 ath5k,mac80211,ath
sdhci_pci               5470  0 
sdhci                  15462  1 sdhci_pci
ricoh_mmc               2923  0 
soundcore               6620  1 snd
led_class               2864  2 ath5k,sdhci
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
psmouse                63245  0 
serio_raw               3978  0 
agpgart                31724  1 nvidia
vga16fb                11385  0 
vgastate                8961  1 vga16fb
i2c_nforce2             5199  0 
k8temp                  3024  0 
lp                      7028  0 
parport                32635  2 ppdev,lp
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
uvesafb                22297  1 
video                  17375  0 
output                  1871  1 video
ahci                   32008  1 
forcedeth              49556  0 
pata_amd                8766  0 
```

---

### Post by racie on 2010-05-02
Bump.  I see that it shows up, but why does it not work?

---

### Post by anewguy on 2010-05-02
I'll need to do some searching on the net and some reading to see if I can figure out how to help you more.

In the mean time, might I suggest you edit the thread title and put the actual type (usb) and model of your adapter in the title - it might get you more help.

In addition, there is a multi-media and video forum within these forums that might be of more help if you also post there:

[Multimeida & Video - Ubuntu Forums]("http://ubuntuforums.org/forumdisplay.php?f=334")

There is also another forum that may be of help (I'm not sure exactly what gets posted there as I've never used it):

[Hardware & Laptops - Ubuntu Forums]("http://ubuntuforums.org/forumdisplay.php?f=332")


You may find more help in those forums, especially the multimedia and video forum.

Dave ;)

EDIT:  BTW - I noticed you bumped the thread up after about 5 hours.  Normally the forum requests you wait 24 hours before bumping a thread.  Remember everyone here is voluntary and as such may not be available at all times.  Thanks.

---

### Post by rmt1947 on 2010-05-03
The Ubuntu-specific forum for this device is at:

[http://ubuntuforums.org/showthread.php?t=924504](http://ubuntuforums.org/showthread.php?t=924504)


The project's Open Discussion forum is on Sourceforge at:

[http://sourceforge.net/projects/easycapdc60/forums/forum/1071438](http://sourceforge.net/projects/easycapdc60/forums/forum/1071438)


As stated in the tarball's README, the driver does not work with Camorama.  It might be possible to get it to work with other userspace programs which look exclusively for /dev/video0 by making a minor change to the source code as detailed here:

[http://sourceforge.net/projects/easycapdc60/forums/forum/1071438/topic/3673472](http://sourceforge.net/projects/easycapdc60/forums/forum/1071438/topic/3673472)


Looking at the output from `lsusb -v` I see that the audio section contains the ominous line

        wMaxPacketSize     0x0009  1x 9 bytes

This shows that the EasyCAP suffers from the "slow audio USB" syndrome, which has been the cause of much anguish amply expressed on the project's Open Discussion forum.  The present version (0.7.1) of the easycapdc60 driver is unable to deliver audio from such an EasyCAP, though I would expect it to be capable of delivering video.  I intend to look into possible palliatives for the "slow audio usb" syndrome shortly, and if I find any they will be incorporated in the next release of the driver, due in a month or two (hopefully).

Mike

---

### Post by no2498 on 2010-05-03
open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

if it comes on try it in cheese
this sets the dev's

hope this works for you and you dont need to jump through hoops any more

---

### Post by racie on 2010-05-04
> **anewguy said:**
> I'll need to do some searching on the net and some reading to see if I can figure out how to help you more.

In the mean time, might I suggest you edit the thread title and put the actual type (usb) and model of your adapter in the title - it might get you more help.

In addition, there is a multi-media and video forum within these forums that might be of more help if you also post there:

[Multimeida & Video - Ubuntu Forums]("http://ubuntuforums.org/forumdisplay.php?f=334")

There is also another forum that may be of help (I'm not sure exactly what gets posted there as I've never used it):

[Hardware & Laptops - Ubuntu Forums]("http://ubuntuforums.org/forumdisplay.php?f=332")


You may find more help in those forums, especially the multimedia and video forum.

Dave ;)

EDIT:  BTW - I noticed you bumped the thread up after about 5 hours.  Normally the forum requests you wait 24 hours before bumping a thread.  Remember everyone here is voluntary and as such may not be available at all times.  Thanks.

My apologies.  I bumped the thread too soon and was too busy respond after doing so.  :/  Thank you for directing me to that section of the forum, but I don't think I'll post in there just yet, as I don't want to be too much of a nuisance.  :P  Also, I don't know how to edit the title of the thread.  Haha.  I guess I posted here because I still consider myself a beginner.  Thank you for your response.

> **rmt1947 said:**
> The Ubuntu-specific forum for this device is at:

[http://ubuntuforums.org/showthread.php?t=924504](http://ubuntuforums.org/showthread.php?t=924504)


The project's Open Discussion forum is on Sourceforge at:

[http://sourceforge.net/projects/easycapdc60/forums/forum/1071438](http://sourceforge.net/projects/easycapdc60/forums/forum/1071438)


As stated in the tarball's README, the driver does not work with Camorama.  It might be possible to get it to work with other userspace programs which look exclusively for /dev/video0 by making a minor change to the source code as detailed here:

[http://sourceforge.net/projects/easycapdc60/forums/forum/1071438/topic/3673472](http://sourceforge.net/projects/easycapdc60/forums/forum/1071438/topic/3673472)


Looking at the output from `lsusb -v` I see that the audio section contains the ominous line

        wMaxPacketSize     0x0009  1x 9 bytes

This shows that the EasyCAP suffers from the "slow audio USB" syndrome, which has been the cause of much anguish amply expressed on the project's Open Discussion forum.  The present version (0.7.1) of the easycapdc60 driver is unable to deliver audio from such an EasyCAP, though I would expect it to be capable of delivering video.  I intend to look into possible palliatives for the "slow audio usb" syndrome shortly, and if I find any they will be incorporated in the next release of the driver, due in a month or two (hopefully).

Mike
Thank you for that link on changing the file easycap0 to video0.  I will try that and post back later.  Right now, the audio doesn't really concern me, especially since they may have a new driver for it soon.  I'm more concerned about making something work on the device.  Thank you for your help. 

> **no2498 said:**
> open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

if it comes on try it in cheese
this sets the dev's

hope this works for you and you dont need to jump through hoops any more

Unfortunately, none of this works because the EasyCap device shows up in /dev/easycap0 and /dev/easysnd1.  Gstreamer seems to only detect /dev/video0.  I will try Mike's solution for this.  Thank you for showing me these options, though, because I did not know about them.

**EDIT: Renaming the file does not work.  Now instead of easycap0, I get video0, but it is not recognized.**

---

