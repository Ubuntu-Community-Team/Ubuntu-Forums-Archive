---
title: "super slow connection with vpnc to my office network"
date: 2016-03-30
forum: Networking &amp; Wireless
---

### Post by borisb2 on 2016-03-30
hi .. first post here :)

I recently installed kubuntu 14.04 on my lenovo W530 laptop. Now I want to connect with my office-network. I was reading because I am using a cisco-based router in my office (fritzbox) I could easily install the vpnc-plugin, setup a new vpn user at the router and just transfer the vpn-settings into the network-manager (like I am using it successfully with my iPad and the fileBrowser app).

Done that - when connecting to the vpn kubuntu says "successfully activated vpn.." . but I can't ping to anything in the network from outside. When I'm IN my office-network ping to the NAS for example works .. and I guess mount would work too. But when I'm outside - nothing is reachable.

EDIT: ping and connecting with dolphin (either nfs://ip-to-NAS or smb://ip-to-NAS) now works but super slow, close to 0kb/s
EDIT: I can see the files/folders but  transfering a file is more or less impossible.

Whats wrong there?

Thanks for any help - I'm still new to linux

---

### Post by borisb2 on 2016-03-30
getting closer.

A friend told me that ping wouldnt be needed anyway. I should use smb://192.xxx in fileManager instead to access my files (where 192.xxx is the IP of my NAS).

So when I'm inside the network smb://.. works indeed, I can connect to the NAS. But when I enable the vpn (as a test), the connection fails again - same as being outside of the network. Dolphin is searching for folders and fails with "timeout on server"

So I guess the "blocking" is related to the settings in the vpnc-connection?

---

### Post by wyliecoyoteuk on 2016-03-30
Try traceroute <ipaddress>
paste the results here

---

### Post by borisb2 on 2016-03-30
traceroute to 191.168.178.45 (191.168.178.45), 30 hops max, 60 byte packets
 1  81.210.141.74 (81.210.141.74)  8.828 ms  11.662 ms  11.096 ms
 2  81.210.141.73 (81.210.141.73)  13.475 ms  13.407 ms  12.825 ms
 3  84.116.197.245 (84.116.197.245)  12.226 ms  12.051 ms  11.925 ms
 4  de-fra03b-ri1-ae5-0.aorta.net (84.116.133.118)  13.236 ms  14.548 ms de-fra03b-ri1-ae12-0.aorta.net (84.116.133.97)  14.065 ms
 5  213.46.179.130.aorta.net (213.46.179.130)  14.472 ms  14.373 ms  14.329 ms
 6  ae7.sanpaolo8.spa.seabone.net (195.22.219.17)  243.296 ms ae6.sanpaolo8.spa.seabone.net (195.22.219.3)  237.930 ms  237.951 ms
 7  ae7.sanpaolo8.spa.seabone.net (195.22.219.17)  239.195 ms  241.344 ms ae6.sanpaolo8.spa.seabone.net (195.22.219.3)  237.097 ms
 8  149.3.181.18 (149.3.181.18)  241.695 ms  238.068 ms  238.047 ms
 9  * * *
10  * * *
11  * * *
12  * * *
13  45.178.168.191.isp.timbrasil.com.br (191.168.178.45)  3437.376 ms  3406.299 ms  3455.646 ms

---

### Post by slickymaster on 2016-03-30
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by borisb2 on 2016-03-30
well it "sort of" works, but ridiculously slow. I managed to copy a 1.8kb file in roughly 20sec .. in dolphin over nfs://ip-address as well as smb://ip-address. Copying a 4Mb file I canceled after a while with 0kb/s ..but at least I can see the files from the NAS

are these slow speeds due to permission settings with the vpnc-config? or firewall?

---

### Post by SeijiSensei on 2016-03-30
> **borisb2 said:**
> are these slow speeds due to permission settings with the vpnc-config? or firewall?

```

8 149.3.181.18 (149.3.181.18) 241.695 ms 238.068 ms 238.047 ms
9 * * *
10 * * *
11 * * *
12 * * *
13 45.178.168.191.isp.timbrasil.com.br (191.168.178.45) 3437.376 ms 3406.299 ms 3455.646 ms 

```

It doesn't look that way to me.  The biggest problem is the connection to the last hop, with ping times in the 3.5 second range.  Connections 9-12 do not support ICMP requests, so you just get asterisks for those.  Thus it's hard to know whether the delay happens on one of them, or between 191.168.178.45 and its upstream router.  

What if you have no VPN running and just ping the router at the office from your machine?  What kind of times do you see then?

---

### Post by borisb2 on 2016-03-30
> **SeijiSensei said:**
> 
What if you have no VPN running and just ping the router at the office from your machine?  What kind of times do you see then?
you mean the ip from the router (which is set to 192.168.178.1) or the IP it gets from the IS-provider? .. the latter I guess

> **SeijiSensei said:**
> ..  Thus it's hard to know whether the delay  happens on one of them, or between 191.168.178.45 and its upstream  router.  
191.168.178.45 in the trace-route list was the NAS.

So you're saying since I do got a connection its not the settings in the vpnc-config but a delay somewhere. What about setting in the router (is there anything that could cause the slowdowns) .. but as mentioned, I did setup another vpn-user on the router for the iPad quite similar and this works without any issues (connceting with cisco fileBrowser app)

---

### Post by wyliecoyoteuk on 2016-03-30
191.168.178.45
is an internet address, not a private network address.
What is your office network address range?

---

### Post by borisb2 on 2016-03-30
uups .. sorry.

Well, just one digit was different .. hmm, how often does that happen

---

### Post by borisb2 on 2016-03-30
so... ping without vpn to (dynamic) IP used by the router gives me this:
24 packets transmitted, 24 received, 0% packet loss, time 23034ms
rtt min/avg/max/mdev = 25.024/30.538/73.045/9.494 ms

tested again vpn both with smb:// and nfs;// (in dolphin) to get access to the files on my office-NAS. I can see the files/folders but transfering a file is super, super slow, close to 0kb/s.

No chance that its related to some settings in kubuntu? firewall? vpnc settings? I tested also again: similar vpn-setup with the ipad in the same external wireless works flawless:
opening a folder with several files and subfolders takes about 1-2 sec with the ipad and 10-15sec with the laptop, sometimes I got timeout if it takes too long ( I guess >20s)

---

### Post by wyliecoyoteuk on 2016-03-30
Well assuming that you used 192.168 (and not 191.168 which is a public address range), the routing would seem to be the trouble.
Why the routing would be different for Linux is not obvious.
Try a tracert from the ipad and compare them.
By the way disclosing private addresses which are not visible on the internet anyway is not much of a risk.

---

### Post by wyliecoyoteuk on 2016-03-30
Just had a thought. You are only trying to connect one device at a time aren't you?

---

### Post by borisb2 on 2016-03-30
of course only one connection at a time. :) the idea with the ipad was only to show the similar setups

I continue investigating. Its just so annoying when all the tutorials say how easy it now should be

---

### Post by wyliecoyoteuk on 2016-03-30
I sometimes connect my laptop and forget to close the VPN link on my desktop or phone first, causes all sorts of problems.

---

### Post by borisb2 on 2016-03-31
ok, but in this case the ipad wont be the problem I suppose. Problems were there form the beginning setting up the vpnc

---

### Post by borisb2 on 2016-03-31
think I solved it ..without solving it.

I connected into a completely different wlan-network - and voila, everything works as expected. More or less acceptable transfer-speeds.

So it appears that my cable-provider and "its way" into the internet caused the slow down. No idea why the ipad in the same network wasnt affected.

---

