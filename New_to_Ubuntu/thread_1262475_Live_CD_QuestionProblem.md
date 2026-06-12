---
title: "Live CD Question/Problem"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by Marlowe221 on 2009-09-09
Well I downloaded the file and I am typing this in Ubuntu 9.04 off the live CD!!

It's pretty cool so far but for one thing... When I try to change to the proprietary driver on my  ATI 3200 video card so I can play around a little more, it says it's searching for a driver and then it tells me that it could not be found. Interestingly enough I can see the driver listed in the Hardware Drivers window.... 

Is this because I'm working off the CD and it can't download it or what?

Thanks

---

### Post by mc4man on 2009-09-09
Not sure about with ati but anyway...

Go to System -> Admin.. -> Software Sources and enable all the Ubuntu software boxes and disable the 'cdrom' source. Click close and reload.

Then see if you can dl and install the driver. If so it will say you need to restart which you obviously can't do.

Just log out instead and after you're logged back in the driver will have been loaded even though it still will say to restart.

( I do this all the time with nvidia on a 9.04 live cd, though as said don't know about ati which has some issues in 9.04 in a real install

---

### Post by nandemonai on 2009-09-10
> **Marlowe221 said:**
> Well I downloaded the file and I am typing this in Ubuntu 9.04 off the live CD!!

It's pretty cool so far but for one thing... When I try to change to the proprietary driver on my  ATI 3200 video card so I can play around a little more, it says it's searching for a driver and then it tells me that it could not be found. Interestingly enough I can see the driver listed in the Hardware Drivers window.... 

Is this because I'm working off the CD and it can't download it or what?

Thanks

LiveCDs are not persistent anyway so even if you manage to install the driver in the LiveCD it wont be there next boot.

Unless you're planning on leaving this machine on 24x7 with the Live CD on then I suggest you do an install. I believe you'll have much more luck that way. ;)

---

### Post by mc4man on 2009-09-10
You can get a decent idea of how the 'real' install will perform. While there are several other factors that would skew things one way or the other it certainly is worth seeing.


@Marlowe221
Karmic (9.10), which releases in about 5 - 6 weeks, will be  far superior to 9.04 in every which way.

---

### Post by Marlowe221 on 2009-09-10
I guess I just wanted to play around with the desktop effects a little... :)

So should I wait for the Karmic 9.10 version?

Edit: haven't heard this thing make a sound? Is that normal? or is my sound card not compatible? How do I tell?

---

### Post by nandemonai on 2009-09-10
> **Marlowe221 said:**
> I guess I just wanted to play around with the desktop effects a little... :)

So should I wait for the Karmic 9.10 version?

Edit: haven't heard this thing make a sound? Is that normal? or is my sound card not compatible? How do I tell?

Entirely up to you :P

As far as sound goes you should be hearing it yes. Might want to check the mixer levels and speaker connections etc.

Failing that, please post the output from this command in terminal:

```
lspci
```

---

### Post by mc4man on 2009-09-10
> 
So should I wait for the Karmic 9.10 version?

Not totally suggesting that, just thought I'd note what should be taken as a IMO. ( though I believe it to be clearly so.

Certainly wouldn't hurt to use jaunty a bit.

Did or were you able to install the driver, ect. or didn't try..?

---

### Post by LinuxRocks9.04 on 2009-09-10
Hi all, I'm also pretty new to the forums and Ubuntu, but about Marlowe's problem, when you install the driver, it should be stored on the cd, right? But if you're using a CD-R, and it's already non-reusable(because its been burned with data), how could you install the driver? 

(My apologies if I asked a obvious question...) :)

---

### Post by Marlowe221 on 2009-09-10
Video - Says it's installed but not in use. When I try to enable the desktop effects it tells me it can't do it

Sound - volume is turned up. I'm on a laptop so speakers are always connected. 

Version - how tough will it be to update to 9.10 from the current version?

Do I need the 64 bit version?

---

### Post by nandemonai on 2009-09-10
> **LinuxRocks9.04 said:**
> Hi all, I'm also pretty new to the forums and Ubuntu, but about Marlowe's problem, when you install the driver, it should be stored on the cd, right? But if you're using a CD-R, and it's already non-reusable(because its been burned with data), how could you install the driver? 

(My apologies if I asked a obvious question...) :)

The contents of the LiveCD are stored in memory when you boot from a live CD, nothing is re-written to the CD itself when you're using it. All changes are stored in memory so when you power off the machine, all changes are then lost.

---

### Post by Marlowe221 on 2009-09-10
info requested:

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Hewlett-Packard Company Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
08:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
08:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
08:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
08:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller
09:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

---

### Post by nandemonai on 2009-09-10
> **Marlowe221 said:**
> Video - Says it's installed but not in use. When I try to enable the desktop effects it tells me it can't do it

Sound - volume is turned up. I'm on a laptop so speakers are always connected. 

Version - how tough will it be to update to 9.10 from the current version?

Do I need the 64 bit version?


Video - That would be because of the lack of 3D restricted driver.

Sound - Please post the output from ```
lspci
``` in terminal so we can lookup support for your sound chip.

