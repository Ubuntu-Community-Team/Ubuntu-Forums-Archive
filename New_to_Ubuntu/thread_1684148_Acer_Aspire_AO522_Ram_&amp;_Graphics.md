---
title: "Acer Aspire AO522 Ram &amp; Graphics"
date: 2011-02-08
forum: New to Ubuntu
---

### Post by Xenomorph05 on 2011-02-08
Hey! I just installed Ubuntu 10.10 because Windows 7 Starter is horrible. I have an ugly AMD watermark saying Unsupported Hardware and in the system monitor it only shows 728 of my 1Gb ram?

AMD C-50 Dual Core 1.0Ghz, ATI Radeon HD 6250.

---

### Post by josephmills on 2011-02-08
I am a big time nOOb at all of this so take this with a grain of salt  but try going to 
System>Administrator>Additional Driver>check for updates there.

---

### Post by Xenomorph05 on 2011-02-08
> **josephmills said:**
> I am a big time nOOb at all of this so take this with a grain of salt  but try going to 
System>Administrator>Additional Driver>check for updates there.

I have already installed the ATI Drivers from there. It was after I installed the driver that I got the Unsupported Hardware watermark at the bottom right corner of my screen. thx though.

---

### Post by Xenomorph05 on 2011-02-08
I tried Crunch Bang live and it also says 728mb RAM but I checked my bios and it clearly says 1024mb.

---

### Post by Paul820 on 2011-02-08
Your graphics card may be sharing the system memory that's why it looks smaller. I have 2Gb of ram and only 1.7Gb is allocated to the system, the rest is used on the graphics card.

---

### Post by Xenomorph05 on 2011-02-08
> **Paul820 said:**
> Your graphics card may be sharing the system memory that's why it looks smaller. I have 2Gb of ram and only 1.7Gb is allocated to the system, the rest is used on the graphics card.

It is a 256 dedicated card. The ATI Catalyst Control Center only mentions the 256. Is there somewhere else I can check to confirm this idea and maybe even change how much shared RAM is used?

---

### Post by Rowan_ on 2011-02-08
Check this post. [http://ubuntuforums.org/showthread.php?p=10441039#post10441039]("http://ubuntuforums.org/showthread.php?p=10441039#post10441039")

---

### Post by Xenomorph05 on 2011-02-08
> **Rowan_ said:**
> Check this post. [http://ubuntuforums.org/showthread.php?p=10441039#post10441039]("http://ubuntuforums.org/showthread.php?p=10441039#post10441039")

I don't have any freezing issues and my wireless is working fine. I will check out installing the catalyst manually to get rid of the watermark but I haven't done that before. 

Should I remove my current CCC or can I install another ontop?

---

### Post by Rowan_ on 2011-02-08
xenomorph, i would try andrewthong's tip.  Post #121 on this thread: [http://art.ubuntuforums.org/showthread.php?p=10441065#post10441065]("http://art.ubuntuforums.org/showthread.php?p=10441065#post10441065")

---

### Post by dsummy on 2011-02-09
Hey, i just purchased an acer ao522 also and am having the same issue with the watermark. I installed windows 7 x64 for the time being and have been searching for a fix to the ubuntu driver issue. It seems amd has not yet released drivers to support the 6250 on linux yet. but i did find these drivers..don't know how to install them though :(
[http://www.phoronix.com/scan.php?page=news_item&px=OTA3Nw](http://www.phoronix.com/scan.php?page=news_item&px=OTA3Nw)

I also seem to be having an over heating issue..today while on the train I had the netbook in my bag, not turned off, just sleeping and when I woke it up and closed some applications and when to turn on a movie..it got EXTREMELY hot in the bottom left corner of the screen and under the power button, Also, in the middle of the screen right by the letter 'a' in acer there a little circle the size of a screw that looks to have melted the plastic of the screen :( going to talk to acer tomorrow.

---

### Post by Xenomorph05 on 2011-02-09
I went back to Win 7 Starter. Even in Windows it says 1GB RAM but only 748 is usable? My graphics card only uses 117 of my ram so why am I still missing 139mb? Win 7 uses about 380mb ram just idling. 

I have noticed a few times I get horizontal lines jumping up and down my screen. Possibly a defect? This laptop also only has 1 speaker on the left. I guess this is what I get for paying 300 for an Acer... 

I want to use linux, I tried the minimal debian but the new kernel doesnt have wacom driver support. I couldn't figure out how to install gentoo minimal. Crunchbang looked interesting... Is it worth taking the time to learn LFS to make a system with only the stuff I need?

---

### Post by Mo0 Linux Newb on 2011-02-28
hello i also have a ao522 and im also having display driver problems the c-50 is a APU you have to download the driver from amd website under notebook drivers just follow the drop down menus so it does have shared memory meaning you do lose the 256 out of your ram you can upgrade your ram to a larger 4 gigs but the system will only use 2gigs but you get the whole 2 gigs usable ram i know for a fact this works cuz its what im doing as for the over heating problem im clueless i have noticed this thing heats up quite a bit anyways i cant find out how to install the driver ive never used linux before tonight

---

### Post by Mo0 Linux Newb on 2011-02-28
ok ive done it my display drivers are working flawlessly im using Linux Mint 10 "Julia" and it looks beautiful heres the link for the C-50 driver
 [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&#9001;=English ]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English")

i could not get this to work on ubuntu 10 i hope this helps you guys

---

### Post by RPhipps on 2011-07-09
I can't even get Ubuntu 11.04 to install, just gets stuck on the ubuntu logo with the dots underneath. The disk works fine on my Desktop. Tried both the 32bit and 64bit (which I now know is the right one for the C-50, neither of which work.) 

[SIZE=2]Please help, as I know nothing about Linux.[/SIZE] :(

---

### Post by insaner on 2011-07-19
11.04 has a kernel where the wireless module makes it hang. you are going to have to install 10.10 and then upgrade, and boot using the 10.10 kernel  alternatively, and this might be your best bet, go into the BIOS and change the boot order to have the atheros netboot be before your other boot choices, this should do the trick.  you can also just plug in your ethernet cable, and as long as that is connected, it should be ok..  let me know if that helps  --  insaner [http://www.insaner.com](http://www.insaner.com)

---

### Post by qamelian on 2011-07-19
> **insaner said:**
> 11.04 has a kernel where the wireless module makes it hang. you are going to have to install 10.10 and then upgrade, and boot using the 10.10 kernel  alternatively, and this might be your best bet, go into the BIOS and change the boot order to have the atheros netboot be before your other boot choices, this should do the trick.  you can also just plug in your ethernet cable, and as long as that is connected, it should be ok..  let me know if that helps  --  insaner [http://www.insaner.com](http://www.insaner.com)

You can also blacklist the atheros module to eliminate the problem.

---

