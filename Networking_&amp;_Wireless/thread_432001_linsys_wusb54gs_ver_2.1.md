---
title: "linsys wusb54gs ver 2.1"
date: 2007-05-03
forum: Networking &amp; Wireless
---

### Post by dmurray73 on 2007-05-03
hi i am new to ubuntu and am trying to get my linksys wusb54gs ver 2 wireless adapter to work, but there doesnt seem to be linux drivers for this product. anybody any ideas thanks

---

### Post by gorgor_bay on 2007-05-04
I'm in the same position here, my desktop at home is connected to the internet using this usb linksys device... looking for a driver.

---

### Post by Josey on 2007-05-04
install this
[http://ubuntuforums.org/attachment.php?attachmentid=30328&d=1177147133](http://ubuntuforums.org/attachment.php?attachmentid=30328&d=1177147133)
reboot

enjoy :)

---

### Post by RitchieTheBrit on 2007-05-06
Hmmmm, I'm a complete newbie as well, and as a Windows admin, Linux takes some real getting used to!

Anyway, I've NDISWrapper, and encountered nothing but invalid driver errors, so I was over the moon when this post appeared on Google!  So, installed, restarted, and nothing.  The network manager only show my two ethernet controllers, still no wireless.

Any idea where I'm going wrong?  It's the latest public release of Feisty.  :confused:

---

### Post by Josey on 2007-05-06
> **RitchieTheBrit said:**
> Hmmmm, I'm a complete newbie as well, and as a Windows admin, Linux takes some real getting used to!

Anyway, I've NDISWrapper, and encountered nothing but invalid driver errors, so I was over the moon when this post appeared on Google!  So, installed, restarted, and nothing.  The network manager only show my two ethernet controllers, still no wireless.

Any idea where I'm going wrong?  It's the latest public release of Feisty.  :confused:

I should have mentioned that you need to 
```
sudo apt-get remove ndiswrapper
```
before installing that

hope it works for you.

---

### Post by colinut on 2007-12-01
I also have same adapter ver 2.1

I have installed whay Josey said but still the linksys adapter doesn't appear in my list of network devices.

Do I have to somehow associate this driver to the adapter?

Thanks all. I appreciate any help.

---

### Post by numb_sky on 2007-12-02
> **Josey said:**
> install this
[http://ubuntuforums.org/attachment.php?attachmentid=30328&d=1177147133](http://ubuntuforums.org/attachment.php?attachmentid=30328&d=1177147133)
reboot

enjoy :)


this isnt working for me. im looking for the same drivers for the linksys wusb54gs ver 2.1 but im having no luck. can anyone help?

---

### Post by RitchieTheBrit on 2008-05-05
I managed to successfully install this the other day, thought I would mention it here.  If anyone is still having problems, send me a message, and I will go through it again, and write down the steps.

It was actually pretty damn easy!  Lol!

---

### Post by Xanxer82 on 2008-05-29
> **RitchieTheBrit said:**
> I managed to successfully install this the other day, thought I would mention it here.  If anyone is still having problems, send me a message, and I will go through it again, and write down the steps.

It was actually pretty damn easy!  Lol!



I'm running ubuntu 8.0.4.
having trouble getting this device working too.

---

### Post by DeadMyke87 on 2008-06-09
I'm in the very same boat :/

---

### Post by Xanxer82 on 2008-06-18
> **RitchieTheBrit said:**
> I managed to successfully install this the other day, thought I would mention it here.  If anyone is still having problems, send me a message, and I will go through it again, and write down the steps.

It was actually pretty damn easy!  Lol!

Tried a few times still no luck. Running hardy heron 8.0.4.

---

### Post by hman469 on 2008-06-18
I am running Hardy as well and cant get it working I have the Linksys wusb54g s ver.2 and I need to also be able to connect my wired ethernet connection to a router and share the connection if anyone can help please.

---

### Post by GrimBlaZter on 2008-06-25
I have the same device, and I was able to get it working using 2 methods. Pick one :popcorn: :

Method 1
  - [http://www.jooz.net/rndis/](http://www.jooz.net/rndis/)
  - Download the rndis wlan snapshot and install it as it tells
    you
    restart and it works.
  - You have to install it again if you either install any
    kernel 
    updates.

Method 2
  - Install ndiswrapper
  - Enter for example "sudo ndiswrapper /home/myusername
    /WUSB54GSv2.inf" in a terminal (basically location of the
    .inf)
  - Copy rndismp.sys and usb8023.sys into the folder you see at
    /etc/ndiswrapper
  - To start it, enter "sudo modprobe ndiswrapper"
  - Type this in terminal "sudo ndiswrapper -m". This will
    autostart ndiswrapper

---

