---
title: "Problem with 11.04 and Dell Laptop"
date: 2011-05-09
forum: New to Ubuntu
---

### Post by JerryC on 2011-05-09
Ubuntu v11.04 will not boot from the CD on my Dell Studio 1749 Laptop.  We have an Intel Core i3 CPU, 2.27 GHz; 4GB Ram; Intel Graphics.  This is a 64 bit CPU and neither the 32 bit or 64 bit versions of 11.04 will boot.  It gets up to the point where the 5dots are blinking across as a progress indicator.  After several moves across, it locks up the machine and it has to be shut off to be reboot. I presume it is a graphics problem.  Any ideas?  Need any more info?

JC

---

### Post by collisionystm on 2011-05-09
> **JerryC said:**
> Ubuntu v11.04 will not boot from the CD on my Dell Studio 1749 Laptop.  We have an Intel Core i3 CPU, 2.27 GHz; 4GB Ram; Intel Graphics.  This is a 64 bit CPU and neither the 32 bit or 64 bit versions of 11.04 will boot.  It gets up to the point where the 5dots are blinking across as a progress indicator.  After several moves across, it locks up the machine and it has to be shut off to be reboot. I presume it is a graphics problem.  Any ideas?  Need any more info?

JC

Press the UP arrow key on your keyboard at this screen. It will hide the purple splash and show you the text output of whats happening. 

You can then share the info

---

### Post by JerryC on 2011-05-09
The last 4 lines of text are:

Starting bluetooth
Stopping save kernel meessages
PulseAudio configured for per-user sessions
saned disabled; edit /etc/default/saned

Hope this helps

JC

---

### Post by collisionystm on 2011-05-09
Is this from the live cd?

EDIT: nevermind... re-read your post. Try the alternative install cd from ubuntu.com. 11.04 is very finicky because it ttys to load with compiz. The purple dots is a sure sign that it can't immediately load the driver for your graphics card. Do the alt. Install and run the updates

---

### Post by JerryC on 2011-05-09
Where does one find this alternative install CD?  A search wasn't helpful.

JC

---

### Post by ubume2 on 2011-05-09
These are daily builds of 11.04 in alternate cds:


[http://cdimage.ubuntu.com/daily/current/]("http://cdimage.ubuntu.com/daily/current/")

---

### Post by JerryC on 2011-05-11
Well folks, I'm sorry, but I think this version wasn't anywhere near ready for release unless you are the usual linux geek.  This release will do major damage to the idea of trying to make Ubuntu a desktop for the masses and the various releases were coming along so well.  Maybe in another 2 or 3 years.....

JC

---

### Post by BertN45 on 2011-05-11
> **JerryC said:**
> Well folks, I'm sorry, but I think this version wasn't anywhere near ready for release unless you are the usual linux geek.  This release will do major damage to the idea of trying to make Ubuntu a desktop for the masses and the various releases were coming along so well.  Maybe in another 2 or 3 years.....

JC
I remember the transfer from XP to VISTA with the same type of problems. Some drivers did not even exist.  At least you did not have to pay anything.

You have integrated Intel graphics, it is a known problem and you seemingly have to add **noacpi** to the GRUB boot loader. Try to google for the best description how to do it.

I switched to Xubuntu, which worked for my integrated Intel chip set. It is a nice OS with some real improvements.

---

### Post by JerryC on 2011-05-11
> **BertN45 said:**
> I switched to Xubuntu, which worked for my integrated Intel chip set. It is a nice OS with some real improvements.

Is it possible to do a Wubi install with Xubuntu?  How about a wubi install of 10.10?  That way I don't have to partition.

JC

---

### Post by BertN45 on 2011-05-11
> **JerryC said:**
> Is it possible to do a Wubi install with Xubuntu?  How about a wubi install of 10.10?  That way I don't have to partition.

JC
Both support Wubi install.

---

### Post by JerryC on 2011-05-11
Good to know.  Now how do you do it?  When I run wubi now, it goes after 11.04 automatically.

JC

---

### Post by dnns on 2011-06-04
Guys,

This might be of help:

I wanted to upgrade my Dell Studio 1749 to 11.04 via a fresh install.

But, I could not for the life of me figure out why the Natty 11.04 Live CD would not boot on my Dell Studio 1749.

32 bit, 64 bit, alternate CD, nothing worked. I eventually upgraded to 11.04 from within 10.10 (64 bit). The upgrade installation completed without errors, but tragedy struck again, after a reboot I could not boot the 2.8.38 kernel!

Long story short: THIS IS THE SOLUTION: 
The Dell Studio had the A05 BIOS installed. I upgraded to the A08 BIOS and now everything works!

---

