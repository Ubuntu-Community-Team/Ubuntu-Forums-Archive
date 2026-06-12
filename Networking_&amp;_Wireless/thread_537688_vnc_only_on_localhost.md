---
title: "vnc: only on localhost?"
date: 2007-08-29
forum: Networking &amp; Wireless
---

### Post by Jonne on 2007-08-29
Hi people,

I've set up vnc (vino, using the gui) on my box (Feisty) at home, and I want to make sure it can only be accessed from localhost. I set up an ssh tunnel to forward port 5900, so when i vnc into the box it's over ssh, which is more secure.

My worry is when I connect my laptop to a LAN I can't trust, or if I have to connect it to the web directly. So how can I force vnc to only allow connections from localhost? I couldn't find anything for that in /etc/vnc.conf.

My computer is behind NAT, so I don't have to worry about anyone trying to guess my password from the internet (only port 22 is open, and i have fail2ban running so people can't keep guessing). I just don't want to have too many services open...

---

### Post by sonofusion82 on 2007-08-29
it depends on which VNC server that you are using.

for x11vnc, you can use the -listen localhost switch

if not, as usual, setup you firewall to block all incoming connections exception from ssh port 22.

for me, I prefer to tunnel my vnc connections through openvpn.

---

### Post by Jonne on 2007-08-29
The VNC server I'm using is Vino (I want to stick to what Ubuntu recommends). I guess it can't hurt to play with iptables a bit to block everything except ssh, smb and 7347 (which I use for gnutella). It just seems odd that there seems to be no way of telling vino who you're going to allow, and who you're not letting in. Especially since vnc uses just a password for authentication (not even a login+pass combo, or a key pair or something).

---

