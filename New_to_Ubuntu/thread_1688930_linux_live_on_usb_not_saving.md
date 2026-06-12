---
title: "linux live on usb not saving"
date: 2011-02-16
forum: New to Ubuntu
---

### Post by KXTwo on 2011-02-16
this might be a dumb question and I found nothing doing a search.  Im currently running ubuntu from a usb card, it runs great, except its not saving.  I have to enter my pw for my wireless network everytime, it doesnt keep bookmarks etc etc.  Am I doing something wrong or is this just the way it is?

---

### Post by KXTwo on 2011-02-16
This must have been a trickier question than I thought.

---

### Post by nothingspecial on 2011-02-16
Make another usb stick with usb-creator-gtk

and tick the stored in reserved space box

You have not got persistance enabled so in your case, yes thats the way it is.

---

### Post by clhsharky on 2011-02-16
KXTwo

Welcome to UF.

Are you using live ISO image?
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)
or are you using a persistent image?
[https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)


I recommend install on 8GB usb stick.


Sharky

---

### Post by KXTwo on 2011-02-16
I downloaded unbuntu 10.10 and followed the instructions for installing to usb by using universal usb installer.

---

### Post by tea for one on 2011-02-16
> **KXTwo said:**
> I downloaded unbuntu 10.10 and followed the instructions for installing to usb by using universal usb installer.

Good evening

It is not quite clear which software utility you used to create your device.

The method that works most of the time is to use the Startup Disk Creator within the Ubuntu System menu.

System > Administration > Startup Disk Creator (with or without persistence)

"Universal USB Installer" sounds like the Unetbootin software, which does not offer automatic persistence.

---

### Post by KXTwo on 2011-02-16
I guess im not fully understanding.  What I want to do is be able to boot linux from my usb drive, and for any changes I make to be saved to the usb like if I had ubuntu installed on my harddrive.  All of the walkthroughs I've looked at are for if I actually had a live cd and wanted the usb to be persistent.

---

### Post by KXTwo on 2011-02-16
omg I feel like an idiot.  There is an option right on universal usb installer for persistance.  Im trying it now and let everyone know if it works.

---

### Post by BananaPeal on 2011-02-16
I'm trying to do the same thing and honestly, it appears there are limitations to persistence... 

First thing I tried were to install proprietary gpu drivers and ... after some mad googling and some terminal commands, although I got the drivers installed, it wasn't clear if they worked and after I did a synaptic update of the whole system, my sudo became inoperative and other things seemed to break. now i'm stuck.

so another option to persistence is to use a physical linux cd to do a full install to usb by choosing the usb as the target instead of your hdd. if you try this, be careful that grub doesn't install to your hdd (as default)  but your usb instead!

that should give all the functionality of a real linux install.

my 54 cents. (really felt shorter in my head!)
):P

---

### Post by KXTwo on 2011-02-16
universal usb installer did the trick.  Simply follow the link from the ubuntu download page, download installer and the iso, when you copy the iso to your usb card simply set persistance to whatever size you so chose.

---