Version - Upgrading from version to version in Ubuntu is relatively painless in my experience. No reason to not use Jaunty for the time being ;)

---

### Post by nandemonai on 2009-09-10
> **Marlowe221 said:**
> info requested:

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Hewlett-Packard Company Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
08:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
08:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
08:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
08:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller
09:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```
Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
```

That's the one :)

Looks like this might fix the issue (on an install, not the LiveCD)

edit /etc/modprobe.d/alsa-base

add at the end of the file:

options snd-hda-intel model=laptop

reboot

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

EDIT:

Actually, you could try this to test..

From terminal:

```
gksudo gedit /etc/modprobe.d/alsa-base
```

add at the end of the file:

options snd-hda-intel model=laptop

Save then again in terminal:

```
sudo modprobe -R alsa-base && sudo modprobe alsa-base
```

Not 100% on this, I'm at work at the moment and can't test.

---

### Post by Marlowe221 on 2009-09-10
Right on - thanks for the help.

Gonna install to a partion. Just in case....

Results to follow...

---

### Post by Marlowe221 on 2009-09-10
Ummmm.... Ok this is a little scary looking:

If you continue, the changes listed below will be written to the disks.
Otherwise, you will be able to make further changes manually.

WARNING: This will destroy all data on any partitions you have removed as
well as on the partitions that are going to be formatted.

The partition tables of the following devices are changed:
 SCSI1 (0,0,0) (sda)

The following partitions are going to be formatted:
 partition #5 of SCSI1 (0,0,0) (sda) as ext3
 partition #6 of SCSI1 (0,0,0) (sda) as swap

Now I'm supposed to hit "Next" - I'm not going to lose Vista on the other partion when I do am I??

I partiioned of 30 GB or so of space, the goal being to be able to dual boot (and not lose Vista just yet).

---

### Post by mc4man on 2009-09-10
@ Marlowe221
looks like with ati your better off testing from an install, if things don't run as well as you hope as mentioned karmic promises to be much improved.

With nvidia there's no issue running the driver from a live cd as long as you've got a decent amount of ram to start
screen shows live cd with cube enabled and a windowed 720p video

---

### Post by longtom on 2009-09-10
> **Marlowe221 said:**
> 

Now I'm supposed to hit "Next" - I'm not going to lose Vista on the other partion when I do am I??

I partiioned of 30 GB or so of space, the goal being to be able to dual boot (and not lose Vista just yet).

Answer:

> 
This will destroy all data on any partitions you have removed as
well as on the partitions that are going to be formatted.

I don't know which partition Vista is on (can't see from here).  But you can see quite clearly which partitions are going to be affected.  Did you use the manual option of gparted?

I would also VERY strongly suggest, before anybody does anything to any partition to do a **comprehensive backup** of all which is important
to you.

Some good help:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)


Good Luck!!

---

### Post by Marlowe221 on 2009-09-10
Well, I've got Unbuntu up and running (I managed not to delete Vista). I like it a lot. Need to fix the colors though, I'm not much of a sepia guy...
 
The restricted ATI driver seems to work just fine - Compiz is up and running with only minor screen/window tearing in certain animations.
 
Now to work on the whole no sound thing....

---

### Post by Marlowe221 on 2009-09-11
> **nandemonai said:**
> ```
Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
```That's the one :)

Looks like this might fix the issue (on an install, not the LiveCD)

edit /etc/modprobe.d/alsa-base

add at the end of the file:

options snd-hda-intel model=laptop

reboot

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

EDIT:

Actually, you could try this to test..

From terminal:

```
gksudo gedit /etc/modprobe.d/alsa-base
```add at the end of the file:

options snd-hda-intel model=laptop

Save then again in terminal:

```
sudo modprobe -R alsa-base && sudo modprobe alsa-base
```Not 100% on this, I'm at work at the moment and can't test.

I tried to follow these directions but it tells me I do not have permission to edit the alsa-base.config file. I went into properties to change the permissions but found that they were greyed out and I could not change them. What do I do?

---

### Post by nandemonai on 2009-09-11
> **Marlowe221 said:**
> I tried to follow these directions but it tells me I do not have permission to edit the alsa-base.config file. I went into properties to change the permissions but found that they were greyed out and I could not change them. What do I do?

```
**gksudo** gedit /etc/modprobe.d/alsa-base
```

Were you prompted for a password with the above command from terminal? Are you running as the first created user (admin rights)?

---

### Post by Marlowe221 on 2009-09-11
It didn't ask for a password or anything. I am running as the user I created on installation. Should I be running under root??

It says I'm not the owner... What does that mean?

---

### Post by Marlowe221 on 2009-09-11
bump.... not sure what to do here. Google search was not terribly helpful...

---

### Post by nandemonai on 2009-09-12
Oops, my bad, wasn't at my Linux box at the time.

```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

You can run the above command from either terminal within Gnome or from the run prompt (alt-F2).

Edit: You don't need to run as root. The first user created at installation has admin rights. Any command run with sudo or gksudo (gui version of sudo) will have temporary root privileges.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

