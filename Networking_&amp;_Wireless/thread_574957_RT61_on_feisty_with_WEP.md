---
title: "RT61 on feisty with WEP"
date: 2007-10-13
forum: Networking &amp; Wireless
---

### Post by akshayas1986 on 2007-10-13
Hi folks
I have the RT61 based D-Link DWL G510 Rev C. My wireless network at home is WEP based. I have been trying really hard to get my wireless network working. There are no links that talk about WEP for RT61. None have worked for me. In feisty, the "make all" of the rt61 driver from Ralink website gives errors. Please help me

Thanks

---

### Post by kevdog on 2007-10-13
Can you post the errors?? Were the complaining about missing .h files and such??

---

### Post by Haim on 2007-10-19
You could probably follow these instructions, but substitute rt61 for the  rt73, it has reference to wep

[http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey](http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey)

---

### Post by akshayas1986 on 2007-10-21
Hey guys
I have tried everything and nothing seems to be working. 

I have a TPLink router at 192.168.1.1. One breakthrough: With all the iwpriv settings my network gives a non zero finite Link Quality (around 80/100). 

But since my wireless network is DHCP enabled, I need to dynamically get my IP address. Almost all the posts on RT61 talks about static IP Addresses.

Also when I do 'sudo iwlist scan', I can see my network but it says 'Quality: 0/100'. But if I do iwconfig, I see that my Link Quality is some finite non-zero value.

And whenever I do dhclient ra0, it tries to acquire an IP address but ends up saying no DHCPOFFER or something

Please help me. Without th internet, my life has becomre quite bad.

Thanks and regards

---

### Post by Haim on 2007-10-23
I suggest you turn off security and get it working, then you can play around with putting it back on.

[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61)

Thats the standard howto.  

But also look here...

[http://ubuntuforums.org/showthread.php?t=132980](http://ubuntuforums.org/showthread.php?t=132980)

Old thread but I think its useful.  First post is a how to and has a specific thing on the no DHCP problem and is for WEP so could be the answer.

---

### Post by wieman01 on 2007-10-23
Suggestion I have for you (I am repeating myself, I know) is that you replace the current driver with "ndiswrapper" and the native Windows driver and then use Network Manager to connect to your WEP secured network. That should work.

The tutorial in my signature will guide you through the set-up.

---

### Post by Herrsmag on 2007-10-23
Hi,

I've soon tried all how-to's, all different methods and tricks in the book to get my DWL-G630 Rev E up and running on 7.04, but no luck.

I have started to toss out Windows in favor for Ubunto on my boxes at home but I cannot get the wireless to work on any of them.

I have installed the ndiswrapper now, but I can't get hold of a driver that works. Do you have a link that I can use?

Cheers,
/Magnus

---

### Post by akshayas1986 on 2007-10-29
Guys after spending almost 7 days on this trivial problem, I am proud to say that I HAVE SOLVED IT (But with the help of Raubsau. So a BIG THANKS to you man)

Well I noticed something.
> sudo ifconfig ra0 down does not restart the network interface. So irrespective of the changes made to the interface file, it used to not reflect on it. So I tried > sudo /etc/init.d/networking restart after making changes to the interface file and it finally worked

So this is my /etc/network/interfaces file

> uto lo
iface lo inet loopback


auto eth2
iface eth2 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto ra0
iface ra0 inet dhcp
pre-up ifconfig ra0 down
pre-up iwconfig ra0 essid Slash
pre-up iwconfig ra0 mode managed
pre-up ifconfig ra0 up
pre-up iwpriv ra0 set AuthMode=OPEN
pre-up iwpriv ra0 set EncrypType=WEP
pre-up iwpriv ra0 set Key1=hindu
pre-up iwpriv ra0 set DefaultKeyID=1
pre-up iwpriv ra0 set TxRate=0
pre-up ifconfig ra0 mtu 1464

Please ignore the last line. That is an MTU settings for my Broadband connection.

---

