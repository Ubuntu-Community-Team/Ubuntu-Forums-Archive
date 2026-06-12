---
title: "[SOLVED] Wired network no internet"
date: 2008-08-07
forum: Networking &amp; Wireless
---

### Post by drwest on 2008-08-07
I just installed Ubuntu 8.04 LTS x386.  I cannot connect to internet.  Using onboard nic SIS190 Gigabit Ethernet Adapter and  Linksys Router (wired and wireless but my pc is wired to the router).

I launch firefox and the loading bar goes halfway and hangs.  Web page ([www.google.com](www.google.com)) doesn't load.

1 - Tried Static IP - didn't work.  Changed to DHCP (to match router settings) - still won't connect.

2 - Edited dhclient.conf to prepend DNS to 192.168.1.1., 208.67.222.222, 208.67.220.220 - still won't connect.

3 - Changed MTU settings on router to 1492 and changed in ubuntu by editing /network/interfaces - still won't connect.

I can ping google.com, ubuntu.com, the router, and other pc's on my network successfully.

Kernel version is 2.6.24-19-Generic
Ethernet Card:  Onboard SIS 190 Gigabit Ethernet Adapter
ID Hardware: 1039:0190
Module Hardware: sis190

No ISA bridge errors in dmesg.

I don't know what else to try.  Please help.

---

### Post by tuxxy on 2008-08-07
Did you read the internet help

[https://help.ubuntu.com/8.04/internet/C/index.html](https://help.ubuntu.com/8.04/internet/C/index.html)

---

### Post by drwest on 2008-08-07
Yes I went through it and did all the steps.  

the only thing I saw that might be questionable was when I was doing the:

sudo ifdown eth0
and
sudo ifup eth0

that one of the lines reads:

sudo:unable to resolve host...
there is already a pid file...

but at the end I get the 
dhcp (some #'s)... renewing in (like 40k seconds)

---

### Post by loligager on 2008-08-08
This might be a hardware problem...

---

### Post by drwest on 2008-08-08
I thought hardware too... or a driver issue.  I found some posts regarding previous versions of ubuntu (7.10) searching for ISA Bridge ID 965 when the nic is using a different ID.

According to lspci -nn

my nic is using 966.  but I don't get ISA bridge errors when using:

dmesg | grep '00:04.0'

---

### Post by drwest on 2008-08-08
bump

---

### Post by drwest on 2008-08-08
bump

---

### Post by drwest on 2008-08-09
bump

---

### Post by drwest on 2008-08-09
bump

---

### Post by bicyclebarron on 2008-08-09
If you can ping outside your home network then connectivity is up. Try checking your firewall and router settings.

---

### Post by drwest on 2008-08-11
I disabled the firewall in the router and turned off the Uncomplicated Firewall in Ubuntu.  No change.

---

### Post by drwest on 2008-08-12
Fixed by doing the following:

1.  Turned off all pc's on the network.
2.  Turned off cable modem and router.
3.  Waited about 5 minutes.
4.  Turned on modem.
5.  Waited a full 60 seconds.
6.  Turned on router.
7.  Waited a full 60 seconds.
8.  Turned on pc running ubuntu.
9.  Launched firefox and it worked!
10.  Turned on the other pc's on my network one at a time.

Sometimes its the simple things.  :)

Can anyone tell me how to flag this thread as "solved"?

---

### Post by Iowan on 2008-08-12
> **drwest said:**
> 
Can anyone tell me how to flag this thread as "solved"?
CERTAINLY! It's under the "Thread Tools" option above the posts.

---

