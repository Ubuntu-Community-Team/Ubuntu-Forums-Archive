---
title: "Totally confused about VPN"
date: 2007-01-11
forum: Networking &amp; Wireless
---

### Post by kidders on 2007-01-11
Hi everyone,

I've always tried to steer clear of VPNs, because the mechanics of the things always confuse me. :-( Unfortunately, now I *need* one. The wrinkle is that traffic gets NAT-ed twice on one side of the connection. Basically, I have...

**192.168.5.0/24 <-> 192.168.1.0/24 <-> (Internet) <-> 10.0.0.0/8**

On one side, I have OSX, and on the other, I have a LAN running Gentoo & Ubuntu. Tbh, I really don't care where the VPN server is, although it would make the most sense for it to be in 192.168.5.0/24, on my Ubuntu box. The one place it *can't* be is in 192.168.1.0/24, and (just to make me even more confused), I would _realllly_ prefer not to make the machine performing the NAT in 192.168.5.0/24 the VPN server. (Afaik, that would make things a little easier.)

I tried running a VPN service on my Mac [SIZE="1"](at 10.0.0.2, behind a cable modem bridged with an Airtunes gizmo)[/SIZE] and connecting to it from my Ubuntu box [SIZE="1"](at 192.168.5.114, routed to 192.168.1.0/24 via a Gentoo box and then onto the internet by a dumb ADSL modem/router)[/SIZE], which seemed the easiest choice, but I couldn't wrap my head around all the firewalls & address translation & silly screwing around ... so I couldn't figure out where to look for problems.

Could someone pleeeeeeease take me through making this work. It's making me feel so stupid! :confused: Bonus points for suggestions that don't involve an X server.

(Even if you can't help, thanks for reading all this!)

---

### Post by linuchsan on 2007-01-11
what vpn package are you using?

---

### Post by kidders on 2007-01-11
> **linuchsan said:**
> what vpn package are you using?Oops... it was sorta dumb of me to leave that out. I've experimented with openswan on Ubuntu... but I haven't a clue what OSX's VPN architecture is based on.

---

### Post by linuchsan on 2007-01-11
Have you tried openvpn, easy to setup and compatible with mac osx.

---

### Post by kidders on 2007-01-12
I'll give it a go, thanks. I read somewhere that not every VPN app works when you NAT it twice. Is that even true?

---

### Post by koenn on 2007-01-12
> **kidders said:**
> I'll give it a go, thanks. I read somewhere that not every VPN app works when you NAT it twice. Is that even true?
yes. even if you NAT them only once. I believe especially IPsec -based vpn's suffer have trouble with it because they encrypt the source addresses, so it can't be NATed, or the NATing changes a or checksum because the addresses get modified or something - I don't remember exactly. 

OpenVPN doesn't suffer from that, though.

---

### Post by kidders on 2007-01-12
Hey again,

Sticking with OpenVPN both server-side and client-side was the key! :-) It just works. (I was expecting to have to put you through walking me through it step by step :-? )

I guess my only question now is how safe it is.

Thanks for your suggestion ... you were a big help.

---

