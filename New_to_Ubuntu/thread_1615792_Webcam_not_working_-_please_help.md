---
title: "Webcam not working - please help"
date: 2010-11-07
forum: New to Ubuntu
---

### Post by luckylucky on 2010-11-07
Hi, got a new samsung netbook (N145) which has a little camera built in... great for skype.  Installed Ubuntu 10.10

I tried "cheese" (linux webcam program) and I get no picture and no video.

How do I figure out how to fix it?  Thank you.

---

### Post by no2498 on 2010-11-07
you may try this but if cheese did not find the cam most likely the dev/video 0 is not setting


gstreamer-properties


open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

cheese has a nice help file look in the faq's

---

### Post by luckylucky on 2010-11-07
Thank you for your help.  Unfortunately neither option helped.  

Any other ideas... anyone?
thanks

---

### Post by Jeff.Smith on 2010-11-07
Perhaps a driver issue? Sometimes the proprietary drivers offered by the manufacturers work better (provided that they have one for linux). I had an issue with a graphics card that was resolved by using the proprietary driver instead. So you man check your manufacturer's website and see if they offer anything for linux.

---

### Post by no2498 on 2010-11-08
lets see what you get if you type webcam click enter in a terminal
? did it load a grabber

---

### Post by luckylucky on 2010-11-08
> **no2498 said:**
> lets see what you get if you type webcam click enter in a terminal
? did it load a grabber

I tried your suggestion, and here is what came of it

```

violetta@amethyst:~$ webcam
The program 'webcam' is currently not installed.  You can install it by typing:
sudo apt-get install webcam
violetta@amethyst:~$ sudo apt-get install webcam
[sudo] password for violetta: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  openssh-server ssh xawtv-plugins
Suggested packages:
  rssh molly-guard openssh-blacklist openssh-blacklist-extra
The following NEW packages will be installed:
  openssh-server ssh webcam xawtv-plugins
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 428kB of archives.
After this operation, 1,442kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  openssh-server ssh xawtv-plugins webcam
Install these packages without verification [y/N]? y
Get:1 http://ca.archive.ubuntu.com/ubuntu/ maverick/main openssh-server i386 1:5.5p1-4ubuntu4 [302kB]
Get:2 http://ca.archive.ubuntu.com/ubuntu/ maverick/main ssh all 1:5.5p1-4ubuntu4 [1,286B]
Get:3 http://ca.archive.ubuntu.com/ubuntu/ maverick/universe xawtv-plugins i386 3.95.dfsg.1-8.1ubuntu1 [86.2kB]
Get:4 http://ca.archive.ubuntu.com/ubuntu/ maverick/universe webcam i386 3.95.dfsg.1-8.1ubuntu1 [38.7kB]
Fetched 428kB in 4s (98.8kB/s)  
Preconfiguring packages ...
Selecting previously deselected package openssh-server.
(Reading database ... 161057 files and directories currently installed.)
Unpacking openssh-server (from .../openssh-server_1%3a5.5p1-4ubuntu4_i386.deb) ...
Selecting previously deselected package ssh.
Unpacking ssh (from .../ssh_1%3a5.5p1-4ubuntu4_all.deb) ...
Selecting previously deselected package xawtv-plugins.
Unpacking xawtv-plugins (from .../xawtv-plugins_3.95.dfsg.1-8.1ubuntu1_i386.deb) ...
Selecting previously deselected package webcam.
Unpacking webcam (from .../webcam_3.95.dfsg.1-8.1ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for ufw ...
Setting up openssh-server (1:5.5p1-4ubuntu4) ...
Creating SSH2 RSA key; this may take some time ...
Creating SSH2 DSA key; this may take some time ...
 * Stopping OpenBSD Secure Shell server sshd                             [ OK ] 
ssh start/running, process 2057
Setting up ssh (1:5.5p1-4ubuntu4) ...
Setting up xawtv-plugins (3.95.dfsg.1-8.1ubuntu1) ...
Setting up webcam (3.95.dfsg.1-8.1ubuntu1) ...
violetta@amethyst:~$ webcam
reading config file: /home/violetta/.webcamrc
video4linux webcam v1.5 - (c) 1998-2002 Gerd Knorr
grabber config:
  size 320x240 [none]
  input (null), norm (null), jpeg quality 75
  rotate=0, top=0, left=0, bottom=240, right=320


```

