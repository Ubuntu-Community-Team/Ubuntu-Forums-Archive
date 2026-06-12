---
title: "problem faced connecting ubuntu with internet"
date: 2010-04-03
forum: New to Ubuntu
---

### Post by sanchitadatta on 2010-04-03
I could not connect ubuntu o.s. with BSNL Broadband service India's modem ADSL2+CPE manufactured by Teracom as ubuntu could not read the BSNL's cd. Do I need any driver for that? If yes then please tell me where can I get that driver? I downloaded rp-pppoe-3.10.ter but ubuntu failed to read that file.

---

### Post by dineshs on 2010-04-04
if you are connecting via ethernet,you dont need a driver.Just plugin the modem and try```
ifconfig -a
```and post the output
How do you connect to internet in Windows?Do you have a pppoe dialler?If yes follow this method
[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

---

### Post by dineshs on 2010-04-06
Also you can configure your modem for an always on internet in which case you dont have to use rp-pppoe /ADSL pppoe.For this
Open browser
Type 192.168.1.1 in Address bar. click GO
Enter both Username and Password as [COLOR="Blue"]admin[/COLOR]
Click OK
Click configuration on the left margin
Click internet connection  below
Click delete (the drum symbol)right to 0/35(confirm with ISP)
Click add below
give pvc name as abcd
give VPI as 0 and VCI as 35
Click Next
tick PPP over Ethernet
Select LLC/SNAP as encapsulation
Click next
Ensure that  Enable NAT and Add default route are ticked
Click next
Service name-asdf
enter username and password given by your ISP
Confirm password
Click Next
Apply
Click Admin on the left margin 
Click Reboot
Select reboot from last and Click reboot
Wait for 3 minutes.
Once the link and data lamps glow you can start browsing.
If data and link lamps are glowing but  pages are not loading ```
sudo gedit /etc/resolv.conf
```copy and paste this
```
nameserver 8.8.8.8
nameserver 8.8.4.4

```save the file and try

---

