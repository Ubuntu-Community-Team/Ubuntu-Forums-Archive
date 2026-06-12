---
title: "Am I being attacked?"
date: 2014-03-26
forum: Networking &amp; Wireless
---

### Post by speed32219 on 2014-03-26
Sometimes my video server will slow down when I am watching a movie.  It goes into buffering, so I checked dmesg and I am getting a tremendous amounts of IP's address trying different ports.  Here is a snippet of the log.

```

[Wed Mar 26 20:05:57 2014] [UFW BLOCK] IN=eth1 OUT= MAC=00:1f:d0:5c:aa:02:00:26:50:cb:ad:81:08:00 SRC=84.85.83.119 DST=192.168.1.118 LEN=134 TOS=0x00 PREC=0x00 TTL=107 ID=5107 PROTO=UDP SPT=41435 DPT=50126 LEN=114
[Wed Mar 26 20:06:15 2014] [UFW BLOCK] IN=eth1 OUT= MAC=00:1f:d0:5c:aa:02:00:26:50:cb:ad:81:08:00 SRC=177.106.99.15 DST=192.168.1.118 LEN=123 TOS=0x00 PREC=0x00 TTL=112 ID=2976 PROTO=UDP SPT=27774 DPT=50126 LEN=103
[Wed Mar 26 20:06:34 2014] [UFW BLOCK] IN=eth1 OUT= MAC=00:1f:d0:5c:aa:02:00:26:50:cb:ad:81:08:00 SRC=50.97.88.70 DST=192.168.1.118 LEN=93 TOS=0x00 PREC=0x00 TTL=112 ID=4820 PROTO=UDP SPT=15010 DPT=50126 LEN=73
[Wed Mar 26 20:06:53 2014] [UFW BLOCK] IN=eth1 OUT= MAC=00:1f:d0:5c:aa:02:00:26:50:cb:ad:81:08:00 SRC=117.206.59.39 DST=192.168.1.118 LEN=129 TOS=0x08 PREC=0x00 TTL=100 ID=28170 PROTO=UDP SPT=16815 DPT=50126 LEN=109
[Wed Mar 26 20:07:13 2014] [UFW BLOCK] IN=eth1 OUT= MAC=00:1f:d0:5c:aa:02:00:26:50:cb:ad:81:08:00 SRC=117.206.59.39 DST=192.168.1.118 LEN=129 TOS=0x08 PREC=0x00 TTL=100 ID=28175 PROTO=UDP SPT=16815 DPT=50126 LEN=109
```

If so what can I do to stop it?  I rebooted the GW to get a different ip address, but it has not made a difference yet.  I checked some of the ip address and they are from the US and  all over the world it seems.  It keeps filling the log with these errors.

Any help would be appreciated.

---

### Post by TheFu on 2014-03-26
Yes, every system on the internet is attacked constantly. That is the way of the world.
If you want to reduce this, put a hardware firewall in front of the system and block the ports.

---

### Post by speed32219 on 2014-03-26
Thank you for the heads up.  I have checked the dmesg logs every so often, for Raid or hardware  errors but I never seen this in the logs before that I can remember.  I was curious as to why it is currently happening.  I just recently left a monthly subscription usenet service and I was wondering if that may have something to do with it.

---

### Post by TheFu on 2014-03-27
> **speed32219 said:**
> Thank you for the heads up.  I have checked the dmesg logs every so often, for Raid or hardware  errors but I never seen this in the logs before that I can remember.  I was curious as to why it is currently happening.  I just recently left a monthly subscription usenet service and I was wondering if that may have something to do with it.

Usenet is pull, not push.  If you use BT, then that is the reason. Put a hardware firewall/router in front and block everything. That is what those devices are for.  How are those getting through the NAT router?  Is that port open or did your client request packets?


Legally, in the USA, BT is **very** different from usenet.  I don't know of any BT client that is safe to use - forget the encryption and other claims about security. If you BT in your home country AND it is illegal there, I think you are crazy.  Get a VPS in eastern Europe, do all the BT there and setup openVPN on that VPS that can be accessed from your home to transfer files securely.

---

### Post by SeijiSensei on 2014-03-27
All those are attempts to connect to UDP port 50126.  That port ring a bell?

Are you using DHT discovery in a BitTorrent client?  [DHT]("http://www.bittorrent.org/beps/bep_0005.html") uses UDP to discover hosts.

---

### Post by speed32219 on 2014-03-31
Thank you for the information.  I am going to see if I can block those ports using my ATT gateway.  I have no Blue Tooth enabled devices on the network.  @TehFu yes it is a pull, just concerned that I noticed this traffic after I left usenet.  I have nothing in that port 5000 port range that I am aware of.  Thank you again for the heads up. Come to think of it I have the ATT gateway and attached to it I have another GW running DD-WRT for N connectivity to the other wireless devices and except for this PC all information has to pass through it to get to the wired and wireless network.  I will setup a block on both and look at the DD-WRT firewall otpions, should be more robust than the ATT GW.

**EDIT**  Turned on strict udp control and removed some network protocols I do not use for inbound access and I have not had an intrusion in the past 30 minutes.  Thank you once again for help with this issue.  Checked to make sure all my inbound and outbound network traffic works and I am good to go.

---

### Post by chili555 on 2014-03-31
>  I have no Blue Tooth enabled devices on the network. IS BT referring to bluetooth or bittorrent, I ask somewhat rhetorically.

---

