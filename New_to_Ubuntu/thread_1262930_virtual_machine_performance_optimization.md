---
title: "virtual machine performance optimization?"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by pcrussell50 on 2009-09-10
for the past few years i've been dual booting.  i'm only just now playing with virtualization, and it has become very obvious to me that running two os'es is very demanding of resources.  my question is, _which_ resources? processor power? or memory?

i'm  running a 2.2Ghz core2 duo processor, which is not exactly a gaming-level processor, but it's got to be a pretty mainstream level of power, hopefullly it's not a disqualifier for smooth virtulaization.

but i've only got 1Gb of ram.  i could easily up it to 2 or 4Gb, but i don't want waste my money if the real issue is the processor.

anyone have good knowledge of exactly what is required to run a virtual machine smoothly?

i'm not a gamer, just web surfing and email.  and i know not to recode video with two os'es running at the same time, or that it will have to run slower if i do.

-peter

---

### Post by LowSky on 2009-09-10
you need RAM , the processor is mor than fine, a Core 2 duo is a great chip

4 GB should be a good amount to get and its about $50 on newegg

---

### Post by NightwishFan on 2009-09-10
A forums expert could tell you if Intel offers anything like this, because I only know AMD processors:

Learn if your bios has any virtualization extensions. I have a AMD-VT extension, and I enable it in bios and then enable it in Virtualbox-ose (which is a great program). My CPU actually is "idle" when running Karmic in Virtualbox.

The downside? When you are done with virtualization you have to reboot into bios and disable the extension, or normal CPU performance is reduced. You also have to remember to disable it in Virtualbox if you want to run a virtual machine and you turned off the VT in bios.

Other than that, try to close all normal programs and services that are not needed when running Virtual machine.

My machine:

Ubuntu 9.04 AMD64
AMD Athlon x2 3800+ at 2.0ghz
885 MB RAM
128 MB Integrated Nvidia

In Virtualbox I use:

Ubuntu Karmic 32-bit
AMD-VT Extension
384mb RAM
32mb VRAM

Performance is fine, even without VT it is usable, as one core handles Vbox and the other my normal OS.

---

### Post by NoaHall on 2009-09-10
I'd get more ram - or make sure you have a quite big swap, and no heavy programs running on either the VM or the host.

---

### Post by ashwinhgtx on 2009-09-10
**RAM**.

Increase your RAM to 4GB or at least if possible. Your processor is more than enough.

VirtualBox is one of the easiest to setup and use. The open source version is in the repositories. The proprietary but free to use version with extra features like USB support is available from the VirtualBox website.

Have fun.

---

### Post by XCan on 2009-09-10
Although I agree with NightwishFan that you should see if your CPU supports virtualization instructions, I don't think it will hit your performance noticably even if you stop using a VM. You should safely leave it on.

---

### Post by NightwishFan on 2009-09-10
I would not recommend leaving it on, but it shouldn't hurt anything. I think it will reduce some performance.

---

### Post by pcrussell50 on 2009-09-10
thanks gang.  memory ordered.

FWIW, i forgot to mention that the computer i'm using is:
macbook 3,1
2.2Ghz core2 duo
1 Gb ram, [until the 4Gb upgrade arrives :) ]
host OS is: osx 10.6 snow leopard, [supposed to do more parallel processing]

virtual box
guest OS is: jaunty

-peter

---

