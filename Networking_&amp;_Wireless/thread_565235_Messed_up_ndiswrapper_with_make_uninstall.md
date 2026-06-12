---
title: "Messed up ndiswrapper with make uninstall"
date: 2007-10-02
forum: Networking &amp; Wireless
---

### Post by halfB on 2007-10-02
I tried an older ndiswrapper from source then realized there was a newer version in the repositories.  Since had not gotten wifi to work yet I did a make uninstall of ndiswrapper and then installed 1.9 through repositories.  But I think the 'make uninstall'  deleted something needed for the newer (1.9) version to work.  When I sudo modprobe ndiswrapper I get the following message:

oslo@oslo:~$ sudo modprobe ndiswrapper
FATAL: Could not open '/lib/modules/2.6.22-12-generic/misc/ndiswrapper.ko': No such file or directory

How should I correct this??

Eric

---

### Post by Azegul on 2007-10-02
I'm in the same boat. Same message. Tried Gutsy Beta, didn't work, reinstalled Feisty.
Followed "Easy Wifi Howto" Didn't work. fwcutter didn't work either.
I hope someone has an answer. But it's good to know it's not just me!

---

### Post by halfB on 2007-10-03
Azegul
Well, I am up and wifi. After much deleting this and that I decided to fresh install gutsy.  Once installed I then used adept to download build-essentials, ndiswrapper and ndiswrapper utilities 1.9.

I have a broadcom 4306 wifi.
I had the broadcom drivers in a file in my home directory.

Next         sudo rmmod bcm43xx
  which removes the bcm43xx if it had been installed
Then        echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
  which blacklists the bcm43xx so it will not interfere 
then         sudo ndiswrapper -i /home/oslo/broadcom/bcmwl5/bcmwl5.inf
   which is where I stored the broadcom driver I needed
then         sudo ndiswrapper -m
then         sudo modprobe ndiswrapper
And it works great.

Take care Azegul

---

### Post by halfB on 2007-10-03
On reboot the wireless is missing. 
Darn

---

### Post by Ayuthia on 2007-10-03
> **halfB said:**
> On reboot the wireless is missing. 
Darn
You most likely need to add the word ndiswrapper in /etc/modules

---

### Post by halfB on 2007-10-03
You are so right.
I added ndiswrapper to /etc/modules and did a reboot and am connected via wifi.
thanks
Eric

---

