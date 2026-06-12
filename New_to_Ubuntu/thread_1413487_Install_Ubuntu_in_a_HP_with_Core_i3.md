---
title: "Install Ubuntu in a HP with Core i3"
date: 2010-02-22
forum: New to Ubuntu
---

### Post by estani on 2010-02-22
Hello everyone,

I just got an Hp dv6 2150us with Core i3 (2.13GHz 4Gb RAm (DDR3 SDRAM (2 DIMM)320 Gb (7200 rpm). I have read that some people have had some troubles while they were trying to install Ubuntu. Since it is my first time installing Linux (and I really want to get Ubuntu) I would like to ask if someone has try to install Ubuntu in a machine like mine and had succeed?? If there is! do you have any suggestions, recommendation or advise??

Thank you all.

Stan

---

### Post by JaxM on 2010-02-22
I've got a machine in the dv series so my hopes are as high as yours :P Still waiting for it to arrive (6-10 grouling weeks) Mine's a HP Pavilion dv7-1464nr about 4 GB of RAM (8GB max), 500GB Hard drive (newly put in), 2.20 GHz AMD Turion X2 Ultra ZM-82 Dual-Core Mobile Processor
 
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01801119&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&lang=en&product=3998676](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01801119&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&lang=en&product=3998676)
 
 
There's a link to my machine's specs page. Not much experience with operating systems I'm more of a general user. I think Linux will definitely increase anyone's knowledge of computers.

---

### Post by kvmapr on 2010-02-22
I have the HP Dv6 2150us, and just tried installing Ubuntu 9.10 under Windows 7 from CD using wubi.exe. The install went fine but when I rebooted and selected Ubuntu versus Windows 7 from the boot loader, it began to boot but quickly halted. Blanks screen similar to what's been described in other posts.

I'm looking around now to the 10.4 beta which I understand has been booted successfully on these i3 processors. Here's hoping 10.3 has full support for the i3, i5, i7.

---

### Post by Glavata on 2010-02-23
I have the exact same machine, dv6-2150us and I can't start the install. It boots to the menu, then it hangs with a blank screen :\ Some of the hardware must be causing a problem. Any one have any suggestions on how to fix this? I hate getting a new laptop as most of the stuff does not work in linux at first :\

Update: 9.04 booted fine from the CD. Problem lies with 9.10 somewhere.

---

### Post by thecliff on 2010-02-23
I've sent this out to our internal opensource linux team @ HP.  I'll repost with what they provide.

---

### Post by JiuJitsu500 on 2010-02-23
Glavada and to all who have this machine I have installed it on your machines, three of the first installs I ever did on laptops were on the dv6 series (the first couple was on my Gateway and an old, old HP I was about to shoot because of a virus in windows).

Anywho, at the language selector and live boot screen, press F4 I believe (extra options one) and choose to boot into safe graphics mode. The video card doesn't allow full acceleration until it's installed. Once it is, install the proprietary driver and do all your updates, then re-boot and all will be well.

So for the actual topic, Linux can be put on damn near anything, and HP is very, very open-source friendly so I doubt you'll run across one of their machines (even their printers, etc) that can't be made to work fairly easily if not out of the box. My old dv4 I'm using now didn't need any drivers, nothing extra at all and it worked 100% right after install. The only thing with new computers is usually graphics or sound drivers, easy after installing in safe graphics mode.

Hope I helped :)

---

