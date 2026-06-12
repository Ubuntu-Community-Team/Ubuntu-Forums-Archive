---
title: "installing ubuntu on a older mac"
date: 2011-04-05
forum: New to Ubuntu
---

### Post by josephmills on 2011-04-05
hi there I was at the flea market the other day and bought a older Mac G3 [http://lowendmac.com/ppc/blue-white-power-mac-g3.html](http://lowendmac.com/ppc/blue-white-power-mac-g3.html) I Could not set a new account up and could not change it in single user mode. I then tried to install ubuntu 10.04 power pc by download from here [http://cdimage.ubuntu.com/ports/releases/10.04/release/](http://cdimage.ubuntu.com/ports/releases/10.04/release/)    and  turning on the machine holding down the commmand+option+o+f and got to a boot menu I then typed in ```
boot cd:,/install/yaboot
```
And nothing happened for allittle bit then it acted like it wanted to boot the OSX 10.04 but then bam, I got a kernel panic and am stuck with no os what-so-ever.:confused: What am I doing wrong I am new to all of this and confused and frustrated I would like just to have ubuntu as my main os and no mac os what so ever because ubuntu is the Best :) so could some one please help me out on this one thanks

---

### Post by jtarin on 2011-04-05
It could be a bad burn. Did you check the MD5 Checksum? How much memory do you have? Less then 256mb you might want to try the "Alternate CD".

[Here's something noteworthy]("http://www.ghacks.net/2009/06/10/revive-your-old-mac-g3-g4-or-g5-with-linux/").....scroll down to the "Ubuntu" install.

[Other images ]("http://cdimage.ubuntu.com/")(under ports for PPC)

---

### Post by josephmills on 2011-04-05
> **jtarin said:**
> It could be a bad burn. Did you check the MD5 Checksum? How much memory do you have? Less then 256mb you might want to try the "Alternate CD".

[Here's something noteworthy]("http://www.ghacks.net/2009/06/10/revive-your-old-mac-g3-g4-or-g5-with-linux/").....scroll down to the "Ubuntu" install.

[Other images ]("http://cdimage.ubuntu.com/")(under ports for PPC)

thank you so much I will try and burn at a slower speed  the firmware is 3.1.1 dont know if that helps any I will also try a alternate cd.

---

### Post by josephmills on 2011-04-05
good news everybody I took the ram out and cleaned it also put some new fans in and new heat grease disconnected and reconnected the hd cable and turned the machine back on it almost loaded but then I got a kernel panic again so I tried to restart in "single user mode" and it booted so I am know at the cli going to look at the cd in the cdrom drive feels good to start moving on this but still dont understand how to install ubuntu is it like installing on a pc where you just change the boot order to boot from the cdrom? is so what is the syntax for that? I talked to the people at mac and the guy on the phne told me to press command+option+o+f and I get the boot menu then he tod me to put in ```
boot cd:,/install/yaboot 
``` but I think that this is what gave me the kerenal panic in the first place but I dont know, At any rate getting closer thanks again

---

### Post by arochester on 2011-04-05
> I would like just to have ubuntu as my main os and no mac os what so ever because ubuntu is the Best 

I had a G3. The CD-ROM was booted by holding down the "C" key on startup. In my case a problem was the amount of RAM and I had to use Xubuntu PPC.I couln't get the newer versions of Xubuntu PPC to work and used 8.04 or 8.10.

---

### Post by josephmills on 2011-04-05
> **arochester said:**
> I had a G3. The CD-ROM was booted by holding down the "C" key on startup. In my case a problem was the amount of RAM and I had to use Xubuntu PPC.I couln't get the newer versions of Xubuntu PPC to work and used 8.04 or 8.10.

thanks man I just woke up and am going to get at it. hopefully I will get it today thanks for the heads up about the ram too. I will try using xubuntu power pc right now I just am trying to get this thing to boot the c this won't work I think that It has to do with the kerenel panic but I could be wrong but I will try with a different drive and see how that goes wish me luck

---

### Post by Daniel0108 on 2011-04-05
> **josephmills said:**
> thanks man I just woke up and am going to get at it. hopefully I will get it today thanks for the heads up about the ram too. I will try using xubuntu power pc right now I just am trying to get this thing to boot the c this won't work I think that It has to do with the kerenel panic but I could be wrong but I will try with a different drive and see how that goes wish me luck

Unfortunately, xubuntu isn't very lightweight anymore.

I suggest using lubuntu. :)

Yours,
Daniel

---

### Post by josephmills on 2011-04-06
After working on this for a long time I could not get it to install I tried everything that I could think of . I think the cdrom drive  was busted I then tried to replace the cd rom and the power went out on it, and would not return. I then tried to replace the fuse in the power box and got nothing.It was funny my voltage meter would not read anything. But would read other power box's. At this point I got so upset that I pulled the ram and hd and went down to the basement and grabbed a old gateway with a p3 in it and put the hd and ram from the mac in it and fired it up changed the boot order and installed xubuntu It works fine.After thinking about it I should have tried to pull the HD and install the os on it in another machine then put it back in to the mac but I don't have any other powerpc.Next time .  I will make a new machine when I get more hardware and will try lubuntu.thank you all for the input.

---

