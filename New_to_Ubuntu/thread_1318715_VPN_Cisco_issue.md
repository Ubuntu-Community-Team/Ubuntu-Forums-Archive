---
title: "VPN Cisco issue"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by RoRoRed on 2009-11-07
Hey out there,

I am brand new to Linux and before I say anything  ubuntu is pretty nice;

That being said; I try to figure out how to establish my VPN connection to my University-Network and I have no clue how 
 
1) so I tried to import the vpn.pcf into the linux build-in vpn connection manager
 as a result the message is displayed "TCP tunneling not supported" 
 and when I try to connect anyways a dialouge appears asking for keyring
  (don't know what that is?)
 thus I press "allow it" with the result that another dialouge appears which wants to have a password for authentication.

If anyone can explain to me what to do that would be really nice,


2) So after having no clue what to do about the first problem I decided to use the "Shrew Soft VPN connect" - thingy; so I got the shrew config file imported it got connected to the University Network; but as I wanted to use firefox, it did not find anything anymore; don't know either where the problem is supposed to be.

Again if anyone can explain to me what to do that would be really really nice,


thanks in advance
Ro

---

### Post by Benic on 2009-11-11
First question: what version of Ubuntu did you install?

If it's 9.10, you should check this [_page_]("http://ilapstech.blogspot.com/2009/09/cisco-vpn-client-on-karmic-koala.html") and follow the instructions.  

If it's 9.04, 8.10 or 8.04, check this [_page_]("http://www.blog.arun-prabha.com/2008/05/01/cisco-vpn-installation-issue-with-ubuntu-804-hardy-heron/") instead.

The next step will be to set up you firewall, using firestarter or guarddog, whatever you choose, just tell me which one and I will help you.

---

### Post by RoRoRed on 2009-11-11
Version: 9.10 

^_^

thx

---

### Post by Benic on 2009-11-13
Ok, then you need to set up the firewall. What you need is an interface such as Firestarter or Guarddog to tweak the settings (the firewall is already running, but changing the settings manually is more complicated, so you need an interface that will make things easy). Firestarter is quite simple, but I prefer Guarddog. 

With Guarddog, you need to make those changes (in Advanced tab):
Allow UDP port 500 and 10000
TCP port 10000
Tick the TCP clock option

Don't forget to allow those in the internet and local zone protocoles.

In protocoles:
http, https, and DNS (to use internet)
ftp (if needed)
NTP time synchro
Ping
PPTP
IMAP or POP and SMTP (to use mail if needed)
NFS

I did the same for both internet and local zone, because I think you need both to use the internet with the vpn. Maybe I allow too many things. I don't know, I'm far from being an expert. But at least it works for me.

For Firestarter I'm not sure. It has never worked for and if you want to use it, you can browse the forums for some help because I don't know much about it.

---

### Post by RoRoRed on 2009-11-13
new issue after doing as described.

I can connect via vpn,

but if I try to open firefox linux freezes 
(and I mean a windows freeze/crash/nothing goes anymore bluescreen-like-crash w/o the bluescreen but a frozen desktop)

That kind of worries me

---

### Post by ukripper on 2009-11-13
Here is my guide if that helps - [http://ubuntuforums.org/showthread.php?t=1227209](http://ubuntuforums.org/showthread.php?t=1227209)

---

### Post by RoRoRed on 2009-11-14
is there any way to enable the tcp tunneling in the already build in vpn-client?

---

