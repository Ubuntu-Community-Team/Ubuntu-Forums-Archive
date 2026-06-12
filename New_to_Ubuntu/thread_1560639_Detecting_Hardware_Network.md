---
title: "Detecting Hardware Network"
date: 2010-08-25
forum: New to Ubuntu
---

### Post by Zhuyou on 2010-08-25
Attempting to do minimal install of xubuntu. Use the alternative image file, put it on usb and enter command-line when prompted. Somehow, along those lines, at the "Detecting Hardware Network", it sorta fail. As in can't detect it, or maybe it didn't not work. I don't remember the exact wording. I'm assuming it's not able to detect the wired controller card. And after that, everything can't be done without it. 

If I were to go into the expert command-line prompt, it has the option to give me some drivers to install, but none of these matches the one that I got.

I use a Acer Aspire One D250-1156. It's a Atheros driver for wired. 

I'm trying to do minimal install, but it certainly feel like I should stop that and go with standard install and strip it down from there. Harder, maybe but I'm not sure how hard it'll be to install my drivers for wifi, touchpad, and everything to work just for that netbook. So, I'm keeping my options open.

I google quite a bit over the few days, but I can't seem to find any solution. Any acer aspire one user out there trying to do the same? or any help? Any comments? Anything is fine.

---

### Post by Peter09 on 2010-08-25
the command
```
ifconfig
```
will show your network status - cut and paste it here if you are unsure.

---

### Post by Zhuyou on 2010-08-25
Strange. I just did a full instant of xubuntu to get that command inputed, and I attempt to do so with my eternet connected through lan for it. It didn't work. It's strange since i remember 8.04 was able to connected through wired, but not wireless. This time, wireless work out of the box and not wired. But let me post the ifconfig note than. Maybe it's because it didn't work out of the box that I need to fix it somehow. That, or make use of an another version of xubuntu to check if it affects me anyway. 

> eth0      Link encap:Ethernet  HWaddr 00:23:5a:9b:09:08  
          inet6 addr: fe80::223:5aff:fe9b:908/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:20988117 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:515248 (515.2 KB)  TX bytes:3888 (3.8 KB)
          Interrupt:29 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:276 errors:0 dropped:0 overruns:0 frame:0
          TX packets:276 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:21632 (21.6 KB)  TX bytes:21632 (21.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:2c:98:63:84  
          inet addr:192.168.1.8  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:2cff:fe98:6384/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2674 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2260 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3039389 (3.0 MB)  TX bytes:390019 (390.0 KB)


Thanks for any help.

---

### Post by Peter09 on 2010-08-25
Can you do then ifconfig without the wireless connection working and with a wired connection plugged in.

---

### Post by Zhuyou on 2010-08-25
Would it tell me what I need to know or at least hint at what drivers I need or what's wrong with it? Currently, I cannot access my wired internet with this netbook since I'm logging in from work, and I wouldn't be able to do so until maybe until 8-9pm tomorrow.

Some more questions to asked , if you don't mind while i wait to do the ifconfig tomorrow. Given what I know about minimal install, they'll would be drivers to be installed for the minimal setup, right? I'm not quite sure what my system needs in term of drivers,and I'm not that great with the commandline, so it might prove to be diffcult for me. Anyone else got experiences with something like this? I'm assuming they're a bunch of package tha goes to a standard installed that is necessary for it to work correctly, like controlling speed fan, brightness, wired/wireless, etc. I'm thinking of i should just go standard install and trim it down that way. Or at least attempt this minimal install and do as i go.

Any good suggestion?

---

### Post by varunendra on 2010-08-26
I guess [this]("http://ubuntuforums.org/showthread.php?t=1552177") is what you want. For any support, you may post in the thread or PM [linux18]("http://ubuntuforums.org/member.php?u=1108811") (the thread starter).

---

### Post by Zhuyou on 2010-08-26
Sorta, but at least something recent. And so that I know what's being installed otherwise my cpu fan's never gonna stop, or brightness doesn't work, etc. They are some issues, but that' would be a cool way to install. Though, I wish he submit a list of what he uninstalled. Or what he installed in it.

---

### Post by varunendra on 2010-08-26
That's why I suggested to discuss your project in his thread ! (at least until some right person picks your thread up.... :))

---

### Post by Zhuyou on 2010-08-26
this is while it's trying to connect to the wired connection.
```
eth0      Link encap:Ethernet  HWaddr 00:23:5a:9b:09:08  
          inet6 addr: fe80::223:5aff:fe9b:908/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4387 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:269454 (269.4 KB)  TX bytes:3546 (3.5 KB)
          Interrupt:29 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:632 errors:0 dropped:0 overruns:0 frame:0
          TX packets:632 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:50608 (50.6 KB)  TX bytes:50608 (50.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:2c:98:63:84  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:2cff:fe98:6384/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1254 (1.2 KB)  TX bytes:5192 (5.1 KB)


```


This is after the wired connection failed.
```
eth0      Link encap:Ethernet  HWaddr 00:23:5a:9b:09:08  
          inet6 addr: fe80::223:5aff:fe9b:908/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1817 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:111850 (111.8 KB)  TX bytes:2520 (2.5 KB)
          Interrupt:29 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:632 errors:0 dropped:0 overruns:0 frame:0
          TX packets:632 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:50608 (50.6 KB)  TX bytes:50608 (50.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:2c:98:63:84  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:2cff:fe98:6384/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1086 (1.0 KB)  TX bytes:5008 (5.0 KB)


```

Not sure what you're looking for, I mention earlier that my wired connection failed to work out of the box. That might be why I couldn't detect the hardware network on the minimal install. As far as I'm aware, the 8.04 LTS is the the earliest x/ubuntu distr. that would make wired ethernet work out of the box. If i attempted that as the minimal, do you think it'll work? And if so, when i'm updating to the new vision, 9.04 than 9.10 and finally 10.4, would it also install the unnecessary installation/packages that is present in every normal install?

Thanks.

---

### Post by Zhuyou on 2010-08-26
Xubuntu 8.04.1 would work wired out of the box. Using the alternate cd and booting from USB for minimal install, it stall at the same place as the xubuntu 10.04 area. I guess it's not that different distr. version's affecting it.

---

### Post by Zhuyou on 2010-08-26
Eh, I give up. I exhausted a lot of my resources by myself, and maybe some of your. I believe I'm just going to install xubuntu and trim it down. That or install Lubuntu, though I don't like it, it's very fast. Thanks, guys, for your attempt.

---

