---
title: "Restricted driver installed, now what?"
date: 2007-03-26
forum: Networking &amp; Wireless
---

### Post by ubuntnewb on 2007-03-26
I installed the latest beta over the weekend (Had problems installing with every other release so it was suggested I try the beta) on my Dell Inspiron 640m/Latitude e1405 and have managed to get everything up except for my wireless connection. The card (Intel Pro 3945) was detected and is listed under the "Restricted Drivers Manager", "Enabled" and "In Use" are checked, but when I go to System->Administration->Network there is no "wireless" option listed. Here's a copy of my ifconfig and iwconfigs.

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:22:AB:15:DF  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 

eth0:avah Link encap:Ethernet  HWaddr 00:14:22:AB:15:DF  
          inet addr:169.254.7.9  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:38 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2986 (2.9 KiB)  TX bytes:2986 (2.9 KiB)

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

I've rebooted into windows and can access my wireless network fine, so I know that the card is functioning. Any help would be appreciated.
TIA,
Shannon

---

### Post by chili555 on 2007-03-26
Please try the following commands:```
sudo depmod -a
sudo modprobe ipw3945
```and rerun sudo iwconfig and see if your wireless interface shows up. If so, configure it through System -> Administration -> Network and you should be good.

---

### Post by ubuntnewb on 2007-03-26
That didn't work =(

Here's what I did and the results.

shannon@shannon-laptop:~$ sudo depmod -a
Password:
shannon@shannon-laptop:~$ sudo modprobe ipw3945
shannon@shannon-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by chili555 on 2007-03-26
> installed the latest beta I believe that Network Manager is installed by default. It's that whirlygig thing at the top of your Gnome panel. Does it see your network?

Be sure no wired connection is present when you try to connect, as Network Manager gives preference to wired and will not, without some tricks, connect if wired is available.

---

### Post by ubuntnewb on 2007-03-26
> **chili555 said:**
> I believe that Network Manager is installed by default. It's that whirlygig thing at the top of your Gnome panel. Does it see your network?

Be sure no wired connection is present when you try to connect, as Network Manager gives preference to wired and will not, without some tricks, connect if wired is available.

It says "No Network Connection". It doesn't have a wired connection ATM (had it connected via ethernet, but disconnected and have kept it DC'd while trying to get wireless working.) All of the information given thus far has been with no wired connection.

---

### Post by aqualad on 2007-03-26
do

```
ifconfig -a
```

and post results

also, show us:

```
cat /etc/networking/interfaces
```

You could try compiling the drivers from the source by getting the source files here:

[http://ipw3945.sourceforge.net/downloads.php](http://ipw3945.sourceforge.net/downloads.php)

If you don't know how just ask..or search for a howto possibly ( [http://wiki.ubuntu.com](http://wiki.ubuntu.com) )

---

### Post by chili555 on 2007-03-26
Just saw this, which looks very promising: [http://www.ubuntuforums.org/showthread.php?t=392265&highlight=ipw3945](http://www.ubuntuforums.org/showthread.php?t=392265&highlight=ipw3945) See post #4

---

