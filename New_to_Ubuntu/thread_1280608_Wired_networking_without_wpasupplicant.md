---
title: "Wired networking without wpasupplicant?"
date: 2009-10-02
forum: New to Ubuntu
---

### Post by greno1 on 2009-10-02
Hi all - I'm a total boob to Ubuntu (and Linux in general), trying to get my first install working. 

I'm installing on an old Thinkpad T23 that has no built in wireless capabilities, and I don't need it either.  I went through the 9.04 desktop install (32 bit) successfully, but continually hit a problem of high CPU about a minute after booting.  

Running TOP reveled that wpasupplicant was consistently over 90% CPU.  Browsing the internet worked, but it CRAWLED.  So, since it seems that wpasupplicant is specifically for wifi, I uninstalled the package, which totally eliminated the performance problem.

However, now I can't get networking to work at all.  How do I disable wpasupplicant and still get networking to work through a wired connection?

BTW, my T23 has 768mb ram.  I'm just using it at an entertainment center and want to use it as a browser / media streamer on my LCD TV.

Thanks!
-Gregg

---

### Post by Bachstelze on 2009-10-02
Uninstalling wpa_supplicant probably also uninstalled networkmanager, which is the application... managing network connections. ;)

One way to get your network back is to configure it using the /etc/network/interfaces file. Do you know if your netwok is using DHCP or static IPs?

---

### Post by greno1 on 2009-10-02
Thanks for the quick reply!

I'm using DHCP, but it would be fine to switch to a static IP address if that simplifies the configuration.

-Gregg

---

### Post by Bachstelze on 2009-10-02
Nope, DHCP is fine too. So first, we need to get the name of your wired interface. It will probably be eth0, but just to be sure, run

```
sudo ifconfig -a
```

It will output something like this:

```
eth0      Link encap:Ethernet  HWaddr 00:1c:c0:27:7f:50
          inet addr:88.191.79.242  Bcast:88.191.79.255  Mask:255.255.255.0
          inet6 addr: 2a01:e0b:1:79:21c:c0ff:fe27:7f50/64 Scope:Global
          inet6 addr: fe80::21c:c0ff:fe27:7f50/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2007714760 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3106080915 errors:4 dropped:0 overruns:4 carrier:4
          collisions:0 txqueuelen:1000
          RX bytes:593055199530 (552.3 GiB)  TX bytes:4014622759402 (3.6 TiB)
          Interrupt:19 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:42507416 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42507416 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:15076847927 (14.0 GiB)  TX bytes:15076847927 (14.0 GiB)
```

So here, my Ethernet interface is indeed eth0. Now, open the /etc/network/interfaces file in your favourite text editor, for example:

```
gksudo gedit /etc/network/interfaces
```

It should look like this:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
```

Make it look like this:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```

save your changes and quit gedit. Now run

```
sudo /etc/init.d/networking restart
```

and if all went well, you should be connected to your network.

---

### Post by greno1 on 2009-10-02
Thanks Bachstelze - I really appreciate the help! I'm at work, so I won't be able to try this until Saturday.  I'll post back with my results then.

BTW, do I need to re-install the wpasupplicant package first?

---

### Post by Bachstelze on 2009-10-02
> **greno1 said:**
> Thanks Bachstelze - I really appreciate the help! I'm at work, so I won't be able to try this until Saturday.  I'll post back with my results then.

BTW, do I need to re-install the wpasupplicant package first?

Nope, here we operate at a lower lever.

---

### Post by greno1 on 2009-10-02
Great - thanks again.

---

### Post by greno1 on 2009-10-03
Bachstelze,

I made the changes you suggested, and everything is working great!  I've got wired internet access working, and no CPU issues.  This is an old laptop, but running much faster now than XP was with all the antispyware and antivurs programs running on it.

Thanks so much for your help!  

-Gregg

---

