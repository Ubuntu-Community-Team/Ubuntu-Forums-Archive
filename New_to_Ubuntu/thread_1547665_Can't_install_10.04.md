---
title: "Can't install 10.04"
date: 2010-08-07
forum: New to Ubuntu
---

### Post by twinaxel on 2010-08-07
Hi Been running Ubuntu since jaunty with no problems, so I decided to upgrade from karmic to Lucid I also spent some money on a new system.

Loading the CD brings up a screen filled with text mainly about 
USB connections, although I can see a line that that says unexpected exit with status 0x0009. 

Tried the CD in my old system works perfectly, out of interest I
loaded a windows XP disc in the new system it installed perfectly!


can anyone offer any advice?

---

### Post by phillw on 2010-08-07
Hi,
 my first suggestion would be to confirm that both the downloaded iso and your CD has burned okay.

[md5 checksumming](https://help.ubuntu.com/community/HowToMD5SUM)

Regards,

Phill.

---

### Post by twinaxel on 2010-08-07
Hi thanks for the advice still won't install, downloaded 9.1
installed no problems.

---

### Post by Rubi1200 on 2010-08-07
Could you please post the output of this from the terminal:
 
```
 
lspci | grep VGA

```

---

### Post by Kellemora on 2010-08-07
Hi TA

I've burned over 25 CD's, 2 USB sticks and have 3 computers that will not load 10.04 no matter what you do.

Pulled a hard drive and used one of the computers it would load onto, then put the drive back.

10.04 CRASHES on every computer we have here after about 10 to 30 minutes of running.

I finally gave up on it after wasting over 80 hours messing with it.

Stuck Debian 505 on in it's place and it installed with zero problems.
Trouble is, it takes me weeks to get Debian set up, as nothing ever works the way the tutorials out there show to do things.  Took 2 days just to get the NVIDIA drivers installed.
Today I CHEATED and just COPIED the module for FLASH into the iceweasel folder, worked like a charm without all the hoopla.

I really LOVE Ubuntu, but as far as I'm concerned 10.04 is enough to drive one back to Windows, well almost, I'll run 8.04 until it's no longer supported and to be on the safe side, I'm setting up triple boot systems to Debian.  Which is no problem as I already had XP, Ubuntu and CentOS, I just used the CentOS partition to try 10.04 and since it don't work, Debian 505 is going to get another crack at winning me over!

TTUL
Gary

---

### Post by Elmer Fudd on 2010-08-08
> **Kellemora said:**
> Hi TA

I've burned over 25 CD's, 2 USB sticks and have 3 computers that will not load 10.04 no matter what you do....
TTUL
Gary

Gary, 
You were asked on another thread if you burned the 25 cds from the same iso image or did you download other images. I never saw your reply. I have installed 10.04 or seven different types of laptops/desktops/tablets and the only problems that I have had were with dual boot (solved by changing to Burg) and Netflix not working ( a MS DRM issue- in that they won't support Linux).
You are the only one that I have seen with this 30 minute issue and I am hoping that you just got a bad iso.
Please post if you find a solution or a kernel update fixes your problem.

---

### Post by twinaxel on 2010-08-08
Hi output from lspci | grep VGA 
00:02.0 VGA compatible controller: Intel Corporation Auburndale/Havendale Integrated Graphics Controller (rev 12)

---

### Post by Elmer Fudd on 2010-08-08
> **twinaxel said:**
> Hi Been running Ubuntu since jaunty with no problems, so I decided to upgrade from karmic to Lucid I also spent some money on a new system.

Loading the CD brings up a screen filled with text mainly about 
USB connections, although I can see a line that that says unexpected exit with status 0x0009. 

Tried the CD in my old system works perfectly, out of interest I
loaded a windows XP disc in the new system it installed perfectly!


can anyone offer any advice?

Shouldn't have to but..
Did you try an install of 09.10 and then ugrade to 10.04?

---

### Post by Rubi1200 on 2010-08-08
> **twinaxel said:**
> Hi output from lspci | grep VGA 
00:02.0 VGA compatible controller: Intel Corporation Auburndale/Havendale Integrated Graphics Controller (rev 12)
Take a look here for some possible fixes for Intel chipsets:

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

### Post by linuxnomad4850 on 2010-08-08
are you using the same ISO file or did you try re-downloading it? it is probably corrupt.

---

### Post by twinaxel on 2010-08-08
> **linuxnomad4850 said:**
> are you using the same ISO file or did you try re-downloading it? it is probably corrupt.

I have downloaded 10.4 three times and burned five CDs and 1 DVD
still won't install.


 	
Rubi1200  Tried your suggestion still the same.

I know that the intel chip and the lack of a compatible driver is the cause of my problems.

So it's decision time do I buy a nvidia graphics card that I hope
will solve the problem.

Or do I buy Windows 7 which will solve the problem?

---

