---
title: "Ubuntu, LAN and Wndows XP"
date: 2006-09-04
forum: Networking &amp; Wireless
---

### Post by Lilac on 2006-09-04
This place has helped me out so much but I have never needed to ask for help before. I have 2 computers. This one I'm on is the main one. I have partitioned it, dual-booting, windows XP Home and Ubuntu dapper drake. It's connected to the internet via a USB cable to a Telstra NT1 Plus 2 modem and is ISDN 128k (I know... slow).

The other one belongs to my little brother. OS is Windows XP Home and is connect via ethernet to the main computer so he is able to access files on the main and use the internet as we dont have a wireless adaptor.

This works perfectly on Windows to Windows, but I'm unable to get it working whilst using Ubuntu on the main computer.

Also, when I typel dpkg -l samba, this comes up: 
```
Desired=Unknown/Install/Remove/Purge/Hold 
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed 
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad) 
||/ Name           Version        Description 
+++-==============-==============-============================================ 
ii  samba          3.0.22-1ubuntu a LanManager-like file and printer server fo
```

I'm not sure what I'm doing wrong.  :confused:

---

### Post by austin987 on 2006-09-05
Does the modem work under ubuntu?

You need to setup internet sharing, ie, through NAT. These should help you out:

[http://ubuntuguide.org/wiki/Dapper#How_to_install_DHCP_Server_for_automatic_IP_addresses_assignment](http://ubuntuguide.org/wiki/Dapper#How_to_install_DHCP_Server_for_automatic_IP_addresses_assignment)
[https://wiki.ubuntu.com/ThinClientHowtoNAT](https://wiki.ubuntu.com/ThinClientHowtoNAT)
[http://www.marianistas.org/comunidad_56_6493_0.htm](http://www.marianistas.org/comunidad_56_6493_0.htm)

---

### Post by Lilac on 2006-09-07
Modem works fine.  Everything set up.  I just managed to get samba working on both computers but on my brothers computer, I cant get the internet working on his. Tried //192.168.1.x in run on windows and opened up samba on his but still... no internet, it's connected via ethernet so in therory it should connect straight away.

---

### Post by Lilac on 2006-09-07
how embarrassing  :)

I worked out where I was going wrong.  I forgot to add a 0 at the end of an IP address.  I've got it working now!!

---

