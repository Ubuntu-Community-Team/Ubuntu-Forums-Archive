---
title: "Suddenly rejecting only one IP address"
date: 2020-12-22
forum: Networking &amp; Wireless
---

### Post by nurbles on 2020-12-22
(question also posted to askubuntu.com)
 I have a ubuntu 18.04.5 system that has been a well behaved mail server for the past two years. Yesterday morning it decided to start rejecting 'secure' connections (TCP ports 22, 143, 443) but it still allows plain ftp or http connections. Stranger still, it is only rejecting these connections from ONE IP address -- the external address of our internet gateway. The gateway and mail server machines both run the same version of ubuntu are physically in the same rack and connected to the same cable modem. I use apt to keep them up-to-date. The IP addresses of the gateway and mail server are on the same external subnet (in fact, the node addresses are sequential.)
 I run shorewall, fail2ban, postfix and dovecot. None of them are logging anything about the rejections. Neither fail2ban nor shorewall shows any activity related to ANY of our external IP addresses. However, I can run tcpdump on the mail server to see the rejections occurring as well as wireshark on the client computers to see the same thing from the other end. All I see is the TCP SYN being received and a TCP RST being sent in response, so I don't think there's any chance that a security certificate, blacklist or anything like that could've been involved that early in a connection, could it? It seems completely arbitrary and nothing is being logged, so I'm at a loss as to how I should proceed.
 This system had been working perfectly since it was initially built with ubuntu 12.x, through the 14.x, 16.x and 18.x upgrades. The most recent update that I performed was about a week ago. I have rebooted the clients, the gateway and the mail server plus I waited 24 hours then rebooted everything and tried again, but the secure connections are still being instantly rejected, while the unsecure are allowed -- they just redirect to their secure versions, though, which are immediately rejected. Sigh.  I need to find out what is causing the rejections, but since nothing is logged, I don't know where to start. I'm not a linux expert, but I can follow instructions if any one has any ideas that may help me track this down.
 Oh, one final note: The mail server also has second NIC with an address on our private office network. The secure connections from other computers in the office work fine, so only the external address is blocking our gateway address.

---

### Post by TheFu on 2020-12-22
I'd disable the firewall completely for a few minutes and see if that lets the connections through.

Internet servers can be hacked, especially those directly with public IPs. I would be inclined to assume this if the firewall test doesn't fix it, then wipe the system and restore from my backups. Should take about 45 minutes, tops.

BTW, running all those services on the same machine maybe isn't a good idea. Because email is a high-risk service, I run an email gateway which is religiously patched between the real email server and the internet.  All inbound/outbound SMTP goes through it.  To access the real server, people must use our VPN, period. There was pushback initially - especially from the CEO - then I showed him the thousands of attempted IMAPS connections to his account from foreign countries.  I didn't get any more lip from him after that.  The gateway blocks about 95% of all SMTP traffic.

No way would I have plain FTP on any server I run. No freakin' way.  To get files we publish to the world, the HTTP server can be used.  To push files to us, they need to use another service, not plain FTP. Never plain FTP. Heck, we can grab files off their HTTP/S server if needed.  I wouldn't have a web server or ftp or sftp or imap server on our SMTP-gateway. Too many moving parts on a single OS is a security risk.

Are these physical machines or VMs or containers?

---

### Post by nurbles on 2020-12-23
Found it.  Somehow our gateway's IP got added to the dynamic DROP list in iptables, but fail2ban insisted that the address was not banned by any of my jails, so it would not remove it.  I finally figured out how to manually delete it from iptables and things are working again.

---

