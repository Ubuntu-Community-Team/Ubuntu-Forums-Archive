---
title: "Network is unreachable. help"
date: 2016-08-30
forum: Networking &amp; Wireless
---

### Post by Gwanyoung Kim on 2016-08-30
Hi all.

I installed ubuntu 14.04 LTS 32bits on my laptop.
And I am trying compile vlc.
But I get the error message as follows.

```
gykim@gykim-Compaq-Presario-CQ61-Notebook-PC:~/winvlc/vlc-2.2.4/contrib/win32$ make prebuilt
curl -f -L -- "ftp://ftp.videolan.org/pub/videolan/contrib/i686-w64-mingw32/vlc-contrib-i686-w64-mingw32-latest.tar.bz2" > "vlc-contrib-i686-w64-mingw32-latest.tar.bz2"
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:--  0:00:04 --:--:--     0
curl: (7) Failed to connect to ftp.videolan.org port 21: Network is unreachable
make: *** [vlc-contrib-i686-w64-mingw32-latest.tar.bz2] Error 7
make: *** Deleting file `vlc-contrib-i686-w64-mingw32-latest.tar.bz2'
```

The forum of vlc tell me to check my network.

```
- netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
```

```
 - ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:9e:09:37:bd  
          inet addr:192.168.0.106  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2832 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1631 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:931727 (931.7 KB)  TX bytes:280873 (280.8 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:79 errors:0 dropped:0 overruns:0 frame:0
          TX packets:79 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5262 (5.2 KB)  TX bytes:5262 (5.2 KB)
```

I don't know what should I do.
Help me please.

Regards,
Gwanyoung Kim.

---

### Post by wildmanne39 on 2016-08-30
You know that vlc comes preinstalled in ubuntu?

---

### Post by Gwanyoung Kim on 2016-08-30
Hi.
I don't know it.
If the vlc is already preinstalled, is the error message normal status?

---

### Post by wildmanne39 on 2016-08-30
When I searched that error it says it is for windows, are you trying to comple vlc  for windows and not ubuntu?
If it is ubuntu look under sound and video or go into dash if you are using unity and type vlc and it should find it.

---

### Post by howefield on 2016-08-31
Certainly looks like an attempt to install the Windows version but just to point out that VLC doesn't come preinstalled but it is available to install with..

```
sudo apt-get install vlc
```

---

### Post by Gwanyoung Kim on 2016-08-31
Hi,

I'm trying to compile vlc source, not install.

Regards,
Gwanyoung Kim.

---

### Post by Bucky Ball on 2016-08-31
As mentioned, as VLC comes as a default app with Ubuntu, I'm curious as to why you are trying to do this? There is a problem with the VLC you already have? :-k

In any case, is it only with this that you are getting 'Network Unreachable'. Your thread seems to be about both the VLC install and the dead network. Is the network working fine otherwise or is the network problem your first and foremost issue?

---

### Post by Gwanyoung Kim on 2016-08-31
Hi,
1. I need a vlc that have different skin, function.
2. Yes, the problem is only "network Unreachable".
3. Web surfing, apt-get install, etc, have no problem.

Regards,
Gwanyoung Kim.

---

### Post by howefield on 2016-08-31
Linking to your post on the VLC forums.

[https://forum.videolan.org/viewtopic.php?f=14&t=135242](https://forum.videolan.org/viewtopic.php?f=14&t=135242)

---

