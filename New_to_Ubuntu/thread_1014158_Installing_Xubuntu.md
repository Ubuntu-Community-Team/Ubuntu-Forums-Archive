---
title: "Installing Xubuntu"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by Latitude on 2008-12-17
Hi, I'm trying to install Xubuntu on an old laptop that my friend gave me. The specs are terrible but it actually runs Windows XP. It has an Intel Pentium II processor @ 397 MHz and 128 megs of ram. It does not have a CD / DVD drive or an Ethernet port. The big pie chart says I have 3.81 GB of space on an NTFS formatted disk. I put the Xubuntu .iso and the Wubi installer on the laptop by transferring with my PSP. When I click Wubi it says :
Extracting... %'s
You have 127 MB of memory the installer requires 256mb, Continue?
I click Yes then it says:
You have 1273 MB free, the installer requires 5000 MB free, continue?
I click Yes again and then I pick Xubuntu and make a user name and password and click install. 
It does some stuff then says : Please connect to the internet now.I cant connect it to the internet. 
 Is there anything more I can do without connecting it to the internet? I cannot connect it since I dont have a cable old enough for the hole it has. Any help at all is appreciated

---

### Post by Latitude on 2008-12-17
-not a bump-

---

### Post by evilkastel on 2008-12-17
you are using a standard cd intall, in iso form. i believe the DVD install doesn't need to connect to internet (since it includes most of the repositories files) yet, i do not know if you will have acces to medibuntu, so you'll have to download the debs and pass trough the psp. So, get the DVD iso, pass it and mount it, and tell me how it goes.

---

### Post by Latitude on 2008-12-17
Ill try to find the DVD install, but is it bigger then 1gb?

---

### Post by mrbiggbrain on 2008-12-17
> **evilkastel said:**
> you are using a standard cd intall, in iso form. i believe the DVD install doesn't need to connect to internet (since it includes most of the repositories files) yet, i do not know if you will have acces to medibuntu, so you'll have to download the debs and pass trough the psp. So, get the DVD iso, pass it and mount it, and tell me how it goes.

arnt most DVD iso's 3GB, he would need a 4GB memory stick to perform this action, thats quite a size for most people... but he might have it

---

### Post by evilkastel on 2008-12-17
it is around 4.3 GB.

---

### Post by evilkastel on 2008-12-17
mrbigbrain he said he uses a psp, i do not know how memory those have... but it was worth the shot. 

edit: double post ----doh!
>.<
i do not know how to erase posts, srry.

---

### Post by Latitude on 2008-12-17
I only have 1 GB flash drives and my PSP memory card is also 1 GB

---

### Post by Latitude on 2008-12-17
This hard drive actually doesnt even have enough space for a single DVD.

---

### Post by halitech on 2008-12-17
with only 128 meg of ram, I'd be looking at another distro. Normally I'd recommend Debian with XFCE but since you don't have an ethernet port on it, can't do the normal net install. With no cd you are limited what you can do as well. If you have another machine with a cd, you could try running puppy linux, install it to a usb drive and then doing a hard drive install on the laptop. I don't know how well or if this will work but its something to try.

---

### Post by evilkastel on 2008-12-17
Well, xubuntu will run in that machine, i had that running in a similar one. but if you do not have a way to access the iso, probably ubuntu is not the best. Puppy linux is a very good small linux distro. DSL is said to be good too, but it is a bit more complicated to use. and another small linux distro 'ill recommend is vector linux. we have pcs running vector in my college.

---

### Post by mkvnmtr on 2008-12-17
Would it not be possible to use the minimal install disk. It is about 14 MB. Then use a normal install disk as a repository.

---

### Post by halitech on 2008-12-17
> **Latitude said:**
> It does not have a CD / DVD drive or an Ethernet port. 

> **Latitude said:**
> This hard drive actually doesnt even have enough space for a single DVD.

> **mkvnmtr said:**
> Would it not be possible to use the minimal install disk. It is about 14 MB. Then use a normal install disk as a repository.

if they had a cd rom then that would work but alas, they say no cd rom

---

### Post by anjilslaire on 2008-12-17
get the alternate cd iso and try that, maybe?

---

### Post by Latitude on 2008-12-17
This craptop doesnt have a CD drive. Its taken out. Its an IBM 600E. The Bios says its from 11/20/99. It cannot boot from USB...

---

### Post by halitech on 2008-12-17
personally, I've tried Xubuntu on a P2 300 with 196 meg of ram and it was less painful to jab a fork in my leg. Forget the ubuntu family and look at a lightweight distro like puppy, dsl, vectra or something similar that will install from a usb thumbdrive that might stand a chance of running on a P2 300.

---

### Post by 2blue on 2008-12-17
Hi Latitue

I have an old laptop not much better than yours and after I installed as much RAM as I could find it runs Xbuntu very well, not noticeably slower than Puppy and DSL. I was lucky, both my laptops boots from CD. That said I have a friend who swears by Ubuntu and has it installed on the oldest laptops with the least memory imaginable. RAM and wireless internet usb stick can be found on ebay at a low price these days. You might even get your hands on a new or used CD-rom

Even thought Puppy Linux is very light and installs easily it requires a minimum of 128 MB RAM, and if you could double (or more) that would be an advantage. Puppy is very easy to like, but a bit more work to configure hardware like internet card and usb ports can be expected. I would recommend you try both Xubuntu and Puppy :-) 


[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Good luck and let us know how things turn out.

---

### Post by 2blue on 2008-12-17
Come to think of it, it is probably not worth your time or money. Look at what these old things go for on ebay, CDROM and PCMCIA input intact. If you keep your eyes open there are probably someone who will give you an old laptop to mess with that is not robbed of anything. 

[http://cgi.ebay.com/Thinkpad-600E-Good-working-condition_W0QQitemZ160304461877QQcmdZViewItemQQptZLaptops_Nov05?hash=item160304461877&_trksid=p3286.c0.m14&_trkparms=72%3A1234|66%3A2|65%3A12|39%3A1|240%3A1318|301%3A0|293%3A1|294%3A50](http://cgi.ebay.com/Thinkpad-600E-Good-working-condition_W0QQitemZ160304461877QQcmdZViewItemQQptZLaptops_Nov05?hash=item160304461877&_trksid=p3286.c0.m14&_trkparms=72%3A1234|66%3A2|65%3A12|39%3A1|240%3A1318|301%3A0|293%3A1|294%3A50)

---

### Post by Latitude on 2008-12-17
Wow you guys are helpful! 
I downloaded Puppy Linux and its a 94.3 MB ISO. 
If I extract it and put it on a flash drive or other memory stick how would I start installing it?

---

### Post by 2blue on 2008-12-18
I again

There is a rather good manual on how to install Puppy on their website. Hard drive install requires a bit more work before installing. Every thing is explained in detail in the manual. There is also a forum you can search for answers.

[http://www.puppylinux.org/manuals/puppy-40/english/how-install-puppysolutions](http://www.puppylinux.org/manuals/puppy-40/english/how-install-puppysolutions). 


[http://www.murga-linux.com/puppy/](http://www.murga-linux.com/puppy/)

Good Luck

---

