---
title: "Ubuntu 16.04.4 can't establish ethernet connection"
date: 2018-03-06
forum: Networking &amp; Wireless
---

### Post by kiaat on 2018-03-06
tl;dr Ethernet Connection can't be established. Don't own a Wireless-Adapter. Network Information pasted here: [https://pastebin.ubuntu.com/p/NwJp6MpCHV/](https://pastebin.ubuntu.com/p/NwJp6MpCHV/)

I formatted my old computer and flashed Ubuntu on it. After installation was done I did "*sudo apt update"* and such. Everything went fine. The next evening, I turned my pc on, but the internet connection was lost. Now it's constantly trying to reconnect but after a while it shows Ethernet Connection lost, stays off and then tries again.

Currently on my new PC which uses Windows. No internet problems, neither does my mobile phone have any.

---

### Post by TheFu on 2018-03-06
Welcome to the forums.

That is a wireless troubleshooting script.  

Thanks for saying that other systems are working. That means the issue is in the router or cables or on the linux machine.

RTL8101/2/6E PCI Express is what lspci says you have.
Using the r8169 driver.  Sometimes this driver is a problem, but we aren't there yet.

Basic troubleshooting first. Run some commands, in order, and show both the commands AND the output here.```

$ route -n
$ ifconfig
$ ping {insert-the-router-IP}
$ ping 8.8.8.8 # this is a well-known IP 
$ ping google.com # this will check if DNS is working
```

Here's what those commands tell us:

route should say if there is any connection to the router.  If that doesn't have an IP, then it is either a driver issue, cable issue, or router port issue. It would be easiest to just swap the Windows ethernet cable with the Ubuntu computer.  

DHCP could be an issue. You didn't mention if a DHCP server or static IP was being used.

If the ping to the router works, that means it isn't a physical problem (most likely). It also isn't a driver issue.

If the ping to 8.8.8.8 works, that means everything **is** working, except, perhaps, DNS.  DNS issues seem like the entire network is broken, but really just the "name to telephone number" lookup is failing.


please,please use 'code tags' like i did above. This makes the output readable.  It is much harder to read otherwise.

---

### Post by kiaat on 2018-03-06
> **TheFu said:**
> 
[...] Basic troubleshooting first. [...]


Maybe I didn't mention it clearly enough, but my old pc (with Ubuntu) tries to connect but fails every attempt. Therefore never having any internet connection whatsoever. 

Here are the outputs. 

```

$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


$ ifconfig
enp1s0    Link encap:Ethernet  HWaddr 00:19:66:85:07:e0  
          inet6 addr: fe80::2551:16c4:b215:67e1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:137 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:23927 (23.9 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:996 errors:0 dropped:0 overruns:0 frame:0
          TX packets:996 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:73840 (73.8 KB)  TX bytes:73840 (73.8 KB)


$ ping 192.168.2.1
connect: Network is unreachable


$ ping 8.8.8.8
connect: Network is unreachable


$ ping google.com
ping: unknown host google.com

```

---

### Post by TheFu on 2018-03-06
Internet connectivity doesn't necessarily mean no LAN connectivity. I didn't assume Internet, but it is often the situation that systems have LAN.

Try a different cable?
Try connecting the cable to a different port on the router/switch?

Where should the ubuntu machine get an IP?  Could that pool be limited enough to prevent any new IPs being handed out?

I'm trying to avoid "the driver" issue. It is a hassle to fix and isn't always the problem.  You can google for solutions "ubuntu {driver} {realtek card}" to see what issues and solutions other people have solved.

Since you did an update/upgrade, can you look through your logs of that to see what packages might have been changed that are related to drivers and networking?  I keep logs, but most people don't unless the system does it automatically. I think it might, but don't know where those logs might be ... /var/log/apt/ looks promising on my systems.

That's all I got for ideas. Sorry.

---

### Post by kiaat on 2018-03-06
> **TheFu said:**
> [...] Try connecting the cable to a different port on the router/switch? [...]

My router has two LAN-Connections (LAN1 and LAN2). My old computer is connected via lan2 while my new one is at lan1. I switched cables and switched connections and the conclusion is that LAN2 (connection which my old computer was in) is strangely not working.

So, to sum it up, it's my router that's behaving weird. 


> **TheFu said:**
> [...] That's all I got for ideas. Sorry.


I should sorry for taking your time to troubleshoot a problem that has nothing to do with Ubuntu. And I ought to say thanks that you brought up all those ideas.

---

### Post by TheFu on 2018-03-06
The problem could have been something else. Without working through the possible issues, we'd never know.
You certainly aren't the only person here that had a bad switch/router port. It has happened to me before too. I've had entire switches burn out before.

Really just happy this can be solved.  I'm not certain how interested you are in having a router that will actually be maintainable for years, unlike most commercially sold routers for "consumers", but ... [https://arstechnica.com/gadgets/2016/01/numbers-dont-lie-its-time-to-build-your-own-router/](https://arstechnica.com/gadgets/2016/01/numbers-dont-lie-its-time-to-build-your-own-router/) - I wasn't onboard with a Linux-based router before talking with Jim at a conference.  I use a  cheapo "home" router for some internal LAN stuff, but wouldn't trust it facing the internet.

---

### Post by kiaat on 2018-03-06
Well, the router came with our new internet connection/internet contract and it's rented by contract. A simple replacement should be possible. 
It's a router which supports IPVoice. The company that owns the ethernet cables underground upgraded to IPVoice, thus a change of routers was (sadly) needed. Some google searches show that it can happen, that one of the LAN-Ports are suddenly getting broken.

---

