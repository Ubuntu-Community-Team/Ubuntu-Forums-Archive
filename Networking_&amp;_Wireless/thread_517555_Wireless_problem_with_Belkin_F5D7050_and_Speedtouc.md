---
title: "Wireless problem with Belkin F5D7050 and Speedtouch 780"
date: 2007-08-04
forum: Networking &amp; Wireless
---

### Post by jchoco on 2007-08-04
Hi,

I am going mad with my wireless network on Ubuntu 7.04.

I have a belkin F5D7050 usb dongle which I use with a old pc. I use this pc with the dongle without any problems.

I installed Ubuntu 7.04 and I installed the driver using ndiswrapper without any problem. Now in the network icon, when I left click, I saw the network AP I am trying to access. When I click on it I get the windows to enter the WEP key which I do but then the icon transform in a series of bar without any connection (signal bar).

I have started the interface manually and it appears that the process failed on the DHCP request like if the DHCP wasn't accepted or something. I have double check I don't have any firewall which might block the request. I have been trying everything for something like 3 hours but still not working. I tried to use a static address but no sucess either (I am not sure if the router Speedtouch 780 I am using allows it anyway).

The WEP key I am using is a 64bit Hex key.

I am not sure if my problem is a DHCP problem or WEP key problem.

Please help me configure my network it's driving me mad. ](*,)

Thanks a lot.

Julien

---

### Post by kevdog on 2007-08-04
Did you install any drivers for your device??  Basically Im trying to figure the chipset of your usb dongle.

Could you post
lsusb -v
lshw -C network

My first guess is that it is a driver problem.

---

### Post by jchoco on 2007-08-04
Thanks for your reply.

I use ndiswrapper to install my driver (taking the *.inf file).

The driver is the rt73 I believe. I will try to post the output of the command you put.

---

### Post by kevdog on 2007-08-04
Not trying to get you to do something you dont want to do, but I would probably take a different approach, and rather than use ndiswrapper, I would probably use the serial monkey drivers for your ra chipset.  ndiswrapper is an emulation driver, where I believe the ra drivers (rt73) are written specifically for your chipset.

You dont have to delete everything you have done up to this point (in case you need to revert), I would just add ndiswrapper to the /etc/modprobe.d/blacklist file, and then just remove the kernel module
sudo rmmod ndiswrapper

Then take a look at this thread how to install the rt73 serial monkey drivers:
[http://ubuntuforums.org/showthread.php?t=400236&highlight=serialmonkey](http://ubuntuforums.org/showthread.php?t=400236&highlight=serialmonkey)

If you need any help, just post back!

---

### Post by jchoco on 2007-08-06
Unbelievable.

This one work. I am using my ubuntu computer with wireless to post this message. That's great.

The only problem which is not a big issue is that since I am using DHCP, there is a wrong DNS server set (I don't know from where it come from) therefore I have to update it manually in /etc/resolv.conf each time I connect.

Thanks a lot for your help

---

