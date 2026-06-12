---
title: "Possible mount point help."
date: 2011-06-04
forum: New to Ubuntu
---

### Post by wavemaker on 2011-06-04
Gooday all. I have been trying to get Linux onto a spare puter that I'm going to lend to a mate.He needs to do nothing further at this point than get email and do some web browsing. Now,  have been messing around with Linux for a few years and installed quite a few distros on different machines. My problem is I cant load a distro to this HD. It has served well in other instances. Hopefully the attachment will point to where I want to go with this. There is something going on here that I can't figure out. All help most gratefully received. 
I have tried different cables going from the HD to MOBO. I have tried every position that the jumpers can be in.
The HD is a Seagate Barracuda 7200.7 I am trying to install ubuntu 10.10. I downloaded this on 28/12/10 and successfully mounted it on another box. I am going to attach a screen shot of what parted magic shows me. So here we go.

---

### Post by corncob on 2011-06-04
Can you change that mount point from /media/sda1/ to / ?  You might have to use the live CD to do it.  What version of Ubuntu is it?  If nothing else, reinstall the whole thing -- it doesn't sound like you have anything to loose.

---

### Post by Lateralis on 2011-06-04
I'm probably being slow and thick here, but, what exactly is your problem?  You've attached the screenshot and it shows a mounted ext3 partition and an inordinately large swap partition.  (Side question: is 11.5 GBs of swap *really* necessary?)  Aside from he size of the swap partition, nothing looks out of the ordinary there to me so far... 

So, from what I can gather, you've downloaded the Ubuntu image, burned it to disc, booted into a computer through the live CD with this blank hard drive attached and tried to install Ubuntu to it.  Then what?

---

### Post by seawolf167 on 2011-06-04
Like corncob said, it looks like you need to set your / mount point  (instead of the current /dev/sda1 if that is indeed your / (root) system) and hopefully that will be it and you should be good to go.

---

### Post by wavemaker on 2011-06-05
Thanks all for input, for some reason it decided it wanted to play this arvo.

---

