---
title: "Windows XP cannot connect to Internet"
date: 2006-12-13
forum: Networking &amp; Wireless
---

### Post by pkelkar on 2006-12-13
Hi,

I have the following setup 
ubuntu + dhcp3-server + shorewall with 2 nic. I have connected one nic to dsl modem. other nic is connected to gigabit switch which connects other pcs including windows xp.

I am unable to browse internet from the Windows xp workstation. It looks like Win Xp box is getting the IP address assigned by Ubuntu Dhcp server. I checked the ipconfig on xp. I am able to make skype calls from windows xp but cannot browse internet using IE.

Any ideas???

---

### Post by gerowen on 2006-12-13
Open IE, click Tools, Internet Options, then go to Connections.  Click LAN Settings, tell it to automatically detect proxy settings.  Then open your Network Connections and make sure that you don't have any other network connections set as the default.  If they are right click them and click "Cancel as Default".  If it still doesn't work, run the "Network Setup Wizard" and see if that helps.

---

### Post by pkelkar on 2006-12-15
Changing the IE settings did not work. Any other suggestions???? 


:-k

---

### Post by cracker on 2006-12-15
Looks like a DNS problem to me. Check that DNS works on your server, then on the XP box, by doing something like this:
```
nslookup www.google.com
```
Just as a personal recommendation, I highly suggest you install and configure bind on the Ubuntu server...I installed it on my local Linux server and it has vastly improved my DNS lookup times (and in turn browsing speed) over my ISP's servers.

---

### Post by pkelkar on 2006-12-16
You are correct. It is an issue with DNS. nslookup from win xp gives a time out error. I installed BIND9 and trying to configure it. any good pointers on setting config files. I am also checking how-to in the forums.

---

### Post by pkelkar on 2006-12-18
> **cracker said:**
> Looks like a DNS problem to me. Check that DNS works on your server, then on the XP box, by doing something like this:
```
nslookup www.google.com
```
Just as a personal recommendation, I highly suggest you install and configure bind on the Ubuntu server...I installed it on my local Linux server and it has vastly improved my DNS lookup times (and in turn browsing speed) over my ISP's servers.

I added the dns server names of my ISP provider in the TCP/IP settings and internet is now working from windows xp. What do I need to get it working without specifing the DNS server names (obtain DNS server address automatically) ?

---

### Post by cracker on 2006-12-19
You need to configure your DHCP server to send those addresses to the clients. I don't have any experience with the one you're using, but it should be one of the basic options listed in any guide, configuration, or man page. As for bind, I really didn't need to specify anything special in the configuration...in fact, it set itself up and I just entered it as my DNS server. However, my DNS server runs Trustix Secure Linux (redhat based) so I don't know if the package comes so nicely set up under Ubuntu. There is a guide on the wiki for it though.

---

