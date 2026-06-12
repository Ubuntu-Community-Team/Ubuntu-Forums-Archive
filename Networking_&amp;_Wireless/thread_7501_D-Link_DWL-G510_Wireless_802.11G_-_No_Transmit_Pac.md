---
title: "D-Link DWL-G510 Wireless 802.11G - No Transmit Packets"
date: 2004-12-08
forum: Networking &amp; Wireless
---

### Post by Albertaco on 2004-12-08
I'm trying to get my D-Link GWL-G510 (ver 2) working with Ubuntu  version 4.10. Ndiswrapper loads correctly, and the Access point is found
on iwconfig. However, the device appears only to receive packets. (Looking at ifconfig, it receives packets fine, but transmitted packets remains at 0). Also, looking at the lights at the back, both seem to be working ok. However, I can't acquire a DHCP lease. Can anybody help??

Thanks in advance,
Albert


My system specs:
(Booted with ACPI=noirq and PNPBIOS=off flags)

root@ubuntu:/usr/local/src # uname -a
Linux ubuntu 2.6.8.1-3-386 #1 Thu Nov 18 11:47:33 UTC 2004 i686 GNU/Linux

root@ubuntu:/home/awang/dlinkdriver # ndiswrapper -i NetA3AB.inf
ls: /etc/ndiswrapper: No such file or directory
Installing neta3ab
Warning: Cannot locate
Warning: Cannot locate
Warning: Cannot locate
Warning: Cannot locate
Warning: Cannot locate
root@ubuntu:/home/awang/dlinkdriver # ndiswrapper -l
Installed ndis drivers:
neta3ab driver present, hardware present


root@ubuntu:/home/awang/dlinkdriver # dmesg
...Other stuff...
ACPI: PCI interrupt 0000:00:0d.0[A] -> GSI 18 (level, low) -> IRQ 185
ndiswrapper: using irq 185
ndiswrapper (NdisAcquireSpinLock:950): Windows driver trying to use uninitialized lock e4d81418, fixing it.
wlan0: ndiswrapper ethernet device 00:11:95:88:c7:6d using driver neta3ab
wlan0: encryption modes supported: WEP, WPA with TKIP, WPA with AES/CCMP
ndiswrapper: driver neta3ab (D-Link,07/28/2004,3.3.0.157) added


root@ubuntu:/home/awang # lspci
0000:00:0d.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 001a (rev 01)


awang@ubuntu:~ $ ifconfig
wlan0 Link encap:Ethernet HWaddr 00:11:95:88:C7:6D
inet6 addr: fe80::211:95ff:fe88:c76d/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:122 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:40068 (39.1 KiB) TX bytes:0 (0.0 b)
Interrupt:185 Memory:f9c00000-f9c0ffff

---

### Post by p!=f on 2004-12-08
Do you have ndiswrapper module loaded?
Does this device have some firewall built in? If so, is it setup correctly to permitt DHCP traffic?

---

### Post by Albertaco on 2004-12-08
>  Do you have ndiswrapper module loaded?
I'm assuming yes. The dmesg output shows that ndiswrapper was loaded
(I forgot to paste the line:)
ndiswrapper version 0.12 loaded (preempt=yes,smp=no)


>  Does this device have some firewall built in? If so, is it setup correctly to permitt DHCP traffic?
I don't think so. I'm able to connect normally via the wired Ethernet port.

-Albert

---

### Post by Andrieshr38 on 2007-05-15
> **Albertaco said:**
> &gt;  Do you have ndiswrapper module loaded?
I'm assuming yes. The dmesg output shows that ndiswrapper was loaded
(I forgot to paste the line:)
ndiswrapper version 0.12 loaded (preempt=yes,smp=no)


&gt;  Does this device have some firewall built in? If so, is it setup correctly to permitt DHCP traffic?
I don't think so. I'm able to connect normally via the wired Ethernet port.

-Albert


[Cash Advance caffeine blood pressure insects Google](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/forced-porn.html)

---

