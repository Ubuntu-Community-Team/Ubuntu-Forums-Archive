---
title: "deluge and network management"
date: 2009-09-12
forum: New to Ubuntu
---

### Post by JohnsShadow on 2009-09-12
i have my router setup as DHCP 
im using deluge 1.1.9
im trying to seed this torrent
[http://www.mininova.org/tor/2943437](http://www.mininova.org/tor/2943437)
for some reason deluge has stoped seeding files

i think it may have somthing to do with my network connection driver
my driver is 8139too 

Weird: everytime i turn my computer off the network lite on my work group switch stays on

i also use random ports in deluge, my other theory is that some of them are interfearing with my firewall (i use firestarter and i block a LOT of weird stuff)

stuff i block:
SSH 22
Telnet 23
Back orifice 2K 54321
DNS 53
Samba (SMB) 137-139 445
pop3 110
sun-RCP portmap 32769
NTP 123
NNTP 119
IMAP 143
NFS 111 2049
Wipid 1300
Traceroute 33548
FTP 20-21
WebAdmin 10000
SSDP 1900

am i blocking too much or not enough or the wrong things?

im gunna be honest i just blocked stuff that poped up in my firewall as serious threats

am i blocking somthing that bitorrent needs to operate?
if so why can i still download? and why can i upload for a small section of time but not for weeks?

is this my ISP's doing? how can i stop it?

---

### Post by misfitpierce on 2009-09-12
Ummm under preferences are you blocking ICMP? That messes up torrent seeding etc usually.

---

### Post by JohnsShadow on 2009-09-12
i am not blocking ICMP (what port is that?)

in deluge prefrences

i have been playing with the network extras UNpN, NAT-PMP, Peer-Exchange, LSD, DHT

ive tryed all kinds of diffrent combinations to no avail

thanks for replying,

need any info i havent provided? just ask

---

