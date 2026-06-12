---
title: "Newbie help on setting up FTP server"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by SickNick on 2008-11-04
OK I have been messing around on my desktop that I do not use any more and I want to make it my backup and set up an ftp server on it. I have GProFTPD and I believe i have it set up right. I have my host name as lets say "sicknick.homelinux.com", I have a DynDNS account and I registered that domain and my ip address I have on it is 192.168.2.20. I have a belkin router, I forwarded port 21 to 192.168.2.20. I have the belkin N1 Vision and it has a DDNS setup area, I selected my DNS service which was DynDNS nd all i had to do is give my login details and my domain name. It says domain found and everything is ok. Now I activate my ftp server, when I goto sicknick.homelinux.com, it sends me straight to my belkin router page. My friend told me to set up a static ip, so I went to administration>network, and went to my wired connection properties selected Static Ip, and I put in 192.168.2.20 subnet 255.255.255.0 and thats it I tried putting my gateway to 192.168.2.1 which is my router. When I do that I completely loose internet. I have no idea what to do any more, I am in school for this but i have not taken any network classes. Help me out please

---

### Post by cariboo on 2008-11-04
It sounds like you have everything set up right, is your ISP blocking port 21, to check go here:

[http://www.canyouseeme.org/](http://www.canyouseeme.org/)

If you are able to access your routers management page from the internet, turn off remote access.

Jim

---

### Post by SickNick on 2008-11-05
#-o

---

### Post by SickNick on 2008-11-05
Error: I could not see your service on (myIP) on port (21)
Reason: Connection timed out

I am forwarding port 21 in my modem now, and I am a lil confused if I should pick

Host:Allows unsolicited inbound traffic to a particular PC on the LAN.

Dynamic:Enables inbound traffic based on specific outbound traffic.

For Hosted Service, Select a PC on the LAN

Select a Discovered LAN device: 	Or manually enter a LAN IP: 	


I am assuming dynamic? Let me know, thank you for your help

---

