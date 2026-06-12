---
title: "detects wifi but won't connect"
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by cooldudeak on 2008-05-27
Hi, I have installed Hardy Heron last week on my laptop....
Everything worked fine...except for the wifi...
after following instructions on one of the thread, I managed to install the driver for my wireless card..so that ubuntu now detects the networks that are present nearby, but that is it.
I cannot connect to the internet.
I have an Atheros AR5007EG wireless card. My wifi network has no encryption.
Also, using the following steps, I was able to connect once and only once:
$ sudo ifconfig eth0 down
$ sudo iwconfig
$ sudo dhclient ath0

Please help....
thnx in advance..

---

### Post by cooldudeak on 2008-05-29
cummon people...I need sum help over here....

---

### Post by ApUUbunU on 2008-05-29
I had a similar problem recently.
If you have an IP blocker, such as Moblock installed, then you may find your router could be blocked by default.
That was the problem with my system, and some simple configuration fixed it!
However, I do not have much other experience in this field. You could disable/remove the connection and try starting from scratch, that sometimes works for me.

---

### Post by phidia on 2008-05-31
You didn't say whether your using 32 or 64 bit ubuntu. With 64 bit you need to add a line to your /etc/network/interfaces file.

---

### Post by shak2 on 2008-05-31
Hi, I have a same problem, I have an Atheros AR5007EG wireless card too, I 'm running ubuntu 8.04, 64bit. 
Although I 've installed the wifi driver from ndiswrapper, sometimes I have to reboot 2 - 3 times (or even more) to be able to connect to my wifi network. 

Any solution?

---

### Post by phidia on 2008-05-31
> **shak2 said:**
> Hi, I have a same problem, I have an Atheros AR5007EG wireless card too, I 'm running ubuntu 8.04, 64bit. 
Although I 've installed the wifi driver from ndiswrapper, sometimes I have to reboot 2 - 3 times (or even more) to be able to connect to my wifi network. 

Any solution?

There are people at the forums here that say Atheros cards are well supported, but I've found that this particular card is not. I have got mine working again but often going through the uninstall and reinstall of ndiswrapper is required-for me anyway, and I have had to edit /etc/network/interfaces (for 64 bit Ubuntu only) Below is what my interfaces file looks like:

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

#the wlan0 interface copied fron external HD install 5-30-08
pre-up /sbin/ifconfig wlan0 hw ether 00:1e:4c:4d:dc:f2


You need to use ifconfig to find your cards hw address (HWaddr) and then put that line in there.

---

### Post by shak2 on 2008-06-01
> **phidia said:**
> There are people at the forums here that say Atheros cards are well supported, but I've found that this particular card is not. I have got mine working again but often going through the uninstall and reinstall of ndiswrapper is required-for me anyway, and I have had to edit /etc/network/interfaces (for 64 bit Ubuntu only) Below is what my interfaces file looks like:



You need to use ifconfig to find your cards hw address (HWaddr) and then put that line in there.
Hey it works fine untill now, rebooted my laptop some times and I m able to connect to my wifi net. Thanks

---

### Post by cooldudeak on 2008-06-02
hey people...sorry for the late reply....
I am on 32 bit...
I have 3366 madwifi package installed...
Everything seems ok...
my driver is recognized...
access point is in range...
even DHCPOFFERS received and I am assigned an IP address with renewal time in range of 200-300 sec...
and sometimes it even works....SOMETIMES...that too for 20-30 secs...dunno what is happenning...
please help..
and ask whatever extra info is requires...

---

