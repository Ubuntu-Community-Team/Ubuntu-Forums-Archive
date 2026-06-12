---
title: "new kernels don't boot"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by adobrakic on 2011-02-15
hello all, 

i'm currently running 64-bit Ubuntu using 2.6.35-24 kernel. when it updated to 2.6.37-12, every time I would try to boot into that kernel, it would take me to a black screen saying something like "ado@Ado-PC tty1," and ask me for my login. i would log in fine, but then it just stays at that screen. pretty much like having terminal at full-screen and thats it. i just thought it was that specific kernel and didnt pay much attention to it. however, now that it updated to 2.7.38-3, it's still doing the same thing and idk what the problem is. 

any suggestions?

---

### Post by Hippytaff on 2011-02-15
Do you still have and can you still boot into the 2.6.35-24 kernel?

What graphics card do you have?

---

### Post by coffeecat on 2011-02-15
I presume you mean 2.6.38-3, not 2.7.38-3. Kernels 2.6.37-12 and 2.6.38-3 are from Natty/10.04 testing whereas the 2.6.35 series are from Maverick. Which version of Ubuntu are you using?

---

### Post by adobrakic on 2011-02-15
> **Hippytaff said:**
> Do you still have and can you still boot into the 2.6.35-24 kernel?
What graphics card do you have?

Yup, that's what I've been using instead of the two newer kernels that came up.

```
ado@Ado-PC:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 RAID bus controller: ATI Technologies Inc SB700/SB800 SATA Controller [Non-RAID5 mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS880 [Radeon HD 4200]
02:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
04:06.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
ado@Ado-PC:~$ 

```

> I presume you mean 2.6.38-3, not 2.7.38-3. Kernels 2.6.37-12 and 2.6.38-3 are from Natty/10.04 testing whereas the 2.6.35 series are from Maverick. Which version of Ubuntu are you using? 

Sorry, yeah.. i misread it. I'm using 10.10.

[img]http://img822.imageshack.us/img822/8710/screenshotstartupmanage.png[/img]

The kernels after 2.6.35-24 are the ones that don't work.

---

### Post by Hippytaff on 2011-02-15
What graphics card do you have?

---

### Post by adobrakic on 2011-02-15
01:05.0 VGA compatible controller: ATI Technologies Inc RS880 [Radeon HD 4200]

---

### Post by coffeecat on 2011-02-15
This video card...

> **adobrakic said:**
> 01:05.0 VGA compatible controller: ATI Technologies Inc RS880 [Radeon HD 4200]

...runs OK with the 2.6.37 and 2.6.38 kernels in Natty. I have that video chipset in my Acer laptop, but I don't know about running the Natty kernels in Maverick.

Why are you trying to run the 2.6.37 and 2.6.38 kernels in Maverick? How did you install them?

---

### Post by adobrakic on 2011-02-17
They just installed with an update in terminal. I've added a few sources with Ubuntu Tweak, but nothing I can think of that would download that.

---

### Post by coffeecat on 2011-02-17
> **adobrakic said:**
> They just installed with an update in terminal. I've added a few sources with Ubuntu Tweak, but nothing I can think of that would download that.

It is not a good idea to try to run the Natty kernels in Maverick unless you have a specific reason. Clearly, they are not working for you. What sources did you add with Ubuntu Tweak? Did you have a reason for adding those sources?

---

### Post by adobrakic on 2011-02-23
I didn't add those repos for any specific reason. I added a bunch, such as VLC, daily chromes builds, etc.. I just can't figure out which one is downloading the Natty kernels. Can someone point it out, please?

> # deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) maverick main
deb [http://ppa.launchpad.net/ferramroberto/vlc/ubuntu](http://ppa.launchpad.net/ferramroberto/vlc/ubuntu) maverick main
deb-src [http://ppa.launchpad.net/ferramroberto/vlc/ubuntu](http://ppa.launchpad.net/ferramroberto/vlc/ubuntu) maverick main


---

### Post by Hippytaff on 2011-02-24
None of them look like they are the culprit. They are all pointing to maverick.

---

### Post by coffeecat on 2011-02-25
> **adobrakic said:**
> I didn't add those repos for any specific reason. I added a bunch, such as VLC, daily chromes builds, etc.. I just can't figure out which one is downloading the Natty kernels. Can someone point it out, please?

You posted your sources.list file which usually doesn't contain sources for PPAs. Have a look in the /etc/apt/sources.list.d/ folder. There will be several *.list files there, one for each PPA. And/or, open Synaptic, Settings menu > Repositories > Other Software tab. Either of those will tell you what PPAs you have.

Another thing to check: have you enabled either of the proposed or backports repositories?

---

### Post by adobrakic on 2011-03-01
> **coffeecat said:**
> You posted your sources.list file which usually doesn't contain sources for PPAs. Have a look in the /etc/apt/sources.list.d/ folder. There will be several *.list files there, one for each PPA. And/or, open Synaptic, Settings menu > Repositories > Other Software tab. Either of those will tell you what PPAs you have.


There aren't any PPAs that don't have "ubuntu maverick" in them, except for the first four, which are:
- Canonical Partners
- Canonical Partners (Source Code)
- Independent
- Independent (Source Code)

> **coffeecat said:**
> 
Another thing to check: have you enabled either of the proposed or backports repositories?


I'm not sure what those are, but in the Updates tab in Software Sources, I have 'maverick-backports' disabled. 

All I can see in Synaptic are the 2.6.35 headers, the 2.6.37-* & 2.6.38-* aren't even visible from there. Yet they keep being installed. I just had 2.6.38-5 installed. -_-

---

### Post by adobrakic on 2011-03-02
Forget it, I did myself a favor and went ahead and reinstalled. Thanks anyway.

---

