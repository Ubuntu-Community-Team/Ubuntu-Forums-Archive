---
title: "eth0 device not found"
date: 2007-11-11
forum: Networking &amp; Wireless
---

### Post by parkhensley on 2007-11-11
I see the other threads, but none of the suggestions seem to work.  On a brand new Dell Inspiron 530 I used the included live cd to boot to Ubuntu 7.04 and even here the integrated NIC is not being found. Installing does not help. lspci gives as in the other threads: "Intel Integrated Controller unknown device 10c0". ifconfig -a only lists lo, and trying to add eth0 or any other ethx to /etc/network/interfaces just results in ERROR while getting interface flags no such device messages for any of the ethx lines. Dmesg contains nothing about networking or eth0.

---

### Post by parkhensley on 2007-11-12
Found instructioins in other threads on how to download, compile and modprobe module e1000. But now, I get the following:

Listening on LPF/eth0/mymacaddress
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
""                                                       "                              "          16
"                                                        "                              "          7
No DHCPOFFERS received.
No working leases in persistent database... sleeping.

And that's it.

Now, what

---

### Post by parkhensley on 2007-11-12
It turns out that all that was needed was the instructions on downloading the e1000 driver from the Intel site, compiling it and then doing modprobe e1000.  The DHCP messages in previous post were because I had disconnected the network cable to check that it was good and then didn't reconnect. 

So everything is cool now.

---

