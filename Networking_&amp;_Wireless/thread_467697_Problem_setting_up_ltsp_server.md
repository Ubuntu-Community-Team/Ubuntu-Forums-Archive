---
title: "Problem setting up ltsp server"
date: 2007-06-08
forum: Networking &amp; Wireless
---

### Post by jozmak on 2007-06-08
Hi,

I am trying to setup an ltsp server on ubutnu feisty with one client and I am having problems. First of all, I am pretty new to this. This is what I have done so far. I installed the following software:

sudo apt-get install ltsp-server-standalone openssh-server

and built the client

sudo ltsp-build-client

Evrything went without a glitch. 
Next, I downloaded the boot image iso for cd. Now, when I try to boot the thin client I get a message “Searching for server (DHCP), No IP address.

Any idea what should I do now.

Thanks a lot.
jmak

---

### Post by cantormath on 2007-06-08
Here is a good tutorial
[http://www.edubuntu.org/GettingStarted](http://www.edubuntu.org/GettingStarted)

look at the dhcp server stuff.

---

### Post by jozmak on 2007-06-08
Thanks for the tutorial. I followed the tutorial and I replaced the Ip addresses in the dhcpd.conf file but I still get the exact same error massage;

“Searching for server (DHCP), No IP address.

What now?

---

### Post by williams402 on 2007-06-08
Make sure that the range of you IP is within the 192.168.0.1....254 and that your Subnet is 255.255.255.0
That is what cured the same problem for me.

---

