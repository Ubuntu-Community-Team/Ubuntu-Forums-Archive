---
title: "Installing Belkin F5D7011Network card-HELP"
date: 2007-01-28
forum: Networking &amp; Wireless
---

### Post by helliewm on 2007-01-28
I have followed the instructions re the driver at ndiswrapper sourceforge wiki for the F5D7011 Network card . It says the driver will work in Ubuntu. Also a search of the Ubuntu forum reveals other people have got this Network card working.

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B)

I have also installed ndiswrapper for Edgy as per these instructions at Ubuntu

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

I have blacklisted bcm43xx as per instructions at the above Ubuntu help Wiki.

When I try to install the driver at the terminal I get this error message .

helen@helen-laptop:~$ sudo echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
blacklist bcm43xx
helen@helen-laptop:~$ sudo ndiswrapper -i ~/bcmwl5.inf
Installing bcmwl5
couldn't copy /home/helen/bcmwl5.inf at /usr/sbin/ndiswrapper-1.8 line 144.
helen@helen-laptop:~$ 

bcmwl5.inf is on my Desktop.

Help where I am going wrong?

Helen

---

### Post by bigken on 2007-01-29
hello helen i have a spare linksys A+G pcmcia card that works out of the box if you want it simple solution m8 let me know

---

### Post by bigken on 2007-01-30
you need to cd to your Desktop :D

---

### Post by helliewm on 2007-01-30
Yes please Ken. I am still struggling following every How to guide I can find.

I need work downstairs with the dogs, its annoying I can't! Laptop seems fine now after you gave that clean! It has Ubuntu on it I got rid of Windoze ASAP.

Helen

---

### Post by bigken on 2007-01-30
email your address Ill stick in the post :D

---

### Post by helliewm on 2007-01-30
Have done Ken. Thanks ever so much.

Helen

---

### Post by bigken on 2007-01-30
no probs ;)

---

### Post by zigmat on 2007-02-11
PLZ Help me too with it!

---

