---
title: "How to set up SSH access to my router?"
date: 2021-01-23
forum: Networking &amp; Wireless
---

### Post by bhuether on 2021-01-23
Hi,

I am using an ZYXEL router (418N). In its NAT Application section I enabled SSH. There it asked for a server IP. I put IP of my computer, from which I am trying to access my router via SSH.

If I do "nmap routerip" I don't see port 22 listed as open. I see

```
PORT     STATE SERVICE
23/tcp   open  telnet
80/tcp   open  http
5431/tcp open  park-agent
```

On my computer if I do "nmap localhost" I see

```
PORT     STATE SERVICE
80/tcp   open  http
443/tcp  open  https
3306/tcp open  mysql
8080/tcp open  http-proxy
9502/tcp open  unknown
9503/tcp open  unknowwn
```

On my computer I can SSH to my webserver, so I know SSH is working fine on my computer. I just can't figure out why I can't SSH to my router. The router also has NAT setup and port triggering, but I didn't tough those since I thought it was enough to just enable SSH. When I do "ssh user@routerip" I get "Connection Refused"

Ideas on what I need to do?

---

### Post by cmcanulty on 2021-01-23
Besides enabling ssh on router there is probably a place to set the ssh port. Also to ssh to the port through a router use the router password not the computer password. It is also good to change the router port from the default 22 for ssh to enhance security. But if you change the ssh router port also allow that port through your ubuntu firewall. Another way is to set a port forwarding to the desired computer and make the local port 22 and the port range or outside port to whatever you want for example you set it for 2277 so you ssh using 2277 but the router interprets that as 22 for your address and you don't have to change anything in your ssh config files on your computer. I use an asus router so the words for ports may vary on a different router.

---

### Post by SeijiSensei on 2021-01-23
Did you try both the internal and external addresses of the router?

---

### Post by Holger_Gehrke on 2021-01-23
The NAT (Network Address Translation) settings are for enabling access to servers inside the LAN from the Internet. You've basically told your router - the machine which is both on the internet and on your LAN - to sent any traffic coming in from the internet on port 22 to your machine. This is probably not what you wanted ... 

Since I don't have this router, I don't know whether there's an ssh-server on the router but I doubt it. This is usually a feature for professional devices and the 418N is sold as a home router. The manual available at zyxel.com doesn't mention ssh at all.

Holger

---

### Post by QIII on 2021-01-23
@bhuether:

Please use the default font and color in your posts.

Enclose all terminal commands and results in code tags:

1. If you are using the "Reply to Thread" button then type or paste your text, highlight the text and use the # button in the text box header.  Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

### Post by The Cog on 2021-01-23
Are you trying to connect to the router, or to your PC?

If you are trying to connect to the router then do **not** configure NAT for SSH - this will make the router forward SSH connections to your PC, and presumably then hide the router's SSH service even if it does exist (I don't know if this router can accept SSH).

If you are trying to get the router to forward SSH connections to your PC, then you need to install an SSH server on your PC - at the moment it's not listening on port 22.

---

