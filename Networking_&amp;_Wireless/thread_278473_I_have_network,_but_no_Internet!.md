---
title: "I have network, but no Internet!"
date: 2006-10-16
forum: Networking &amp; Wireless
---

### Post by r6mile on 2006-10-16
I have just installed Ubuntu 6.06 on my computer. But I have no internet. I have network though because I tried several ping tests and they worked. What is the problem?

---

### Post by jd65pl on 2006-10-16
[LIST=1]
[*]How do you connect to the internet?
[*]Can you ping a web address?[/LIST]
```
ping www.google.com
```

---

### Post by r6mile on 2006-10-16
I connect to the internet through an RJ45 cable.
I have already tried pinging a web adress and it didn't work. Just in case I also tried to ping one of google's ip adresses but it didn't work either.
What is my problem? I tried sudo ifconfig and everything seems right.

---

### Post by srt4play on 2006-10-16
I think what he was asking was what type of internet you have. Cable? Do you go through a router or straight into your cable modem?

---

### Post by mips on 2006-10-16
Can your ping your routers/modems ethernet port ?

---

### Post by Netherwolf on 2006-10-16
I'm a linux demi-noob with a similar problem to r6mile. I have IP running, albeit oddly slow, and no DNS resolution. I can't ping google.com, but I can ping 64.233.187.99. As you can imagine, my APT updates are well over due. One possible problem is that when I first installed the OS on this system, it had a public IP and the computer adopted itself into my friend's domain. Now, it has neither of these. I had hoped that modifying the etc/network/interfaces file would fix this, but alas! Not working yet. Not sure how to get rid of it's domain fixation.
I also have two NICs in the server, but the second one is disabled via software.
Here's my interfaces:

auto lo eth0
iface lo inet loopback
iface eth0 inet static
        address 192.168.2.222
        netmask 255.255.255.0
        network 192.168.2.0
        broadcast 192.168.2.255
        gateway 192.168.2.1
        dns-nameservers 68.94.156.1, 68.94.157.1

Any thoughts?

---

### Post by r6mile on 2006-10-16
I go through a switch to my ADSL router. 
I can ping the router, and the other computers in the network, but I cannot ping any internet adress.

---

### Post by nothingxs on 2006-10-16
> **r6mile said:**
> I go through a switch to my ADSL router. 
I can ping the router, and the other computers in the network, but I cannot ping any internet adress.

I don't think this is the problem, but have you tried doing sudo dhclient in a prompt?

---

### Post by dbott67 on 2006-10-16
It may just be a DNS issue.  Can you please post the output of the following commands:

```
dbott@dapper:/$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:15:C5:0C:AD:05
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:672 (672.0 b)  TX bytes:672 (672.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:16:CE:31:88:6F
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:ceff:fe31:886f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:36599 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27357 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:37959911 (36.2 MiB)  TX bytes:3283196 (3.1 MiB)
          Interrupt:169 Memory:dfcfc000-dfd00000

dbott@dapper:/$


```

```
dbott@dapper:/$ cat /etc/resolv.conf
nameserver 192.168.1.1

```

The output should be the IP address of your DSL router (in my case, it's **nameserver 192.168.1.1**).

Can you also post the output of **tracepath 72.14.205.104** ([www.google.com)?](www.google.com)?)

-Dave

---

### Post by mips on 2006-10-17
Can you ping 209.85.129.99 ?

Show us the output of **cat /etc/network/interfaces**
Show us the output of **ifconfig -a**
Show us the output of **route -n**

---

### Post by r6mile on 2006-10-17
I don't know why, but today more things are working.
If I put one of Google's IP's (66.102.9.104) on firefox, it loads the Google page. However, no other websites work.
And now I can ping any IP and website and it will work. I don't know how all that is working now, but I'm happy.
Now that there's improvement, what do you think is the problem?

---

### Post by mips on 2006-10-17
DNS/IPv6 comes to mind...

---

### Post by r6mile on 2006-10-17
Thank you, now it's all working. I tried openDNS and it's working now. In fact, I'm writing this from Ubuntu.

---

### Post by Netherwolf on 2006-10-17
This is THE OTHER GUY who can't manage his network connections.
Thanks dbott. It was my /etc/resolv.conf that was messing my connection up.
-NW

---

### Post by dbott67 on 2006-10-18
You're welcome.... glad it's working.

-Dave

---

