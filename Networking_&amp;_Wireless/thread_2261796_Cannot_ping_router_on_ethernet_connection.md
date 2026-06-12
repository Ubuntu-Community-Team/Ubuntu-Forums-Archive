---
title: "Cannot ping router on ethernet connection"
date: 2015-01-21
forum: Networking &amp; Wireless
---

### Post by swagatsarma on 2015-01-21
Please do not laugh if the problem seems too trivial, but I am simply not being able to solve it.

Initially I was connecting to internet on my Ubuntu machine using a TPLink wireless dongle and life was fine. However, I tried connecting to my router using an ethernet cable, and Ubuntu was just not able to connect to the router. 

First of all, pasting the simple diagnostics that I have done on the system:

```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 74:d4:35:5b:63:68  
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::76d4:35ff:fe5b:6368/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:361 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:235 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33538 (33.5 KB)  TX bytes:3687 (3.6 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:230 errors:0 dropped:0 overruns:0 frame:0
          TX packets:230 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17684 (17.6 KB)  TX bytes:17684 (17.6 KB)


$ ping -c 5 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.


--- 192.168.0.1 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4031ms


$ arp -a
? (192.168.0.1) at <incomplete> on eth0

$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0




ping -c 5 192.168.0.102
PING 192.168.0.102 (192.168.0.102) 56(84) bytes of data.


--- 192.168.0.102 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 3999ms
```


Tried ping a local system on the network as well. Didn't work. I tried playing with the /etc/network/interfaces file as well as /etc/resolv.conf file to fix this. In the process, the inbuilt network manager seems to work intermittently. 

Can you please point out to me what I am doing wrong?

Cheers!!

---

### Post by slickymaster on 2015-01-21
Hi swagatsarma, welcome to the forums.

I'm moving your thread from the Resolution Center (which is the place to contact a forum admin concerning problems with your forum account, to appeal moderator action, to request a thread be moved from the jail, or to file a complaint about forum harrassment or abuse) to the **Networking & Wireless** sub-forum, which is the proper venue for it.

Also, I've edited your post adding code tags to it, because output code posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand. The [use of 'Code' tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") makes the post clean, compact and more appealing, thus getting more attention from readers.

---

### Post by swagatsarma on 2015-01-21
Thanks slickymaster. Just waiting for a solution to this now! :D

---

### Post by The Cog on 2015-01-21
I know it's not much help, but I can see two things that look wrong.
* eth0 shows hundreds of dropped transmit packets - it is very unusual to see any.
* eth0 shows a queue length of 1000. I think 1000 packets or bytes are still waiting to be sent. This figure is usually 0.

So I think there is something wrong quite low down in the hardware or drivers. However, eth0 does show RUNNING which means it has seen that the cable is plugged in.

Sorry I can't add anything more useful.

---

### Post by kpatz on 2015-01-21
Try another ethernet cable, or a different port on the router.

txqueuelen is 1000 on my systems as well.  It's not indicative of a problem.  The dropped packets is an issue though. Not sure what causes this, but try another cable just in case.

---

### Post by TheFu on 2015-01-21
Looks like there is a physical issue. Bad port, bad cable. I'd swap those first, since they are easier to check than anything else. If you have another computer, try it on the switch/router port to see if that works or not.  Test, isolate, simplify, repeat until the broken component is determined.  So far, your network settings appear to be fine.

Also - don't ever manually touch resolv.conf. Since 2012, settings for it has been managed in the interfaces file.

---

### Post by swagatsarma on 2015-01-21
Ok this is what I did.

1) I reinstalled my realtek ethernet drivers. Vola! Internet was up, and I felt the world working!!
2) Shut down my PC, next morning, internet is not working again. Route tables are empty, etc etc, so I reinstalled realtek ethernet drivers, and I get internet again.

Guess this is a case of bad drivers.

---

### Post by swagatsarma on 2015-01-21
Everything is working perfectly fine now. Drivers are working, even after reboot, no reinstallation required. I simply blacklisted the previous ethernet controller driver. Thanks for the idea guys!!

---

