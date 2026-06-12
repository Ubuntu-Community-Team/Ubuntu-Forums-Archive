---
title: "card only operating at 100mbps"
date: 2008-04-03
forum: Networking &amp; Wireless
---

### Post by kamasabi on 2008-04-03
gents,

I have recently upgraded to gigabit networking (w00t!), however, I'm having a small problem.  I got a couple NIC's for my servers, the Rosewill RC-400 to be specific, to partner with the rest of the setup.  All other computers are going wonderfully, however, this one is only broadcasting at 100Mbps, vs. the 1000Mbps it should be doing (the new card is a gigabit card).  Running ubuntu 7.10. 

Ran lspci and it is listed as Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)

Any suggestions?

 -Kama

EDIT:  tried going to realtek's site and downloaded the r8169-6.004.00 package, cd to directory, ran make then make install.  then

sudo ethtool -i eth1
[sudo] password for kamasabi:
driver: r8169
version: 2.2LK
firmware-version: 
bus-info: 0000:00:09.0  

it still isn't running up to speed, I tried copying a 400MB iso file and it took about 2 minutes or so to copy.  any ideas on why it is going this slow?

---

### Post by kamasabi on 2008-04-04
anyone?

---

### Post by anjilslaire on 2008-04-04
I had a similar issue before I got a new router, but my problem was it would stay at 1/2 duplex (that is REALLY slow), and I found a workaround.

Pardon the plagiarism, as I don't remember where I found it, but try the following (edit as needed for gigabit speeds):

> 
Debian or Ubuntu Linux permanent settings

Under Debian or Ubuntu Linux just create a script as follows:
# vi /etc/init.d/100Mbs
OR
$ sudo vi /etc/init.d/100Mbs
Append following lines:
#!/bin/sh
ETHTOOL="/usr/sbin/ethtool"
DEV="eth0"
SPEED="100 duplex full autoneg off"
case "$1" in
start)
echo -n "Setting eth0 speed 100 duplex full...";
$ETHTOOL -s $DEV speed $SPEED;
echo " done.";;
stop)
;;
esac
exit 0

Save and close the file. Setup executable permission:
# chmod +x /etc/init.d/100Mbs
OR$ sudo chmod +x /etc/init.d/100Mbs

Now run script when Debian or Ubuntu Linux boots up. Use update-rc.d command install System-V style init script links:# update-rc.d 100Mbs defaults
OR
# sudo update-rc.d 100Mbs 
defaults Output:

 Adding system startup for /etc/init.d/100Mbs ...
   /etc/rc0.d/K20100Mbs -> ../init.d/100Mbs
   /etc/rc1.d/K20100Mbs -> ../init.d/100Mbs
   /etc/rc6.d/K20100Mbs -> ../init.d/100Mbs
   /etc/rc2.d/S20100Mbs -> ../init.d/100Mbs
   /etc/rc3.d/S20100Mbs -> ../init.d/100Mbs
   /etc/rc4.d/S20100Mbs -> ../init.d/100Mbs
   /etc/rc5.d/S20100Mbs -> ../init.d/100Mbs

Reboot the system to take effect or just type scrit name:
# /etc/init.d/100Mbs start
OR
$ sudo /etc/init.d/100Mbs start


---

