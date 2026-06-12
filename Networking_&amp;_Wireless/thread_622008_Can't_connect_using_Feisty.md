---
title: "Can't connect using Feisty"
date: 2007-11-24
forum: Networking &amp; Wireless
---

### Post by thomasyen on 2007-11-24
Hello.
I have been using Feisty for a while now. Recently, I had the Windows partition of my machine reformatted (I run a Widows/Ubuntu dual boot machne.) However, after the reformat,I found that I could no longer connect using Feisty. Can anyone help me out?

My settings:

Location: [blank]

Connections
Wired connection: roaming enabled
Modem connection: not configured

General
Host settings:
Host name: ***
Domain name: [blank]
Auto service discovery: disabled

DNS
DNS servers: 168.95.192.1
Search domains: [blank]

Hosts
***

My Windows system provided this information:
Device name: WAN Miniport (PPPoE)
Device type: PPPoE
Server type: PPP
Transmission: TCP/IP
Authentication: PAP
Compression: (none)
PPP mutiple link structure: disabled
Server IP: ***.***.***.***
Client IP: ***.***.***.***

Note: 
My Internet connection works fine in Windows. I really need the Internet connection because I intend to upgrade to Gutsy.

---

### Post by seventynine on 2007-11-24
> Connections
Wired connection: roaming enabled
Modem connection: not configured

It's not listing your "Wireless connection: " here, so it seems that the driver may not working.

Try reinstalling the driver. Whats the chipset on your wireless card? Go to Terminal and type "lshw" and hit enter to find out.

---

### Post by thomasyen on 2007-11-24
I don't have a wireless card, since I use a desktop barebone.

---

### Post by seventynine on 2007-11-25
Try pinging this ip: 63.226.12.96

Since you're getting a DNS server, it probably can't be a bad connection/driver problem. Perhaps you have a bad DNS server. If you can ping the above address, ask your ISP to give you the ip address of a working DNS server or find a public DNS server (such as 63.226.12.96). Thats all I can think of at the moment.

---

### Post by thomasyen on 2007-12-07
The DNS you see is the one I set, not the one I'm getting a connection from. I tried pinging the DNS(which I know is valid because I can connect to it just fine under Windows), but got no reply. I tried pinging the IP you gave me, but got the same results. I was wondering if my ISP is blocking Linux connections...

---

