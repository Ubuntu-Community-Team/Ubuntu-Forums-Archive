---
title: "Problem whilst Installing Ubuntu Studio"
date: 2010-06-19
forum: New to Ubuntu
---

### Post by Smithernz on 2010-06-19
Hi. I'm completely new with linux, but I've been meaning to get round to giving it a go. I downloaded Ubuntu Studio, as I liked the sound of its audio editing capabilities, and I thought it had installed fine. Then, when I loaded it up from the GRUB bootloader, my screen just went black, although I could hear that it was still running. What am I doing wrong?

---

### Post by anewguy on 2010-06-19
At the grub menu, select the recovery mode so that you get to a text login.

After logging in, do the following:

lspci | grep  VGA <press enter>

Post the output back here.  There are some known problems with some Intel graphics and drivers/work around for others.  The lspci is asking Ubuntu to "list" (ls) all know PCI devices, then the "|" is redirecting the output to the grep command, which we are asking to only show lines containing the string "VGA".

Dave ;)

---

### Post by Smithernz on 2010-06-19
It seems like it hasn't properly set up my kepboard, so I cant find how to get the '|' to work. Sorry about this. Any suggestions?

---

### Post by anewguy on 2010-06-19
It will create a lot of output instead of just the line we want, but you can always just open a terminal window and type:

lspci <press enter>

copy and paste that output back in a reply here and we'll go from there.

Dave ;)

---

### Post by anewguy on 2010-06-20
You may also want to try this as a test:

when the grub menu comes up, press the "e" key to edit the default selection.

Where you see something like "quiet splash" change it to:

quiet nosplash nomodeset

Then follow the prompt on the screen to boot with those modifications (ctrl-x ??).  If that works we can get you through a simple edit and a single following command so this becomes permanent.

Dave ;)

---

### Post by Smithernz on 2010-06-20
Right, have managed to get the lspci command to give me this:

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

Hope this helps.

I tried the quiet nosplash nomodeset, but it had no effect that I could see.

I have also managed to load up the desktop on the failsafex graphics mode, running low graphics I think.

Andrew

---

### Post by anewguy on 2010-06-20
Ah....it's the Intel 855 graphics.  There seem to be known problems with it and 10.04.  I know there are some posts on the forum about it, but let me do some searching as well and I'll get back to you.

In the mean time, you may want to check under thread tools and see if it allows you to change the title of the thread.  If so, I would change it to "10.04, Intel 855 Graphics help needed" as that might get more responses.  

Dave ;)

---

### Post by Smithernz on 2010-06-20
Thanks very much.

I've looked but I can't change the title of the thread. I know it would be wrong pretty much as soon as I submitted it!

---

### Post by anewguy on 2010-06-20
EDIT:

I feel stupid!  Check in System/Administration/Hardware Drivers and see if there is a driver for your video card and if so enable it and reboot.

I found something else you may want to try - I know it doesn't match "855" but I think it's worth a shot:

Do the same "e" to start editing the boot line:

delete the quite and nosplash

add:

i915.modeset=0 

Then follow the instructions on the screen to boot (can't remember the sequence off the top of my head - I'll edit back here as I'm going to try it just so I can see right after I post this).  EDIT:  As far as the boot goes, it is ctrl-x after you made the modifications on the boot line.

Dave ;)

---

### Post by Smithernz on 2010-06-20
Nope. No luck with either of these I'm afraid.

---

### Post by anewguy on 2010-06-21
I'm not sure what's going on (it will probably end up being something simple that I just don't know).

I would do the following:

- open a terminal window again

- type:

lshw -C display <press enter> and post the output back here.  We are asking Ubuntu to list hardware described as "display".  This differs from the lspci in that it will show other information, including the driver being used.

lsmod <press enter> and post the output back here as well.  We are asking Ubuntu to list loaded kernel modules.  Given the driver from the lshw output, we can check to see if the driver module is getting loaded.

Dave ;)

---

### Post by k3lt01 on 2010-06-21
I have that card and filed [this bug report on it]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/566379")

So instead of this> **anewguy said:**
> add: i915.modeset=0 
make the =0 a =1 and try that.

Let us know how you go.

@ Dave, thanks for yesterday. You are indeed a scholar and a gentleman.

---

### Post by anewguy on 2010-06-21
Thanks so much for posting in this thread!  I don't have the 855 so it's hard for me to debug a problem with it since I can't try some things myself.  Any help in this thread is GREATLY appreciated!

Dave ;)

---

### Post by anewguy on 2010-06-22
Indeed, what k3lt01 seems to be the solution, as noted in this how-to:

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes]("https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes")

It deals specifically with issues with 10.04 and Intel integrated graphics including the 855.

Sorry I didn't find it earlier.

Dave ;)

---

### Post by Smithernz on 2010-06-22
Yep, that worked fine and loaded correctly! Thanks all! Will that change be permanent, or will I have to re-change it every time I want to boot?

---

### Post by k3lt01 on 2010-06-22
If you followed the instructions in the link I posted, which gives another link to check out, it will be permanent.

---

### Post by anewguy on 2010-06-22
> **k3lt01 said:**
> If you followed the instructions in the link I posted, which gives another link to check out, it will be permanent.

Thanks for the help in this thread!!  It was greatly appreciated!

Dave ;)

---

### Post by k3lt01 on 2010-06-22
Dave, that's what this community is all about, to me it is anyway. I believe "Pay it forward" is a good motto and it is what I try to do.

Have an excellent day gentlemen.

---

### Post by Smithernz on 2010-06-23
When opening etc/default/grub, it loads as Read Only, so I can't save my changes. How do I get around this?

---

### Post by k3lt01 on 2010-06-23
> **Smithernz said:**
> When opening etc/default/grub, it loads as Read Only, so I can't save my changes. How do I get around this?```
gksudo gedit /etc/default/grub
``` will open it with root privileges so you can edit it.

---

### Post by Smithernz on 2010-06-23
Right, thanks everyone very much, my problem has now been solved.

---

### Post by k3lt01 on 2010-06-23
> **Smithernz said:**
> Right, thanks everyone very much, my problem has now been solved.That's great.

---

