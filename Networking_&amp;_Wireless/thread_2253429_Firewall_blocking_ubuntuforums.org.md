---
title: "Firewall blocking ubuntuforums.org"
date: 2014-11-19
forum: Networking &amp; Wireless
---

### Post by mike262 on 2014-11-19
Upgrading from 10.04 LTS to 12.04.5 LTS.  Very disappointed so far Unity is so heavy.


When ever i try to go to the Ubuntu forum's i get block (example: [http://ubuntuforums.org/showthread.php?t=1002912](http://ubuntuforums.org/showthread.php?t=1002912)) by third party firewall and it gives me this message and drops the traffic.

Seems to only happen when i go to something with (.php?t=1002912) in the URL.
 

Intrusion Prevention Alert
 
An intrusion has been detected. The packet has been dropped automatically.

 
Details about the intrusion alert:
 
Message........: SPECIFIC-THREATS RedKit Repeated Exploit Request Pattern
Details........: [http://www.snort.org/search/sid/23218?r=1](http://www.snort.org/search/sid/23218?r=1)
Time...........: 2014:11:19-10:44:33
Packet dropped.: yes
Priority.......: high
Classification.: A Network Trojan was detected IP protocol....: 6 (TCP)
 
Source IP address: 192.168.2.55
Source port: 38411

Destination IP address: 91.189.94.12 (feijoa.canonical.com)
Destination port: 80 (http)
       


This is driving me crazy why does 12.04 LTS do this but not 10.04 LTS. 

What do i need to disable to get this to stop. 

I have tested on a windows 7 PC and I don't get this problem. Also problem seems to happen on all linux fav. Fedora 20 aswell.

---

### Post by buzzingrobot on 2014-11-19
Since it happens on Fedora, it's not an Ubuntu issue.

Ubuntu ships with the ufw firewall but it is not enabled unless the user enables it.  Many (most?) use the gufw GUI to do that.

What third-party firewall have you installed?  What happens when you disable it?  Is the same firewall installed on Fedora 20?

---

### Post by oldos2er on 2014-11-19
Moved to Networking & Wireless.

---

### Post by mike262 on 2014-11-20
The firewall is a stand alone server. It is not installed on the ubuntu or fedora machine I am testing on. What I don't get is what would cause Linux to get blocked and not windows. Also I have not enabled ufw. it is a sophos firewall astaro.

---

### Post by Mike_Walsh on 2014-11-20
Hi, Mike.

So; just out of curiosity, why don't you use the built-in firewall, and control it via gufw?

Regards,

Mike.

---

