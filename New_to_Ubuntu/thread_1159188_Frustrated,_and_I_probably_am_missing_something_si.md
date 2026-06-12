---
title: "Frustrated, and I probably am missing something simple."
date: 2009-05-14
forum: New to Ubuntu
---

### Post by Ericj1186 on 2009-05-14
I am running an AMD Athlon 64 Bit (I believe that's right) processor on an ABit KN8 SLi Motherboard.  I have two HDDs one is my main one for Windows with 139GB total, and the other is for everything else with 500GB total.  I have two video cards running in SLi mode (Nvidia Gefore 250 GTS) and a Creative Sound Blaster X-Fi (Fata1ity) sound card.    I have googled this problem, and I have seen it come up a few times on these boards, but I didn't see anything that worked for me.    So, I installed Ubuntu 9.04.  When installing, it didn't notice Vista on my hard drive that it is installed on, but on the 500GB HDD.  I proceeded, and the GUI came up.  The first time I installed it, I was able to go to Windows once or twice, but when I updated my video card to the one Ubuntu suggested, it would only boot in the terminal.  I was advised to try reformatting and reinstalling, which I did.  This time I updated the driver right away, restarted, into terminal.    In the terminal I get the following messages:   >  Boot from (hd1,4) ext 3 fe8d35ae-1ebd-4988-8c56-88eea3bca305  Starting up.... Loading, please wait...  19+0 records in  19+0 records out   kinit: name_to_dev_t(/dev/disk/by-uuid/3c908[...]) = dev(8,22)  kinit: trying to resume from /dev/disk/by-uuid/3c908[...])  kinit: No resume image, doing normal boot...    Ubuntu 9.04   eric-desktop tty1    eric-desktop login:       I ran StartX, and got:    >  Fatal server error:  no screens found [...]    giving up.   xinit: no such file or directory (errno2): unable to connect to X server  xinit: No such process (errno3): Server error.      Then, I ran Sudo gdm, and it said GDM was already running.       Finally, I load the "sudo fdisk /dev/sda" and press P for printing. What loads is the following:  > Disk /dev/sda: 500.1GB, 500107862016 bytes 255 heads, 63 sectors/track, 60801 cylinders Units = cylinders of 16065 * 512 = 88225280 bytes Disk identifier: 0x63d68e97  Device Boot - /dev/sda1 * Start - 1 End - 60802 Blocks - 488385024 Id - 7 System - HPFS/NTFS  The thing is this is not the correct drive. This is my secondary drive, which has no files on it except games and such. The drive that has Linux, its Swap, and Windows is the other drive, which GParted shows.  As I said, I am sure I am missing something really simple, but any help would be great.  Thanks.

---

### Post by Regenweald on 2009-05-14
try
```

sudo dpkg-reconfigure -phigh xserver-xorg

```in the terminal. That may help with the fatal server eror.

---

### Post by Ericj1186 on 2009-05-14
Thanks for the quick reply.  I will try that when I get home after work and post the results.

---

### Post by Ericj1186 on 2009-05-14
Sorry for the double post.  Here is what came back when I typed that:

> xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/x11/xorg.conf.20090514161615

I typed StartX again and got this:

> 
xor-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd)
Before reporting problems, check http:wiki.x.org
to make sure you have the latest version.

