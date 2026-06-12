---
title: "Unknown interface wlan0"
date: 2016-11-23
forum: Networking &amp; Wireless
---

### Post by 2CV67 on 2016-11-23
Hi!

As part of diagnosing another problem, I ran ```
sudo ifdown wlan0
```
and was surprised to get back ```
Unknown interface wlan0
```

When I run "sudo ifconfig" then it finds wlan0 OK:
```
~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr f8:0f:41:c5:9d:ed  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:310 errors:0 dropped:0 overruns:0 frame:0
          TX packets:310 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:27601 (27.6 KB)  TX bytes:27601 (27.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:c0:ca:75:bf:17  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:caff:fe75:bf17/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:358 errors:0 dropped:0 overruns:0 frame:0
          TX packets:471 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:273607 (273.6 KB)  TX bytes:85639 (85.6 KB)

```
Is this surprising?
What could/should I do to try to get "sudo ifdown wlan0" working?

Thanks

---

### Post by 2CV67 on 2016-11-23
Attached wireless-info.tar.gz in case that helps.
Couldn't see how to just paste it in code tags...

---

### Post by chili555 on 2016-11-23
> As part of diagnosing another problem, I ran
Code:
sudo ifdown wlan0
and was surprised to get back
Code:
Unknown interface wlan0Not surprising at all. ifdown and ifup are used to control interfaces declared in /etc/network/interfaces. In the typical default install of Ubuntu, wlan0 and eth0, etc., are not so declared as Network Manager handles them. 

From *man ifup*:> DESCRIPTION
       The  ifup  and  ifdown  commands  may be used to configure (or, respec&#8208;
       tively, deconfigure) network interfaces based on interface  definitions
       in  the  file  /etc/network/interfaces.  ifquery command may be used to
       parse interfaces configuration.


You will have better luck with:```
sudo ifconfig wlan0 down
```

---

### Post by 2CV67 on 2016-11-23
Thanks chili555 for your help.

Good illustration of my complete lack of comprehension in wifi & networking!

As you said - "sudo ifconfig wlan0 down" works OK to cut off the wifi.

Surprisingly (for me...) "sudo ifconfig wlan0 up" does not then bring wifi back up again...

But if, after "sudo ifconfig wlan0 down" I then disable/enable wifi in the networking applet, it works again...

I find all that quite mysterious!

---

### Post by 2CV67 on 2016-11-25
Should "sudo ifconfig wlan0 up" bring WiFi back up?

Any ideas why it doesn't?

Or how I can troubleshoot that?

Thanks!

---

### Post by chili555 on 2016-11-25
> **2CV67 said:**
> Should "sudo ifconfig wlan0 up" bring WiFi back up?

Any ideas why it doesn't?

Or how I can troubleshoot that?

Thanks!It's probably related to Network Manager. Do you have any better luck with:```
sudo service network-manager restart
```

---

### Post by 2CV67 on 2016-11-25
Yes - thank you very much!

"sudo service network-manager restart" works OK.

I don't dare to ask why...

---

### Post by chili555 on 2016-11-25
> I don't dare to ask why...Network Manager is a mysterious thing. It works perfectly and seamlessly for most uses. However, when we want to use the old school methods, ifconfig and many more, when we wish it would step aside and defer to our wishes, it sometimes is troubled. NM has come a lonnnng way in the past several years but still has a few rough spots.

For the most common use, connecting and staying connected, with few exceptions, it is fine.

---

