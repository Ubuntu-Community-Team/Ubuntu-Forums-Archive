---
title: "Network unusable right out of the box"
date: 2007-02-19
forum: Networking &amp; Wireless
---

### Post by The MJ on 2007-02-19
I just installed Ubuntu 6.10 onto a separate partition of my hard drive. Everything went smoothly, but I have no internet access. Whenever I ping anything but localhost I get
> connect: Network is unreachable

ifconfig returns
> eth0
Link encap: Ethernet HWaddr 00:13:D4:1B:4F:DF
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets: 0 errors: 0 dropped: 0 overruns: 0 frame: 0
TX packets: 0 errors: 0 dropped: 0 overruns: 0 carrier: 0
collisions: 0 txqueuelen: 1000
RX bytes: 0 (0.0 b) TX bytes: 0 (0.0 b)
Interrupt: 193


and netstat -nr and route return empty tables (there are no rows)

All of the quoted text was copied by hand so it might not be perfect.

Thanks for any suggestions,
-Max

---

### Post by chili555 on 2007-02-19
And when you went to System -> Administration -> Networking and selected eth0 Properties and enabled the interface and selected DHCP, what happened?

What is the output of sudo ifup eth0?

---

### Post by The MJ on 2007-02-19
In the networking box, it says that eth0 is already enabled and configured with dhcp.
ifup eth0 returns "ifup: interface eth0 already configured"

Just to double check, I tried pinging my router again, but I still get the same error

---

### Post by gradedcheese on 2007-02-20
Don't ping until ifconfig shows that you have an IP address on eth0 ;)

Try manually asking for an IP address:

```

sudo killall dhclient
sudo dhclient eth0

```

does that work?  Also, sometimes it helps to reload the driver at least as a test.  Post the output of "lspci" (the line starting with Network Controller) and we'll see what chipset you have, and then what driver.  Your MAC address looks like Asus, who probably use someone else's chips.

---

### Post by The MJ on 2007-02-20
Well I got it to work. It turns out that i have 2 network cards and it was trying to use the one that wasn't plugged in! I had almost completely forgotten I had two.

Thanks for your help,
-Max

---

