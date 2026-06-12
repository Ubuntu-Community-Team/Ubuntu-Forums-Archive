---
title: "Help with a Hercules Dualpix HD Webcam"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by Greyeyedkiller on 2009-01-22
Now before I ask this question I did do a check to see if my question had been posted and/or solved already.  It has been posted in 2007 but it was not solved.  This being 2009 and all I kind of figure there is sufficient space between my question and that other user's to re-examine the question again.

Here is my problem.  I am running the newest stable version of Ubuntu, Intrepid Ibex on an HP Pavilion 754n.  I have dual booted Ubuntu and Windows XP on my machine.  The webcam I am using is a Hercules Dualpix Webcam.  

Currently I have "partial" use of the webcam.  When I run an "EasyCam 2" check of my system it instantly recognises that I actually have the webcam since it will show that I have a Hercules Dualpix webcam and will even give me the option of installing it.

However, when I do install it, nothing happens and it says "No Camera Found".  So... I installed Ekiga Softphone and hell's bells !! It actually makes a blue light flash in the webcam and I am able to hear my recorded voice in the built in mike from the webcam BUT... I still cannot see a picture.

I asked the folks at Hercules this question, "do you have a driver to enable my Hercules Dualpix webcam to work in Linux Ubuntu?"  They actually said yes, it is Linux compatible however, I'm not an adept enough of a Linux user to make heads nor tails of their advice?

Here is their email to me:

Dear M*. K**** L*****,
Thank you for your request. In order to resolve the issue you have encountered with your Dualpix HD webcam, please refer to our response herewith:


We are sorry for the problem you are having with the Hercules Dualpix HD webcam.

Dualpix Exchange is UVC compliant, so it is supported under Linux by standard uvcvideo driver ([http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/))

Thank you for your time and cooperation.



We hope that the information we have provided is useful and has helped to resolve your query. Have a good day and please remember that Hercules Technical Support is at your disposal for any other information you may need. You can reach us via the Web at the following addresses:

[http://ts.hercules.com/eng](http://ts.hercules.com/eng) for the latest updates and FAQs

or by telephone at one of the numbers listed on the following page:

[http://ts.hercules.com/eng/index.php?pg=contact](http://ts.hercules.com/eng/index.php?pg=contact)

King regards,

Your Hercules Technical Support Agent, Costin

PS: To ensure the most efficient follow-up of your query, please be sure to include the reference number [70976-1231620505] of your file in the subject line of any emails you may send us later on.

---

### Post by stderr on 2009-01-22
I'm not able to offer any specific advice, but doing a search through packages for "uvc video" came up with this:

```
ace@ace1:~$ apt-cache search uvc video
luvcview - USB Video Class grabber
uvccapture - USB UVC Video Class snapshot software

```

```
ace@ace1:~$ apt-cache show luvcview
[...]
Description: USB Video Class grabber
 luvcview is a camera viewer for UVC based webcams. It includes an mjpeg
 decoder and is able to save the video stream as an AVI file.

```

```
ace@ace1:~$ apt-cache show uvccapture
[...]
Description: USB UVC Video Class snapshot software
 The purpose of this software is to capture an image from a USB webcam at a
 specified interval, and save it to a JPEG file, no other formats are supported.
 .
 Right now this software is really a hack, since still image support is not yet
 available in the UVC driver. The program continually polls the UVC driver in
 MJPEG mode, and at a specified interval writes a JPEG header and a single frame
 to file, creating a JPEG image.
```

And from UVC's website:

> Linux 2.6.26 and newer includes the Linux UVC driver natively. You will not need to download the driver sources manually unless you want to test a newer version or help with development.

...so you already have the UVC driver. I would advise trying luvcview and seeing if it a) works and b) is any good for you:

```
sudo apt-get install luvcview
```

---

### Post by Greyeyedkiller on 2009-01-23
Thanks! 

At the moment I'm tooling around with my windows XP and when I get that done I will attempt the fixes you have suggested and inform ya'all here of my results.

In the meantime... :popcorn: if you got em'!

---

### Post by Greyeyedkiller on 2009-01-23
And this is what I discovered in terminal:

k****l*****@ubuntu:~$ sudo apt-get install luvcview
[sudo] password for k****l*****: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package luvcview

:confused:

I also looked in the Synaptic Package Manager.  It could not locate that file "lucview"

Am I doing something wrong?

Well, I did finally get lucview installed.  I also went to the following site and followed some directions from there as well.  This is what happened...

