---
title: "ebay items  easy cap and bluetooth usb dongle"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by gigaferz on 2009-09-16
ok so i bought this items about a month ago:

[http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=330341563494&ssPageName=STRK:MEWNX:IT]("http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=330341563494&ssPageName=STRK:MEWNX:IT")

usb bluetooth dongle
and :

[http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=390077459240&ssPageName=ADME:B:EOIBSA:US:1123]("http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=390077459240&ssPageName=ADME:B:EOIBSA:US:1123")

easycap 2.0

Now check this out:

fer@fer-desktop:~$ sudo lsusb
Bus 001 Device 005: ID 05e1:0408 Syntek Semiconductor Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 006: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 004: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 002 Device 002: ID 045e:009d Microsoft Corp. 
Bus 002 Device 003: ID 045e:028e Microsoft Corp. Xbox360 Controller
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


The syntek Semiconductor is the easycap usb 2.0 and obviously the bluetooth dongle is listed as well.

Now my question is how do i get to use them.

I Had many problems with the easycap 2.0 driver, but it worked.

I copied moviemaker from xp to my existing windows 7 but didnt work then tried vlc with ugly results (note: vlc is a really powerful tool, i just do not know how to use it). Until I found windows media encoder 9. 

Anywyas so back to ubuntu is there an easy way to use the easycap and the bluetooth?


I almost forgot!!!
i believe last year I found a thread and it was to get nautilus to use a script right clicking a file, the script converted the files into mp3  but from nautilus (does it make any sense?)

I would like to know how or where to go to learn to do a little extension for nautilus to right click any video to convert it to any other format  i mean, i can do it using the command line but just to right click it , would be awesome. besides anyone has seen that thread im talking about?

thanks in advance!

ps, also if I update my computer right now, am i gonna have to deal with the nvidia drivers?? because last time, i got tired of it and my solution was to install jaunty over hardy, so basically i do not wanna deal with nvidia drivers atm.

---

### Post by gigaferz on 2009-09-16
wow that was easy!!!!

#!/bin/sh
for arg 
do
ffmpeg -i "$arg" -b 300k -s 176x144 -vcodec mpeg4 -ac 2 -ab 128k -acodec libfaac /home/fer/Videos/3gpdump/"$arg".3gp
done


i just need to try it with multiple files!!!

---

### Post by gigaferz on 2009-09-19
please any help is welcome

---

### Post by gigaferz on 2009-09-22
for reals, nobody?

---

### Post by gigaferz on 2009-09-30
so there is no bluetooth capability in ubuntu??

What about video/sound capture???

There is no way???

---

### Post by gwalborn on 2010-01-05
There is plenty of support for bluetooth and USB in Ubuntu.  However, I have had no success (yet) with this device.   It is possible that it is not supported under Ubuntu (or any other Linux, for that matter).  If you find anything out, please let me know.

I am using a Kensington bluetooth dongle just fine.  I have also used a number of the "mini" bluetooth adapters available on eBay for $2-$3 just fine. Such as:

[http://cgi.ebay.com/Smallest-USB-2-0-Mini-Bluetooth-V2-0-EDR-Dongle-Adapter_W0QQitemZ250513038907QQcmdZViewItemQQptZLH_DefaultDomain_0?hash=item3a53bd9e3b](http://cgi.ebay.com/Smallest-USB-2-0-Mini-Bluetooth-V2-0-EDR-Dongle-Adapter_W0QQitemZ250513038907QQcmdZViewItemQQptZLH_DefaultDomain_0?hash=item3a53bd9e3b)

I'm going to do a little digging around for the Syntek device.  Hopefully there is some way to make it "go".

Gary Walborn
[email]gwalborn@gmail.com[/email]

---

### Post by anewguy on 2010-01-05
I found another thread that may be of interest to you:

[http://ubuntuforums.org/showthread.php?t=924504](http://ubuntuforums.org/showthread.php?t=924504)

Here's a post from page 2 of that thread:

Old July 23rd, 2009 #18
busman.guru
First Cup of Ubuntu

Join Date: Jan 2009
Beans: 1

Re: Linux driver for EasyCap USB2.0 Video Adapter DC60
For me, the easycap USB2.0 works fine (kernel 2.6.23)... just use:

Syntex DC-1125 (1.4.0 not the last version)
[http://sourceforge.net/projects/syntekdriver/files/](http://sourceforge.net/projects/syntekdriver/files/)

Then apply two patch's:
(add support for the easycap, more specifically using lsusb: ID 05e1:0408 Syntek Semiconductor Co., Ltd)
[http://www.ivor.org/stk0408-1.patch](http://www.ivor.org/stk0408-1.patch)
(ntsc compability)
[http://www.bentrask.com/NTSC.diff](http://www.bentrask.com/NTSC.diff)

Then compile using the syntex instructions, if all goes normally you should create a kernel extension (.ko), to load it do:
sudo insmod kernelextension.ko

plug your camera and check dmesg, normally you camera is in /dev/vide0 or /dev/video1, I got 30fps, it doesn't work very nice with opencv but with mplayer the image is very nice...
enjoy!, Busman


And this post from page 3 of the thread:

Old September 24th, 2009 #22
romeshj
First Cup of Ubuntu

Join Date: Sep 2009
Beans: 1

Re: Linux driver for EasyCap USB2.0 Video Adapter DC60
I was having a real hard time trying to view video off a DC60 from a PC running Ubuntu 9.04 Desktop, and the post by Busman was extremely useful. Busman gives 2 patches that should be applied. My problem was that i applied only the patch at [http://www.ivor.org/stk0408-1.patch](http://www.ivor.org/stk0408-1.patch)
and not the patch at [http://www.bentrask.com/NTSC.diff](http://www.bentrask.com/NTSC.diff)

After applying both patches i could view NTSC video at 25 and 30 fps without any problem with mplayer. really smooth!! Thanks, Busman.

Environment used was as follows:
- the latest stk driver v2.2 obtained from
-r 82 svn co https: / / syntekdriver.svn.sourceforge.net / svnroot / syntekdriver / trunk / driver syntekdriver
with the above two patches applied.
- The video source used was a DVD player (NTSC format) - Composite video output.
- mplayer was invoked with following syntax:

mplayer tv:// -tv driver=v4l2:width=320:height=240:fps=25utfmt=rgb 24:device=/dev/video0

Only 640*480 resolution worked despite the resolution specified in the syntax. Also, when i tried to quit mplayer, the application got frozen. You can issue a "Ctrl-Z" followed by "exit" to exit the shell and re-launch mplayer.

I tried xawtv as well. It displays garbled screen with default invoke. Some websites mention that the xawtv output is de-interlaced with DC60. However, the application closes smoothly on user's command.

The audio capturing for DC 60, however, didnt seem to work under Windows XP or Ubuntu. There seems to be no audio support in the stk driver.

url00, it seems the NTSC patch should be applied to the file "stk11xx-dev-0408.c".

Overall, great quality for a cheap capture device!!
romeshj is offline Report Post Reply With Quote Multi-Quote This Message Quick reply to this message
romeshj
View Public Profile
Send a private message to romeshj
Find More Posts by romeshj
Add romeshj to Your Contacts


The thread still appears to be active - you may want to check it out.

BTW, I did a Google search with Syntek usb 05e1:0408 to find this. If you don't know, the 05e1:0408 are the unique USB manufacturer and device id's for your device. I am not familiar with it at all, so I just went from that. It would appear your device is a video capture device that connects via USB? For your bluetooth device I don't have any suggestions yet.

Dave :)

---

