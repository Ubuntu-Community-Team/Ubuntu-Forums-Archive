---
title: "Cannot connect to internet with Ubuntu"
date: 2007-09-09
forum: Networking &amp; Wireless
---

### Post by caver_w on 2007-09-09
I just installed Ubuntu 7.05 64-bit version on my AMD dual core 64-bit based computer. I had trouble loading Ubuntu until someone pointed out that the SCSI card might be the problem. Apparently it was.

All is working well except I cannot connect to the internet. I have Hughes satellite service and a router. While I have Microsoft XP accessing the internet OK on two computers I cannot get Linux to do so.

The router is configured as follows:

    MAC Address : 00-19-5b-56-1e-41
    IP Address : 172.16.0.1
    Subnet Mask : 255.255.0.0
    DHCP Server : Enabled
    Wan:
    MAC Address : 00-1a-4d-84-98-4f
    Connection : DHCP Client Connected
    IP Address : 192.168.0.6
    Subnet Mask : 255.255.255.0
    Default Gateway : 192.168.0.1
    DNS : 192.168.0.1

Using network tools I manually set the IP address for the router 172.16.0.1 and the gateway address for the satellite modem 192.168.0.1 -- same as for XP.

I can ping the router OK but cannot address the router from Firefox. I cannot ping anything on the internet.

Ubuntu does recognize the other computer and I can transfer files OK over the in house network.

Any suggestions for setting Ubuntu up for internet access?

Thanks much,
Bill Walden

---

### Post by noob12 on 2007-09-09
From the Windows machine, if you can post the output of 
```

ipconfig /all

route print

```
run in a cmd window, then it might help suggest the right settings for Ubuntu.

---

