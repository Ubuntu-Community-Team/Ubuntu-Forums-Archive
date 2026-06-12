---
title: "Ubuntu crashes with 'cheese' and playing MTS video"
date: 2011-09-02
forum: New to Ubuntu
---

### Post by Merlijn Janssen on 2011-09-02
Hello Experts!

I assembled a new itx-mini computer based on Intel i3, no separate graphics card. I decided to try Ubuntu 10.10, and at first sight, things work pretty well. But I have 2 problems that I cannot solve, even with your help in forums found so far.

1) I have 2 webcams. One is not recognised as such. No /dev/video0 appears. The other is recognised, but Skype does not show the video feed. Cheese doesn't either, and crashes the system. Rebooting with alt-sys-REISUB is the only option then.

2) When I upload MTS video from my SD camcorder, the videoclips have a picture as thumbnail, but when trying to play with Movie Player, the system crashes in the same way. Playing with VLC does not show the picture, sound plays for 2 seconds, and system crashes also. In all cases, I cannot bring up the system monitor with the keyboard shortcut that I defined.

Video, also HD, plays fine in Youtube. I installed the 'restricted-extras' as suggested in one post. Compiling, making and linking stuff is a bridge too far for me. Any suggestion what could be the source(s) of the problem and how to solve it?

Thanks,
Merlijn

---

### Post by LowSky on 2011-09-02
1) What models are the webcams? With one or both connected what is the output of the this command from a terminal:

```
lspci
```

2) Open a terminal and copy and paste this very long command. Basically this is going to give you access to some software Ubuntu does not include in its software center by default.

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update && sudo apt-get install app-install-data-medibuntu apport-hooks-medibuntu
```

Next look for w32codecs (or w64codecs if you are using 64bit OS) in software center. This should help.

---

### Post by no2498 on 2011-09-02
make sure you have gstreamer 0.10 from the bad set installed
in your package manager look for gstreamer
you need the good set,bad set,ugly set plus the 0.10 from the bad set 
that should help cheese
if that does not help
open a terminal copy and paste
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese     click enter

you do need to close the package manager first

---

### Post by Merlijn Janssen on 2011-09-03
Hello LowSky and no2498,

Thank you for your help. I believe I did all you suggested, but get the same results: a crashing computer.

1) The webcam models are:
Creative VFO35O  &  A4 tech PK935. Both rather old. I do not mind buying a new one, but since the MTS video is not being played, I believe there is another issue to be solved first.

2) The output of lspci is:
00:00.0 Host bridge: Intel Corporation Sandy Bridge DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Sandy Bridge Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579V Gigabit Network Connection (rev 05)
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 2 (rev b5)
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation Cougar Point LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 05)
02:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)

3) I installed the w64codecs.

4) I installed:
libstreamer0.10-0-dbg
gstreamer0.10-plugins-base-dbg
gstreamer0.10-plugins-good-dbg
gstreamer0.10-plugins-bad-dbg
gstreamer0.10-plugins-ugly-dbg
gstreamer0.10-plugins-bad-multiverse-dbg
gstreamer0.10-plugins-ugly-multiverse-dbg
gstreamer0.10-gnomevfs

5) The command 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese' also crashed the system.

Any more ideas? 

Thank you,
Merlijn

---

### Post by no2498 on 2011-09-04
do you have the win 32 codes installed or and win ff
in a terminal type copy and paste
gstreamer-properties click enter

should only need to test v4l2

click video
try v4l and v4l2
use the bottom test button for each 1

---

### Post by Merlijn Janssen on 2011-09-04
Hi no2498,

Thanks for your reply.

I have the w32codecs installed. After reading your message, I also installed the WinFF GUI for FFMPEG. That didn't help.

gstreamer-properties yields in terminal:
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc'

In the window that opens, I tested Video/Default input. Device: Default. Pipeline v4l(2)src:
1) v4l: a window opens which reads: Could not get/set settings from/on resource. System hangs after that.
2) v4l2: a window opens Testing... Click Ok to finish. Progress bar is stuck at start. System hangs again.

I feel you are getting close to the root cause of the problem. But since I am new to Linux, I do not understand the messages and how to solve the issue. Do you have any idea?

Thank you for your help,
Merlijn

---

### Post by no2498 on 2011-09-05
only thing i can think of is you have a web cam program open/running like skype
? did you use the bottom test button in gstreamer-properties

---

### Post by Merlijn Janssen on 2011-09-07
Hi,
 
I decided to re-install the computer. 
 
First, I tried Ubuntu 10.4 32b. My ethernet (eth0) was not even found in this version.
 
Then, I tried Ubuntu 11.4 32b. This played the MTS files, and the gstreamer test showed webcam output. Skype video did not work out of the box, but there seems to be hope!
 
To confirm the issues with Ubuntu 10.10 32b, I reinstalled this version. And the computer crashed again on playing an MTS file.
 
So I will continue to use Ubuntu 11.4. I liked the user interface of 10.10 better, and it also seems faster, but perhaps I can customise it to my liking.
 
Thank you very much for your ideas. I very much appreciate it.
Merlijn

---

### Post by Merlijn Janssen on 2011-09-08
Hi,
 
For other people with the same questions:
 
The webcam in Skype, I got working in a terminal with:
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
 
You can make a script file ´SkypeLauncher.sh' in the home folder to call Skype automatically:
#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
 
Then change the permissions on the script file with chmod to be able to execute it. 
Then make a launcher on the desktop that calls the script with the command:
./SkypeLauncher.sh
 
As mentioned, Ubuntu 11.04 was the only version of Ubuntu where the MTS video, ethernet, and webcam were working on this new computer. But I preferred the user interface of 10.10. It is possible to use Ubuntu 11.04 using the Ubuntu 10.10 user interface. Click the Off button on the top right and choose 'System Settings'. Then go to 'Login screen', unlock it, and choose 'Ubuntu Classic (without effects)' for a fast and crisp interface.
 
I am starting to love Ubuntu!

---