k****l*****@ubuntu:~$ ls /dev/video*
ls: cannot access /dev/video*: No such file or directory
k****l*****@ubuntu:~$ ls /dev/audio*
/dev/audio  /dev/audio1
k****l*****@ubuntu:~$ sudo apt-get install mplayer mencoder
[sudo] password for k****l*****: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libartsc0 libaudio2 libenca0 libfaac0 libfreebob0 libggi-target-x libggi2
  libgii1 libgii1-target-x libglide2 libjack0 liblzo2-2 libmp3lame0 libmpcdec3
  libopenal1 libsvga1 libtwolame0 libx264-59 libxvidcore4 libxvmc1
  mplayer-skins ttf-dejavu ttf-dejavu-extra
Suggested packages:
  nas libggi-target-emu libggi-target-monotext libggimisc2 device3dfx-module
  device3dfx-source glide2-bin jackd w32codecs libdvdcss mplayer-doc
  ladspa-sdk
The following NEW packages will be installed:
  libartsc0 libaudio2 libenca0 libfaac0 libfreebob0 libggi-target-x libggi2
  libgii1 libgii1-target-x libglide2 libjack0 liblzo2-2 libmp3lame0 libmpcdec3
  libopenal1 libsvga1 libtwolame0 libx264-59 libxvidcore4 libxvmc1 mencoder
  mplayer mplayer-skins ttf-dejavu ttf-dejavu-extra
