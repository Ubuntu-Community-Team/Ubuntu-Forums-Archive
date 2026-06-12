---
title: "bcm4318 nightmare!"
date: 2007-10-02
forum: Networking &amp; Wireless
---

### Post by spincaster on 2007-10-02
:)

This is my first post ever so Hi to one and all.
 Been using windows for years and decided to try 
Ubuntu for a change,but after days of trying to get my 
Broad com BCM4318 working ,I gave up in disgust and
wiped out my ubuntu install.

 I tryed using compwiz18 and ravens guidlines to
no avail. (and researched a ton of other info}.

 But I'm at it again!! REINSTALLED UBUNTU.

 I ran ndisgtk, installed driver (from linksys cd)
ndisgtk says device not present. 
ndiswrapper says driver wmp54gs installed 
device i4e4:4318 present,
alternative driver:bcm43xx.

 Under Network setting
essid: belkin
auto dhcp config
 I've no password set
same as winxp setting on my first drive.

iwconfig says (wireless) eth1:managed,
access point: invalid.

I tryed drivers bcm43xx_compwiz18.1-all.deb
 from that link,and ones from linux site,nothing.
 What am I doing wrong ?:confused:

Help!

---

### Post by Lambert on 2007-10-03
post the out put of these commands

```

sudo lshw

```

If you can pinpoint just the section on the wireless device, please post just that.

With iwconfig showing eth1, I'm not sure you're using ndiswrapper as the driver right now as that should have an interface of wlan0 but is possible eth1 is correct.

Also run 

```

sudo lsmod

```

look to see if you have ndiswrapper in the list and bcm43xx. If so try to run these commands.

```

sudo ifdown eth1
sudo modprobe -r bcm43xx
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
iwconfig

```

see if you have wlan0 as an interface or eth1 and try to configure and connect the device through network manager.

---

### Post by kevdog on 2007-10-03
You shouldn't have any problem getting your card working with ndiswrapper -- it will work.  Make sure the bcm43xx module is blacklisted in the /etc/modprobe.d/blacklist file and that the ndiswrapper module is listed to start at boot in the /etc/modules file.  You might have to monkey with the /etc/iftab file to make sure the MAC address of your card (if it is listed) is associated with wlan0 and not another interface name such as eth1.  Thats about the long and the short of it!!!!

---

### Post by EngDrewman on 2007-10-03
I have the same card, the 4318. Here's why you can't get it to work. The Linux kernel includes an opensource broadcom driver that is sort-of a "one size fits all" deal. The problem is the 4318 is one of the few cards that does not work with this driver. Despite the fact that it won't work, the kernel tries to use this driver anyway, and prefers it to ndiswraper. What you have to do to get your card to work it to tell the kernel to not load the opensource driver. Here's how you do it:

open your terminal and type:

sudo gedit /etc/modprobe.d/blacklist

at the end of the file add:

blacklist bcm43xx

Save the file and restart your computer. Now try ndiswrapper and see if it works.

---

### Post by Sand Lee on 2007-10-04
I got my bcm4318 card to work with bcm43xx. ATM, I'm using gutsy, but it should be the same in Fiesty. Just install bcm43xx-fwcutter from synaptic, then it'll prompt you for the broadcom firmware (I have a copy if you need it). Speeds are abysmal though ~24mb/s. If you don't mind the low speeds, then I recommend using fwcutter.

---

### Post by kevdog on 2007-10-04
ndiswrapper should give you better transfer rates.

Im not too sure who would find slow transfer rates acceptable :)

---

### Post by High Roller on 2007-10-13
I noticed that you mentioned you have a Linksys WMP54GS as do I.
I've been testing the Gutsy Beta and RC and it will automatically download
the driver and install it under Restricted Drivers.  Works like a charm.

Just make sure you use your wired connection to get things going at first.
So wait a week and give it a shot.  Gutsy rulez.

---

