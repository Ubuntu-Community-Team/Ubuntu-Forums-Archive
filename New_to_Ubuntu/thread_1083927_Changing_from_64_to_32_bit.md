---
title: "Changing from 64 to 32 bit"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by agarzon on 2009-03-01
Hi all,

I screwed up my install. I had disks for both 8.10 1386 and x86_64. Unfortunately I installed the 64 bits disk and only found out when I tried to install the adobe plugins and noticed it was downloading and installing the ai32 libs. :lolflag: Iknow, most of you are saying "what was he thinking?"

Some caviats: The system is installed on a second partition on the second hard drive. I used the manual install option, alocating some swap space, a root partition (sdb3) and a /home partition (sdb4)

```
agarzon@agarzon-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb3             5.5G  2.9G  2.4G  56% /
tmpfs                 469M     0  469M   0% /lib/init/rw
varrun                469M  100K  468M   1% /var/run
varlock               469M     0  469M   0% /var/lock
udev                  469M  2.8M  466M   1% /dev
tmpfs                 469M  344K  468M   1% /dev/shm
lrm                   469M  2.4M  466M   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sdb4             114G  988M  107G   1% /home
agarzon@agarzon-desktop:~$ 
```


Does anyone know a "simple" way of switching to 32 bit version? :confused:

---

### Post by Perfect Storm on 2009-03-01
What's wrong using 64-bit? Is it because it installs some 32-bit libs in /usr/lib32 that you don't like? :confused:

---

### Post by perlluver on 2009-03-01
Running 64 bit here, an no problems to speak of.  There are 64 bit plugins available for Flash and Java now available.  Other than that, the only way to get to 32 bit is to install it off of the 32 bit CD.

---

### Post by agarzon on 2009-03-01
No that's not the problem. I simply like to keep it simple. Some apps (skype for example or some plugins) are easier to install in their native 32 bit envirnment. 

I am running 64bit at my office machine. So I am somewhat familiar with it.

---

### Post by agarzon on 2009-03-01
So, there is no way to change the "sources" and switch it?

---

### Post by agarzon on 2009-03-01
I intend to configure the TV card (Hauppauge PVR-150) and since I am not all that knowledgeable I wanted to keep the 32/64 bit out of my variables.

---

### Post by perlluver on 2009-03-01
> **agarzon said:**
> So, there is no way to change the "sources" and switch it?

No it uses two different kernels, one with 64 bit technology enabled, and the 32 bit kernel, with 64 bit disabled.  It also depends on a lot of packages that are installed.  You will have to re install using the 32 bit cd.

---

### Post by agarzon on 2009-03-01
How do I do reinstall it without loosing my home partition and data?

---

### Post by perlluver on 2009-03-01
> **agarzon said:**
> How do I do reinstall it without loosing my home parition and data?

You will have to back it up, either to a CD, DVD, or another Hard Drive.

---

### Post by pspsampsp on 2009-03-01
i would suggest you back up your home partion and all data that is needed and if you have any special settings in your xorg file back them up aswell

---

### Post by agarzon on 2009-03-01
re-installation from CD it is

Thank you all.

:(

---

### Post by oldos2er on 2009-03-01
> **agarzon said:**
> I intend to configure the TV card (Hauppauge PVR-150) and since I am not all that knowledgeable I wanted to keep the 32/64 bit out of my variables.

 I have a Hauppauge PVR; there's no difference in configuring it in 64-bit Ubuntu as opposed to 32-bit.

---

### Post by presence1960 on 2009-03-01
> Does anyone know a "simple" way of switching to 32 bit version? 

You should be asking yourself "why not 64 bit?" Flash & java are working good now on 64 bit so you might as well make use of that 64 bit processor you paid for. If you have any problems or questions there are loads of help available on the x86-64 Users topic on this forum. This includes a great tutorial in getting java and flash to work, it is in the stickys.

---

### Post by agarzon on 2009-03-01
> **oldos2er said:**
> I have a Hauppauge PVR; there's no difference in configuring it in 64-bit Ubuntu as opposed to 32-bit.
Great to know you do. You may see me asking questions later on about the TV card :p

Thanks Ann

---

