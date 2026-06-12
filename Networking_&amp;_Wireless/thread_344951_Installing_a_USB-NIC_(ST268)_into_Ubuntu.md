---
title: "Installing a USB-NIC (ST268) into Ubuntu"
date: 2007-01-23
forum: Networking &amp; Wireless
---

### Post by nathockens on 2007-01-23
Sorry to Noob out on you guys straight out of the gates, but I'm having a hard time installing a USB-NIC(wired) dongle on my Thinkpad 570.  I found this readme.txt 
[here]("http://ptm2.cc.utu.fi/ftp/USB/TMP/USB-RJ45/ST268/linux/readme.txt") but am problems with the order of operations in which I need to do this (or whether I can even do it in Dapper.

From what I can make, I need to compile the two files:
"gcc -DMODULE -D__KERNEL__ -I/usr/src/linux/include -Wall -Wstrict-prototypes -O6 -c ST268.c"

then insert the module into the kernel:
"insmod ST268.o" 

then configure an IP
"ifconfig eth0 172.22.3.18"

then maybe activate the routing table:
"route add default netmask 255.255.255.0 eth0"


Does this make sense to you guys or am I an idiot?
Thanks.

---

### Post by Peppi_GOE on 2008-01-06
Hello!
It's totaly crazy! Pidgin (Linux ICQ) works without the driver, but nothing else.
I have many Problems to install the driver.
I do the following steps, but
nothings works.
And at the discription is on C a simply and temporary method???
So I think, ok maybe this can work.... nothing.

I need help!

---

