---
title: "block ip-range with iptables"
date: 2014-03-27
forum: Networking &amp; Wireless
---

### Post by chris137 on 2014-03-27
Hi,
on my vserver I wanted block an IP range since those Asians won't stop to flood my access-log.
Kernel is 2.6 and Ubuntu is 10.04.4 LTS

I tried with this line:
```
iptables -A INPUT -p tcp -m iprange --src-range 116.10.191.0-116.10.191.255 -j DROP
```
but all I get is
iptables: No chain/target/match by that name.

Just recently I tried to do something different and it did not work either because of the same error.
Since it was not that important and it really drove me mad I just pressed Ctrl+D and did not care anymore.
But this really annoys me now and I want to solve it.
Google did not bring me far last time and since it is the same error I will not stress myself anymore.

Hopefully some of you can help.

---

### Post by houstonbofh on 2014-03-28
How about;
iptables -A INPUT -p tcp -s 116.10.191.0/24  -j all


EDIT:  I made a typo!  Thanks,  SeijiSensei.  You do not want all...  reject or drop might be better. :)

---

### Post by SeijiSensei on 2014-03-28
I think you want "-j REJECT" at the end of the that rule.

---

### Post by chris137 on 2014-03-29
Sorry, was too excited to remember to reply :D
Thanks!
Works like a charm.
I used
iptables -A INPUT -p tcp -s 116.0.0.0/8  -j DROP

---

### Post by houstonbofh on 2014-03-30
FYI:  My firewall blocks...
These are folks that just kept coming up in my logs.
```
 		* 	58.17.30.0/23 	* 	* 	* 	Block China - ShangHai Shelian commpany  	
		* 	59.69.128.0/19 	* 	* 	* 	Block China - Nanyang Institute of Technology  	
		* 	61.164.145.0/24 	* 	* 	* 	Block China - Wenzhou Telecom Co.,ltd  	
		* 	81.196.20.0/23 	* 	* 	* 	Block Romania - RCS & RDS S.A.  	
		* 	82.213.64.0/19 	* 	* 	* 	Block Italy - MIPIACE.COM SPA  	
		* 	111.0.0.0/10 	* 	* 	* 	Block China - China Mobile Communications Corporation  	
		* 	125.23.218.0/24 	* 	* 	* 	Block India - Bharti Tele-Ventures Limited  	
		* 	183.129.128.0/17 	* 	* 	* 	Block China - Zhejiang Telecom  	
		* 	200.105.224.0/20 	* 	* 	* 	Block Ecuadore - PUNTONET S.A.  	
		* 	203.99.130.0/23 	* 	* 	* 	Block Indonisa - PT. Varnion Technology Semesta  	
		* 	210.83.84.64/26 	* 	* 	* 	Block China - China Unicom CncNet  	
		* 	222.96.0.0/19 	* 	* 	* 	Block Korea - Korea Telcom
```

---

