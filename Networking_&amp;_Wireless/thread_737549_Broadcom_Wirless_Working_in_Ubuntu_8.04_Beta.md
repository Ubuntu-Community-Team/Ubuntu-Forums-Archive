---
title: "Broadcom Wirless Working in Ubuntu 8.04 Beta"
date: 2008-03-27
forum: Networking &amp; Wireless
---

### Post by ajitflora on 2008-03-27
Hiya All, 
              This is my first forum regarding Broadcom wirless in ubuntu 8.04 beta. It is working. Use Hardware drivers listed under System-Administration. Click on broadcom wireless. it will download the necessary drivers. Restart the computer, then go to terminal, type command

sudo apt-get install b43-fwcutter

Restart computer again and it will work. 
Note: don't install b43fwcutter with synaptic.
Also in between i  followed the steps from this website([https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)) and it didn't work. If u have already installed b43fwcutter with synaptic, uninstall it and install it with terminal with the command mentioned above.

Thank You and I have really liked Ubuntu 8.04 Beta. Hope Ubuntu always keep the momentum

---

### Post by bl4k3r on 2008-03-27
Had the same problem and b43-fwcutter already installed. So I did:

sudo apt-get remove b43-fwcutter
sudo apt-get install b43-fwcutter
reboot

Works like a charm - thanks mate!

---

### Post by keenish27 on 2008-03-31
Yup, had to remove it and reinstall it, works perfect now.

thanks for the advice.

---

### Post by kevdog on 2008-03-31
Weird -- wonder why a reinstall is necessary.  Certainly would like to see some dmesg output prior to the uninstallation.

---

### Post by jpyanowski on 2008-03-31
Thank you!! I have wireless again and it was effortless.

---

### Post by abhilashkumar on 2008-04-01
has anybody has any luck with getting atheros AR5006EG working in Hardy?

---

### Post by Jacksonstevena on 2008-04-01
how do I install b43-fwcutter from a usb flash drive, im a total noob.

Also no drivers are listed under system>administration>hardware drivers   absolutely nothing comes up.

Tried to:
 sudo apt-get remove b43-fwcutter
sudo apt-get install b43-fwcutter

It said the package does not exist

---

### Post by rustybronco on 2008-04-01
> **kevdog said:**
> Weird -- wonder why a reinstall is necessary.  Certainly would like to see some dmesg output prior to the uninstallation.I can supply that info, hopefully tonight.

---

### Post by Helios1276 on 2008-04-01
This work with Gutsy?

---

### Post by Derspankster on 2008-04-01
> **ajitflora said:**
> Hiya All, 
              This is my first forum regarding Broadcom wirless in ubuntu 8.04 beta. It is working. Use Hardware drivers listed under System-Administration. Click on broadcom wireless. it will download the necessary drivers. Restart the computer, then go to terminal, type command

sudo apt-get install b43-fwcutter

Restart computer again and it will work. 
Note: don't install b43fwcutter with synaptic.
Also in between i  followed the steps from this website([https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)) and it didn't work. If u have already installed b43fwcutter with synaptic, uninstall it and install it with terminal with the command mentioned above.

Thank You and I have really liked Ubuntu 8.04 Beta. Hope Ubuntu always keep the momentum

Thanks, that did the trick.

---

