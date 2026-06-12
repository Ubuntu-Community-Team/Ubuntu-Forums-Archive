---
title: "[SOLVED] broadcom 4328 -- still trying, the return."
date: 2008-03-02
forum: Networking &amp; Wireless
---

### Post by rafaelsaraiva on 2008-03-02
good friends,
as well as multiple users,
i am having problems with the configuration of wireless.
i am using a hp dv6000, which has the plate **broadcom 4328**.
my operating system is the Ubuntu 7.10_amd64 / dual boot with vista [argh!].
[at vista wireless is working perfectly].

the wireless red light persists and insists ...
after a few days trying to almost
topics of the forum related to the subject with no sucess,
i decided ask your help.

i know that the subject is hit,
but I am no more to do...

**some information:**

ndiswrapper is installed.
windows network drivers
current installed windows drivers:
bcmwl5
hardware present: yes
_ _ _

rafael@laptop:~$ sudo ndiswrapper -l

[sudo] password for rafael:

bcmwl5 : driver installed

        device (14E4:4328) present

_ _ _
	
Thank in advance. 
The best compliments

---

### Post by Kralizec on 2008-03-02
Did you make sure to run ```
ndiswrapper -m
``` to create an alias for the wireless card? I know I had forgotten that step when I reinstalled Ubuntu; made for a frustrating time while I searched for the original How-To I followed.

---

### Post by rafaelsaraiva on 2008-03-03
i had already given this, but forgot to post. 

the response of the terminal for 'ndiswrapper -m' was: 

**configuration module already contains alias directive.**

which means? 
[actually i'm new here and i'm only reproducing 
the information and codes i find on the forum]

greetings.

---

### Post by Kralizec on 2008-03-03
That means that supposedly when you load you load the ndiswrapper module into your kernel, it should have a set network interface to work with. Are you sure you did load ndiswrapper? The command would be ```
sudo modprobe ndiswrapper
```

Additionally, you need to make sure you've removed the default Broadcom module, bcm43xx and blacklisted it: 
```
sudo -s
echo blacklist bcm43xx >> /etc/modprobe.d/blacklist
rmmod bcm43xx

```

This is the link to the HowTo I followed (its not just for Dells like the title says) and it worked where none of the others I read did: [http://ubuntuforums.org/showthread.php?t=297092]("http://ubuntuforums.org/showthread.php?t=297092")

---

### Post by rafaelsaraiva on 2008-03-04
thank you, my comrade. 
i decided to follow the howto you provided and succeed! 
i had tried this link, but as i'm beginner and 
i am still familiarising with the terminal, 
must have done something wrong in the first attempt. 
now i will fight to set up wi-fi. :) 
a hug and thanks.

---

