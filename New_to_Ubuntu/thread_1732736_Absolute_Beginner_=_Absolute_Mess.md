---
title: "Absolute Beginner = Absolute Mess"
date: 2011-04-18
forum: New to Ubuntu
---

### Post by nfoglesbee on 2011-04-18
I need help. Seriously - I've got issues. In the space of 24 hours I've "ruined" my laptop and my desktop.
 
Two problems:
 
1:
 
I've successfully installed 10.10 on my desktop, however - when the login screen pops up I'm only able to login under "Desktop Edition (Safe Mode)". When I attempt to log in under the normal Desktop Edition nothing is present - the top and bottom bars don't show and I'm unable to right-click on anything. I'm also unable to connect to the internet in Safe Mode... I think Ubuntu may not recognize my NIC, but I have been unable to get into the normal Desktop to check. Is it possible to solve this through Safe Mode - or do I have to reinstall everything over again?
 
2:
 
I've got a Dell Studio 1555 with Vista x64 installed, and GRUB2 on the MBR. The extra hard drive that 10.10 was on is gone - so each time I boot it reads an error (device not listed). I need to rewrite the MBR, but don't have a disk to do so yet - this problem is more temporary. However, I was wondering if there is a solution through the GRUB> command line.
 
Any help will be much appreciated...

---

### Post by Wobblybob on 2011-04-18
Q1.Do you have a background on the desktop you get? or just a blank screen are you using the gnome edition? have you installed over a previous version which had a home on another partition?

You could try using a live cd if it loads to a desktop you should be able to see if the nic card is recognized because if you are connected to a router via a cable you should get a connection to the net. 

Q2 sorry not my area but for anyone else are you saying you have removed a HD with ubuntu on it and now just have windows only on one HD and want it to load direct to windows?

---

### Post by nfoglesbee on 2011-04-18
A1: Yes, there is a background - but it's just the background and cursor (nothing else). The install was "complete" it erased the the whole HHD, but I had previously tried to install it a couple times beforehand (kept messing up because of a bad DVD drive, once I cleaned it it installed fine) as a secondary, but decided to go ahead with a full install.
 
Does Safe Mode not have network capabilities? I will try the LiveCD when I get off work... come to think of it I think it was working off the CD a day or so ago.
 
A2: Yep, exactly! Thanks anyways.

---

### Post by Wobblybob on 2011-04-18
Q1 If you can use the live CD to get onto the desktop you should be ableto navigate to the installed ubuntu and into your home folder. I would ctrl +H to show the hidden files then remove or rename the gconf folders so that it re creates the config files on next boot. Then re boot. 

Q2 this thread may help

[[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=891118[/COLOR]]("http://ubuntuforums.org/showthread.php?t=891118")

---

### Post by nfoglesbee on 2011-04-18
Thanks!  I'll try this as soon as I get home.  I appreciate the help - I will let you know how it goes tonight.

---

### Post by nfoglesbee on 2011-04-18
Okay, updates...

I tried to load a LiveCD into the desktop and it when I select "Try Ubuntu" it simply boots to a black screen w/cursor & start-up sound.  That's all.
I tried loading it up into Safe Mode and deleted the .gconf folders.  That didn't help either - still can't load "Desktop Edition" (only the Safe Mode).

I'm also wondering if there is a way to use the LiveCD to remove GRUB2 from my laptop (or somehow reverse back to the Vista boot record without a Recovery Disk).

Currently downloading a Vista recovery disc for the second problem.   ...Considering installing a different version (maybe 10.4) on the desktop, if I can't figure it out.

---

### Post by Dutch70 on 2011-04-18
Try nomodeset...
[[COLOR="RoyalBlue"]http://ubuntuforums.org/showthread.php?t=1613132[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1613132")

---

### Post by nfoglesbee on 2011-04-18
Problem #2 solved, thanks everyone.  I used a x64 Vista Recovery Disc and reinstalled the MBR.

Still unable to get into Ubuntu Desktop Edition 10.10, any suggestions on another build perhaps?

I'm going to try out the "Nomoset" right now.

---

### Post by nfoglesbee on 2011-04-18
Nomodeset worked!!!  Thanks so much, now to explore a bit (safely)...

---

### Post by Dutch70 on 2011-04-18
Nice! Have fun & welcome to UF :)

---

### Post by Wobblybob on 2011-04-19
glad you sorted both your problem, hope you enjoy Ubuntu

---

