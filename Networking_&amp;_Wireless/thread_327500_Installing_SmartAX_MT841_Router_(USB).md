---
title: "Installing SmartAX MT841 Router (USB)??"
date: 2006-12-29
forum: Networking &amp; Wireless
---

### Post by Madvirus on 2006-12-29
Hi Everyone, 

Firstly i would like to congratulate ubuntu team for such a wonderfull operating system. I Just installed it find very impresive. Well it has some shortcoming's but i guess it will overcome those in coming years. Keep it up guys!.  Now here is my problem

1. I want to use SmartAX MT 841 Router to connect to internet. I have attached it to my computer using USB as i dont have a ethernet card. Now what i want to know is how can i install this device and how i will setup my connections. I have the driver cd for the router but cant figure out how i will do it. :( 

I have checked other Wiki's of Ubuntu but they said there is no info on connecting SmartAX 841 with USB. I have searched alot ova google but couldnt find anything. 

Can any here please please help me to setup my broadband connection.???

I am using Ubuntu 5.10 .


Regards

---

### Post by Madvirus on 2006-12-30
Day 1: No Solution Yet ](*,) 

Bad Bad Bad support!

---

### Post by Madvirus on 2006-12-31
Day 2: No Solution Yet. ](*,)

---

### Post by Madvirus on 2007-01-01
Day 3: No Solution Yet ](*,)

---

### Post by melsa on 2008-04-06
The instructions are as follows
1) Log in as root
2) Cd /usr/src
3) Copy orginal codes to /root/MT841
4) Make clean
5) Make all
6)
add alias eth1 CDCEther to /etc/modules.conf
7) modify /etc/modules.conf
vi /etc/modules.conf with:
"pre-install CDCEther modprobe -a ABC XYZ" where ABC is the 1st
n/w driver and XYZ is the 2nd n/w driver
8) copy CDCEther.o to /lib/modules/2.4.x/kernel/drivers/usb
9) reboot linux connect USB cable to ADSL
10) cd /root/MT841
insmod ./CDCEther
11) ifconfig eth0 down
ifconfig eth1 192.168.1.3 up

These instruction as given on Modem CD but I have not used   , I am not sure if this works

Melsa

---

### Post by melsa on 2008-04-06
Please visit for driver download and instructions on connecting and config 

[http://members.driverguide.com/driver/detail.php?driverid=640162&action=filfo](http://members.driverguide.com/driver/detail.php?driverid=640162&action=filfo)

[http://www.calcuttatelephones.com/dataoneinstall/mdm06.swf](http://www.calcuttatelephones.com/dataoneinstall/mdm06.swf)

---

### Post by kmashraf on 2008-04-12
USB drivers are not properly provided for GNU/Linux by device manufacturers. Some distro's take the trouble to provide them, some don't. The simplest thing to do would be to add a network card. Costs less than Rs. 500/- for the best one, D-Link. And connect to the router HUAWEI MT841 via ethernet. As far as I know if you use ethernet it should work out of the box. Ensure that your distro, Ubuntu in this case, is set to use DHCP to get an IP from the router. And it will be an always on connection. If you feel uncomfortable with it you can power on the router whenever you want to use the internet.
And please understand that this is a forum and support/help  is not mandatory. Kindly refrain from casting aspersions in the forum. This is a slightly different world where politeness is appreciated.
Thank you

---

