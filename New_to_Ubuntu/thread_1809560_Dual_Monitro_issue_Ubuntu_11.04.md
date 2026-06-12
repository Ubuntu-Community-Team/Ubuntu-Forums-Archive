---
title: "Dual Monitro issue Ubuntu 11.04"
date: 2011-07-21
forum: New to Ubuntu
---

### Post by behrouzjaz on 2011-07-21
Hello,

I am new with ubuntu and I am using my Toshiba netbook(NB200) with Ubuntu.

The problem is when I connect external monitor, it hangs.

Can anyone help me with that?

Thank you

My system spects:
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"

Cpu: Atom 1.6
Graphic: Intel Graphics Media Accelerator 950

---

### Post by roololing on 2011-07-21
Sorry, but what do you mean by 'hangs'? Does the monitor not get recognized? Or does your computer freeze up?

---

### Post by behrouzjaz on 2011-07-21
Hello,

Monitor is recognized, when I use lap top monitor and external one , it becomes so slow but when I switch off the lap top one and only use external Monitor , it works perfectly!

---

### Post by Immolatus on 2011-07-21
The max resolution for the integrated 950 is 2048x1536. If you run two monitors you'll almost split this resolution capacity between the two.  
Try setting the resolutions to 1024x768 (half of the max from the white papers for this chipset).

I assume you are trying to extend your desktop??

P.S. Is this a net book??

---

### Post by behrouzjaz on 2011-07-21
Hello,

Yes , I am trying to extend my desktop ,laptop resolution is 1024x600 and monitor is 1280x1024 but its still the same.

Do i have to install any specific package ? because in windows I can set to this resolutions without any issue; and Yes, its net book.

---

### Post by Immolatus on 2011-07-22
Notice that the external monitor resolution is higher. 
What is the make and model of the external??
you might need to edit your Xorg.conf to include this monitor and force a specific resolution to make it work correctly.

---

### Post by behrouzjaz on 2011-07-22
Thank you for your reply,

I cant find Xorg.conf. Can you tell me where is it located and what should I add in it?

My external monitor is Samsung synMaster 733N.

Is there any way to set it globally so when I connect to other external moitor I dnt face any issue.

I connect my netbook to my LCD in home as well and I have the same issue.

---

