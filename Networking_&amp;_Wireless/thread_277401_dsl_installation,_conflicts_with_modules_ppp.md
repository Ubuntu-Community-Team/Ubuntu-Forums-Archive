---
title: "dsl installation, conflicts with modules ppp"
date: 2006-10-14
forum: Networking &amp; Wireless
---

### Post by Stoff on 2006-10-14
hello,

i tried to install my dsl access using pppoeconf this works fine until i reboot my computer.

lsmod shows me the modules pppoe und pppox pppoe does not work, there is a 0.

first, i stop the processes networking and ppp.

/etc/init.d/networking stop
/etc/init.d/ppp stop

then i stop the modules pppoe and pppox using rmmod.

i startnetworking again and the internet connection works.

now i have a look at my interfaces and am confused:
--------------------------------------------------------------------------
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

# added by pppoeconf

auto eth0
iface eth0 inet manual

pre-up /sbin/ifconfig eth1 up # line maintained by pppoeconf

# added by pppoeconf
auto eth1
iface eth1 inet manual
----------------------------------------------------------

ifconfig gives:
-----------------------------------------------
xxx@computer:/etc/network$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:0C:F1:01:8B:A1
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:10 Base address:0xc000 Memory:e0200000-e0200fff

eth1 Link encap:Ethernet HWaddr 00:40:CA:C5:43:EF
inet6 addr: fe80::240:caff:fec5:43ef/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:1778 errors:0 dropped:0 overruns:0 frame:0
TX packets:1706 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:1325739 (1.2 MiB) TX bytes:344902 (336.8 KiB)
Interrupt:10 Base address:0x2800

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)

ppp0 Link encap:Point-to-Point Protocol
inet addr:85.182.3.209 P-t-P:213.191.89.24 Mask:255.255.255.255
UP POINTOPOINT RUNNING NOARP MULTICAST MTU:1492 Metric:1
RX packets:1686 errors:0 dropped:0 overruns:0 frame:0
TX packets:1612 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:3
-----------------------------------------------------------

the contents of my resolv.conf:
---------------------------------
der Inhalt der resolv.conf:
-------------------------------
nameserver 213.191.74.12
nameserver 213.191.92.84
----------------------------

i use a dsl-modem to access the net directly - no router.

which ethernet card am i using now? probably i have to change the interfaces accordingly.

but first and foremost, how do i solve the modules riddle?

i hope anyone can help me.

thanks a lot well in advance,

Christoph

---

### Post by mips on 2006-10-14
> **Stoff said:**
> 
i use a dsl-modem to access the net directly - no router.


If you are connecting via Eth then you have a router, you just dont know it. There are easier ways than using pppoe

---

### Post by Stoff on 2006-10-14
thanks for the first reply.

definitely not, i do not have a router. the little machine is called Siemens ADSL C2-010-I Modem. a data sheet can be found here:
[http://www.siemens.ch/Daten/siecom/Switzerland/ICP/Internet/ICP_Unitwide/WORKAREA/chicpedi/templatedata/Deutsch/file/binary/icp_pl_sad_SANTIS_ADSL_15_150_pdf_1092074.pdf](http://www.siemens.ch/Daten/siecom/Switzerland/ICP/Internet/ICP_Unitwide/WORKAREA/chicpedi/templatedata/Deutsch/file/binary/icp_pl_sad_SANTIS_ADSL_15_150_pdf_1092074.pdf)

---

### Post by Stoff on 2006-10-14
now i am reading in a german forum that my machine can be used as a router as well. however, my provider distributes it as a modem only. maybe it is somehow locked. nevertheless, i would like to use it as a modem.

---

### Post by mips on 2006-10-15
> **Stoff said:**
> thanks for the first reply.

definitely not, i do not have a router. the little machine is called Siemens ADSL C2-010-I Modem. a data sheet can be found here:
[http://www.siemens.ch/Daten/siecom/Switzerland/ICP/Internet/ICP_Unitwide/WORKAREA/chicpedi/templatedata/Deutsch/file/binary/icp_pl_sad_SANTIS_ADSL_15_150_pdf_1092074.pdf](http://www.siemens.ch/Daten/siecom/Switzerland/ICP/Internet/ICP_Unitwide/WORKAREA/chicpedi/templatedata/Deutsch/file/binary/icp_pl_sad_SANTIS_ADSL_15_150_pdf_1092074.pdf)

Looking at the spec sheet you provided it's definately a router, willing to put my money where my mouth is.

---

### Post by mips on 2006-10-15
> **Stoff said:**
> now i am reading in a german forum that my machine can be used as a router as well. however, my provider distributes it as a modem only. maybe it is somehow locked. nevertheless, i would like to use it as a modem.

If you want to make life hard for yourself then I cannot help you. Good luck.

Your other option is to access the management interface, configure it for pppoe (take it out of bridged mode and into routed mode), configure the authentication (username & password). On the PC simply enable DHCP and you should be ok.

---

### Post by Stoff on 2006-10-17
can you expand on the dhcp issue a little bit? i have hardly an idea what you mean. :-?

---

### Post by mips on 2006-10-17
When you configure your IP parameters on the PC there is a option to select either static configuration or use DHCP. With DHCP all the required parameters will be sourced from the router without any intervention on your part.

But you first have to ensure your router is properly configured.

---

