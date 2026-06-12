---
title: "Can't access internet after changing routers"
date: 2015-03-04
forum: Networking &amp; Wireless
---

### Post by dawe-charlie on 2015-03-04
Hey, new to the forums but I have had linux for a couple of years. I am currently running xubuntu on my acer c chromebook and currently can't access the Internet.  It was working fine until I switched routers and now I can only connect to the router and not the Internet.  I am somewhat familiar with terminal commands but I am better at following directions when it comes to fixing specific issues. I have searched forums for a couple of hours and can't seem to get it working. I have tried switching the 2.4ghz to only broadcast b/g but it doesn't work. Any help would be greatly appreciated. If someone could let me know what terminal commands to type to get you pertinent information,  that would be very helpful too. Thanks guys

---

### Post by chili555 on 2015-03-04
If you can reach the router but not the internet, then I doubt it is a driver or Ubuntu issue. I suspect it's something in the way that the router doesn't get an IP address from your internet service provider.

On your computer, do you have an IP address from the router?```
ifconfig
``````
wlan0     Link encap:Ethernet  HWaddr xx:94:6b:99:55:xx
          [COLOR="#FF0000"]inet addr:10.255.16.104[/COLOR]  Bcast:10.255.16.255  Mask:255.255.255.0
          inet6 addr: fe80::5a94:6bff:fe99:55a0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1

```Can you ping the router?```
ping -c3 <gateway_address>
``````
PING 10.255.16.99 (10.255.16.99) 56(84) bytes of data.
64 bytes from 10.255.16.99: icmp_seq=1 ttl=64 time=3.01 ms
64 bytes from 10.255.16.99: icmp_seq=2 ttl=64 time=3.03 ms
64 bytes from 10.255.16.99: icmp_seq=3 ttl=64 time=3.40 ms

--- 10.255.16.99 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 3.019/3.155/3.409/0.185 ms

```If all this is correct, I'd look at the router, not your Ubuntu computer.

---

### Post by houstonbofh on 2015-03-04
Is it a static IP or DHCP?  To get out you need and IP address and a gateway.  However, to get "someplace" you also need a DNS.

From the CLI try;

ping 4.2.2.2
This tests connectivity.

ping [www.google.com](www.google.com)
This tests dns.

---

### Post by dawe-charlie on 2015-03-04
Thanks for the quick responses guys, I can ping the router, 192.168.0.1, and I can also ping 4.2.2.2 but cannot ping google. Sounds like it might be a DNS issues maybe? I do have an iP address from the router as well, 192.168.0.7.

---

### Post by chili555 on 2015-03-04
Does the router have an IP address from the ISP?

[ATTACH=CONFIG]260450[/ATTACH]

---

### Post by dawe-charlie on 2015-03-04
Yeah, I have multiple other things connected with no problem, phones and chromecast and such

---

### Post by chili555 on 2015-03-04
> Sounds like it might be a DNS issues maybe? Yes, indeed. What does this tell us?```
nm-tool
cat /etc/network/interfaces
cat /etc/resolv.conf
```

---

### Post by dawe-charlie on 2015-03-04
I'm leaving for work right now, I gotta figure out how to get the terminal text from my computer to this site....using my phone for Internet now....I'll post the results when I get home from work....thanks for the fast help guys

---

