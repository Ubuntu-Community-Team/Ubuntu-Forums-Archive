---
title: "eth0 not showing"
date: 2007-07-19
forum: Networking &amp; Wireless
---

### Post by edsmgldby on 2007-07-19
Hi
i just installed 6.06 server when asked to configure network card it recognized my card however i picked configure later. Now i have already configured my /etc/network/interfaces for eth0 to use DHCP.
when typing 'ifconfig' a device called eth0 shows up and says that it is up, but it does not have an IP address. and if i try to 'ping' it says 'connect: network is unreachable'
if i ping 127.0.0.1 (ie loop back) it responds correctly.


when i dmesg i see the device (with the correct MAC address) it says that the ethernet is an Intel pro/100 network driver, 3.4.14-k4-NAPI and 
"e100: eth0 e100_probe:addr 0x80013000, irq 9, MAC addr 00:E0:C7:07:FE:7B"

a couple dmesg later it says:
 "e100: eth0: 100_watchdog: link down"
"e100: eth0: 100_watchdog: link up, 100mbps, full duplex"
it repeats the down and up lines 20 times with the last one saying up

How do i get eth0 to work?

Thanks

---

