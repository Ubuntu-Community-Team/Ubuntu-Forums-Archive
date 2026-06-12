---
title: "Planet wireless setup completion...help please! I'm a newbie..."
date: 2007-03-26
forum: Networking &amp; Wireless
---

### Post by christiaanb on 2007-03-26
Hey,

I would like some help to set up my "Planet 802.11g Wireless USB Adapter" on a pentium 2 Compaq Armada 1750, running Xubuntu Server with 130mb ram.

Well, so far I've followed this guide ([https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)) to install ndiswrapper, and everything went well, until i came to 8.2.3  .   

I did the ifconfig : 

me@ubuntu:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:172 (172.0 b)  TX bytes:172 (172.0 b)

And iwconfig :

me@ubuntu:~$ iwconfig
lo        no wireless extensions.

sit0      no wireless extensions.

Can anyone tell me what that means, and how to finish the installation? I'm a newbie to wireless...

I also did this :

me@ubuntu:~$ ndiswrapper -l
Installed ndis drivers:
rt73            driver present, hardware present

So the driver is the right one i think...?

Also this forum says that my device needs to be "wlan0". Well, it is "lo"...is that okay?

Thanks!
Christiaan

---

### Post by spd106 on 2007-03-26
Could you post the output produced by the following command?
```
sudo lshw -class network
```

It could be that there is a module for your card already loaded that needs to be removed before you can proceed.

Alternatively, you might want to try this wiki page to build the OSS driver [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73).

---

### Post by christiaanb on 2007-03-26
Hey thanks, I had a pci card installed that I wasn't using...my bad...

When i did "lwconfig" it picked it up fine! Thanks!

GB

---

