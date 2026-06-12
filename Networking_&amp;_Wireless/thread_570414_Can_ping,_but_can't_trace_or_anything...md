---
title: "Can ping, but can't trace or anything.."
date: 2007-10-08
forum: Networking &amp; Wireless
---

### Post by etharo on 2007-10-08
Downloadet 7.04 desktop from here
[http://isv-image.ubuntu.com/vmware/](http://isv-image.ubuntu.com/vmware/)

using wmware player - latest version
nat

In ubuntu I enable the wired connection, and dhcp.
Thats pretty much it, and it should go straight onto the net.

I can ping ip and dns - but i cant trace, apt-get can't connect, ff can't load the page. Seems like system wide network problems.

ifconfig...
```

ubuntu@ubuntu:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:0C:29:0C:DD:4C  
          inet addr:192.168.222.128  Bcast:192.168.222.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe0c:dd4c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:51 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6760 (6.6 KiB)  TX bytes:6857 (6.6 KiB)
          Interrupt:17 Base address:0x1400

```

the mac adress should be unique for what I could see...

Either the problem is with ubuntu, or the wmware player/system, or host os WinXP, or firewall. 
Firewall on computer is removed, and windows fw is off.
Wmware is reinstalled, upgraded, downgraded .. no change.
wmware nat/bridge tried - no change.
ubuntu image is re-downloaded and retried etc .. no change.
Everything else on winxp workes ok - only wmware/ubuntu image have network problem.

note: ubuntu image did previous work, it just suddenly got this problem.
So... where is the problem? I think ubuntu is fine, but how to prove it?

---

