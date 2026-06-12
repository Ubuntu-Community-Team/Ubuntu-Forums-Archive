---
title: "Hacking attempt or a bit of Paranoia?"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by GeordieJedi on 2009-01-16
Hi all, hope your all doing well.

I was hoping for some suggestions or advice on a little surprise I got this afternoon.

I was having a quick look online. and noticed firestarter had another attack/hit,
but when I looked at the log there was an extensive amount of attack attempts within
a short (20 mins timescale).

Now normally I get 1 supposed attempt whenever I start firestarter. (it seems to come
from Samba & It usually looks like this)

```

Time:Jan 16 12:49:38 Direction: Unknown In:wlan0 Out: Port:137 Source:192.168.1.1 Destination:192.168.1.100 Length:78 TOS:0x00 Protocol:UDP Service:Samba (SMB)

```

Anyway Here is a list of what came up on the events list =

```

Time:Jan 16 12:49:38 Direction: Unknown In:wlan0 Out: Port:137 Source:192.168.1.1 Destination:192.168.1.100 Length:78 TOS:0x00 Protocol:UDP Service:Samba (SMB)
Time:Jan 16 13:06:10 Direction: Unknown In:wlan0 Out: Port:39980 Source:192.168.1.1 Destination:192.168.1.100 Length:311 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan 16 13:21:30 Direction: Unknown In:wlan0 Out: Port:45754 Source:67.15.12.17 Destination:192.168.1.100 Length:1492 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jan 16 13:21:30 Direction: Unknown In:wlan0 Out: Port:45761 Source:67.15.12.17 Destination:192.168.1.100 Length:1492 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jan 16 13:21:31 Direction: Unknown In:wlan0 Out: Port:137 Source:192.168.1.1 Destination:192.168.1.100 Length:78 TOS:0x00 Protocol:UDP Service:Samba (SMB)
Time:Jan 16 13:21:33 Direction: Unknown In:wlan0 Out: Port:45754 Source:67.15.12.17 Destination:192.168.1.100 Length:1492 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jan 16 13:21:33 Direction: Unknown In:wlan0 Out: Port:45761 Source:67.15.12.17 Destination:192.168.1.100 Length:1492 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jan 16 13:21:34 Direction: Unknown In:wlan0 Out: Port:137 Source:192.168.1.1 Destination:192.168.1.100 Length:78 TOS:0x00 Protocol:UDP Service:Samba (SMB)
Time:Jan 16 13:21:39 Direction: Unknown In:wlan0 Out: Port:45754 Source:67.15.12.17 Destination:192.168.1.100 Length:1492 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jan 16 13:21:39 Direction: Unknown In:wlan0 Out: Port:45761 Source:67.15.12.17 Destination:192.168.1.100 Length:1492 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jan 16 13:21:46 Direction: Unknown In:wlan0 Out: Port:137 Source:192.168.1.1 Destination:192.168.1.100 Length:78 TOS:0x00 Protocol:UDP Service:Samba (SMB)
Time:Jan 16 13:21:51 Direction: Unknown In:wlan0 Out: Port:45754 Source:67.15.12.17 Destination:192.168.1.100 Length:1492 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jan 16 13:21:51 Direction: Unknown In:wlan0 Out: Port:45761 Source:67.15.12.17 Destination:192.168.1.100 Length:1492 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jan 16 13:21:52 Direction: Unknown In:wlan0 Out: Port:137 Source:192.168.1.1 Destination:192.168.1.100 Length:78 TOS:0x00 Protocol:UDP Service:Samba (SMB)
Time:Jan 16 13:22:15 Direction: Unknown In:wlan0 Out: Port:45754 Source:67.15.12.17 Destination:192.168.1.100 Length:1492 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jan 16 13:22:15 Direction: Unknown In:wlan0 Out: Port:45761 Source:67.15.12.17 Destination:192.168.1.100 Length:1492 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jan 16 13:22:23 Direction: Unknown In:wlan0 Out: Port:137 Source:192.168.1.1 Destination:192.168.1.100 Length:78 TOS:0x00 Protocol:UDP Service:Samba (SMB)
Time:Jan 16 13:23:03 Direction: Unknown In:wlan0 Out: Port:45754 Source:67.15.12.17 Destination:192.168.1.100 Length:1492 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jan 16 13:23:03 Direction: Unknown In:wlan0 Out: Port:45761 Source:67.15.12.17 Destination:192.168.1.100 Length:1492 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jan 16 13:24:39 Direction: Unknown In:wlan0 Out: Port:45754 Source:67.15.12.17 Destination:192.168.1.100 Length:1492 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jan 16 13:24:39 Direction: Unknown In:wlan0 Out: Port:45761 Source:67.15.12.17 Destination:192.168.1.100 Length:1492 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jan 16 13:24:41 Direction: Unknown In:wlan0 Out: Port:137 Source:192.168.1.1 Destination:192.168.1.100 Length:78 TOS:0x00 Protocol:UDP Service:Samba (SMB)
```

A little bit of background, I normally see the samba hit as soon as I start firestarter then once every few hours. (I wasn't too botherd by it, as it happens even if I freshly install Ubuntu. But that's the ONLY hit I've ever seen on firestarter

Now here's my bit of paranoia...When I went down stairs to turn the router on, there was an abandoned car outside of my house. I went upstairs, to the PC and saw all the activity on firestarter. I was wondering if someone had been war-walking/war-driving?

(When doing a quick search of the networks in my area, there are 3. Myself, someone using Sky broadband, and someone with a Netgear router. Both mine and the sky router are encrypted.).

I haven't set up any policies in firestarter, I just set it away in its default configuration.
(I'm in the process of searing how to lock things down as securely as possible).

Now I've been online using Linux tonight for about an hour so far, and only had the 1 "normal" samba hit.

Sorry if the post is too long,
But thanks in advance for any help or suggestions. Very Happy

---

### Post by Daz_S on 2009-01-16
What is your network configuration?

These are client ports and could be used by all manner of software.

To check if your firewall is working (I use ufw, but also have Firestarter installed as I like the way is outputs on the GUI), you could use Steve Gibson's port probe tool at [https://www.grc.com/x/portprobe=45761]("https://www.grc.com/x/portprobe=45761")and change the last five digits as required for your port numbers.  

If you see a Stealth indication, you should be okay from hacking.  If not... maybe you should let us know and some other people can help out.  This will be affected by your internet connection and network configuration though - the online test will check your public IP address, which is probably your router.

---

### Post by minsf on 2009-01-16
for what it worth, whois.net can get you a bit of info about this ip. 
are you using "the planet" as an internet service provider? if yes, maybe these "attacks" are just something from your ISP. on the other hand, it could also be someone in your ISP network... 
maybe you can view the packets via "tcpdump". (on the other hand, if your firewall frops them, then they'll probably never get to the tcpdump.)

---

### Post by GeordieJedi on 2009-01-16
Thanks very much for the replys.

My set-up is as follows

Modem-->Wi-Fi router-->My PC via a Wi-Fi dongle. Im using WPA/WPA2
encryption on both the router and the PC.


@ minsf

No, its not my ISP. I'm based in the UK. And as you rightly say. They're originating from Texas.

---

