---
title: "Ubuntu &amp; Airport Extreme (old model)"
date: 2008-11-17
forum: Networking &amp; Wireless
---

### Post by prami on 2008-11-17
Hi all and thanks in advance for any help.

Following situation
Cablemodem (dynamic IP from ISP)
\--> Airport Extreme WAN port
Airport Extreme (AE) is dhcp server
AE LAN port 
\--> 5-port Switch
...\--> Thecus NAS (dhcp)
...\--> Ubuntu PC (dhcp)
AE WLAN 
\--> Laptop 1, WinXP (dhcp)
\--> Laptop 2, Mac OS-X (dhcp)

My problem is that all except Ubuntu PC get a IP from AE.
Ubuntu does not open Network as such.
Cables changed, same behaviour.
Switch Port changed, same behaviour.
Using same switch port and cable on Laptop 1, laptop get dhcp address without problems.

In case I change my environment as followed:
Airport Extreme (AE) is still dhcp server
Cablemodem  (dynamic IP from ISP) 
\--> 5-port Switch
...\--> AE WAN port
...\--> Thecus NAS (dhcp)
...\--> Ubuntu PC (dhcp)
AE WLAN port
\--> Laptop 1, WinXP (dhcp)
\--> Laptop 2, Mac OS-X (dhcp)
then all except Ubuntu PC get a IP from AE and Ubuntu PC get another IP from ISP range ....
Means in second environment I could go to Internet with Ubuntu but could not share data with other PC's of my net because of different Subnet.

Strange.
I'm lost.

How to get my environment (the first described) up & running with Ubuntu ?

I also tried to assign a fix IP to Ubuntu PC, but also then it does not work...

Switching off all pieces and restarting also done several times ;-(

Thanks and greetings from Basel
Wolfgang

P.S. Thecus NAS works also fine with fix IP and will be used with fixed IP. I just wanted to point out that also there dhcp works.

---

### Post by prami on 2008-11-20
Hi all

no ideas ??

In the meanwhile, I reinstalled Ubuntu.
Same effect.
Conecting Ubuntu directly after Kabelmodem, Network works well within miliseconds.
Connecting in Switch behind Airport Extreme box, no internet-connection at all.

Do I really need to install WXP in order to get my network up & running ?

regards
Wolfgang

---

