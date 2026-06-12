---
title: "Motherboard with integrated HD 4200"
date: 2010-05-29
forum: New to Ubuntu
---

### Post by FinnMan on 2010-05-29
Hello. I'm sorry to bother you once more, but I ran into a comment on the Internet. :) You see, I am planning to build a new box to run **Lucid Lynx** and I had my mind set on an *Asus M4A* motherboard with Advanced Micro Devices chipset.

The comment that was made to me was that I should go with **nVidia** graphics for Linux, because Linux drivers for AMD are "very bad". Personally, I don't even want to use the N-word due to some bad experiences, but is there truth to this? ;)

---

### Post by antenna on 2010-05-29
I have no problems with my integrated HD4200, with either the proprietary or open source driver.  Everything from compiz to basic games works great. 
The proprietary has better 3D performance, while the open source one works with KMS.  

Having said that, I am looking to get a dedicated card for better 3D performance as that's obviously not what the HD4200 is really for.

---

### Post by FinnMan on 2010-05-29
I see. The board I am considering is M4A785-M. I also thought about getting a graphics card, but that makes no sense, since I'm only planning desktop use for the machine.

I'd like other people's input as well on how their AMD (ATI) graphics chips are performing with Ubuntu. I was told it would be extremely slow even on mere desktop.

---

### Post by quadproc on 2010-05-29
> **FinnMan said:**
> ...
I'd like other people's input as well on how their AMD (ATI) graphics chips are performing with Ubuntu. I was told it would be extremely slow even on mere desktop.
I don't know who told you that but my experience is with HD 4870x2 in crossfire mode in a desktop system and I find that the glxgears program usually runs at about 2000 frames per 5 seconds, i.e., about 400 FPS while using the fglrx driver, Ubuntu 9.10, and the default size of the "gear window".  Granted, glxgears is not a benchmark but it does provide order of magnitude performance indications.

The main problems that I have had with ATI hardware/software relates to new releases: I find that it is necessary to completely uninstall the fglrx driver before upgrading the kernel, and later reinstall the same driver.  Not doing it that way leads to everything from a dead display system to weird and bizarre bugs in a partially functioning graphics environment.

ATI has been working very closely with the open source community and I expect that the open source driver will fairly soon be using most of the ATI card's features.

quadproc

---

### Post by anewguy on 2010-05-29
I'm running an old ATI 9250 Pro (Radeon) and haven't loaded any special drivers of any kind.  I get excellent results with Compiz and my glxgears rate is 4649 to 4659.  I don't run any graphic intense games, and I don't use 3D (that I'm aware of anyway), so I can't comment on other performance.

I also had bad experiences in the past with nVidia, which is why I went to ATI and haven't gone back yet.  I see lots of posts about bad results with ATI versus nVidia, but by the same token I see people with problems booting after a new install, etc., with nVidia.  I have no real idea which is "better" (that's a relative term anyway).  Benchmark tests, etc., state how things technically work, but there is also the "perceived" test, which only you can tell.

Dave ;)

---

### Post by FinnMan on 2010-05-30
All right. Armed with this information I shall stick with the AMD board. :) Thanks for your replies!

---

