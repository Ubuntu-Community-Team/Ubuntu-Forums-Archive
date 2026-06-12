---
title: "problem installing Ubuntu on to laptop"
date: 2010-11-16
forum: New to Ubuntu
---

### Post by ianb72 on 2010-11-16
I am trying to install Ubuntu 10.04 LTS on to my laptop to replace Windows XP, but it starts to boot up with the Ubuntu logo and then goes to a blank screen, nothing works, not the caps lock or anything.

Any ideas~??

---

### Post by migs73 on 2010-11-16
Hi there,

Try these options; [http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html](http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html)

---

### Post by Hippytaff on 2010-11-16
> **migs73 said:**
> Hi there,
 
Try these options; [http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html](http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html)
 
Could have done with that link lst night...my Lubuntu on crap pc is missing xorg.conf :-)
 
I'll give that a bash later

---

### Post by ianb72 on 2010-11-16
> **migs73 said:**
> Hi there,

Try these options; [http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html](http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html)

nope that didn't work.
If its any help the laptop has a Intel on board video card, an Intel 82852/82855 GM/GME

---

### Post by theozzlives on 2010-11-16
If all else fails, you can use the Alternate CD that's text based.

---

### Post by ianb72 on 2010-11-16
> **theozzlives said:**
> If all else fails, you can use the Alternate CD that's text based.

I'll give that a go, I had this same problem with an Nvidia PCi-e card but cant remember how I solved it now!! lol

---

### Post by Hippytaff on 2010-11-16
In that case this might be worth a try
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

---

### Post by ianb72 on 2010-11-16
Well for an experiment I decided to try installing 10.10 version and it booted up fine straight from the cd!!!!

That seems strange to me, I really did want the LTS version but I guess this version will have to do!!

---

### Post by Hippytaff on 2010-11-16
Probably an Nvidia thing - if you really want 10.04LTS then the link I posted might work, though if your happy with 10.10, and don't fancy messing around do that :-)

---

### Post by theozzlives on 2010-11-16
If that's the case, 10.04 might have been a bad download, or a bad burn. You could run a md5sum on it.

---

### Post by ianb72 on 2010-11-16
> **Hippytaff said:**
> Probably an Nvidia thing - if you really want 10.04LTS then the link I posted might work, though if your happy with 10.10, and don't fancy messing around do that :-)

Thanks for that, it worked!! :)

I deleted the quiet and splash from the grub and entered xforcevesa and bingo and worked great :-)

Cheers
Ian

---

### Post by ianb72 on 2010-11-16
> **theozzlives said:**
> If that's the case, 10.04 might have been a bad download, or a bad burn. You could run a md5sum on it.

I thought that, but it worked fine on my main pc, but I did download another copy just to be sure!!

---

### Post by Hippytaff on 2010-11-16
Excellent - Glad it's sorted.
 
Remember to mark the Thread as solved in the thread tools at the top of the page so others with the same problem can see how you fixed it :-)

---

