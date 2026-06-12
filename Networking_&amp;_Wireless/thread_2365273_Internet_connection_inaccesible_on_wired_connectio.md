---
title: "Internet connection inaccesible on wired connection"
date: 2017-07-04
forum: Networking &amp; Wireless
---

### Post by nickschurch on 2017-07-04
I'm having a really weird problem with my wired connection on my 16.04 file server. After a few (5-6) minutes of activity on the internet, my internet connection suddenly drops and is unable to reconnect without a hard restart the computer. Whats really strange is that I'm still connected to the router fine, I can ping it, and other machines on the network, but I cannot get beyond to the WAN. My router is configured to give the server a static IP (which it has) and the server is not running a firewall at all (so its not that).
Anyone have any idea what might be going on?[B]

Things I have tried that don't work:[/B]

```
nmcli con down "Wired connection 1"; nmcli con up "Wired connection 1"
```
```
sudo service network-manager restart
```

**Other details:**
Ubuntu 16.04
```
> lspci | grep Ethernet
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5723 Gigabit Ethernet PCIe (rev 10)
```
```
> ifconfig

ifconfig
eth0      Link encap:Ethernet  HWaddr 3c:4a:92:7a:f8:51  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::3e4a:92ff:fe7a:f851/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9007696 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24966368 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10219897210 (10.2 GB)  TX bytes:32511985007 (32.5 GB)
          Interrupt:18 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:573406 errors:0 dropped:0 overruns:0 frame:0
          TX packets:573406 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:54659283 (54.6 MB)  TX bytes:54659283 (54.6 MB)


tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.8.0.1  P-t-P:10.8.0.2  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8803 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:0 (0.0 B)  TX bytes:3331760 (3.3 MB)


tun1      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.60.10.6  P-t-P:10.60.10.5  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:49256 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38940 errors:0 dropped:2039 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:60037070 (60.0 MB)  TX bytes:3182594 (3.1 MB)



```

```

tracepath -n 8.8.8.8
 1?: [LOCALHOST]                                         pmtu 1500
 1:  no reply
 2:  no reply
 3:  no reply
 4:  no reply
 5:  no reply

```

---

### Post by johndough2 on 2017-07-06
Hi

I didn't have a clue about the problem, but I did pick up on your ability to ping.  

Therefore I had a thought, it is not your ethernet that is the problem but the tunneling link that is being dropped and not picked up again.

There is a connection from the server to the router cuz it pings, so I would look at processes for the tunnelling and see if one need's a kick to re-start.

I notice you are using 2 private IP ranges (192.168.0.0 and 10.0.0.0) and do wonder about the routing protocol.

I use these - ping LOOPBACK  &  ping MICROSOFT.COM, you ping Google? 8.8.8.8.
Do you ping the gateway 192.168.1.?, then the 10.?.?.? and find all well?

If so I still thing config file or process need attention.

---

### Post by nickschurch on 2017-07-06
Thanks for the reply. I figured it out actually. The problem was actually being caused by the VPN I use - which I use by default because... well, why wouldn't you. It seems that I had an unholy trinity of changes that occured at the same time that made it difficult for me to track down - I changed my ISP, my router, and the VPN provider changed something at the same time. I didn't realise the latter had happened actually at all. I eventually found the solution here:

[https://www.reddit.com/r/PrivateInternetAccess/comments/646mfc/vpn_causing_drop_outs_help/](https://www.reddit.com/r/PrivateInternetAccess/comments/646mfc/vpn_causing_drop_outs_help/)

Of course, disabling the VPN and tesing the conenction for a long period would have told me where the problem was, but since it'd always been rock solid I didn't think to even try! 20:20 huh.

Thanks anyway.

---

