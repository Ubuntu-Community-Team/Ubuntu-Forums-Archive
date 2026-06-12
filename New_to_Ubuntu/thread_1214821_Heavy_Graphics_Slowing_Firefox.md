---
title: "Heavy Graphics Slowing Firefox"
date: 2009-07-16
forum: New to Ubuntu
---

### Post by E.T.Smith on 2009-07-16
When using Firefox on my machine, websites with a large number of video elements slow down the application. Especially damning are lots of embedded youtube videos; more than three on the same page can freeze or crash Firefox. One of these crashes usefully gave an error message saying that my browser only had 64MB of RAM available for processing graphics, which is significantly less than the 1000 or so MB's in my system. I run a dual-boot system, and under Windows Firefox suffers no difficulty at all, so clearly its a software issue. Is there a method to up the amount of RAM used for graphics?

Running Ub' 8.04 on an Intel Pentium 4 desktop.

---

### Post by halitech on 2009-07-16
upping the video ram depends on the type of card you have. if its onboard, you may have an option in the bios to up it but some older boards capped out at 64meg. If its an add on card then the only way to change it is by installing a new card. The system ram is different then the video ram.

What video card do you have?

Are you running compiz?

---

### Post by E.T.Smith on 2009-07-16
> **halitech said:**
> What video card do you have?

Are you running compiz?

I don't know the answer to either of those questions. How do I find out?

Again, I point out that Firefox doesn't have this problem under Windows, so I'm confused how the same hardware can have different limitations under the different systems.

---

### Post by halitech on 2009-07-16
to find out what video card, open a terminal and post the output of
```
lshw -c video
```
to check compiz, go to System - Admin - visual effects (I think) and set it to none.

depending on things like compiz and video drivers can make things not run as smoothly

---

### Post by NightwishFan on 2009-07-16
Go to: System -> Preferences -> Appearence

The last tab is desktop effects, set it to 'None' and see if your performance issue is resolved. If so, then it was a Compiz issue.

Also you can try to disable smooth scrolling. It should be in the firefox options somewhere.

---

### Post by halitech on 2009-07-16
> **NightwishFan said:**
> Go to: System -> Preferences -> Appearence

The last tab is desktop effects, set it to 'None' and see if your performance issue is resolved. If so, then it was a Compiz issue.

Also you can try to disable smooth scrolling. It should be in the firefox options somewhere.

Thanks, I'm using XFCE so my options are a little different for tabs.

---

### Post by NightwishFan on 2009-07-16
Ah I see you were just explaining that you are on XFCE. I got distracted and just answered. :D

Does disabling smooth scrolling help?

---

### Post by halitech on 2009-07-16
I'm not the one with the issues, my card works fine on my system :)

---

### Post by E.T.Smith on 2009-07-16
> **halitech said:**
> to find out what video card, open a terminal and post the output of
```
lshw -c video
```
Unfortunately, that seems to have resulted in a long error message:
```
Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.12.01)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
```

---

### Post by NightwishFan on 2009-07-16
Try the hardinfo command I gave for a simple solution. If you want to try lshw try:

```
sudo lshw | grep network
```

---

### Post by E.T.Smith on 2009-07-16
As instructed, I've turned off both smooth scrolling and visual effects. Unfortunately, the problem persists.

---

### Post by halitech on 2009-07-16
> **E.T.Smith said:**
> Unfortunately, that seems to have resulted in a long error message:
```
Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.12.01)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
```

did you put spaces where I had spaces? it should have brought back info like this
```
daryl@debian:~$ lshw -c video
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: RS690 [Radeon X1200 Series]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list
       configuration: driver=fglrx_pci latency=64 module=fglrx

```

try ```
lspci
```

---

### Post by m_ad on 2009-07-16
I'm actually having the same problem as the OP. Firefox is so slow it's almost unusable in 9.04. I have compiz enabled with minimal effects (open/close/min animations is basically it). I don't see how this could cause such a slowdown in firefox.

 Not trying to take over the thread, but for notes..

```
[matt@matt-desktop:~]$ lshw -c video
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: C51 [GeForce 6150 LE]
       vendor: nVidia Corporation
       physical id: 5
       bus info: pci@0000:00:05.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia
```

---

### Post by NightwishFan on 2009-07-16
Well chaps, I have to sign off, sorry I cannot be of more help, I hope you fix it. Perhaps you have the web page 'zoomed in'. That causes slowdowns. There is a zoom option under view menu in Windows.

---

### Post by halitech on 2009-07-16
> **m_ad said:**
> I'm actually having the same problem as the OP. Firefox is so slow it's almost unusable in 9.04. I have compiz enabled with minimal effects (open/close/min animations is basically it). I don't see how this could cause such a slowdown in firefox.

 Not trying to take over the thread, but for notes..

```
[matt@matt-desktop:~]$ lshw -c video
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: C51 [GeForce 6150 LE]
       vendor: nVidia Corporation
       physical id: 5
       bus info: pci@0000:00:05.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia
```

will keep it short here, maybe follow along or start a thread of your own for faster assistance :)

did you check and see if there is a restricted driver for your card or if the Nvidia drivers will work (185.xx I think is the latest)

---

### Post by E.T.Smith on 2009-07-16
> **halitech said:**
> did you put spaces where I had spaces?

Yes, I copied and pasted directly from the post above, so its exactly as presented.

> Try ```
lspci
```

Here's the output from that command:

```

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 81)

```

---

### Post by halitech on 2009-07-16
ok, so your video card is an Intel

[color="red"]00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
[/color]

so no restricted drivers and the 9.04 drivers aren't the best from what I've seen lately. Open synaptic and see if the intel drivers are installed

---

