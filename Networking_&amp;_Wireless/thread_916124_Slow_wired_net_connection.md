---
title: "Slow wired net connection"
date: 2008-09-10
forum: Networking &amp; Wireless
---

### Post by sunilkumar on 2008-09-10
I am very new to UBUNTU and learning new new things everyday.
My net is very slow. The out put of ifconfig is:

sunil@sunil-desktop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1d:7d:74:6e:5b  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38885 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32012 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28224265 (26.9 MB)  TX bytes:5769351 (5.5 MB)
          Interrupt:221 Base address:0x4000 

sunil@sunil-desktop:~$ 

Can anybody inform me why it is slow (See RX and TX bytes-even if it is not indicating the speed, my experience with common sites also very bad). In Windows, no problem in connection. Now I have to wait few minutes to load the pages of yahoo or google. Many times blank white screen saying read or transferring data ..waiting for blah blah site.. in the down right side of the browser bar.

---

### Post by Julius1988 on 2009-01-06
I am having the same issue too, I don't know whats wrong I faced this problem in all the distros i tried.

---

### Post by aeronotix on 2009-01-06
You might try to lower your MTU, this is the Maximum Transmission Upload. You should be able to access your router then alter the the MTU from there. 

This has helped me before. Could help for you. 1400 is a good place to start.

---

### Post by superprash2003 on 2009-01-06
also try using opendns servers - 208.67.222.222 and 208.67.220.220 [http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by Iowan on 2009-01-06
You might try disabling IPv6.  Ubuntu *seems* to try IPv6 first - although it's becoming more common, if your router or ISP doesn't recognize IPv6, it might cause the slowdown.

Re: post #6 - It's not often I get posted first :)

---

### Post by aeronotix on 2009-01-07
> **Iowan said:**
> You might try disabling IPv6.  Ubuntu *seems* to try IPv6 first - although it's becoming more common, if your router or ISP doesn't recognize IPv6, it might cause the slowdown.

Yeah I came back to post this message but was beaten to it! :D

---

