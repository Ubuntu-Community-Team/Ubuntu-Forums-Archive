---
title: "Cannot access domain outside LAN."
date: 2009-12-31
forum: New to Ubuntu
---

### Post by Hovercat on 2009-12-31
I have gotten my domain set up for [http://173.2.183.98](http://173.2.183.98). My ISP no longer blocks port 80, I got an internet upgrade. I can view my domain ([www.asskickersunited.com]("http://www.asskickersunited.com")) and the IP. No one outside my LAN can view it. However, if I change the IP to have port :81, everyone can view it, then I'm out of a domain. I am using Linux 9.10 Server Edition. I am in desperate need of help.

In my router log, it shows that users connecting to the site, but the LAN Ip. example:

```

[LAN access from remote] from IHIDTHISIP:61666 to 192.168.1.11:80
```

---

### Post by wirelessmonkey on 2009-12-31
Sounds like you need to forward port 80 on your home router/gateway to your server.

---

### Post by lisati on 2009-12-31
> **wirelessmonkey said:**
> sounds like you need to forward port 80 on your home router/gateway to your server.

+1.

---

### Post by Hovercat on 2009-12-31
> **wirelessmonkey said:**
> Sounds like you need to forward port 80 on your home router/gateway to your server.

I already did that, silly!

---

### Post by Hovercat on 2009-12-31
I've checked the server's firewall (iptables) I have something in there for port 80.

```
-A RH-Lokkit-0-50-INPUT -p tcp -m tcp --dport 80 --syn -j ACCEPT
``` That's in /etc/sysonfig/. File name: iptables

Still doesn't work. =\

---

### Post by lisati on 2009-12-31
I clicked the link you provided and it's behaving as if it's blocked. Is that the correct IP address? They sometimes change if you restart your router.


edit: Visiting [www.whatismyipaddress.com](www.whatismyipaddress.com) from your serever (assuming you have a browser) can tell you your current IP address.

---

### Post by Hovercat on 2009-12-31
I know my IP by heart. 173.2.183.98

Edit:

I can't visit a site from my browser, I specifically stated I'm running Ubuntu 9.10 Server Edition (That means no GUI!)

---

### Post by lisati on 2009-12-31
> **Hovercat said:**
> I know my IP by heart. 173.2.183.98

Good.
> **Hovercat said:**
> 
Edit:

I can't visit a site from my browser, I specifically stated I'm running Ubuntu 9.10 Server Edition (That means no GUI!)

I just tried pinging your IP address and got the following message:
> [noparse]PING 173.2.183.98 (173.2.183.98) 56(84) bytes of data.

--- 173.2.183.98 ping statistics ---
2 packets transmitted, 0 received, 100% packet loss, time 999ms

[/noparse]

---

### Post by Hovercat on 2009-12-31
I pinged it with the Windows XP CMD, I get 

Pinging 173.2.183.98 with 32 bytes of data:

Reply from 173.2.183.98: bytes=32 time<1ms TTL=64
Reply from 173.2.183.98: bytes=32 time<1ms TTL=64
Reply from 173.2.183.98: bytes=32 time<1ms TTL=64
Reply from 173.2.183.98: bytes=32 time<1ms TTL=64

Ping statistics for 173.2.183.98:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms

My friend also did a ping, he got a timed out.

---

### Post by lisati on 2009-12-31
> **Hovercat said:**
> I already did that, silly!
From our end it looks as if you didn't. You might want to double check that the settings took.
> **Hovercat said:**
> I've checked the server's firewall (iptables) I have something in there for port 80.

```
-A RH-Lokkit-0-50-INPUT -p tcp -m tcp --dport 80 --syn -j ACCEPT
``` That's in /etc/sysonfig/. File name: iptables

Still doesn't work. =\
On my home server I have absolutely no rules defined for iptables and people are able to access my web site.


edit: is the ip address you have given us one assigned by your home network or one assigned by your ISP?

---

### Post by Dayofswords on 2009-12-31
> My ISP no longer blocks port 80, I got an internet upgrade. 
what evil ISP do you have, that port is the defualt for web servers, with out it, you basically have no web internet

---

### Post by lisati on 2009-12-31
I just spotted the reference to the ports in the OP. Is your /etc/apache2/ports.conf set to listen to the correct port?

---

### Post by Hovercat on 2009-12-31
> **Dayofswords said:**
> what evil ISP do you have, that port is the defualt for web servers, with out it, you basically have no web internet

*Optimum, hosted by retards, but gotta love that speed.* I got their boost service, I made sure Port 80 was open.

[quote=lisati]I just spotted the reference to the ports in the OP. Is your /etc/apache2/ports.conf set to listen to the correct port[/quote]

What does the listen port need to be? 443?

---

### Post by baltadt on 2009-12-31
did you add a port fowarding in your router and if you did are you sure it is the external ip for the computer and not the modem it's self?

---

### Post by Hovercat on 2009-12-31
> **baltadt said:**
> did you add a port fowarding in your router and if you did are you sure it is the external ip for the computer and not the modem it's self?

The service HTTP is forwarded to the Starting port of 80 and ending port of 80. And the server IP is the 192.168.1.11 (Static LAN IP for the computer with the website)

---

### Post by Hovercat on 2009-12-31
I removed my firewall, and it still doesn't work. -_-

---

### Post by Ocxic on 2009-12-31
> **Hovercat said:**
> I removed my firewall, and it still doesn't work. -_-

maybe your ISP is still blocking incoming connections on port 80. 
You said if you changed it to port 81 it worked, that would be my conclusion.

Some ISP's don't like people running servers like that from home. and block incoming connections.

One other thing that might be an issue is that most ISP don't allow loopback connections, you might want to try using a web based proxy on the net to access you site. that's what i have to do to test my server.

---

### Post by Hovercat on 2009-12-31
> **Ocxic said:**
> maybe your ISP is still blocking incoming connections on port 80. 
You said if you changed it to port 81 it worked, that would be my conclusion.

Some ISP's don't like people running servers like that from home. and block incoming connections.

I got an upgrade, I have port 80 enabled. I can view my public IP, no one else can. Also, on their site manager, you can change the IP of the server. Also, when I talked to them and I mentioned my own server, they didn't have a problem with it. If we weren't allowed to host our own server, then they wouldn't give us the option for port 80.

I'll try that proxy server.

Edit: EPIC FAIL.

[img]http://i49.tinypic.com/30w5teu.jpg[/img]

---

### Post by Hovercat on 2009-12-31
I tried it with a friend with the server connected directly into the Optimum modem. Still didn't work. It has to be an internal problem with the server. Someone please, I desperately need help.

---

### Post by lisati on 2009-12-31
> **Hovercat said:**
> *Optimum, hosted by retards, but gotta love that speed.* I got their boost service, I made sure Port 80 was open.



What does the listen port need to be? 443?

It's usually 80 or 81, but if your ISP is blocking it, you'll need to contact them.

edit: Hello, someone just went to my website from this thread! (Well, about 6 minutes ago......, 10 minutes after I originally posted this) Found out by checking my server's logs......
edit 2: it wasn't the OP, it was someone in the UK

---

### Post by rustutzman on 2009-12-31
I see you talking about port forwarding. For my setup I used the dmz function of the router. That makes your machine visible by ip or domain to everyone outside your lan. Just trying to offer suggestions.

Russ

---

### Post by mechro on 2009-12-31
> **lisati said:**
> 

edit: Hello, someone just went to my website from this thread! (Well, about 6 minutes ago......, 10 minutes after I originally posted this) Found out by checking my server's logs......
edit 2: it wasn't the OP, it was someone in the UK

Yes, Hello, Happy New Year! :D

---

### Post by garyed on 2009-12-31
My IP ( Verizon) also blocks port 80 so I port forwarded port 8080 & 
it works. To be sure they're still not blocking port 80 you could forward 8080 & see if you have the same problem. That might eliminate some possibilities.

---

### Post by lisati on 2009-12-31
> **mechro said:**
> Yes, Hello, Happy New Year! :D

:) An opera user?

---

### Post by mechro on 2010-01-01
> **lisati said:**
> :) An opera user?

Correct. Your site stats are working perfectly :)

---