0 upgraded, 25 newly installed, 0 to remove and 0 not upgraded.
Need to get 14.1MB of archives.
After this operation, 33.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main libartsc0 1.5.10-0ubuntu1 [16.7kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main libaudio2 1.9.1-4 [80.3kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe libenca0 1.9-6 [72.7kB]   
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse libfaac0 1.26-0.1ubuntu2 [61.4kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe libfreebob0 1.0.11-0ubuntu1 [146kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe libgii1 1:1.0.2-2 [291kB] 
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe libglide2 2002.04.10-16ubuntu2 [375kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe libsvga1 1:1.4.3-27 [314kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe libggi2 1:2.2.2-1ubuntu1 [370kB]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe libgii1-target-x 1:1.0.2-2 [85.6kB]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe libggi-target-x 1:2.2.2-1ubuntu1 [164kB]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe libjack0 0.109.2-3ubuntu1 [120kB]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main liblzo2-2 2.03-1 [64.5kB]    
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse libmp3lame0 3.98-0.0 [132kB]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main libmpcdec3 1.2.2-1build1 [27.4kB]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe libtwolame0 0.3.12-1 [53.6kB]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse libx264-59 1:0.svn20080408-0.0ubuntu1 [281kB]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse libxvidcore4 2:1.1.2-0.1ubuntu3 [212kB]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main libxvmc1 2:1.0.4-2ubuntu1 [19.2kB]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse mplayer-skins 2-7 [70.3kB]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main ttf-dejavu-extra 2.25-1 [2920kB]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main ttf-dejavu 2.25-1 [3100B]    
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe libopenal1 1:1.3.253-4ubuntu1 [67.2kB]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse mencoder 2:1.0~rc2-0ubuntu17 [3770kB]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse mplayer 2:1.0~rc2-0ubuntu17 [4426kB]
Fetched 14.1MB in 1min41s (140kB/s)                                            
Preconfiguring packages ...
Selecting previously deselected package libartsc0.
(Reading database ... 116116 files and directories currently installed.)
Unpacking libartsc0 (from .../libartsc0_1.5.10-0ubuntu1_i386.deb) ...
Selecting previously deselected package libaudio2.
Unpacking libaudio2 (from .../libaudio2_1.9.1-4_i386.deb) ...
Selecting previously deselected package libenca0.
Unpacking libenca0 (from .../libenca0_1.9-6_i386.deb) ...
Selecting previously deselected package libfaac0.
Unpacking libfaac0 (from .../libfaac0_1.26-0.1ubuntu2_i386.deb) ...
Selecting previously deselected package libfreebob0.
Unpacking libfreebob0 (from .../libfreebob0_1.0.11-0ubuntu1_i386.deb) ...
Selecting previously deselected package libgii1.
Unpacking libgii1 (from .../libgii1_1%3a1.0.2-2_i386.deb) ...
Selecting previously deselected package libglide2.
Unpacking libglide2 (from .../libglide2_2002.04.10-16ubuntu2_i386.deb) ...
Selecting previously deselected package libsvga1.
Unpacking libsvga1 (from .../libsvga1_1%3a1.4.3-27_i386.deb) ...
Selecting previously deselected package libggi2.
Unpacking libggi2 (from .../libggi2_1%3a2.2.2-1ubuntu1_i386.deb) ...
Selecting previously deselected package libgii1-target-x.
Unpacking libgii1-target-x (from .../libgii1-target-x_1%3a1.0.2-2_i386.deb) ...
Selecting previously deselected package libggi-target-x.
Unpacking libggi-target-x (from .../libggi-target-x_1%3a2.2.2-1ubuntu1_i386.deb) ...
Selecting previously deselected package libjack0.
Unpacking libjack0 (from .../libjack0_0.109.2-3ubuntu1_i386.deb) ...
Selecting previously deselected package liblzo2-2.
Unpacking liblzo2-2 (from .../liblzo2-2_2.03-1_i386.deb) ...
Selecting previously deselected package libmp3lame0.
Unpacking libmp3lame0 (from .../libmp3lame0_3.98-0.0_i386.deb) ...
Selecting previously deselected package libmpcdec3.
Unpacking libmpcdec3 (from .../libmpcdec3_1.2.2-1build1_i386.deb) ...
Selecting previously deselected package libtwolame0.
Unpacking libtwolame0 (from .../libtwolame0_0.3.12-1_i386.deb) ...
Selecting previously deselected package libx264-59.
Unpacking libx264-59 (from .../libx264-59_1%3a0.svn20080408-0.0ubuntu1_i386.deb) ...
Selecting previously deselected package libxvidcore4.
Unpacking libxvidcore4 (from .../libxvidcore4_2%3a1.1.2-0.1ubuntu3_i386.deb) ...
Selecting previously deselected package libxvmc1.
Unpacking libxvmc1 (from .../libxvmc1_2%3a1.0.4-2ubuntu1_i386.deb) ...
Selecting previously deselected package mplayer-skins.
Unpacking mplayer-skins (from .../mplayer-skins_2-7_all.deb) ...
Selecting previously deselected package ttf-dejavu-extra.
Unpacking ttf-dejavu-extra (from .../ttf-dejavu-extra_2.25-1_all.deb) ...
Selecting previously deselected package ttf-dejavu.
Unpacking ttf-dejavu (from .../ttf-dejavu_2.25-1_all.deb) ...
Selecting previously deselected package libopenal1.
Unpacking libopenal1 (from .../libopenal1_1%3a1.3.253-4ubuntu1_i386.deb) ...
Selecting previously deselected package mencoder.
Unpacking mencoder (from .../mencoder_2%3a1.0~rc2-0ubuntu17_i386.deb) ...
Selecting previously deselected package mplayer.
Unpacking mplayer (from .../mplayer_2%3a1.0~rc2-0ubuntu17_i386.deb) ...
Processing triggers for man-db ...
Setting up libartsc0 (1.5.10-0ubuntu1) ...

Setting up libaudio2 (1.9.1-4) ...

Setting up libenca0 (1.9-6) ...

Setting up libfaac0 (1.26-0.1ubuntu2) ...

Setting up libfreebob0 (1.0.11-0ubuntu1) ...

Setting up libgii1 (1:1.0.2-2) ...

Setting up libglide2 (2002.04.10-16ubuntu2) ...

Setting up libsvga1 (1:1.4.3-27) ...

Setting up libggi2 (1:2.2.2-1ubuntu1) ...

Setting up libgii1-target-x (1:1.0.2-2) ...
Setting up libggi-target-x (1:2.2.2-1ubuntu1) ...
Setting up libjack0 (0.109.2-3ubuntu1) ...

Setting up liblzo2-2 (2.03-1) ...

Setting up libmp3lame0 (3.98-0.0) ...

Setting up libmpcdec3 (1.2.2-1build1) ...

Setting up libtwolame0 (0.3.12-1) ...

Setting up libx264-59 (1:0.svn20080408-0.0ubuntu1) ...

Setting up libxvidcore4 (2:1.1.2-0.1ubuntu3) ...

Setting up libxvmc1 (2:1.0.4-2ubuntu1) ...

Setting up mplayer-skins (2-7) ...
Setting up ttf-dejavu-extra (2.25-1) ...
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-dejavu
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for UMingCN, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.

Setting up ttf-dejavu (2.25-1) ...
Setting up libopenal1 (1:1.3.253-4ubuntu1) ...

Setting up mencoder (2:1.0~rc2-0ubuntu17) ...
Setting up mplayer (2:1.0~rc2-0ubuntu17) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
k****l*****@ubuntu:~$

---

### Post by arochester on 2009-02-02
See "Hercules Dualpix Exchange webcam in Xubuntu" at [http://cafelinux.org/xubuntuforums/index.php/topic,232.msg1081/topicseen.html#msg1081](http://cafelinux.org/xubuntuforums/index.php/topic,232.msg1081/topicseen.html#msg1081)

---

### Post by manu-tm on 2009-02-09
The Hercules Dualpix HD and Dualpix Exchange are not the same:

    HD       -> usb_id = 06f8:3003
    Exchange -> usb_id = 06f8:3005

EasyCam2 install the ov534 driver, not uvcvideo...

---

### Post by mosibfu on 2009-11-16
well my dualpix HD seems to work (out of the box), in vlc at least, on amsn it uses the ov driver, but then again, once its loaded white screen, dunno what or why but ill find it out!

---

### Post by ukripper on 2009-11-16
Can you post output of the folowing command:
```
lsmod
``` 
Above command will show you if your uvc drivers are loaded in kernel or not. then we take it from there

---

### Post by mosibfu on 2009-11-16
mosibfu@ultramesh:~$ lsmod
Module                  Size  Used by
binfmt_misc             6311  1 
ppdev                   5101  0 
snd_hda_codec_realtek   202151  1 
snd_hda_intel          22647  4 
snd_usb_audio          74681  2 
snd_hda_codec          71914  2 snd_hda_codec_realtek,snd_hda_intel
snd_pcm_oss            37172  0 
snd_mixer_oss          15029  2 snd_pcm_oss
coretemp                4554  0 
snd_pcm                71804  4 snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_pcm_oss
w83627ehf              17895  0 
snd_usb_lib            15278  1 snd_usb_audio
snd_seq_dummy           1456  0 
snd_seq_oss            26458  0 
snd_seq_midi            4435  0 
lm78                   12203  0 
hwmon_vid               2379  2 w83627ehf,lm78
snd_seq_midi_event      5707  2 snd_seq_oss,snd_seq_midi
snd_seq                45535  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_rawmidi            18363  2 snd_usb_lib,snd_seq_midi
snd_timer              19260  2 snd_pcm,snd_seq
snd_hwdep               5257  2 snd_usb_audio,snd_hda_codec
snd_seq_device          5596  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
lp                      6900  0 
gspca_ov534             6802  0 
parport                32240  2 ppdev,lp
iptable_filter          2199  0 
snd                    53253  23 snd_hda_codec_realtek,snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_seq,snd_rawmidi,snd_timer,snd_hwdep,snd_seq_device
gspca_main             20305  1 gspca_ov534
nvidia               7084196  34 
soundcore               6410  2 snd
snd_page_alloc          7140  2 snd_hda_intel,snd_pcm
i2c_nforce2             5490  0 
psmouse                54136  0 
serio_raw               3978  0 
videodev               36381  1 gspca_main
v4l1_compat            13316  1 videodev
ip_tables              10370  1 iptable_filter
x_tables               13791  1 ip_tables
joydev                  8915  0 
agpgart                31758  1 nvidia
usbhid                 35312  0 
ohci1394               28270  0 
floppy                 50470  0 
ieee1394               81514  1 ohci1394
forcedeth              52311  0 

seems not to be loaded.. still puzzeling how vlc and amsn see it (give image.. i see myself) but once i start sending white screen..

---

### Post by ukripper on 2009-11-16
@ Greyeyedkiller - Can you also post lsmod output.

@ mosibfu - your gspca drivers are loaded fine in kernel. you shoudln't have any drivers issue in taht respect. Can you install cheese  using this command: ```
sudo apt-get install cheese
```and run in terminal cheese. And post any error if you get here.

---

### Post by mosibfu on 2009-11-16
ukripper:

runs fine, i see myself perfectly,

mosibfu@ultramesh:~$ cheese
/home/mosibfu/.themes/diehard/gtk-2.0/gtkrc:53: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored. [COLOR="Red"]ignore this error, its because i run xfce[/COLOR]
libv4l2: error converting / decoding frame data: v4l-convert: error parsing JPEG header: Not a JPG file ?


libv4l2: error converting / decoding frame data: v4l-convert: error parsing JPEG header: Not a JPG file ?
 
theres the error.. i guess

---

### Post by ukripper on 2009-11-16
@mosibfu - looks like then problem is with your amsn and webcam.

Have you tried skype video?

---

### Post by mosibfu on 2009-11-16
i actually never tried skype period.

im on some weird cam site now (for testing purposes).. cam works there ill try to fix emesene now some weird libmimic thingy but well..

conclusion: hercules dualpix HD works out of the box for me, amsn doesnt work tho :P

emesene works now ^^

---

