---
title: "[SOLVED] Huawei 220 ppp connection"
date: 2007-12-17
forum: Networking &amp; Wireless
---

### Post by timbosity on 2007-12-17
Got the Huawei 220 USB mobile modem 3G thingee to be recognised as a modem and then to connect following this ([http://www.linux.ie/articles/tutorials/threeirelandUSBmodem.php](http://www.linux.ie/articles/tutorials/threeirelandUSBmodem.php)) which as far as I can tell configures a ppp connection. But then i get this error message (below) and i cant connect to get for eg openoffice from the repository or browse the net. The modem is flashing blue liek it does when it is connected. Any suggestions even as to what is wrong. im thinking the DNS address that i supplied in etc/resolv.config didnt work.??

ive installed Xubuntu 7.10 Gutsy gibbon on 256ram 20GB 1.67 amd athlon. I have dual boot with XP cos im not ready to fully take the plunge, although i most definitely will when it all works ;-)

tim@tim-laptop:~$ modprobe usbserial vendor=0×12d1 product=0×1003

tim@tim-laptop:~$ pon
Serial connection established.
Using interface ppp0
Connect: ppp0 <--> /dev/ttyUSB0
PAP authentication succeeded
Could not determine remote IP address: defaulting to 10.64.64.64
Cannot determine ethernet address for proxy ARP
local  IP address 10.206.155.11
remote IP address 10.64.64.64
primary   DNS address 10.11.12.13
secondary DNS address 10.11.12.14

---

### Post by timbosity on 2007-12-18
alright got everything working. It turns out the resolv.conf file didnt contain the right DNS addresses (I think) It seemed to fix all when i retyped the resolv.conf file to include the DNS server for the ISP (three mobile). That shouldnt have stopped me from connecting to the internet though should it??

---

