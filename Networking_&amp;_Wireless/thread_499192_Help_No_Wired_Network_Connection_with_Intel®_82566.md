---
title: "Help No Wired Network Connection with Intel® 82566DC Gigabit Ethernet Controller"
date: 2007-07-12
forum: Networking &amp; Wireless
---

### Post by shadow2062 on 2007-07-12
Help im a complete Noob! I installed Ubuntu yesterday the 64bit verison 7.04. I have an intel dp35dpmotherboard and everything works fine except the ethernet Intel® 82566DC Gigabit Ethernet Controller!

Do i need to install the drivers? If so how? Im new to ubuntu

Thanks for Your Support!

---

### Post by eylisian on 2007-08-11
I just discovered the same thing while installing Debian onto a Dell Vostro 200. I had to use a Lenny/Sid nightly build installer disk just to get by the "detect CD-ROM" and am now hung on the network controller bit. As a work around I think I am going to install a PCI card until I can build the box, then find and install a driver, or wait till Intel releases something.

At this point I suspect that will be your best bet as we are in the same boat. If I run into any fixes or any more gotchas I will be sure to post it here. Even if I am installing Debian, there will be some benefit to Ubuntu peeps. =)

cheers and luck to you!

---

### Post by jyu617 on 2007-11-18
Hi guys,  I came across your post and was wondering if you've figured out how to identify and configure the Intel 82566DC Gigabit Ethernet Controller.  I'm having the same problem, so please help if you can.

Thanks.

---

### Post by Blutack on 2007-11-18
Could you try running
sudo modprobe -v e1000
in theory this is the driver for your NIC.

---

