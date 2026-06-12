---
title: "Upgrade broke my installation"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by SaaTeeVaaGreen on 2010-05-19
Hi all
i had been using ubuntu 9.04 and recently decided to upgrade to 10.04. first step was to upgrade to 9.10 which i did through the update manager, and worked fine. i ran 9.10 for a while, every thing was running ok so i started the upgrade to 10.04 by the same method. update manager started doing its thing, downloading what it needed and started to install. a little way into this i suddenly got the message

```
could not install /var/cache/apt/archives/indicator-applet_0.3.6.0ubuntu2.i386.deb

unable to install (supposed) new info file /var/lib/dpkg/tmp.ci/md5sums input/output error
```

with an 'ok' button. on clicking ok i got a message along the lines of 'upgrade will continue but something (i didnt note what) might not work', and it started running again. (at this stage, i must be honest, i was quite unconcerned and of the opinion that Linux is fine and wont break and so although i may have made a note of the initial message, i didnt accurately record the following one.) it only ran for a second or two before another message came up and said something like the upgrade could not continue and was shutting down, the system may not be useable. 

it was not wrong.

now, when i start my laptop i get the grub menu ok (i dual boot) with two kernel options for 9.10 (as it was before i started the second stage of the upgrade) but neither of them work. selecting 2.6.31-21 returns the error 

```
mount: mounting none on /dev failed: no such device
```

while selecting the 2.6.28-18 seems to start ok as i get a little white ubuntu logo in the middle of the screen, but then all i get is some flashing rectangle thing, like in the pic.

obviously none of this is good. so my question is, what do you think? is it dead? do i just give up and do a fresh install, or is there a chance of rescuing it? all my important data is backed up, i may lose some settings or configurations or programs ive installed (i dunno) with a fresh install, but this is not a big problem. so, honestly, what do you think? all advice appreciated!

p.s. im still of the opinion that Linux is fine and wont break:P
p.p.s. am running vaio laptop, 1.60GHz pentium processor with nvidia geforce go 6200 graphics card if this makes any difference...

---

### Post by ubunterooster on 2010-05-19
First thing I can think of would be to boot of the liveCD and reinstall grub: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by WinterRain on 2010-05-19
> **SaaTeeVaaGreen said:**
> do i just give up and do a fresh install

I would. You can spend days trying to fix upgrade issues. 10.04 should run just fine with a fresh install.

---

### Post by -humanaut- on 2010-05-19
I'd advise a fresh install fixing it is certainly possible but, a Clean install would be much easier at this point. Do you have your /(root) & /home separate?

---

### Post by pizza-is-good on 2010-05-19
Upgrades are known for breaking things.

My upgrade from 8.10 to 9.04 messed it up enough for me. I have done clean installs every since.

As stated above, you'll probably spend a lot of time trying to fix it. Just go for a fresh install. It'll take only about half an hour to install ubuntu again, and probably another 30 mins to get all your settings back to the way you like them.

---

### Post by wilee-nilee on 2010-05-19
Advice for a fresh install is all good but this appears to be a graphic card problem, probably. Thread starter post from the live cd from the terminal lspci

---

### Post by SaaTeeVaaGreen on 2010-05-20
thanks for all the responses. seems a fresh install is the popular solution at the moment!

> **-humanaut- said:**
> Do you have your /(root) & /home separate?

yes, i do. will this make things easier? is it possible to not format /home when installing thus saving all data there? /home is backed up anyway, but if it doesnt need formatting...

> **wilee-nilee said:**
> Advice for a fresh install is all good but this appears to be a graphic card problem, probably. Thread starter post from the live cd from the terminal lspci

did wonder if it was a graphics card issue. i know there was an issue with 9.10 and nvidia graphics cards, which is why i was still running 9.04, but i had hoped it would be fixed now. i have booted my laptop from a 10.04 live cd though (after this issue), with no problems and i took this to mean i wouldnt have a graphics card problem if i installed. am in work at the moment so cant run lspci but will do tonight when i get back and post the output.

thanks for your advice so far everyone!

---

### Post by linuxisfree on 2010-05-20
> **SaaTeeVaaGreen said:**
> thanks for all the responses. seems a fresh install is the popular solution at the moment!
 
 
 
yes, i do. will this make things easier? is it possible to not format /home when installing thus saving all data there? /home is backed up anyway, but if it doesnt need formatting...
 
thanks for your advice so far everyone!
 
Having / and /home separate DOES make things MUCH easier. And yes its possible not to format /home when installing (i do that all the time). and also just as most of them suggested, a clean / fresh install is the way to go. :)

---

### Post by SaaTeeVaaGreen on 2010-05-20
> **linuxisfree said:**
> ...And yes its possible not to format /home when installing (i do that all the time)...

thanks linuxisfree, thats great news! makes things a lot easier for me!:P looks like a clean install is the way to go. i'm just a little concerned still about wilee-nilee's comment:

> **wilee-nilee said:**
> ...but this appears to be a graphic card problem, probably. Thread starter post from the live cd from the terminal lspci

can anyone confirm that, given i can boot my laptop from a 10.04 live cd without any problems, i shouldnt have any graphics card problems when i install it properly? 

(wilee-nilee - i will still post the output of lspci when i get home tonight, before attempting an install, especially if this will help tell once and for all whether i have an issue)

---

### Post by SaaTeeVaaGreen on 2010-05-20
ok, im running 10.04 from the live cd at the moment and it is running fine. thanks for everyones help and advice, it looks like a fresh install is the way to go. unless anyone can see a reason not to in output of lspci which was requested and is below.

```
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce Go 6200/6400] (rev a1)
06:05.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
06:05.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
06:05.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller
06:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)
06:0b.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
```

---

