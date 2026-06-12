---
title: "Internet Browsing Only After Ping"
date: 2015-06-17
forum: Networking &amp; Wireless
---

### Post by mstern on 2015-06-17
HI,

Complete beginner here; just installed latest Ubuntu 14.04LTS.

My browsers (Firefox and Chrome) can not get to web pages until after I go to the terminal and "ping 8.8.8.8" once.  After I do that, the browers work fine until I restart Ubuntu, then I have to do it again.  I tried adding "8.8.8.8" to the ip4 settings in the Network settings, but that doesn't seem to make a difference.

Any advice greatly appreciated!

Marc

---

### Post by Duck_Dude on 2015-06-17
Hi Marc, 

Can you post a screen of ```
ifconfig
``` from terminal.  That will help us here.

Can we assume that you've left all default settings in tact (except when you tried to change your ip settings to 8.8.8.8?

---

### Post by mstern on 2015-06-17
```
eth0      Link encap:Ethernet  HWaddr 60:a4:4c:aa:01:8a  
          inet addr:172.27.35.16  Bcast:172.27.35.255  Mask:255.255.255.0
          inet6 addr: fd2e:3d96:cd62:0:62a4:4cff:feaa:18a/64 Scope:Global
          inet6 addr: fe80::62a4:4cff:feaa:18a/64 Scope:Link
          inet6 addr: fd2e:3d96:cd62:0:64fa:e905:24fe:1c71/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:458596 errors:0 dropped:0 overruns:0 frame:0
          TX packets:254743 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:572505484 (572.5 MB)  TX bytes:29279932 (29.2 MB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3725 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3725 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:390764 (390.7 KB)  TX bytes:390764 (390.7 KB)


wlan0     Link encap:Ethernet  HWaddr 60:a4:4c:44:47:fb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

---

### Post by mstern on 2015-06-17
To be clear, the above ifconfig result is after I'd already done the ping 8.8.8.8 trick.  I rebooted and did an ifconfig before doing the ping so you can see that result too, in case that matters:

```
eth0      Link encap:Ethernet  HWaddr 60:a4:4c:aa:01:8a  
          inet addr:172.27.35.16  Bcast:172.27.35.255  Mask:255.255.255.0
          inet6 addr: fd2e:3d96:cd62:0:e855:2cbe:35a:3946/64 Scope:Global
          inet6 addr: fd2e:3d96:cd62:0:62a4:4cff:feaa:18a/64 Scope:Global
          inet6 addr: fe80::62a4:4cff:feaa:18a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:207 errors:0 dropped:0 overruns:0 frame:0
          TX packets:407 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:75656 (75.6 KB)  TX bytes:39551 (39.5 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:345 errors:0 dropped:0 overruns:0 frame:0
          TX packets:345 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:25962 (25.9 KB)  TX bytes:25962 (25.9 KB)


wlan0     Link encap:Ethernet  HWaddr 60:a4:4c:44:47:fb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

---

### Post by tgalati4 on 2015-06-18
Please post the output of:

```
netstat -r
```

You might need to reboot your cable modem first, then your router in that order.

---

### Post by wildmanne39 on 2015-06-18
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by mstern on 2015-06-18
Thanks for the pointer Wild Man.

Result of netstat -r
```
Kernel IP routing tableDestination     Gateway         Genmask         Flags   MSS Window  irtt Iface
default         172.27.35.1     0.0.0.0         UG        0 0          0 eth0
172.27.35.0     *               255.255.255.0   U         0 0          0 eth0
```

---

### Post by mstern on 2015-06-18
Again, to be clear, the above was post "ping trick."  I just restarted my machine to do a
```
netstat -r
```
prior to the ping trick and I can tell you that before the ping 8.8.8.8 and after, the results are identical (except after the ping the browsing works)

---

### Post by tgalati4 on 2015-06-18
What is the device at 172.27.35.1?  Log into the device and describe what you see:  [http://172.27.35.1](http://172.27.35.1)

Describe what devices you have hooked up between your computer and your internet connection.

Also post:

```
cat /etc/resolv.conf
```

---

### Post by mstern on 2015-06-19
Problem solve! :)

Thank you all for your help!  tgalati4, the answer to your question was that "http://172.27.35.1/" is my Ooma box (Ooma is a VOIP thing like Vonage). I thought, that seems odd -- sure enough, it was the way I had that wired up. There are two ports on the back of it -- "To Internet" and "To Home Network."  For a modem and computer only set up, I should use both.  For a modem and router and computer setup, I should have only plugged in the "To Internet" one. Removed the cable between the Ooma "To Home Network" and my router and restarted Ubuntu, and web browsing works without the ping first.

Now, as to *why* that solved it, no idea, but I'm sure it probably makes sense to you experts.

Thanks again!

---

### Post by tgalati4 on 2015-06-19
I always answer the phone to my Ooma colleagues "Ooma Ooma".  There is a 30-second delay to make the connection, so I can always tell an Ooma connection.  I don't know how they work internally, but I am glad you got it sorted.  Please mark the Title of this thread as "Solved" in Thread Tools.

---

