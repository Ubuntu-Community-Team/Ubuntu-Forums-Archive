---
title: "Boot CD failure..."
date: 2010-05-25
forum: New to Ubuntu
---

### Post by kromedome on 2010-05-25
[SIZE=3]Hi...
I copied the ubunto OS from the 'net (ubuntu 10.04 desktop 1386.ISO)  and used ImgBurn to create a bootable CD. I went into BIOS to change the boot order, and tried to do a dual boot install, or even a demo of Ubuntu. 
On both a working, functioning computer, and a second hard drive with "NTLDR" missing,  I get an error message to the effect that "no live file found on media."
How can I overcome this problem and get Ubuntu installed to either demo or dual boot, on EITHER hard drive?
Thanks...
Kromedome
[/SIZE]

---

### Post by ranch hand on 2010-05-25
Well, this is interesting.  How did you "copy" the ISO?

Hopefully you downloaded it from;

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

You may want to look at this too;

[http://tinyempire.com/notes/ntldrismissing.htm](http://tinyempire.com/notes/ntldrismissing.htm)

---

### Post by nhasian on 2010-05-25
If your seeing an error message NTLDR when trying to boot that means its trying to boot from the hard disk, not the optical drive.  go into the bios and set the CD/DVD Drive to boot before the hard disk.  make sure to SAVE before exiting the bios.

Also make sure you have burned the ISO as an image to a CD (not a DVD) at the slowest speed possible for your optical drive and media.


> **kromedome said:**
> On both a working, functioning computer, and a second hard drive with "NTLDR" missing,  I get an error message to the effect that "no live file found on media."

---

### Post by kansasnoob on 2010-05-25
This might be helpful:

[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)

---

### Post by Nightstrike2009 on 2010-05-25
I have found sometimes that if you burn an .iso image on a fast speed sometimes the resulting disc suffers from errors, try burning a new disc at a slower speed that works for me.

> **by Nhasian:**Also make sure you have burned the ISO as an image to a CD (not a DVD) at the slowest speed possible for your optical drive and media.

I also use "Imgburn" on windows :-)

---

### Post by nhasian on 2010-05-25
Did you know that Imgburn works great in Ubuntu with Wine as well?  :)

> **Nightstrike2009 said:**
> I also use "Imgburn" on windows :-)

---

### Post by kromedome on 2010-05-25
Wow...I do not have much forum experience and the very helpful response is most gratifying...thank you! I verified a good ISO burn, all files and icons OK. I tried to get the BIOS to boot off the CD in either of my optical drives, but no luck. I did an install from the CD and I now have a dual boot OS setup.
I'll download a manual and try to migrate many of the programs that I was running under XP to run under Ubuntu. I expect there's a procedure for that. Guess I wound up on the Internet, while running Ubuntu, as an update began rather surprisingly...I don't remember clicking an "enable" button on a network icon. Nor had I installed any anti-virus or malware applications. Guess that's next in the learning process...
In any event, I seem to be under way, albeit in a manner that suggests a guy with an arm full of books falling down stairs...I have NO idea what the hell I'm doing, so kindly keep the "Welcome" mat out...I'm sure I'll be back.
Thank you all VERY much!
Kromedome...

---

