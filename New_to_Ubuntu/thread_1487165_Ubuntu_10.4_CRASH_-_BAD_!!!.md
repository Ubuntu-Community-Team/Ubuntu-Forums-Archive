---
title: "Ubuntu 10.4 CRASH - BAD !!!"
date: 2010-05-18
forum: New to Ubuntu
---

### Post by smileyacid on 2010-05-18
Hi my comp keeps crashing under new Ubu (10.4 from 9.10 fresh install) I had no problems before + still have no problems with Win XP (dual boot) so I'm sure its not hardware related it just shuts down screen goes black + a few red + blue squares show up then that's it I have to re-boot,

The screen also blanks + sometimes shows red + blue squares on boot up,

I read that it might be related to new flash install ? on another thread anyway if anyone can HELP and needs more detail please reply

SMILEY - waiting patiently

---

### Post by DOSIX on 2010-05-18
i'm thinking it might be something to do with X server. when you get to grub boot into recovery mode. from there run fsck.

---

### Post by smileyacid on 2010-05-19
Thanks Dosix i tried fsck but it said filesystem was mounted + would  cause severe damage so i aborted

smiley

---

### Post by Catharsis on 2010-05-19
What graphics card do you have?
```
lspci | grep VGA
```

---

### Post by wojox on 2010-05-19
You can run a Filesystem Check on next reboot with this:

```
sudo touch /forcefsck
```

Enter that into the terminal and reboot. :)

---

### Post by smileyacid on 2010-05-19
jamie@jamie-desktop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
jamie@jamie-desktop:~$

---

### Post by Kafubie on 2010-05-19
It's bad but yet... Why the Happy Face..  
DOES NOT COMPUTE!
*BOOM*

---

### Post by Catharsis on 2010-05-19
Please see:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

### Post by smileyacid on 2010-05-19
Thankyou wojox some one on linuxquestions said #lspci -v

and

X logs in /var/log


Also do

#sudo apt-get check

#sudo apt-get update
#sudo apt-get upgrade -y

but i dont know what he means im not an expert

---

### Post by smileyacid on 2010-05-19
Thanks for al your help after much help + research i think i fixed the problem (video driver related) 

CHEERS UBU FORUM

smiley

---

