---
title: "Setup Ubuntu as PPTP VPN Server"
date: 2008-07-30
forum: Networking &amp; Wireless
---

### Post by crazy_cat on 2008-07-30
I'm trying to setup a PPTP VPN to my Ubuntu box at home.  I started out with commands but am now editing options/config thru Webmin.  I can VPN to my Ubuntu server and access resources on that server, but i can't access the LAN or WAN (ie other computers on network or internet).

so basically, it works, but only half way.  and i've tried connecting thru my Mac and PC.

I think the problem may be in my netmask.  In Webmin, under routing and gateways, the netmask for my ppp0 interface is different than for the rest of the network.  (255.255.255.255 instead of 255.255.255.0).

Any suggestions?

Thanks!

---

### Post by crazy_cat on 2008-07-30
here are screen shots of my Wedmin settings.

[IMG]http://dallasfirstassembly.org/images/pptp1.png[/IMG]
-------------------------------------------------
[IMG]http://dallasfirstassembly.org/images/pptp2.png[/IMG]
-------------------------------------------------
[IMG]http://dallasfirstassembly.org/images/pptp3.png[/IMG]

---

### Post by webmaster_ph on 2008-08-13
> **crazy_cat said:**
> I'm trying to setup a PPTP VPN to my Ubuntu box at home.  I started out with commands but am now editing options/config thru Webmin.  I can VPN to my Ubuntu server and access resources on that server, but i can't access the LAN or WAN (ie other computers on network or internet).

so basically, it works, but only half way.  and i've tried connecting thru my Mac and PC.

I think the problem may be in my netmask.  In Webmin, under routing and gateways, the netmask for my ppp0 interface is different than for the rest of the network.  (255.255.255.255 instead of 255.255.255.0).

Any suggestions?

Thanks!

yeah, i was wondering why the netmask is different. anybody can enlighten us on this?

on my part, i can connect but cannot access the network resources like nfs shares, etc.

see my post here:

[Can Connect to VPN (PPTP) But Cannot Access Network Resources]("http://ubuntuforums.org/showthread.php?t=887062")

i wish somebody can help us.

---

### Post by crazy_cat on 2008-08-27
bump.  still trying to resolve this thing.

---

### Post by RayVad on 2008-12-24
What about this:

cat /proc/sys/net/ipv4/ip_forward

Does it return 0 or 1?

If it is returning 0, then do
echo 1 > /proc/sys/net/ipv4/ip_forward 
and see what it does.

To make it permanent edit /etc/sysctl.conf
and uncomment the line:
 net.ipv4.ip_forward=1



About the netmask, it is correct!

---

### Post by Daggo on 2009-01-21
Could someone please explain more in depth on how to configure your routing table after logging into my vpn server as it was stated on another thread?
[http://ubuntuforums.org/showthread.php?t=887062](http://ubuntuforums.org/showthread.php?t=887062)

I have done all the above and have the ability to log into my server with a client but still unable to see any other devices on the network. Do I need to create another active route?

I have attached a webmin screen of my route table on the server.

---

### Post by codywohlers on 2009-06-30
> **RayVad said:**
> 
cat /proc/sys/net/ipv4/ip_forward

Does it return 0 or 1?

If it is returning 0, then do
echo 1 > /proc/sys/net/ipv4/ip_forward 
and see what it does.

To make it permanent edit /etc/sysctl.conf
and uncomment the line:
 net.ipv4.ip_forward=1


Thank-you!  It solved my problem.:p  so simple in hindsight...

---

### Post by lel4kis on 2009-09-12
thank you [U]RayVad,
it helping me a lots
:KS

cheers,

 [/U]

---

### Post by saeed144 on 2011-08-01
I have set up PPTP VPN server on ubuntu.
But accounts are open for concurrent simultaneous connections. means there can be many users using one account at the time.
i need to limit that to one user at the time.
anybody knows how it can be done?

---

