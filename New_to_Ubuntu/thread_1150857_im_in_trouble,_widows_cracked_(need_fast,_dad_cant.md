---
title: "im in trouble, widows cracked (need fast, dad cant notice)"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by patchido on 2009-05-06
i have a dell inspiron 1420, and a SATA EXT hdd in which i have ubuntu, in my int hdd i have vista, and just yesterday i made a partition to my ext hdd to install xp in it aswell, it got installed but awkardly my grub got untouched, and i tried to boot into xp and it woudlnt work , it read NTLDR is missing, and i thought that was my problem, but now today i tried to boot into windows vista normallly and it "starts loading vista" and a blue screen appears saying that it had to stop beacuase something is wrong, that i rebbot, and if that persists it may be a virus, which is not, i think it has to do with xp installation, please help me, i have ubuntu in my EXT becasuse my dad doesnt want me to mess the laptop, and now it happend so :S im in trouble if i cant correct this.

---

### Post by Mil Doc Jr on 2009-05-06
If you have a recovery disk or a partion on your computer try running the startup recovery on the disk to fix your vista startup

---

### Post by patchido on 2009-05-06
if i have a vista cd? i dont :S

---

### Post by nhasian on 2009-05-06
Boot from the Vista DVD -> Advanced/startup repair -> Repair my Startup.

---

### Post by The Mad Mule on 2009-05-06
Yeah, honestly your only solution is to grab a Vista disc and start the Recovery process, because you messed up a boot file somehow.

---

### Post by nhasian on 2009-05-06
you could also try EasyBCD:

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

### Post by patchido on 2009-05-06
> **nhasian said:**
> Boot from the Vista DVD -> Advanced/startup repair -> Repair my Startup.

a friend of mine has a dell installation dvd, and i tried to, but there isnt anywhere a reapiar, its just an isntall dvd, its from dell, or maybe i just dont know how to use it :D

---

### Post by patchido on 2009-05-06
solved :D i found the reapir, now can anyone help me boot my xp? i get NTLDR missing when i open from grub

---

### Post by Snyper450 on 2009-05-06
All you really need is the OEM disk that came with the laptop to fix it BUT without your daddy knowing xDxP

---

### Post by Snyper450 on 2009-05-06
Sorry did not read post above basiclly IF you have another XP computer at home go onto its hard drive and look for the NTLDR file and copy it to a CD or somethign liek that if you got a XP CD put that in and start recovery console and copy the file over (cant remember where it goe either c:\ or c:\windows\system32)
Good Luck

---

### Post by patchido on 2009-05-06
hmmm but that wont crash vista again? take in mind i have ubuntu in the EXT also

---

### Post by LowSky on 2009-05-06
vista cant even read EXT so dont even worry about that... side note dont install an OS on a USB drive without disconnecting the interneal drive.. That way the master boot record and anything else goes untouched.

---

### Post by patchido on 2009-05-06
u mean extract the HD?

---

### Post by LowSky on 2009-05-06
> **patchido said:**
> u mean extract the HD?

Yes. removal of the main hard drive while installing another OS onto a USB can save you some annoying Master boot record issues. Most OS by default will install the MBR to the Primary hard drive and not to the drive your using

---

### Post by caljohnsmith on 2009-05-06
Patchido, please do not start multiple threads about the same problem. If you would have seen my response to your [other thread]("http://ubuntuforums.org/showthread.php?t=1150413"), you would see that I was willing to help you with the exact problem you are facing about Vista being broken. 

Since you don't have a Vista Recovery DVD, I would recommend downloading the Vista Recovery CD from here:

[http://www.pcworld.com/downloads/file/fid,71039/description.html](http://www.pcworld.com/downloads/file/fid,71039/description.html)

Boot that, go to the command line and run:
```
bootrec /fixboot
```
And that should fix your Vista partition's boot sector so you can boot Vista again. Let me know how that goes or if you run into problems.

---

### Post by Maheriano on 2009-05-06
> **LowSky said:**
> Yes. removal of the main hard drive while installing another OS onto a USB can save you some annoying Master boot record issues. Most OS by default will install the MBR to the Primary hard drive and not to the drive your using

Disconnect before or after booting the machine? If you do it before, then the machine won't boot and you can't use it to install to the USB drive. If you try to disconnect it after, I wouldn't want to be the one fiddling with disconnecting hard drives while the computer is on.

---

### Post by Marvin666 on 2009-05-06
Never remove a hard disk while a computer is on. You boot from the installation cd to install the os on the flash drive.

---

### Post by patchido on 2009-05-06
this thread is solved, vista working now, thats why i placed the other thread

---

### Post by mick8985 on 2009-05-06
In that case clikc on thread tools at the top of the page and select mark as solved

---

### Post by patchido on 2009-05-06
> **mick8985 said:**
> In that case clikc on thread tools at the top of the page and select mark as solved

i dont see such thing as that

---

### Post by Didius Falco on 2009-05-06
Patchido,

My sig tells you how to mark it solved.


Regards,

Didius

---

