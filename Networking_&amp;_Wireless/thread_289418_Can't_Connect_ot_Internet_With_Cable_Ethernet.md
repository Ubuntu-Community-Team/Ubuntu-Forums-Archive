---
title: "Can't Connect ot Internet With Cable Ethernet"
date: 2006-10-30
forum: Networking &amp; Wireless
---

### Post by m_vrik on 2006-10-30
I have a direct cable network connection but can't get connected to the internet.  I'm using Ubuntu 6.06 and the Network Monitor indicates that the Eth0 connection is receiving input from the cable.  When I Ping the IP address for Eth0 it doesn't respond, only to the IPv4 Local Host.  How can I make this connection work so that I can get on the internet?:confused:

---

### Post by gustolove on 2006-10-31
ok so the picture i see is:

|computer|-----|cable modem|----|service provider (internet)|

^^is that correct?^^

or is it more like:

|computer|------|router|------|cable modem|-------|isp (internet)|

---

### Post by jpkotta on 2006-10-31
Try ```
ping 192.168.0.1
``` if you have a router or ```
ping 192.168.100.1
``` if you just have the modem.

---

### Post by mips on 2006-10-31
You need to give us more information...

---

### Post by m_vrik on 2006-10-31
It's |computer|....|cable modem|......|ISP Internet|.

---

### Post by m_vrik on 2006-10-31
After bootup, the Connection Monitor shows "lo" available but "idle."  Under the Support Tab, "lo's" IP Protocol -> IPv4, Address -> "127.0.0.1", Sub Net Mask -> "255.0.0.0"; Network Drive Type -> "Local Loopback", Address -> 00:00:00:00:00:00.

Then, I highlighted "lo" and typed in "eth0" with following results, General Tab Name -> "eth0", Status -> switching between "receiving" & "idle" (i.e activity evident.  Under the Support Tab, Network Device Type -> "Ethernet", Address -> "00:02:A5:B6:18:0F".  Pressed the Configure button and was switched to the Network Settings Dialogue Box indicating; "Ethernet connection is active & enabled box was checked", Configuration shown as DHCP.  General tab shows Hostname as "lem-laptop", DNS tab is blank, Hosts tab shows a variety of IP Addresses and Aliases.  Of all these addresses the only ones that I can ping are "127.0.0.1" and "::1" with these respective aliases, "localhost lem-laptop" and "ip6-localhost ip6-loopback".  I am trying to ping under both the "lo" and "eth0" connection but only the two above give any response.  I hope this is not too much info.

---

### Post by jpkotta on 2006-10-31
No such thing as too much info.  What was the result of the ping commands?  I had similar trouble this summer, when I hooked straight into a modem (usually I have a router).  The gateway address of modems is 192.168.100.1 usually, while routers are 192.168.0.1 usually.

BTW, if you're going straight into the modem, it's a good idea to use a firewall.  Try Firestarter.

---

### Post by m_vrik on 2006-10-31
I couldn't get any response when I tried to ping "192.168.100.1" when using the IPv6 eth0 connection.

---

### Post by m_vrik on 2006-10-31
JPKOTTA,
I decided to try and connect through my Xincom router between the cable modem and my laptop and Dapper connected right up.  Thanks to all who offered your ideas, they were all helpfull.

---

