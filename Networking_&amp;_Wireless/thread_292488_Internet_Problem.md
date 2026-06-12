---
title: "Internet Problem"
date: 2006-11-03
forum: Networking &amp; Wireless
---

### Post by koryo88 on 2006-11-03
I'm a newbie to linux and I'm trying to set up a internet connection on Ubuntu. 

The Network settings shows my ethernet card as active but I can't ping any sites or browse out to any. We have cable and I was able to, on a previous ubuntu install(hd died), to connect upon plugging the network cable in. I've tried everything I can think of and any suggestions would be appreciated.

---

### Post by amohanty on 2006-11-04
Ok few questions:
1. Do you use a router or directly connect to the cable modem?
2. If you use a router, do you use dhcp?
3. Can you ping your router?
4. Post the output of **ifconfig**

AM

---

### Post by koryo88 on 2006-11-05
I connect directly to the cable modem.

Here's the ifconfig output:

eth0     Link encap::Ethernet  HWaddr 00:03:47:E7:6E:F2
         inet6 addr: fe80::203:47ff:fee7:6ef2/64 Scope:Link
         UP BROADCAST RUNNING MULTICAST  MTU:1500 Metric:1
         RX packets:1992 errors:0 dropped:0 overruns:0 frame:0
         TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqeuelen:1000
         RX bytes:120648 (117.8 KiB)  TX bytes:2178 (2.1 KiB

lo      Link encap:Local Loopback
        inet addr:127.0.0.1  Mask:225.0.0.0
        inet6 addr: ::1/128 Scope:Host
        UP LOOPBACK RUNNING  MTU:16436  Metric:1
        RX packets:71 errors:0 dropped:0 overruns:0 frame:0
        TX packets:71 errors: 0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:0
        RX bytes:5316 (5.1 KiB)  TX bytes:5316 (5.1 KiB)

---

### Post by amohanty on 2006-11-05
Do you have a static IP or dynapmic IP from the ISP?
Is it s PPPoE sort of plan?
Does your ISP require some software to connect?

Can you post the output of:
**sudo dhclient -rl eth0**

AM

---

### Post by koryo88 on 2006-11-05
I'm pretty sure it's dynamic.

I'm connected directly to a cable modem.

No, I don't believe there should be any software required, I'm using it now on XP.

Usage:   dhclient [-ldqr] [-nw] [-p <port>] [-s server]
         [-cf config-file] [-lf lease-file][-pf pid-file] [e     VAR=val][-sf script-file] [interface]

If this helps any, after using the command "sudo ifdown eth0 sudo ifup eth0" I got "no dhcp offers received."

My cable modem is a Motorola SB5120.

---

### Post by amohanty on 2006-11-05
How about:
**dhclient eth0**

If that does not work:
[B]sudo dhclient -r eth0
sudo dhclient -l eth0[/B]

AM

---

### Post by koryo88 on 2006-11-05
dhclient eht0: 
can't create /var/lib/dhcp3/dhclient.leases: Permission denied
Can't create /var/run/dhclient.pid: Permission denied
drop_privileges: could not set group id: Operation not permitted

sudo dhclient -r eth0:

Listening on LPF/eth0/00:03:47:e7:6e:f2
Sending on   LPF/eth0/:00:03:47:e7:6e:f2
Sending on   Socket/fallback

sudo dhclient -l eth0:

Usage: dhclient [-ldqr] [-nw] [-p <port>] [-s server]
[-cf config-file] [-lf lease-file][-pf pid-file] [e VAR=val]
[-sf script-file] [interface]

---

### Post by babooka on 2006-11-05
Is your PC connectec to the modem via USB or RJ45?

---

### Post by koryo88 on 2006-11-05
Rj45

---

### Post by amohanty on 2006-11-06
Sorry I made a typo. Try this:

**sudo dhclient eth0**

---

### Post by koryo88 on 2006-11-09
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I added the DNS servers for my ISP and now it's telling me at "ifup eth0" the No DHCPOFFERS received and at "ifdown" eth0 not configured.

If anyone has any ideas why on earth it's not working I would really appreciate it.

---

### Post by FrodoB on 2006-11-09
You are really using inet6?

---

### Post by koryo88 on 2006-11-09
Umm...I don't know, what's inet6 and how would I know?

---

### Post by koryo88 on 2006-11-09
Under Network Tools it says the protocol is ipv4 if that is what you're talking about. Would changing it to a static ip fix it do you think?

I got the info from my current connection and changed the net mask and gateway but how do I know what ip address to use?

---

### Post by koryo88 on 2006-11-10
Thanks for all your help! I'm now typing this from Ubuntu. It was the simplest thing. All I had to do was unplug the modem for a minute so the mac address would empty from the memory before I plugged it in to my linux machine and it started working immediately.

---

