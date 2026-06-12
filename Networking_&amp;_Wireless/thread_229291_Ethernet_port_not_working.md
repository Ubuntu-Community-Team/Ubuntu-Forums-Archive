---
title: "Ethernet port not working"
date: 2006-08-04
forum: Networking &amp; Wireless
---

### Post by wildteen88 on 2006-08-04
I am trying tp get an ethernet port to work with my NTL BB connection on Ubuntu Linux. The ethernet port I have is a Sweex 10/100Mbit PCI LANCARD

I have been reading the ubuntu documentation on enabling an ethernet port however my ethernet port is not listed within the networking window (Administration > Networking > Connections tab).

The NIC came with a floppy dik, so I put it in had a read of the readme file on it and it said to got OTHERS/Linux for linux installation So I open up the linux file and it talks about a file called rtl8139.so which I cannot find on my sytstem. Here is an extract of the file:
> Installing Driver:
(1.) Kernel Had Supported Driver:
Check the directory " /lib/modules/¡K./net " if you could find "rtl8139.o"
Your kernel had supported RTL8139 series. You could easy use "linuxconf" 
to setup your card. If you don't like linuxconf, you also could use
"modprobe rtl8139" and "ifconfig up eth0" to load module.
If your driver load properly, your "/etc/conf.modules" should include
line of "alias eth0 rtl8139".

(2.) Kernel Don't Support Driver:
If your kernel doesn't support RTL8139 series, you should compiler driver
by yourself. Please contact [http://www.scyld.com/network/rtl8139.html](http://www.scyld.com/network/rtl8139.html)
to get source code. The compiler command is located on the end of source
code. Maybe like "gcc -DMODULE -Wall -Wstrict-prototypes -O6 -c rtl8139.c".
If you couldn't compiler success, maybe you should refer to error message
and copy library or head file to Linux.
The iK./net folder doesnt exist within the /lib/modules folder. So I went to the secound part and it said to compile the driver yourself however the said site takes me to some other site.

Can someone please help me configure ubuntu to use the ethernet port.

Thank you for any help.

---

### Post by wildteen88 on 2006-08-05
please can any one help.

---

### Post by wildteen88 on 2006-08-07
Hello...

Surely someone must know what to do. Does anyone know where to get the rtl8139 driver for linux.

---