Markers: (--) probed, (**) from config file, (==) default setting, (++) from command line, (!!) notice, (II) informational, (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log File:"/var/log/Xorg.0.log", Time: Thu May 14 16:18:38 2009
(==) Using config file: "/etc/X11/xorg.conf"
Primary device is not PCI
(EE) No devices detected.

Fatal server error:
No screens found

Please consult the The X.Org Foundation support
at [http://wiki.x.org](http://wiki.x.org)
for help.

Please also check the log file at "/var/log/Xorg.0.log" for additional information [cut off] on.

ddxSigGiveUp: Closing log
giving up.
xinit: No such file or directory (errno2): unable to connect to X server
xinit: No such process (errno3): Server error.

eric@eric-desktop:~$

Does that help?

---

### Post by Regenweald on 2009-05-14
Check this thread.

[http://ubuntuforums.org/archive/index.php/t-506363.html](http://ubuntuforums.org/archive/index.php/t-506363.html)

if all you get is the terminal when you boot, try the first command i gave then the one in the thread.

---

### Post by Ericj1186 on 2009-05-14
Here is my results from that:
> 
Using X configuration file: "/etc/x11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.  Device section "Configured Video Device" must have a Driver line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/x11/xorg.conf'
When I reboot, I get the same terminal as before.  Sorry for being a bother.

Also, I can get to the GUI if I use my Live CD, which allows me to access my Ubuntu partition.  Is there anything I can do from this in that may help?

---

### Post by Ericj1186 on 2009-05-14
Not sure if anyone saw the extra bit I added about having access to my Linux files.  I'm sorry to be a bother, but I really want to resolve this issue.

---

### Post by TheBuzzSaw on 2009-05-14
Eric, you're a retard. Get out of the Linux community while you still can.

- Buzz

/just-kidding-i-am-friends-with-eric

---

### Post by Ericj1186 on 2009-05-14
I thought you actually registered just to post that.  

I am trying to revert to 8.04 and see if that works.

---

### Post by bacardiandwatermelon on 2009-05-15
I see you are in tty1, what happens if you hold down ctrl + alt + f7? Ultimately you could just reinstall and not choose the driver it suggests.. Maybe?

---

### Post by Ericj1186 on 2009-05-15
I am using a Microsoft Natural Erogonomic 7000 keyboard, and none of the F-Buttons work unless software is installed/I never actually noticed them work.  I can try another keyboard, but what should this do?  

I installed 8.04, and it seems my errors are solely driver based because when I installed a sound driver, on 8.04, I was unable to actually boot back because it stopped loading on "Loading Hardware" (see my other [thread]("http://ubuntuforums.org/showthread.php?t=1159768")).  I needed this driver that stopped 9.04 from working to even use the Visual Effects, much less to play games.

Can you or someone else help me install drivers, so I can have some functionality?

I appreciate any replies.

---

### Post by Regenweald on 2009-05-15
I'd suggest firstly making sure your hardware is compatible by running the live CD first. If you've already done that, try running one card rather than SLI mode so you'll be sure it's SLI that mucking up. If you can get a fully functioning system running just the one Nvidia card, I'm sure that will give you the inspiration to keep pushing towards sorting this SLI issue properly. Stability before performance :)

---

### Post by Ericj1186 on 2009-05-15
I found a guide that tells me how to run SLi mode on Linux.  When I read that you should disable SLi FIRST before even installing Linux, that gave me the idea to try it like that.  I will give that a try with Ubuntu 9.04 again, since I messed up 8.04.  I'll post results once I get them.  Thanks for all the help.  I really appreciate it.

---

### Post by Regenweald on 2009-05-15
As you can see, i keep popping in and out of the forums, will keep track of the thread though. Hope you are successful :) don't worry, it gets infinitely easier pretty quickly...

---

### Post by Ericj1186 on 2009-07-20
Well after a few months of work, I fixed the issue!

Essentially, Ubuntu was seeing two video cards and freaked out and made neither card the default.  To fix the problem I added the following, so I am not sure what works exactly.  I am just reposting in case anyone has this issue in the future:

```
lspci
``` - to get my video card ports.  On mine, it was PCI 4:00.0 and 5:00.0.

After that I edited the xorg.conf:

```
sudo nano /etc/X11/xorg.conf
```

Under device, I added the line:

```
BusID        "5:00:0"
```  When I added 4:00:0 or anything other than that one in the code, it killed my display.

After that, I added these two to the Screen section:
```
option      "MultiGPU""on"
option                 "sli" "on"  


```

From there, I ran

```
startx
``` - Which said X failed, so I did:
```
sudo [...]gdm start
```

And the gui came back up.  Awesome, awesome, awesome.  If anyone sees any errors in my codes, please tell me so I can fix them, all of this was from memory.  Hopefully anyone with Nvidia cards/sli issues can use this.

Thanks for all the help.

---

### Post by Ericj1186 on 2009-08-01
DAMN.... Not sure what happened, but today, I went play something on Youtube, and the sound wasn't working.  I saw that my volume had an X across it, so I clicked that and it said the GStreamer or something plugin wasn't installed.  I head to Sound Preferences, and there are no default devices for sound.  I type in lshw -C sound, and it says my two cards (onboard) RealTek and (installed card) Creative Labs Soundblaster X-Fi are unclaimed.


So, I read this was linked to the new Kernel (2.6.28-14).  So, I reverted to 2.6.28-13, where I at least had sound.  When it restarted, I got back to the black terminal screen, with no way to restart the GDM...

Can anyone help?

Update:  So, under the new Kernel (2.6.28-14), I can get the GDM to load, but I have no sound...

Can anyone help?

---

