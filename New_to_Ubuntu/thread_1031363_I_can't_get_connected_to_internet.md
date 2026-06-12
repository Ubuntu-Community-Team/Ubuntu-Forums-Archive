---
title: "I can't get connected to internet"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by sssbobbyr on 2009-01-05
I am running ubuntu 6.06 inside windows as a vm

my machine is connected to the internet 

message said it scanned 1 interface, but access concentrator of my provider did not respond.
another running ppoe process may control the modem.

I am running through a router, that got anything to do with it?

---

### Post by superprash2003 on 2009-01-05
in windows do you require a dialer to connect to the internet?? in ubuntu go to the terminal and type ifconfig and post output here

---

### Post by sssbobbyr on 2009-01-05
looks something like this

eth0	Link encap:Ethernet Hwaddr 08:00:27:A2:84:17
	inet addr:10.0.2.15  Bcast:10.0.2.55  Mask:255.255.0
	inet6 addr: fe80::a00:27ff:fea2:8417/64 Scope:Link
	UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
	RX packets:416 errors:0 dropped:0 overruns:0 frame:0
	TX packets:461 errors:0 dropped:0 overruns:0 carrier:0
	collissions:0 txqueulen:1000
	RX bytes:32040 (31.2 KiB)  TX bytes:34508 (33.6Kib)
	interrupt:11 Base address:0xc020


lo	Link encap:Local Loopback
	inet addr:127.0.0.1  Mask:255.0.0.0
	inet6 addr:  ::1/128 Scope/Host
	UP LOOPBACK RUNNING MTU:16436 Metric:1
	Rx packets:239 errors:0 dropped:0 overruns:0 frame:0
	TX packets:239 errors:0 dropped:0 overruns:0 carrier:0
	collisions:0 txqueulen:0
	Rxbytes:11972 (11.6KiB) TX bytes:11972 (11.6KiB)

---

### Post by sssbobbyr on 2009-01-05
looks something like this

eth0	Link encap:Ethernet Hwaddr 08:00:27:A2:84:17
	inet addr:10.0.2.15  Bcast:10.0.2.55  Mask:255.255.0
	inet6 addr: fe80::a00:27ff:fea2:8417/64 Scope:Link
	UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
	RX packets:416 errors:0 dropped:0 overruns:0 frame:0
	TX packets:461 errors:0 dropped:0 overruns:0 carrier:0
	collissions:0 txqueulen:1000
	RX bytes:32040 (31.2 KiB)  TX bytes:34508 (33.6Kib)
	interrupt:11 Base address:0xc020


lo	Link encap:Local Loopback
	inet addr:127.0.0.1  Mask:255.0.0.0
	inet6 addr:  ::1/128 Scope/Host
	UP LOOPBACK RUNNING MTU:16436 Metric:1
	Rx packets:239 errors:0 dropped:0 overruns:0 frame:0
	TX packets:239 errors:0 dropped:0 overruns:0 carrier:0
	collisions:0 txqueulen:0
	Rxbytes:11972 (11.6KiB) TX bytes:11972 (11.6KiB)

---

### Post by sssbobbyr on 2009-01-05
except with everything tabbed in from the "eth0" and "lo" at the start of the paragraphs

---

### Post by donkyhotay on 2009-01-05
According to that, you have an IP address. What are you using to run the VM? I know with vmplayer you have to specify the option within settings to either bridge or NAT your network connection for your VM.

---

### Post by sssbobbyr on 2009-01-05
I am running a sunx vitual box

---

### Post by sssbobbyr on 2009-01-05
sun xVM vitual box make that

I was following the psychocat instructions

---

