---
title: "How to install open office in Lubuntu"
date: 2010-10-14
forum: New to Ubuntu
---

### Post by asifnaz on 2010-10-14
I am working on a project which aims provide 40$ computers to 3rd world students .
I decided to use PIII with lubuntu .
As I am new to Linux I have no idea how to install open office in Lubuntu 
I have downloaded it

it is in (OOo_3.2.1_Linux_x86_install-deb_en-US.tar) format

kindly guide me step by step how can I install it

---

### Post by diablo75 on 2010-10-14
Just open a terminal and type:

```
sudo apt-get install openoffice.org
```

Also... does Lubuntu have Synaptic Package Manager installed on it?  If so, you can just use that to add/remove software if you don't have the Software Center to use.

---

### Post by mastablasta on 2010-10-14
Go to Synaptic and find Open office and then install it.
 
how many Mhz does the ocmputer have? because it might work slow on a P3. well also depends on how much ram you have i guess.
 
Lubuntu is light but if you use "heavy" programmes then that wont' help much.

---

### Post by diablo75 on 2010-10-14
Yeah, you might try AbiWord instead of Open Office if it performs sluggishly.

---

### Post by friTTe81 on 2010-10-14
or give Libreoffice a spin, dont know if its so light but its good.
Ive replaced my Openoffice for it.

---

### Post by Hagar Delest on 2010-10-14
If you want to install the vanilla version, see [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by pinklady14 on 2011-09-03
> **diablo75 said:**
> Just open a terminal and type:

```
sudo apt-get install openoffice.org
```

Also... does Lubuntu have Synaptic Package Manager installed on it?  If so, you can just use that to add/remove software if you don't have the Software Center to use.


Hi, 

I am an absolute beginner and I am trying to install Open Office using Lubuntu  - linux 2.6.38-8-generic (i686), light version of Ubuntu 11.4

I have downloaded the latest version of Open Office 3.3 and I don't know what to do next.

I am switching from windows/microsoft so I am very unfamiliar with Linux language and technical words.

How do I open a'terminal' so that I can type sudo etc...

I can see the synaptic package manager.  

Thank you.
:confused::confused::confused:

---

### Post by pqwoerituytrueiwoq on 2011-09-03
either of these

[LIST]
[*]application-> accesories-> terminal
[*][crtl]+[shift]+[t]
[/LIST]
alternatively you can search for open office in the software center

---

### Post by vasa1 on 2011-09-03
> **Hagar Delest said:**
> If you want to install the vanilla version, see [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

Greetings,

Hagar, in the tutorial, in the section referring "for all Debian-based distros - 1. Remove all the packages from the installed version", there is this:
> But in case you want to upgrade your whole distro, you'll have to install back this package (and the OOo original version).

I know the tutorial is from some time ago but does this caution about having to re-install still apply to 11.04?

---

### Post by Hagar Delest on 2011-09-04
Well, I don't really know. You can try as it is and see if the upgrade is fine or complains about a missing OOo.

But basically, avoid the soft upgrade. I've tried it once or twice and have noticed (as other users in this forum too) that the new system can have flaws due to remnants of the old flavor. Personally, I've dedicated 2 partitions for the root (/). I install an Ubuntu version on 1 partition and the next one on the other and the following one on the 1st. So I always install from scratch with the live CD. You've to do other partitions to store your data of course (I've about 8 partitions in total).

---

