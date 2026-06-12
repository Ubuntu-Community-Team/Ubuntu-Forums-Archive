---
title: "need some help please."
date: 2007-07-27
forum: Networking &amp; Wireless
---

### Post by twstdnightmare on 2007-07-27
ok i am running ubuntu 6.06.1 on a virtual machine. now my computer uses a dell truemobile usb wireless adapter to get internet. can anyone tell me how to get this to work with ubuntu if im running it on a virtual machine.  please and thankyou.

---

### Post by sfarber53 on 2007-07-27
It might help if you told us a bit about your setup.  What is the host OS, general hardware specs, whose hypervisor you are running (VMWare/Parallels), etc.

I have a virtual setup on my MacBook that allows Linux to access the wireless through the MacBook connection with no hassels, no setup.  I couldn't begin to guess what you should do without more information.

Cheers!

Steve

---

### Post by twstdnightmare on 2007-07-27
the host OS is windows vista. and my computer is a dell dimension 3000, 2.8 Ghz procesor, 1g of ram, and a 256mb Nvidia geforce fx 5200 graphics card. and i am running ubuntu using virtualbox

---

### Post by sfarber53 on 2007-07-27
Check out the following link:

[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

It should give you some help with respect to Virtualbox on Ubuntu.

---

### Post by twstdnightmare on 2007-07-27
i did everything on that page, but one i type in:
sudo apt-get install bridge-utils uml-utilities 

it tells me that bridge-utils cant be found

---

### Post by kevdog on 2007-07-27
You might need to enable the multiverse or universe repositories in synaptic.  If not here is a link:
[http://packages.debian.org/stable/net/bridge-utils](http://packages.debian.org/stable/net/bridge-utils)

---