### Post by donkyhotay on 2009-01-05
According to this:
[http://www.virtualbox.org/wiki/User_FAQ](http://www.virtualbox.org/wiki/User_FAQ)
There are occasionally problems with DNS using a windows host so lets find out if this is an actual internet problem or a DNS problem. What are the results of
```
ping -c5 74.125.19.104
```
This IP address is one of googles, if you're curious.

---

### Post by sssbobbyr on 2009-01-05
i'll try it right now

---

### Post by sssbobbyr on 2009-01-05
PING 74.125.19.104 (74.125.19.104) 56(84) bytes of data.
64 bytes from 74.125.19.104: icmp seq=1 ttl=241 time=97.9ms
64 bytes from 74.125.19.104: icmp seq=1 ttl=241 time=55.9ms
64 bytes from 74.125.19.104: icmp seq=1 ttl=241 time=39.8ms
64 bytes from 74.125.19.104: icmp seq=1 ttl=241 time=56.1ms
64 bytes from 74.125.19.104: icmp seq=1 ttl=241 time=32.4ms

---74.125.19.104 ping statistics ---
5 packets transmitted, 5 recieved, 0% packet loss, time 4025ms
rtt min/avg/max/mdev = 32.475/56.464/97.916/22.668 ms

---

### Post by donkyhotay on 2009-01-05
> **sssbobbyr said:**
> PING 74.125.19.104 (74.125.19.104) 56(84) bytes of data.
64 bytes from 74.125.19.104: icmp seq=1 ttl=241 time=97.9ms
64 bytes from 74.125.19.104: icmp seq=1 ttl=241 time=55.9ms
64 bytes from 74.125.19.104: icmp seq=1 ttl=241 time=39.8ms
64 bytes from 74.125.19.104: icmp seq=1 ttl=241 time=56.1ms
64 bytes from 74.125.19.104: icmp seq=1 ttl=241 time=32.4ms

---74.125.19.104 ping statistics ---
5 packets transmitted, 5 recieved, 0% packet loss, time 4025ms
rtt min/avg/max/mdev = 32.475/56.464/97.916/22.668 ms

This is good, this means you actually do have internet but the DNS isn't being resolved. Unfortunately this is a problem with your host windows DNS and how your VM handles it and I don't know your VM enough to fix it (someone else here may however). If you don't know, DNS is what translates web addresses humans understand to IP addresses computers understand. For example you type in [www.google.com](www.google.com) and DNS translates this to 74.125.19.104 for you automatically. So long as you have the specific IP address you can still use the internet. For example to bring up the google home page just type 74.125.19.104 into the firefox address bar and it will show up. As I mentioned previously this is a known issue reported at [http://www.virtualbox.org/wiki/User_FAQ](http://www.virtualbox.org/wiki/User_FAQ) or without DNS at [http://88.198.19.108/wiki/User_FAQ](http://88.198.19.108/wiki/User_FAQ).

---

### Post by nandemonai on 2009-01-05
"To work around this problem, configure a working DNS server in the network configuration inside the guest OS."

---

### Post by sssbobbyr on 2009-01-05
thanks for the help
ill keep slogging away at it

---

### Post by sssbobbyr on 2009-01-05
i was looking at that just now
wondering what it means

---

### Post by nandemonai on 2009-01-05
> **sssbobbyr said:**
> i was looking at that just now
wondering what it means

edit /etc/resolv.conf inside the guest and add a working dns server.

```
nameserver ip.address.of.working.dns.here
```

---

### Post by donkyhotay on 2009-01-05
Take a look at these how-tos:
[http://ulyssesonline.com/2007/11/07/how-to-setup-a-dns-server-in-ubuntu/](http://ulyssesonline.com/2007/11/07/how-to-setup-a-dns-server-in-ubuntu/)

[http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html](http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html)

good luck!

---

### Post by sssbobbyr on 2009-01-05
> **nandemonai said:**
> edit /etc/resolv.conf inside the guest and add a working dns server.

```
nameserver ip.address.of.working.dns.here
```

do wha?

---

### Post by sssbobbyr on 2009-01-05
> **nandemonai said:**
> "To work around this problem, configure a working DNS server in the network configuration inside the guest OS."
still not getting it

---

### Post by sssbobbyr on 2009-01-05
still not getting it 
the edit /etc/resolv. conf thing

---

### Post by donkyhotay on 2009-01-05
> **sssbobbyr said:**
> do wha?

Normally you have a DNS server provided by your ISP and normally DNS issues require that you tell your computer where this server is located so that it can use DNS. This is what nandemonai is trying to suggest. Here's a step-by-step though for you. On the windows machine goto start > run, type in cmd, press ok, you should then see a DOS prompt. At the prompt type
```
ipconfig /all
```
and then look for an entry that says DNS servers and write down the number listed after it. On linux bring up a terminal and type
```
sudo gedit /etc/resolv.conf
```
look for a line that begins with nameserver. On that line (after the nameserver) you will see an IP address (probably 127.0.0.1 based on what I've found about virtualbox). You need to erase the old number and replace it with the number you wrote down previously. Save the file and close out of it and you should be ready to go.

//edit: BTW be a little patient on the forums here, remember we're providing voluntary support and it sometimes takes a little while.

---

### Post by sssbobbyr on 2009-01-05
I think i got it by pure luck

in settings on the vm i changed the 

NAT to host interface

seems to be working

thanks for all the patience

you really gotta want it with this linux

---

### Post by donkyhotay on 2009-01-05
> **sssbobbyr said:**
> you really gotta want it with this linux

Sometimes, but actually this particular problem you had was more due to the VM then with linux itself. Glad it's working regardless of how it was done. Don't forget to mark this as solved. (c:

---

