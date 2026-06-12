---
title: "static ip at work"
date: 2006-08-08
forum: Networking &amp; Wireless
---

### Post by ndaman on 2006-08-08
I am running ubuntu dapper and dual booting with windows xp, here at work I have to use a static ip address, which works when manually configured in windows, but I can't get it to work in ubuntu, is there something else I have to do to configure my linux static ip to get it to work? Thanks in advance.
~Nick

---

### Post by jeff_ on 2006-08-08
Well what have you done so far to try and get it to work? You can assign a static IP under System > Administration > Networking. If you have done this then could you please post the output of ifconfig.

---

### Post by ndaman on 2006-08-08
thanks for the reply, sorry for not mentioning that, I've already tried setting that up, I pasted my ip address, subnet mask, default gateway, and dns server exactly as they were in windows, since windows is the only one with working internet, it might take a little while for me to get the ifconfig data :P.

---

### Post by ndaman on 2006-08-08
here's the output from ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:0F:1F:17:5B:F6
          inet addr:134.121.73.206  Bcast:134.121.73.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:1fff:fe17:5bf6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15512 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2692 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1659359 (1.5 MiB)  TX bytes:172504 (168.4 KiB)
          Interrupt:177

p.s. the one interesting thing I found in the windows configuration that I don't know how to do in linux is a "connection-specific dns suffix", could that be important? how would I set that up in ubuntu?

---

### Post by jeff_ on 2006-08-08
Could you post your windows configuration info (ip, mask, default gateway, etc)? Also are you on a network at work or directly connected to the internet? If you are on a network can you ping your gateway?

---

### Post by ndaman on 2006-08-08
I think I'm on a network, to ping the gateway do I just ping the ip address for the default gateway? I did that, but I'm not sure what data you'd want from it, anyway, the windows configuration:
 ip: 134.121.73.206
 mask: 255.255.255.0
 default gateway: 134.121.79.254
 dns servers: 134.121.2.54
              134.121.80.36
 connection-specific dns suffix: mme.wsu.edu

---

### Post by jeff_ on 2006-08-08
Yeah, just try and ping 134.121.79.254 from linux. You should either get a bunch of replies (Cntrl-C to stop) or a bunch of destination unreachable messages. Also make sure that you have your gateway in the network settings on linux.

---

### Post by ndaman on 2006-08-08
That was kindof odd, I didn't get a bunch of anything, now that I'm in windows again, I forgot the exact message I got, I'll go back and do it again, but it was something about there was no network connection and then it quit, it didn't say destination unreachable a bunch of times.

*the error message in linux said "connection: network unreachable"

---

### Post by ndaman on 2006-08-09
is there any way to set this "connection-specific dns suffix" in linux ?

---

