---
title: "Ubuntu wont connect to Wired Network"
date: 2011-05-17
forum: New to Ubuntu
---

### Post by jakeispwn on 2011-05-17
Okay i just recently installed Ubuntu 11.04 as a dual boot with windows 7. When I run windows, it is connected to the network fine but when I run Ubuntu it is not connected. When i first ran Ubuntu it was connected but when i rebooted it would no longer connect. Yes networking is enabled. It also says there are no available networks to connect to. Is this some stupid thing that even a beginner should be able to fix?
By the way, ifconfig returns this-
 
Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet 6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:24 errors:0 dropped:0 overruns:0 frame:0
TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:1440 (1.4 KB) TX bytes:1440 (1.4 KB)
 
Ive checked other forum posts on this, but none have helped me.

EDIT 

Also when i plug my ethernet cable directly into the modem it does not work.

---

### Post by tmette on 2011-05-17
I don't know a whole lot about networking, but your IP address listed is the actual computer.  You probably need an IP of 192.168.1.whatever

---

### Post by jakeispwn on 2011-05-17
okay well I know my default gateway but even knowing that, I wouldnt know what to do.

---

### Post by gandaran on 2011-05-17
> **jakeispwn said:**
> Okay i just recently installed Ubuntu 11.04 as a dual boot with windows 7. When I run windows, it is connected to the network fine but when I run Ubuntu it is not connected. When i first ran Ubuntu it was connected but when i rebooted it would no longer connect. Yes networking is enabled. It also says there are no available networks to connect to. Is this some stupid thing that even a beginner should be able to fix?
By the way, ifconfig returns this-
 
Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet 6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:24 errors:0 dropped:0 overruns:0 frame:0
TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:1440 (1.4 KB) TX bytes:1440 (1.4 KB)
 
Ive checked other forum posts on this, but none have helped me.
try removing the 'auto eth0' in the network wired tab then disable and enable networking again.
also check that DHCP server is enabled in the router configuration.

---

### Post by jakeispwn on 2011-05-17
> **gandaran said:**
> try removing the 'auto eth0' in the network wired tab then disable and enable networking again.
also check that DHCP server is enabled in the router configuration.
 
um auto eth0 is supposed to be there? it doesnt exist for me.

---

### Post by gandaran on 2011-05-17
> **jakeispwn said:**
> um auto eth0 is supposed to be there? it doesnt exist for me.
well, you said in the first post wired internet worked the first time you used Ubuntu so it should still be there or is there any other wired setups there?

---

### Post by jakeispwn on 2011-05-17
That is really weird. Unless im looking in the wrong location, It is not there.

---

### Post by jakeispwn on 2011-05-17
Aslo no other wired setups are there.

---

### Post by jakeispwn on 2011-05-18
Bump

---

### Post by aphatak on 2011-05-18
Do you see a network manager icon in the menu-bar?  If you do, click it and see if the wired network is enabled.  If it is not, enable it and give it a try.

Take a look at '/etc/network/interfaces' to see if it has any 'auto eth0' in it.  If it doesn't, it is implied:  the network interface will assume it as the default and proceed about its business.

You might want to declare a static network address in the '/etc/network/interfaces' and see if that works:  you might have to do it if the DHCP in your network set up does not generate and assign an IP address for you.  An example of a static IP set up -
```
iface eth0 inet static
 address 192.168.<xxx>.<yyy>
 netmask 255.255.255.0
 broadcast 192.168.<xxx>.255
 gateway 192.168.<xxx>.<zzz>
 dns-nameservers <aaa>.<bbb>.<ccc>.<ddd>

```
The values in angle-brackets will depend on your LAN set-up.  You might want to boot into Windows, and run the command 'ipconfig' to see what values might make sense.

If you could post what you find, it would help find a solution.

---

