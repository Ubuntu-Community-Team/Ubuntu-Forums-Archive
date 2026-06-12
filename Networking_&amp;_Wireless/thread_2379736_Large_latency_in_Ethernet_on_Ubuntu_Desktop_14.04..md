---
title: "Large latency in Ethernet on Ubuntu Desktop 14.04.5 LTS"
date: 2017-12-08
forum: Networking &amp; Wireless
---

### Post by linux2000 on 2017-12-08
Hi, 
   I am having a weird issue on my Dell Latitude 3560 where the ethernet works but when I open a page, it takes about 30 seconds to 1 min but once it opens, the page gets loaded quite fast. This happened after I update the kernel. I have attached the wireless-info.txt file for help with diagnosing the problem. By the way, the wireless does not work at all even before the kernel update. Thanks.

---

### Post by chili555 on 2017-12-09
I notice this in your results:> DNS:             173.212.212.233
    DNS:             8.8.8.8Where do these come from? Did you add them in Network Manager or are they supplied by DHCP automagically?

Here is what I see in a ping test:```
chili@T440p:~$ ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=55 time=8.61 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=55 time=9.78 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=55 time=8.81 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 8.613[COLOR="#FF0000"]/9.071[/COLOR]/9.788/0.519 ms



chili@T440p:~$ ping -c3 173.212.212.233
PING 173.212.212.233 (173.212.212.233) 56(84) bytes of data.
64 bytes from 173.212.212.233: icmp_seq=1 ttl=51 time=113 ms
64 bytes from 173.212.212.233: icmp_seq=2 ttl=51 time=123 ms
64 bytes from 173.212.212.233: icmp_seq=3 ttl=51 time=131 ms

--- 173.212.212.233 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 113.741/[COLOR="#FF0000"]123.008[/COLOR]/131.707/7.345 ms

```It takes, relatively speaking, a loonnnnng time to get a response from your primary DNS nameserver.

You might try setting your own DNS nameservers: [http://farm8.staticflickr.com/7434/11284073675_5f7e637287_z.jpg](http://farm8.staticflickr.com/7434/11284073675_5f7e637287_z.jpg)

I'd enjoy fixing the wireless, by the way. I love a challenge.

---

### Post by linux2000 on 2017-12-12
I would love to make it work as well. But right now I have don't want to spend time in trying to fix it. I migrated to 16.04 and everything works out-of-the-box. Voila! Thanks anyways.

---

