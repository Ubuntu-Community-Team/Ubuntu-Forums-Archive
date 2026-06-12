---
title: "How to uninstall Ubuntu?"
date: 2011-07-21
forum: New to Ubuntu
---

### Post by Howlin1 on 2011-07-21
Hello,
I would like to uninstall Ubuntu 10.10 from a usb key. I did a Google search and found that I need to first remove the partitions. I had 4 partitions, I have managed to remove two of the partitions but I can't remove the other two (sdb1 and sdb5). When I click on them there is no option to delete/resize them. Why is that or is there a different way to remove Ubuntu?

---

### Post by rickytikki on 2011-07-21
if your going to remove ubuntu for im assuming for (Ugh) win-duhs log into windows and do it form there its easier and you will be able to add the partition to windows at he same time. also try and do some research on you r own before posting this. ps you should have gone to a windows forum.

---

### Post by ubudog on 2011-07-21
> **rickytikki said:**
> if your going to remove ubuntu for im assuming for (Ugh) win-duhs log into windows and do it form there its easier and you will be able to add the partition to windows at he same time. also try and do some research on you r own before posting this. ps you should have gone to a windows forum.

I believe the OP was talking about removing it from a flash drive, not the hard drive.  If I'm mistaken, please correct me.  :-)  

Anyway, an easy way to do this, is...
[http://www.howtogeek.com/howto/17001/how-to-format-a-usb-drive-in-ubuntu-using-gparted/](http://www.howtogeek.com/howto/17001/how-to-format-a-usb-drive-in-ubuntu-using-gparted/)

BE SURE TO BACKUP YOUR STUFF ON THE FLASH DRIVE BEFORE CONTINUING (Documents, etc.)

Also, make sure you DO NOT format your HD.  DON'T format anything that says "sda" or "hda".

Hope that helps.  ;-)

---

### Post by MG&amp;TL on 2011-07-21
Umm...Ubuntu can be slightly tricky to uninstall, mainly because it tends to leave grub behind. If it can't find ubuntu, grub has a problem and won't boot until there is linux there. So be careful.

Probably the easiest way is to back your data up, reinstall Windows if you have a cd, and put all your data back on. 

I would suggest you go to a Windows forum, not as rickytikki suggests, because we won't help you here, we will, but because you are likely to be better served. Why do you wish to remove ubuntu?

Good luck! :)

EDIT: or, there again, you may be using a USB, in which case follow the link ubudog gave.

---

### Post by ubudog on 2011-07-21
Um, OP, are you trying to uninstall Ubuntu from your computer, or from a flash drive?

---

### Post by Howlin1 on 2011-07-21
I am only removing Ubuntu because I have it on a usb key and my usb is to slow to run Ubuntu so I'm taking it off that and I'm getting a HDD in the next few days and I'll be putting it on that.

---

### Post by ubudog on 2011-07-21
> **Howlin1 said:**
> I am only removing Ubuntu because I have it on a usb key and my usb is to slow to run Ubuntu so I'm taking it off that and I'm getting a HDD in the next few days and I'll be putting it on that.

Ah, in this case, don't you want to wait until you get the HD so you can install it from the flash drive?  Otherwise, it would be kind of silly to remove Ubuntu from the flash drive and then install it back on just to install to HD.

---

### Post by dodo3773 on 2011-07-21
Just back up any separate files you may have on the flash drive and just reformat the whole thing.

---

### Post by Howlin1 on 2011-07-21
> **ubudog said:**
> Ah, in this case, don't you want to wait until you get the HD so you can install it from the flash drive?  Otherwise, it would be kind of silly to remove Ubuntu from the flash drive and then install it back on just to install to HD.

Don't I need to download a copy of Ubuntu anyway because the copy I have is installed?

---

### Post by westie457 on 2011-07-21
> **Howlin1 said:**
> Don't I need to download a copy of Ubuntu anyway because the copy I have is installed?

That depends on whether or not you actually installed to the stick or created a LiveUSB with a persistence file to store documents and things, including any app/programs from the repositories.

---

### Post by CaptainMark on 2011-07-21
it depends how you have installed ubuntu on the flash drive, you either have a live install which is like a trial session that you can boot (these can also reinstall onto your hdd) or you have actually made a full install on a usb which is less likely if you are a beginner as this is not the default way of things. an easy way to tell would be, if you are greeted with an menu to try ubuntu, you have a live usb

---

### Post by Howlin1 on 2011-07-21
> **westie457 said:**
> That depends on whether or not you actually installed to the stick or created a LiveUSB with a persistence file to store documents and things, including any app/programs from the repositories.
I did actually install it on the USB key


EDIT:

> **CaptainMark said:**
> it depends how you have installed ubuntu on  the flash drive, you either have a live install which is like a trial  session that you can boot (these can also reinstall onto your hdd) or  you have actually made a full install on a usb which is less likely if  you are a beginner as this is not the default way of things. an easy way  to tell would be, if you are greeted with an menu to try ubuntu, you  have a live usb
I did install ubuntu on my usb with the full intention of using it, but it didn't turn go that way because my usb isn't good enough.

---

### Post by CaptainMark on 2011-07-22
so you must have had a cd or something similar to create the usb install to start with, if you still have that you can use that to install onto the hdd if you no longer have it or it you borrowed it temporarily then youll need to get another copy downloaded and burned to cd [from here]("http://www.ubuntu.com/download/ubuntu/download")

---

