---
title: "Stuck: Install GRUB boot loader on hard disk"
date: 2009-12-12
forum: New to Ubuntu
---

### Post by PFree on 2009-12-12
Hi, I,m installing ununtu 9.10 alt 64bit on an Intel box. 

Installation goes all the way to the point of presenting the: 'Ubuntu installer main menu'

with the option: Install the grub boot loader on the hard disk preselected.

I hit enter and it went back to the load screen for a second, than came back to the installer main menu with the 'Install the grub boot loader on hard disk' preselected again. I hit enter again and got the same result.

Not sure what to do at this point.

The remaining options are:
Install LILO boot loader on hard disk
Continue without boot loader
Finish the installation
Change debconf priority
Check the CD-Rom(s) integrity
Save debut logs

Can anybody help me out with this or point me to whatever documentation that I missed?

Thanks,
Paul

---

### Post by PFree on 2009-12-12
Help :P!

---

### Post by PFree on 2009-12-12
Can anybody help me out?

I don't understand why GRUB won't install from the installation CD. Is there a known problem with this or what?

---

### Post by PFree on 2009-12-12
?

---

### Post by raslin on 2010-01-04
Hi, I am have the exact same problem, when tying install the ubuntu server edition 64 bit. (raid 1 lvm installation), despite it has been a windows server 2003 installed earlier on the computer, and their is a HP boot loader that is trying to start the win server. which I cannot get rid of! 

It would be interesting and needed to know what the problem is!?

---

### Post by charlier653 on 2010-01-04
Did either of you disable the boot sector virus protection in your bios? If you don't, grub cannot be installed, bios will not allow writing to that section of the hd.

---

### Post by proksy on 2010-01-16
I would have to say that these users did disable that feature or their mobo doesn't have that. I am also running into the same problem. I have configured 32 bit on different raid volumes with no sweat but with ubuntu 9.10 64bit I'm sweating my **** off, and I'm tired!!!! I have run from the alt cd and every time I get to the point where these guys are and I get stuck. I have read docs throughout the web on manually installing grub2 from the live cd but none of the instructions seem to work...I boot from the live cd >> terminal >> sudo grub >> returns "grub is not installed" I've tried everything that I can possibly find. Where are we going wrong? I have tried creating a separate partition for grub but when the installation gets to that point it does nothing! HELP Please.
 
PS: If I do find a solution before one is posted here I will have a FULL detailed tutorial with commands used, their order and purpose and screenshots of the entire process. I would not wish this process of trial and constant error on my worst enemies and will hopfully have a fix for anyone and everyone having problems with this/

---

