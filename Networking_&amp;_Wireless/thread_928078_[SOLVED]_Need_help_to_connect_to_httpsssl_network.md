---
title: "[SOLVED] Need help to connect to https/ssl network"
date: 2008-09-23
forum: Networking &amp; Wireless
---

### Post by Benic on 2008-09-23
Hi ! I need to connect to a remote networkk through a https/ssl connection for my job. I can see the network using the Firefox (after adding a homemade security certificate), but I can only download files. It's like accessing to a ftp page. I don't really know where to start. I tried gFTP, but it doesn't work with ssl connection, as far as I know. I tried Samba, but I can't figure out how to configure it to deal with a remote network.

---

### Post by willca on 2008-09-24
what vpn platform does your work use?

i mean if you are accessing it via firefox...then likely its only allowing whatever is going to show up as links in that page...otherwise if you expect to be able to use ftp and such, then it has to load some sort of proxy software / ipsec something in the background.

---

### Post by Benic on 2008-09-24
I work for a research center (university). They use Cisco VPN and I can access databases and scientific articles through VPN or Web-VPN (painfully slow). The research center I work for has a some space allocated on a server to store and share documents for research projects. They create accounts so access is limited to a bunch of people. With Windows XP, all I had to do was to install a security certificate, add a URL favorite in network favorites and type in name and password. When I try to connect to a server with Ubuntu, I end up on a Firefox page, without being able to do much than downloading files. I talked to the network guy, but he said he doesn't know much about Linux. 

So if I get it right, you're saying I should try to go through VPN? I'm connected to the VPN, but it doesn't seem to change anything. What should I do?

---

### Post by Benic on 2008-09-24
I've just found a solution. With lftp, I can now access the server properly and upload/download files.

---

