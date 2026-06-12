---
title: "Getting all traffic to route over VPN (LTS 16.04)."
date: 2017-05-09
forum: Networking &amp; Wireless
---

### Post by David_Partridge on 2017-05-09
I used Network Manager to add a VPN which it brings up when the wired ethernet comes up.

ifconfig shows:

```
ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.38.0.38  P-t-P:10.38.0.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1400  Metric:1
          RX packets:71 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:3993 (3.9 KB)  TX bytes:74 (74.0 B)
```

However what I want to happen is for all traffic except the local network (192,.168.129.0) to be routed via the PPTP VPN.

If I try to edit the VPN settings using network manager "edit connections", all the options are greyed out on all the tabs :(

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=275019&d=1494353155[/IMG]

Please could someone put me out of my misery and tell me what I need to do (my google foo seems to have deserted me).

Thanks
Dave

---

### Post by TheFu on 2017-05-11
**route** output please.
You know that PPTP isn't secure, correct?

---

### Post by David_Partridge on 2017-05-11
Never mind I got a connection with another VPN working OK without using Network Manager.  Something screwy there I didn't get to the bottom of, I should have closed this thread off.

Sorry, Dave

---

