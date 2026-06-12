---
title: "netgear stora disk routed through ubuntu computer"
date: 2011-02-08
forum: New to Ubuntu
---

### Post by julec87 on 2011-02-08
So.

Im trying to set up a Netgear Stora disk on my system. The problem is that i do not have physical access to the wireless router in my network, so i can't connect the nas disk directly to it. My plan was to connect the Stora to my computers Ethernet port and use my computers wireless card to connect the Stora to the Internet, which i to some degree have accomplished. The Stora connects to the Internet, as i can check and upgrade the firmware on it, but when i try to connect to it remotely it just keeps loading for ages. Connecting locally is no problem both using the web interface and through FTP.

Here's my setup so far

[LIST]
[*]speedtouch modem. internal ip: 10.0.0.1
[*]linksys wrt54gl router. external ip 10.0.0.2, internal ip: 192.168.1.1
[*]desktop computer connected to the router through wireless (wlan0) with static ip: 192.168.1.2
[*]the computers Ethernet card (eth0) has ip 10.42.43.1 and ipv4 method is set to "shared to other computers"
[*]the Stora has static ip 10.42.43.2 and has ftp enabled.
[/LIST]
netgears "port fowarding tester" [http://support.stora.hipserv.com/en/router/testportforward.html](http://support.stora.hipserv.com/en/router/testportforward.html) says that all four ports (21, 22, 443, 80) are blocked. This might not account for the fact that the Stora is connected through my computer and not directly to my router though?
i've messed around with ufw, firestarter, router and modem settings but can't seem to connect to the Stora remotely. There has to be some connection though since it accepts username and password and starts loading...? make any sense?

So what am asking for at first is just some pointers to which steps that is required for this setup? anyone have an idea what i've missed? i'll post some more info from what i've done so far if that can help, but think i'll just leave it at this for now.

I'm not too experienced with any of this, so any tips can help. I've been trying to find a solution in the forum but can't seem to figure it out.

Appreciate any help i can get. 
Cheers

---

### Post by patrick281981 on 2011-02-10
Hi, if you really want to play with the router you need to connect to the router via Telnet as web based setup is always limited in their options .. as I wanted to setup other connections and secure my old Netgear router I had to connect to is via Telnet ..

It's text based but very powerful read documentation of the router on how to enable Telnet connections..

Regards..

---

### Post by julec87 on 2011-02-11
Dont really see how the router is the problem here though... The nas disk is connected with a ethernet cable to my computer, and my computer is in turn connected with wireless to a linksys router. I assumed that if i managed to use MASQUERADING in iptables i could forward packages from/to the nas disk to the internet through my computer. The linksys router is working as it should, but i dont know how i can get packages sent from the internet (remote connection through [www.mystora.com](www.mystora.com)) to reach the Stora.

My theory is that the Storas ip (and not my computer which should be the destination?) is registered with netgear, and that is the ip used when a remote connection is attemted through [www.mystora.com](www.mystora.com). So even though packages sent from the Stora and replies to those packages are routet correctly, packages sent using [www.mystora.com](www.mystora.com) will not reach the Stora.

hehe hope that wasn't written too confusing.

---

