---
title: "Install a  card PCI AirPlus G+ DWL-G520+"
date: 2015-02-06
forum: Networking &amp; Wireless
---

### Post by RAZAKARIVONY_Rindr on 2015-02-06
Hello everybody
I'm new here
I have a problem for installing my PCI card Wireless
The reference is : AirPlus G+ DWL-G520+ manufactured by Dlink Corporation
I have downloaded Ubuntu 14.04 LTS 64 bits and i would like to use this PCI card on my computer
Everyone can help me please
I'm a new user for ubuntu
I need the driver for this card for 64 bits and how to install it on Ubuntu 14.04 LTS 64 bits
The configuration of my computer is :
Thanks a lot
:confused:

---

### Post by praseodym on 2015-02-06
Hi,

this card is pretty old and only runs with Ndiswrapper:
```

sudo apt-get install linux-headers-generic build-essential dkms ndisgtk ndiswrapper-dkms
```

Driver here:

[http://media.cdn.ubuntu-de.org/forum/attachments/47/01/1271405-ti1130pci_xp.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/47/01/1271405-ti1130pci_xp.tar.gz)

I don't think there is a 64bit driver available, therefore, check Ubuntu 32 bit. How much RAM do you have? If it is below 4 GB, use 32bit.

---

### Post by RAZAKARIVONY_Rindr on 2015-02-07
HI, thank you for answering
Yes this card is so old
I haved try to install it on Ndiswrapper but he didn't installing
I will try the link you give me and tell you what happens after
But if he doesn't work, i think return to 32 bits
I don't like so much the 32 bits because some software I used requires 64 bits
My config is :
Processor : G2030 LGA 1155
RAM : 4 giga DDR3
Hard drive : 1 Tera

---

### Post by praseodym on 2015-02-08
In this case I recommend installing 32bit or buying another card (if you do not find a 64bit driver)

---

