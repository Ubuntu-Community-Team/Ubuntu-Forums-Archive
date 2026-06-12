---
title: "Ubuntu for an old iMac G3?"
date: 2010-03-14
forum: New to Ubuntu
---

### Post by mlthmp on 2010-03-14
I have a 600mhz iMac G3 with 256MB ram.. when I got it it didn't have an OS installed which makes it little more than a paperweight. Needless to say I would like to try and use it for something, even if just to browse the internet and check email!

I am not interested in downloading any pirated OS X for it, and want to try and put Linux on there. I know this CAN be done, but that it's pretty difficult. Can anyone suggest what the best version of Ubuntu may be for me to try, and what additional steps may be required to get it working?

Thanks!

---

### Post by Temposs on 2010-03-14
You might want to try Xubuntu or Lubuntu on a system like that. Also, you will need to install it with the **Alternative Installer**. That's very important, because the normal LiveCD probably won't work with that little amount of RAM.

---

### Post by Donald1715 on 2010-03-14
I've got an old Mac G4. It's a "newworld" MAC. Your's might be an "oldworld" MAC. Just food for thought. I downloaded and installed "EdUbuntu" for PowerPC and it installed and works great. Sorry can't give you a link ATM, you'll have to look it up yourself, but at least I have given you a clue.

BTW, my G4 is a 400mhz PowerPC, with 512mb of ram.

---

### Post by Sef on 2010-03-14
Read the [Power PC FAQ]("https://wiki.ubuntu.com/PowerPCFAQ").

---

### Post by Donald1715 on 2010-03-14
I looked thru my files and found a few links for ya relating to Mac installs.

[http://www.debian.org/ports/powerpc/](http://www.debian.org/ports/powerpc/)

[https://help.ubuntu.com/community/Installation/OldWorldMacs](https://help.ubuntu.com/community/Installation/OldWorldMacs)

[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

---

### Post by Tikkyca on 2010-03-14
It will work,i think i founded one thread about how someone installed Ubuntu on his iMac G3.

---

### Post by mlthmp on 2010-03-14
Hey everyone, thanks for the quick replies!

I just booted up Ubuntu 8.04 without a bit of trouble. It does run a bit slow, but not too bad! I think if I get a little more RAM thrown in, and it'll be usable =)

---

### Post by NightwishFan on 2010-03-14
You could install Debian as well, it is better for lighter machines.
[http://www.debian.org/ports/powerpc/](http://www.debian.org/ports/powerpc/)
[http://cdimage.debian.org/debian-cd/5.0.4/powerpc/iso-cd/debian-504-powerpc-CD-1.iso](http://cdimage.debian.org/debian-cd/5.0.4/powerpc/iso-cd/debian-504-powerpc-CD-1.iso)

Perhaps install XFCE or LXDE.

---

### Post by phillw on 2010-03-14
The thread for xubuntu is here --> [http://ubuntuforums.org/showthread.php?t=1359265](http://ubuntuforums.org/showthread.php?t=1359265)

It's reported as working, but I haven't had time to have another go myself yet.

Regards,

Phill.

---

### Post by subedistra7 on 2010-03-14
it works, but you need to generate a  xorg.conf.

then change the driver part to;

```

Driver      "fbdev"


```

---

### Post by mlthmp on 2010-03-14
Now that I at least known Ubuntu will work.. I am going to try Xubunut (8.10) and see if I can get that to work instead since its "lighter" than normal Ubuntu. Hopefully I'll be able to figure this one out as well. 

If all else fails I will reinstall Ubuntu 8.04 and use it as a paper weight with a pretty screen =) However one would assume if Ubuntu will work, Xubuntu should work also lol!

---

### Post by NightwishFan on 2010-03-14
It should, but do not give up. Debian is not hard to use, Ubuntu is actually based on it, and officially supports powerpc. Xubuntu should work fine I assume. As per suggestions, try LXDE on ubuntu or debian, it is lighter.

---

### Post by kaldor on 2010-03-14
> **NightwishFan said:**
> Debian is not hard to use, **based on Ubuntu**

???

I hear Fedora has good PowerPC support as well.

---

### Post by Temposs on 2010-03-14
> **NightwishFan said:**
> It should, but do not give up. Debian is not hard to use, based on Ubuntu, and officially supports powerpc. Xubuntu should work fine I assume. As per suggestions, try LXDE on ubuntu or debian, it is lighter.

You got that backwards. Ubuntu is based on Debian :-)

---

### Post by NightwishFan on 2010-03-14
> **Temposs said:**
> You got that backwards. Ubuntu is based on Debian :-)

It was just a typo I missed, I am actually multitasking right now. Ill edit now. (I indeed know, Debian was made in 1993)

Yes, Fedora still supports it. I would give that a try as well, RPM based distros are great.

---

### Post by mlthmp on 2010-03-14
I believe I am close now!

Xubuntu is installed. When I leave the system alone it freezes before it launches (black screen) but I can get into it with the "Linux video=ofonly nosplash" command at the "boot" menu. However, then I get the "ubuntu is running in low graphics mode" error.

Now just gotta figure out whats going on, and hopefully get this joker running like it should be!

---

### Post by mlthmp on 2010-03-14
Well I've hit a wall so to speak. I've tried the same xorg.conf setup I used to get Ubuntu 8.04 to work, and it didn't do it this time. No matter what I've tried I get the same things.

Black screen after boot (system freeze) or "Ubuntu is running in low-graphics mode" when I boot with "Linux video=ofonly"

I am getting 3 errors.. can anyone give me an idea of how I should proceed?

(EE) Unable to find a valid frameratebuffer device

(EE) R128(0) Failed to open frameratebuffer device, consult warnings and/or errors above for possible reasons

(EE) Screen(s) found, but none have a usable configuration.


I can hit OK, and then "run in low-graphics mode this session only" and then the session will "restart" and I can login via low-graphics mode. However I am not really able to do anything major. I suppose since its in LGM. Firefox will start, and close before it opens all the way.. same with terminal, games, etc. At least I am HOPING that's just an issue with the graphics mode, lol.

---

