---
title: "How to install Ubuntu 8.10 onto USB flash media with everything encrypted?"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by son of rebanein on 2009-03-05
Hello,

Today I was browsing the web and came across a website with a really great idea, the only thing is this idea was initially thought out for Debian back in 2005... I was wondering if there is a way to take this idea bring it up to date and adapt it to Ubuntu 8.10 or possibly later for the upcoming Ubuntu 9.04 (is there a way to adapt this idea to most versions of ubuntu).

... So treating me like the new boy, could you explain to me what I must change, install, do and not do (... et cetera) in order to do the above?

Here is the website: ([http://www.debian-administration.org/articles/179](http://www.debian-administration.org/articles/179))

I own a '08 HP Pavilion dv7 AMD Turion X2 (Dual-Core Mobile RM-70)

I don't want to install Windows XP -- I don't need it and don't plan on getting it.

I have an 8GB USB thumbdrive -- the Patriot Xporter mini (aka Patriot x-mini). I am somewhat worried about the life span of this device what type of partition type should I use?

Thanks, If you need more information I will be available soon.

---

### Post by son of rebanein on 2009-03-05
Okay, so the first step was simple. I am still not getting any help here -- though I would like some even if it is just about the partition type i should use for the USB thumbdrive...

---

### Post by DGortze380 on 2009-03-05
Some starting points

[http://ubuntuforums.org/showthread.php?t=298941](http://ubuntuforums.org/showthread.php?t=298941)
[http://www.pendrivelinux.com/ubuntu-804-usb-hard-drive-install/](http://www.pendrivelinux.com/ubuntu-804-usb-hard-drive-install/)

---

### Post by son of rebanein on 2009-03-06
> **DGortze380 said:**
> Some starting points

[http://ubuntuforums.org/showthread.php?t=298941](http://ubuntuforums.org/showthread.php?t=298941)
[http://www.pendrivelinux.com/ubuntu-804-usb-hard-drive-install/](http://www.pendrivelinux.com/ubuntu-804-usb-hard-drive-install/)


Would this do the trick?

---

### Post by card_ace on 2009-03-06
i'm not sure about the encryption process as i've never used it before.  as for installing to a USB device it shouldn't be that hard.  personally i have a 250 GB external Western Digital USB hard drive that i have ubuntu 8.10 installed on.  i understand that flash drives are different than hard drives, but i would think that the process would be relatively the same.  i suppose something you should definitely check is if your computer is even able to boot from USB.

---

### Post by DGortze380 on 2009-03-06
> **son of rebanein said:**
> Would this do the trick?

It should work for the install.

You're going to have to play around with the encryption. You're looking for whole disk encryption that will work with Ubuntu.

I assume (and this may be incorrect, I have not tried it), that any whole disk encryption that supports your file system should work equally well on a flash drive as on a HDD.

---

### Post by Haioko on 2009-03-06
Here is a walk through on how to install using a pen drive.

I used this last night to install Ubuntu onto the PC I'm using right now.

Very good tutorial.

---

### Post by son of rebanein on 2009-03-06
> **Haioko said:**
> Here is a walk through on how to install using a pen drive.

I used this last night to install Ubuntu onto the PC I'm using right now.

Very good tutorial.

Pardon me but I think you forgot to post the link.

---

### Post by son of rebanein on 2009-03-06
I have posted a picture of how I partitioned my system on the current install -- 

Okay basically what I want to do is just have the boot partition on the thumb drive but the link I posted at the beginning of this thread states that I must create two partitions on the thumb drive one for /boot and one for / (root). ---- never mind this approach did not work, my computer doesn't support usb boot... I have just tried installing ubuntu with /boot installed on the x-mini forgetting to check whether or not my laptop supports usb boot -- turns out it doesn't...

---