### Post by m_ad on 2009-07-16
> **halitech said:**
> will keep it short here, maybe follow along or start a thread of your own for faster assistance :)

did you check and see if there is a restricted driver for your card or if the Nvidia drivers will work (185.xx I think is the latest)

Yeah, I'm using the latest driver, version 180. I plan to revert back to 8.04 this week due to *many* issues in 9.04. I think I'll stick to the LTS from now on.

---

### Post by halitech on 2009-07-16
> **m_ad said:**
> Yeah, I'm using the latest driver, version 180. I plan to revert back to 8.04 this week due to *many* issues in 9.04. I think I'll stick to the LTS from now on.

seen many people do the same thing, especially those with older video cards or intel cards as 9.04 wasn't all it was cracked up to be.

---

### Post by E.T.Smith on 2009-07-16
> **halitech said:**
> so no restricted drivers and the 9.04 drivers aren't the best from what I've seen lately. Open synaptic and see if the intel drivers are installed

I've got synaptic open, but where do I look for the Intel drivers? What is their file name?

---

### Post by eMJayy on 2009-07-16
Your Intel graphics chip is integrated into the motherboard and uses a portion of your system's Ram to handle 2D and 3D graphics. It doesn't have it's own dedicated memory. This link from Intel has some info on how memory allocation is handled by your graphics chip.

[http://www.intel.com/support/graphics/intel845g/sb/cs-009088.htm](http://www.intel.com/support/graphics/intel845g/sb/cs-009088.htm)

---

### Post by halitech on 2009-07-16
do a search for intel. I'm not sure of the exact name

look here for help

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

[http://ubuntuforums.org/showthread.php?t=1152095](http://ubuntuforums.org/showthread.php?t=1152095)

---

### Post by E.T.Smith on 2009-07-16
> **halitech said:**
> do a search for intel. I'm not sure of the exact name

That still gives a couple hundred results. To back track a bit, what's the nature of the this approach? I'm gathering it has something to do with the Intel graphics not running so well with the default generic drivers under Ubuntu, while the proprietry ones it has in Windows aren't so limited, and this is an attempt to get the propietry drivers installed under Ub'.

> look here for help

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

[http://ubuntuforums.org/showthread.php?t=1152095](http://ubuntuforums.org/showthread.php?t=1152095)
These guides seem mainly about fixing bugs in 9.04; do they still apply to 8.04, which I am running under?

---

### Post by halitech on 2009-07-16
I missed that you were running 8.04, Intel chips are supposed to work fine in 8.04 ...

I'm guessing that you are using the VESA driver instead of the intel driver which will give poorer proformance. Do you know how much ram you have in the system and how much is allocated to the video?

---

### Post by E.T.Smith on 2009-07-16
> **halitech said:**
> 
I'm guessing that you are using the VESA driver instead of the intel driver which will give poorer proformance. Do you know how much ram you have in the system and how much is allocated to the video?

1009.4 MB RAM overall. I'm sorry, but I don't know how much is reserved for graphics.

You're hunch may be right. Searching in synaptic for VESA turns up the following installed package: 
```

X.Org X server -- VESA display driver
version: 1:1.3.0-4ubuntu4

```

---

### Post by halitech on 2009-07-16
ok, open a terminal again and post the result of```
free -m
```
make sure you put the code tags around it so its easier to read

---

### Post by E.T.Smith on 2009-07-16
Here it is:

```

             total       used       free     shared    buffers     cached
Mem:          1009        910         99          0         33        398
-/+ buffers/cache:        477        532
Swap:         1098          0       1098


```

---

### Post by halitech on 2009-07-16
ok, thats the same but what do you physically have installed? 1024m would be a gig which would mean you have 15m going to the video card.

might be time to reboot into the bios and see what its saying.

---

### Post by Garyhans on 2009-07-16
There are two things you could try.

A. In Firefox goto tools/addons/extensions and disable Ubuntu Firefox Modifications close and then open firefox.
B. You could install Firefox 3.5 which is a great improvement over the current Version.

[http://compustorm.no-ip.org/2009/07/howto-install-firefox-3-5-on-ubuntu-jaunty/](http://compustorm.no-ip.org/2009/07/howto-install-firefox-3-5-on-ubuntu-jaunty/)

---

### Post by E.T.Smith on 2009-07-16
> **halitech said:**
> ok, thats the same but what do you physically have installed? 1024m would be a gig which would mean you have 15m going to the video card.

might be time to reboot into the bios and see what its saying.

My machine has the maximum possible installed RAM (a Gig I think), but its borderline obsolete (about 6 years old), so I'm not sure how it compares to a newer machine.

How do I slow the bios to render it readable? It scrolls by far too fast on a reboot.

---

### Post by halitech on 2009-07-16
thats not the BIOS, thats POST. When you first start the machine, press F12 and that should take you into the BIOS and then look for an option on the video card. What model of laptop is it?

---

### Post by m_ad on 2009-07-18
I'm curious, did the OP get this fixed? After disabling the Ubuntu Firefox Addon, I've noticed a major improvement.

That doesn't make sense :lolflag:

---

### Post by Garyhans on 2009-07-19
I don't think it's been fixed at present. And yes it is strange that disabling the Ubuntu Firefox Modification does improve performance very much so.

---

### Post by E.T.Smith on 2009-07-21
Sorry, I wasn't able to get the BIOS information so I had no further to go. However, I have turned off the Firefox Ub' Addons and that has improved things incrementally.

> **halitech said:**
> thats not the BIOS, thats POST. When you first start the machine, press F12 and that should take you into the BIOS and then look for an option on the video card. What model of laptop is it?

If you're still following this thread ... its an old gateway desktop. F12 doesn't bring up any info, but that may be because its a dual-boot.

---

