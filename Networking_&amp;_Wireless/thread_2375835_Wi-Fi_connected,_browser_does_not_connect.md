---
title: "Wi-Fi connected, browser does not connect"
date: 2017-10-27
forum: Networking &amp; Wireless
---

### Post by rolfUser on 2017-10-27
That's basically it.
I run Ubuntu 17.04. I was ready to upgrade to 17.10 when the connection just didn't want to work with the Software Updater. The Wi-Fi icon on the top-right of the desktop says there is a connection--the icon never fluctuates or anything--as if nothing is wrong with the connection. 
Somehow neither Chrome nor Firefox will display web pages.
Windows 10 is dual-booted on this same machine. Internet works just fine on Windows.
I'm not sure where to start/ to restore the Internet connection for real on Ubuntu.
Any ideas?

---

### Post by chili555 on 2017-10-28
Please open a terminal and run and post:```
ping -c3 8.8.8.8
ping -c3 www.ubuntu.com
sudo resolvconf -u
```Thanks.

---

### Post by rolfUser on 2017-10-28
> **chili555 said:**
> Please open a terminal and run and post:```
ping -c3 8.8.8.8
ping -c3 www.ubuntu.com
sudo resolvconf -u
```Thanks.

**input**: ping -c3 8.8.8.8

**output**:
```

PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=57 time=15.3 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=57 time=14.5 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=57 time=12.9 ms


--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 12.935/14.274/15.311/0.993 ms

```

**input**: ping -c3 [www.ubuntu.com]("http://www.ubuntu.com")
**output**:
```

ping: www.ubuntu.com: Name or servicenot known

```

**input**: sudo resolvconf -u
**output**: terminal just asks for my password. No output.


Nothing changes. The problem still persists/

---

### Post by chili555 on 2017-10-29
I suggest that you edit connections in Network Manager and try specific DNS nameservers, like this: 

[IMG]http://3.bp.blogspot.com/-7yAL1fjG_NY/TjqeB_PE-XI/AAAAAAAAAwk/USkoevbfSAg/s1600/Network-Manager-DNS+%25283%2529.png[/IMG]

Of course, select ethernet or wireless as needed.

Reboot.

---

### Post by tiafefa on 2017-10-30
I have this same exact issue but I dual boot 16.04 LTS and I have just not been able to figure out why my internet is not working. Ive tried what you have suggested but still nothing. 

[http://pastebin.ubuntu.com/25852780/](http://pastebin.ubuntu.com/25852780/)

Any ideas on what I can do?

---

### Post by rolfUser on 2017-10-30
> **chili555 said:**
> I suggest that you edit connections in Network Manager and try specific DNS nameservers, like this: 

[IMG]http://3.bp.blogspot.com/-7yAL1fjG_NY/TjqeB_PE-XI/AAAAAAAAAwk/USkoevbfSAg/s1600/Network-Manager-DNS+%25283%2529.png[/IMG]

Of course, select ethernet or wireless as needed.

Reboot.

I tied this very setting, but when I entered the numbers under **DNS Servers**, it doesn't allow me to save.
Couldn't I just create a new connection rather than edit what I am working with?

---

### Post by chili555 on 2017-10-30
> I tied this very setting, but when I entered the numbers under DNS Servers, it doesn't allow me to save.Did you *first *select Automatic (DHCP) Addresses only before you tried to save?

---

### Post by chili555 on 2017-10-30
> **tiafefa said:**
> I have this same exact issue but I dual boot 16.04 LTS and I have just not been able to figure out why my internet is not working. Ive tried what you have suggested but still nothing. 

[http://pastebin.ubuntu.com/25852780/](http://pastebin.ubuntu.com/25852780/)

Any ideas on what I can do?Did you also try the DNS nameservers as I suggested here?

---

### Post by tiafefa on 2017-10-30
I did. Thats the first thing I tried.

---

### Post by rolfUser on 2017-11-01
> **chili555 said:**
> Did you *first *select Automatic (DHCP) Addresses only before you tried to save?

Yes I did. 
I tried both **Automatic (DHCP)** and **Automatic (DHCP) Address Only** and I get the same result: when I enter anything into **Additional DNS Servers**, the **Save **button greys itself out so that I cannot select it.
[ATTACH=CONFIG]277366[/ATTACH][ATTACH=CONFIG]277367[/ATTACH]
**Require IPv4 addressing for this connection to complete **does not affect anything whether it is checked or not checked.

---

### Post by rolfUser on 2017-11-03
You know, I plan to upgrade to 17.10 anyway. I haven't yet. What if I just download it to my USB drive and attempt to install it to the partition with 17.04? My guess is that this would override the settings back to normal with a new and upgraded kernel.

---