tried using cheese to verify camera functioning, but still seeking solution...

---

### Post by no2498 on 2010-11-10
try using xawtv

---

### Post by Crazedpsyc on 2010-11-10
Please post the output of ```
lsusb
```
Even though it is not an external webcam it is still viewed as a usb-connected device

---

### Post by mastablasta on 2010-11-10
when you went to:
 
gstreamer-properties
 
 
Did you see camera as device there? If not then you will probably need to find and load proprietary linux drivers for it (if they exist).
 
edit: and do as post above mine says it will also give us information on what camera you have  and wheather it is actually recognised by the system.

---

### Post by Parrameister on 2010-11-14
The issue could be a driver problem.
I have a Webcam that uses the gspca driver.
Type lsusb (when it is plugged in and see what type of camera it is and if it is recognised).
If you google your camera you may find out what driver it uses.
You can then 'lsmod' to see if the modules are loaded.
Also check your messages (either through the GUI) or via the 'dmesg' command and check after plugging in the camera that it is being registered by the system. My particular problem (see below0 showed up an error after creating the video0 directory. This led me to the gspca driver problem.

My webcam worked in 10.04 but when I upgraded to 10.10 the kernel modules changed and the driver no longer worked.
I had to go to the gspca driver's web site extract the latest tarball and make/install the latest driver.
This fixed it for me (my camera used the gspca_zc3xx.ko modules) , but it would depend on what camera and what driver you have.

---

### Post by Rattle1 on 2010-11-15
[QUOTE="Parrameister"]My webcam worked in 10.04 but when I upgraded to 10.10 the kernel modules changed and the driver no longer worked.[/QUOTE]

This happened to me as well, but I could not compile the gspca driver, it had some errors. Could you please detail how you did it? Thanks.

 I have a A4Tech webcam using the same driver zc3xx. It seems now is embedded in the kernel, but I cannot make it work...

---

### Post by Parrameister on 2010-11-17
I downloaded the tarball from the following gspca web site.
[http://moinejf.free.fr/](http://moinejf.free.fr/)
I used the test version which was gspca-2.11.3.tar.gz

I then followed the readme instructions (within the tarball)
Double click on the downloaded file and it will open up a viewer from which you can extract the contents or view particular files within the archive.
Make sure you are in the correct directory where the make file is.

From memory (as I am not at my PC)
Get a command prompt.
I typed in the command: sudo make gspca_zc3xx.ko
(This compiles only the gspca_main and gspca_zc3xx modules)
Then I typed in the command: sudo make install
(This then installs the modules)
I then rebooted the PC to load the modules.

You could make and install all the drivers if you wanted to by simply typing sudo make install

I hope that helps.

---

### Post by Rattle1 on 2010-11-18
Thanks, but  it seems I'm too dumb to follow the explanations, or something else is wrong...;)
Here is my output, from the folder where I extracted the tarball: 

> #:~$ cd ~/Downloads/gspca-2.11.3 
#:~/Downloads/gspca-2.11.3$ sudo make gspca_zc3xx.ko
make -C /lib/modules/2.6.35.7-custom/build M=/build gspca_main.ko gspca_zc3xx.ko
make[1]: Entering directory `/usr/src/linux-headers-2.6.35.7-custom'
scripts/Makefile.build:44: /build/Makefile: No such file or directory
make[2]: *** No rule to make target `/build/Makefile'.  Stop.
make[1]: *** [gspca_main.ko] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35.7-custom'
make: *** [gspca_zc3xx.ko] Error 2Any ideas? Should I extract the files somewhere else?

---

### Post by ky5u on 2010-11-20
Hi all,

I spent several hours trying to find this info so this isn't a cop out  for easy help....

Does anyone know the command to list out the video input/alias names for  an installed camera?  I used it once but didn't write it down.  It  listed whether a camera was aliased to composite1, camera, camera1 etc.   

I use Gerd Knorr's Webcam program on several machines successfully in  Linux.  I recently added a MAC with VMWare running 10.04 ubuntu.   Cheese, and gucview all see the iSight camera fine.  Knor's program  config file requires a parameter "Input=" which is "camera" for my  Logitec Quickcam and "camera1" for my Logitec 9000. The default  "composite1" does not work.

I can see "video0" added to /dev when I activate the iSight camera so I  know that param is ok in the config file and as I said, Cheese sees the  camera fine.

HELP??!!

---

### Post by Parrameister on 2010-11-21
To Rattle1,

Sorry I was not at my PC - you were in the right directory, just drop off the sudo from the command and it should work fine.
Eg. make gspca_zc3xx.ko

This will go through a make process and produce two new files in the build directory called gspca_main.ko and gspca_zc3xx.ko
(You can check by typing: ls build/*.ko - like the following
user@user-desktop2:~/temp/gspca-2.11.3$ ls build/*.ko
build/gspca_main.ko  build/gspca_zc3xx.ko)

You can then type make install and it should install the modules for you.

---

### Post by honeybear on 2010-11-21
we have a Logitech, Inc. Webcam B500
it is a good webcam, very nice colors, much better than crapy ones

however it is limited to 640x480 live during skype video. i wished larger

well cant help mroe, it took lot of time to find a compatible webcam with linux although all website you can find that tell you that webcam works with linux ok , but you have to change para, and plz avoid microsoft webcam since they are not well supported by linux


does teh command work?

```
 mplayer -tv driver=v4l2:gain=1:width=640:height=480:device=/dev/video0:fps=30:outfmt=yuy2 tv://
```

---

### Post by Rattle1 on 2010-11-21
> **Parrameister said:**
> To Rattle1,

Sorry I was not at my PC - you were in the right directory, just drop off the sudo from the command and it should work fine.
Eg. make gspca_zc3xx.ko

This will go through a make process and produce two new files in the build directory called gspca_main.ko and gspca_zc3xx.ko
(You can check by typing: ls build/*.ko - like the following
user@user-desktop2:~/temp/gspca-2.11.3$ ls build/*.ko
build/gspca_main.ko  build/gspca_zc3xx.ko)

You can then type make install and it should install the modules for you.
  Yay, that did it! And the webcam is functioning once again!:p Thank you very much!

Worth mentioning for others that in my case the order was "make gspca_zc3xx.ko" and "sudo make install", restart and voila!

---

### Post by VcDeveloper on 2010-11-21
I had this working before, but I had to reinstall my server for other reasons but, at the moment its taking time to find all the post I read through to solve it again.

But here is my out of lsub:
```
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 006 Device 007: ID 046d:08ae Logitech, Inc. QuickCam for Notebooks**
Bus 006 Device 006: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 006 Device 004: ID 045e:00dd Microsoft Corp. 
Bus 006 Device 003: ID 0557:8021 ATEN International Co., Ltd 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I can see in my message.log when it was registered/unplug/plug:
```
Nov 21 09:23:25 anointed kernel: [  588.040127] usb 6-1: USB disconnect, address 2
Nov 21 09:23:25 anointed kernel: [  588.040202] usb 6-1: Disconnecting ZC0301[P] PC Camera...
Nov 21 09:23:25 anointed kernel: [  588.040204] usb 6-1: V4L2 device /dev/video0 deregistered
Nov 21 09:23:41 anointed kernel: [  604.322591] usb 6-1: new full speed USB device using uhci_hcd and address 7
Nov 21 09:23:41 anointed kernel: [  604.527537] usb 6-1: configuration #1 chosen from 1 choice
Nov 21 09:23:41 anointed kernel: [  604.530443] usb 6-1: ZC0301[P] Image Processor and Control Chip detected (vid/pid 0x046D:0x08AE)
Nov 21 09:23:41 anointed kernel: [  604.596400] usb 6-1: PAS202BCB image sensor detected
Nov 21 09:23:42 anointed kernel: [  605.072393] usb 6-1: Initialization succeeded
Nov 21 09:23:42 anointed kernel: [  605.072473] usb 6-1: V4L2 device registered as /dev/video0

```

This is my lsmod
```
Module                  Size  Used by
nf_conntrack_ipv4      12980  2 
nf_defrag_ipv4          1481  1 nf_conntrack_ipv4
xt_state                1490  2 
nf_conntrack           73966  2 nf_conntrack_ipv4,xt_state
xt_mark                 1055  4 
xt_NFQUEUE              2344  2 
xt_iprange              1645  2 
xt_tcpudp               2667  7 
ipt_REJECT              2384  2 
nfnetlink_queue         8205  2 
nfnetlink               4142  3 nfnetlink_queue
binfmt_misc             7960  1 
ppdev                   6375  0 
iptable_filter          2791  1 
ip_tables              18390  1 iptable_filter
x_tables               22461  7 xt_state,xt_mark,xt_NFQUEUE,xt_iprange,xt_tcpudp,ipt_REJECT,ip_tables
snd_hda_codec_realtek   279040  1 
snd_usb_audio          92747  1 
snd_usb_lib            19193  1 snd_usb_audio
snd_hda_intel          25773  2 
snd_hda_codec          85759  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  2 snd_usb_audio,snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  4 snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
snd                    71251  19 snd_hda_codec_realtek,snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
softcursor              1565  1 bitblit
soundcore               8052  1 snd
joydev                 11072  0 
intel_agp              29095  0 
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
nvidia              10832442  38 
vga16fb                12757  1 
usbhid                 41084  0 
vgastate                9857  1 vga16fb
psmouse                64576  0 
hid                    83472  1 usbhid
serio_raw               4918  0 
zc0301                 48746  0 
videodev               40518  1 zc0301
v4l1_compat            15495  1 videodev
v4l2_compat_ioctl32    11764  1 videodev
lp                      9336  0 
parport                37160  2 ppdev,lp
ohci1394               30260  0 
ieee1394               94771  1 ohci1394
pata_jmicron            2747  0 
tulip                  50464  0 
e1000e                136269  0 

```

When I test my video using gstreamer-properties it keeps saying: couldn't open /dev/video0 for reading and writing.

I made the changed and I still get the same message and I did put me in the audio/video group.

here is my ls -l
crw-rw-rw- 1 root video 81, 0 2010-11-21 09:23 /dev/video0

Any suggesting while I'm searching?

---

### Post by Revolution on 2010-12-04
I have also bought a Samsung N145 Netbook and removed Win7 and installed Ubuntu 10.10
I've been researching the Webcam and so far have the USB ID 2232:1006.
I installed HAL and found the camera type with 'lshal'.
```
udi = '/org/freedesktop/Hal/devices/usb_device_2232_1006_noserial'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1d_7'  (string)
  info.product = 'WebCam SCB-0355N'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_2232_1006_noserial'  (string)
  info.vendor = 'Image Processor'  (string)
  linux.device_file = '/dev/bus/usb/001/002'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-8'  (string)
  usb_device.bus_number = 1  (0x1)  (int)
  usb_device.can_wake_up = false  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 239  (0xef)  (int)
  usb_device.device_protocol = 1  (0x1)  (int)
  usb_device.device_revision_bcd = 3  (0x3)  (int)
  usb_device.device_subclass = 2  (0x2)  (int)
  usb_device.is_self_powered = false  (bool)
  usb_device.linux.device_number = 2  (0x2)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-8'  (string)
  usb_device.max_power = 500  (0x1f4)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 2  (0x2)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.product = 'WebCam SCB-0355N'  (string)
  usb_device.product_id = 4102  (0x1006)  (int)
  usb_device.speed = 480.0 (480) (double)
  usb_device.vendor = 'Image Processor'  (string)
  usb_device.vendor_id = 8754  (0x2232)  (int)
  usb_device.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_2232_1006_noserial_if1'
  info.linux.driver = 'uvcvideo'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_2232_1006_noserial'  (string)
  info.product = 'USB Video Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_2232_1006_noserial_if1'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.1'  (string)
  usb.bus_number = 1  (0x1)  (int)
  usb.can_wake_up = false  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 239  (0xef)  (int)
  usb.device_protocol = 1  (0x1)  (int)
  usb.device_revision_bcd = 3  (0x3)  (int)
  usb.device_subclass = 2  (0x2)  (int)
  usb.interface.class = 14  (0xe)  (int)
  usb.interface.number = 1  (0x1)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 2  (0x2)  (int)
  usb.is_self_powered = false  (bool)
  usb.linux.device_number = 2  (0x2)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.1'  (string)
  usb.max_power = 500  (0x1f4)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 2  (0x2)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB Video Interface'  (string)
  usb.product_id = 4102  (0x1006)  (int)
  usb.speed = 480.0 (480) (double)
  usb.vendor = 'Image Processor'  (string)
  usb.vendor_id = 8754  (0x2232)  (int)
  usb.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_2232_1006_noserial_if0'
  info.linux.driver = 'uvcvideo'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_2232_1006_noserial'  (string)
  info.product = 'USB Video Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_2232_1006_noserial_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0'  (string)
  usb.bus_number = 1  (0x1)  (int)
  usb.can_wake_up = false  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 239  (0xef)  (int)
  usb.device_protocol = 1  (0x1)  (int)
  usb.device_revision_bcd = 3  (0x3)  (int)
  usb.device_subclass = 2  (0x2)  (int)
  usb.interface.class = 14  (0xe)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 1  (0x1)  (int)
  usb.is_self_powered = false  (bool)
  usb.linux.device_number = 2  (0x2)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0'  (string)
  usb.max_power = 500  (0x1f4)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 2  (0x2)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB Video Interface'  (string)
  usb.product_id = 4102  (0x1006)  (int)
  usb.speed = 480.0 (480) (double)
  usb.vendor = 'Image Processor'  (string)
  usb.vendor_id = 8754  (0x2232)  (int)
  usb.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_2232_1006_noserial_if0_video4linux'
  info.capabilities = {'video4linux', 'video4linux.video_capture'} (string list)
  info.category = 'video4linux'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_2232_1006_noserial_if0'  (string)
  info.product = 'WebCam SCB-0355N'  (string)
  info.subsystem = 'video4linux'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_2232_1006_noserial_if0_video4linux'  (string)
  linux.device_file = '/dev/video0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'video4linux'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/video4linux/video0'  (string)
  video4linux.device = '/dev/video0'  (string)
  video4linux.version = '2'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_2232_1006_noserial_if0_logicaldev_input'
  button.has_state = false  (bool)
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.capabilities = {'input', 'button', 'input.keys'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_2232_1006_noserial_if0'  (string)
  info.product = 'WebCam SCB-0355N'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_2232_1006_noserial_if0_logicaldev_input'  (string)
  input.device = '/dev/input/event5'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_2232_1006_noserial_if0'  (string)
  input.product = 'WebCam SCB-0355N'  (string)
  linux.device_file = '/dev/input/event5'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/input/input5/event5'  (string)

```

It appears to show the webcam as /dev/video0 but Cheese just shows a black output from the camera.
The camera manufacturer appears to be Vimicro.

---

### Post by Revolution on 2010-12-06
I now have my webcam working.

I installed vlc and then installed mplayer.

```
sudo apt-get install vlc-nox
```

```
sudo apt-get install mplayer
```

I then ran Cheese and now have a picture.
It appears something was installed that fixed the problem.

---

### Post by ayupmiduck on 2011-03-16
[http://twistedpairdevelopment.wordpress.com/2010/11/16/installing-ubuntu-on-a-samsung-n145-and-possibly-others/](http://twistedpairdevelopment.wordpress.com/2010/11/16/installing-ubuntu-on-a-samsung-n145-and-possibly-others/)

---

### Post by ubudog on 2011-03-16
Umm, what?

Could you provide more details please?

Also, try using the program Cheese.

```
sudo apt-get install cheese
```

---

