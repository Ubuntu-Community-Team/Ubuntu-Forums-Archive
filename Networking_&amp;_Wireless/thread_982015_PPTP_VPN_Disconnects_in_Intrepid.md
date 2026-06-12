---
title: "PPTP VPN Disconnects in Intrepid"
date: 2008-11-14
forum: Networking &amp; Wireless
---

### Post by Akoi Meexx on 2008-11-14
I use a PPTP connection to log into work servers when I'm at home. After upgrading to Intrepid and discovering the password-saving bug with vpn, I still have issues with the connection. Whenever I connect to the vpn, I establish a connection for a minute or less. I have just about enough time to ssh into a work server and ls -l before the connection drops and Network Manager tells me that "The VPN connection 'VPN Name Here' failed."

This is what I get when I check the messages log, from when the connection is requested and established, to when it is abnormally terminated. Anyone have any ideas? Could really use the help.

**/var/log/messages**```

Nov 14 10:11:54 johnathan-laptop pppd[17080]: Plugin /usr/lib/pppd/2.4.4/nm-pptp-pppd-plugin.so loaded.
Nov 14 10:11:54 johnathan-laptop pppd[17080]: pppd 2.4.4 started by root, uid 0
Nov 14 10:11:54 johnathan-laptop pppd[17080]: Using interface ppp0
Nov 14 10:11:54 johnathan-laptop pppd[17080]: Connect: ppp0 <--> /dev/pts/1
Nov 14 10:11:58 johnathan-laptop pppd[17080]: CHAP authentication succeeded
Nov 14 10:11:58 johnathan-laptop pppd[17080]: MPPE 128-bit stateless compression enabled
Nov 14 10:11:58 johnathan-laptop pppd[17080]: found interface wlan0 for proxy arp
Nov 14 10:11:58 johnathan-laptop pppd[17080]: local  IP address <!-- Edited Out IP -->
Nov 14 10:11:58 johnathan-laptop pppd[17080]: remote IP address <!-- Edited Out IP -->
Nov 14 10:11:58 johnathan-laptop pppd[17080]: primary   DNS address <!-- Edited Out IP -->
Nov 14 10:11:58 johnathan-laptop pppd[17080]: secondary DNS address <!-- Edited Out IP -->
Nov 14 10:12:08 johnathan-laptop pppd[17080]: Modem hangup
Nov 14 10:12:08 johnathan-laptop pppd[17080]: Connect time 0.2 minutes.
Nov 14 10:12:08 johnathan-laptop pppd[17080]: Sent 1759 bytes, received 60 bytes.
Nov 14 10:12:08 johnathan-laptop pppd[17080]: Connection terminated.
Nov 14 10:12:08 johnathan-laptop pppd[17080]: Exit.

```

---

### Post by Akoi Meexx on 2008-11-14
*coughbump*

---

### Post by Akoi Meexx on 2008-11-17
Anyone else having this problem at all?

---

### Post by Jayock on 2008-11-17
what does your ifconfig look like while connected to VPN?

---

### Post by Akoi Meexx on 2008-11-17
**ifconfig**
```
johnathan@johnathan-laptop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:302 errors:0 dropped:0 overruns:0 frame:0
          TX packets:302 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:21060 (21.0 KB)  TX bytes:21060 (21.0 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:*.*.*.43  P-t-P:*.*.*.43  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1496  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:96 (96.0 B)  TX bytes:148 (148.0 B)

wlan0     Link encap:Ethernet  HWaddr ********************************************  
          inet addr:*.*.*.46  Bcast:*.*.*.255  Mask:255.255.248.0
          inet6 addr: fe80::21c:bfff:fe16:bdc4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:229462 errors:0 dropped:0 overruns:0 frame:0
          TX packets:106967 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:205205599 (205.2 MB)  TX bytes:16775306 (16.7 MB)

wmaster0  Link encap:UNSPEC  HWaddr ********************************************  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

**Edit:** That's while currently at work. I have the same issues at home as well.

---

### Post by gfox on 2009-01-26
I'm having this same problem, anybody solved this?

---

### Post by Akoi Meexx on 2009-01-27
No, no one has solved this yet. It would be nice though...

---

### Post by hibliss on 2009-01-27
I have the same problem.

I have searched here and found some threads where people had varying luck.

I also spent quite a bit of time on Google.

This may be a major deal breaker for me in Intrepid. It apparently works fine right out of the box in Hardy :-/

Edit:

This worked for me -- [http://www.splatdot.com/2008/11/19/ubuntu-810-how-connect-microsoft-vpn]("http://www.splatdot.com/2008/11/19/ubuntu-810-how-connect-microsoft-vpn")

I just connected via RDP to a few servers at my office, and a desktop. SUCCESS!!

---

### Post by DFLiddle on 2009-02-09
The link and instructions posted by *hibliss* worked for me, too. I've been struggling along without my VPNs since upgrading to 8.10, and it's fabulous to have them back!

---

### Post by hibliss on 2009-06-11
In case anyone is searching or wondering, I had to do the same thing in Jaunty to get the VPN working.

---

