---
title: "No wired or wireless Internet on my fresh ubuntu 64 bit installation."
date: 2011-02-11
forum: New to Ubuntu
---

### Post by panderohit on 2011-02-11
Hi. I've just installed ubuntu 10.10 64-bit on my new HP ProBook 4720s (clean install replacing Windows 7). However, my computer does not connect to the internet by either the wired or wireless connection. 

The network manager shows that the connection has been made. When I click 'VPN Connections > Configure VPN', the wireless tab shows Auto Palace (my home connection is called Palace), Last Used: now. Whereas the Wired tab shows 'Auto eth0' Last Used never. 

iwconfig shows:
lo  no wireless extensions
Eth0  no wireless extensions
Wlan0  IEEE 802. Llbgn. ESSID: "Palace"
             Mode: Managed Frequency: 2.462 ghz. Access point: 00:22:15:2B:C2:AA
             Bit Rate=54 mb/s   Tx-Power=20 dbm
             Retry long limit: 7. RTS thr:off. Fragment thr:off
             Power Management: off
             Link Quality=70/70  Signal level=-33 dbm
             Rx invalid nwid:0. Rx invalid crypt:0  Rx invalid frag:0
             Tx excessive retried:0  Invalid misc:0. Missed beacon:0

I know it must be something simple like switching something on or entering my network address somewhere but I can't get my head around it. 

Thanks.

---

### Post by thefasterblueone on 2011-02-11
See if you can ping an address in terminal:

ping yahoo.com

---

### Post by GMachine_24 on 2011-02-12
So, first, are you really trying to connect via a VPN? Or is this just a home network thing?

Also, in the upper task bar if you left click on the icon for wireless connectivity, does it list any networks?

Sometimes, depending on which network manager you use, it will show that a network is connected when, in fact, you're not.

I assume you have your wireless connection set up with the proper password/security code?

---

### Post by panderohit on 2011-02-12
Hi. Yes I did. It says:

ping: unknown host [www.google.com](www.google.com)

---

### Post by panderohit on 2011-02-12
Hi. Yes the password is ok and clicking on the network manager shows:

"Wireless Networks
Palace
Disconnect"

I'm aware that this means that I've connected. Furthermore when I ping the modem it gives the following response:

ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data
64 bytes from 192.168.1.1: icmp_req=1 ttl=64 time=88.8 ms
.
.
and so on

Which probably means that all is well with connecting to the modem over wireless. However the wired connection is not responding.

---

### Post by panderohit on 2011-02-12
Update!!!! IT WORKS!!!

I tried the solution given here: [http://ubuntuforums.org/showthread.php?t=1610783](http://ubuntuforums.org/showthread.php?t=1610783)

It worked for me again. :) I remember it worked for me when I had the same issue with my desktop also. :) Yayyy!!!!

---

