---
title: "Unable to connect to internet with 8.04"
date: 2008-06-09
forum: Networking &amp; Wireless
---

### Post by chesman on 2008-06-09
Hello,

I grabbed a copy of 8.04 last week and wanted to try it out, used older versions with no issues on the same computer i have now. When i install / run live cd I get the same problems.

It will not let me connect to the internet what so ever, I an connect to the router, browse internal network, but cannot connect to the internet.

Using a Dell Dimension 9200c with integrated NIC. 

Any ideas would be great, I want to dump widows VERY soon

---

### Post by superprash2003 on 2008-06-09
in your terminal type ping google.com and post output

---

### Post by rickyjones on 2008-06-09
> **superprash2003 said:**
> in your terminal type ping google.com and post output

In addition please post the results of the following commands.

```

cat /etc/resolv.conf

```

```

ifconfig eth0

```

Thanks,
Richard

---

### Post by chesman on 2008-06-11
cat /etc/resolv.conf

> search eastlink.ca
nameserver 192.168.0.1


ifconfig eth0
> 
eth0      Link encap:Ethernet  HWaddr 00:19:d1:0c:7e:7f  
          inet addr:192.168.0.196  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d1ff:fe0c:7e7f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:1330 (1.2 KB)  TX bytes:8785 (8.5 KB)
          Base address:0xecc0 Memory:dffe0000-e0000000 

---

### Post by rickyjones on 2008-06-11
Looks like you are getting information without issue. Here are a few more tests to run:

```

ping www.google.com

```

```

ping 74.125.47.147

```

```

ping 192.168.0.1

```

```

ping 208.67.222.222

```

These ping tests should tell us where the problem is. The last ping,  208.67.222.222, is the OpenDNS DNS server. Try using that one in your /etc/resolv.conf file instead of 192.168.0.1. It might just be that your router is having nameserver issues as well.

Sincerely,
Richard

---

### Post by chesman on 2008-06-11
It works perfectly in XP though, and used to work no problem with 6.10, but wont now.

I will try those and add the output later tonight when I get home.

i REALLY want to get this corrected :)

Thanks for all the help so far guys!

---

### Post by chesman on 2008-06-11
I should also note, since i seem to have forgotten to paste it above.

When i use the network tools and try to click configure on eth0 it states that the interface does not exist....

---

### Post by chesman on 2008-06-12
Okay, Its fixed,


Checked on my router again, since that is as far as i could ping, there was two MAC addresses blocked that i had setup to block people in my old apt from stealing the connection. So i removed them, and bam i started to connect.... go figure..


Thanks guys :)

---

