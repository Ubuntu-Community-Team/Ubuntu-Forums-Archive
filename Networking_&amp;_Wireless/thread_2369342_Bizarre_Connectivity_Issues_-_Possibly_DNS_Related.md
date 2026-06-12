---
title: "Bizarre Connectivity Issues - Possibly DNS Related"
date: 2017-08-21
forum: Networking &amp; Wireless
---

### Post by hildy-guitar on 2017-08-21
I'm working with a fresh install of Ubuntu, and I'm having a strange issue that I believe is DNS-related, but I cannot figure out how to fix it. In a nutshell, I am connecting to the network, but I cannot pull down any websites.

I will say right up front though, that all of my other devices-including a VirtualBox Instance of Ubuntu created with the same iso file I used to install to the problem pc-are connecting and going out to the internet just fine. Also, changing the settings in the network ui's "edit connection" has no effect.

Here's the gist of the issue. If I ping an IP, 8.8.8.8 for instance, eveything looks ok. However, if I ping or use the host command on a host name, then it fails.
[https://i.stack.imgur.com/oHGfJ.png](https://i.stack.imgur.com/oHGfJ.png)

I tried changing the resolv.conf, even though I know the change will be overwritten upon a restart, just to see if it would change the behavior and it did.
But, the ping results did not change, nor can my browser get out to the internet.
[https://i.stack.imgur.com/JWAkV.png](https://i.stack.imgur.com/JWAkV.png)

I've tried just about every solution I can find on the interwebs, to no avail. I'm really beating my head against a wall here, so any help is appreciated.

---

### Post by ajgreeny on 2017-08-22
Please use the default font when posting, and do not add large images inline as you did for terminal output.

It is much easier and more useful to use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by johndough2 on 2017-08-22
Hi

ping just google.com

However, the internet is reachable, but as you surmise the world wide web is not.

So what would ifconfig -a tell you?

```
@DESKTOP-56DAME0:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr b0:5a:da:de:84:28
          inet addr:192.168.1.71  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::18bd:458c:6676:214f/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
and there is no gateway listed, let alone DNS server.

Windows gives... 
```
 Default Gateway . . . . . . . . . : 192.168.1.254
   DHCP Server . . . . . . . . . . . : 192.168.1.254

```
Which seems less than perfect to me.

ERR I just engaged brain, and while still a little foggy...

www would want port 80?
ping uses a different protocol.

So is it a port blocking?  OR a protocol missing?

---

### Post by hildy-guitar on 2017-08-22
> **ajgreeny said:**
> Please use the default font when posting, and do not add large images inline as you did for terminal output.

It is much easier and more useful to use **Code-Tags** for terminal output. See my signature below for a **How-to**

Thanks for the info. I'll try it out in this reply to see how it works. This just a simple route command. I'd love it if you could have a look at the results and give your input on the issue at hand, in addition to your advice on forum mores. 

```

hildy@Scorpion-5-Dio:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         gateway         0.0.0.0         UG    600    0        0 wlp4s0
link-local      *               255.255.0.0     U     1000   0        0 wlp4s0
192.168.0.0     *               255.255.255.0   U     600    0        0 wlp4s0

```

---

### Post by hildy-guitar on 2017-08-22
> **johndough2 said:**
> Hi

ping just google.com

However, the internet is reachable, but as you surmise the world wide web is not.

So what would ifconfig -a tell you?

```
@DESKTOP-56DAME0:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr b0:5a:da:de:84:28
          inet addr:192.168.1.71  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::18bd:458c:6676:214f/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
and there is no gateway listed, let alone DNS server.

Windows gives... 
```
 Default Gateway . . . . . . . . . : 192.168.1.254
   DHCP Server . . . . . . . . . . . : 192.168.1.254

```
Which seems less than perfect to me.

ERR I just engaged brain, and while still a little foggy...

www would want port 80?
ping uses a different protocol.

So is it a port blocking?  OR a protocol missing?

I'll try to reply to your post inline.

When you ask "what will ifconfig -a tell you?" I'm not sure if you mean to say that it won't tell you much, or if you'd like me to run that command and see what the output is. In case it's the latter, here is the ouput:
```

enp5s0f0  Link encap:Ethernet  HWaddr 00:90:f5:bd:68:a4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2172 (2.1 KiB)  TX bytes:2172 (2.1 KiB)


wlp4s0    Link encap:Ethernet  HWaddr 24:77:03:08:95:fc  
          inet addr:192.168.0.11  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2677:3ff:fe08:95fc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6068 errors:0 dropped:1 overruns:0 frame:0
          TX packets:5038 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2316022 (2.2 MiB)  TX bytes:648181 (632.9 KiB)



```

As for a missing protocol, or a firewall blocking my traffic, I don't think that's the case. My thinking is that unless Ubuntu's third party software that is installed on installation contains a software-level firewall, the traffic sent from the problem machine is going through the same network as all of my others. As I said in my original question, all of those are working fine, including a virtual instance of Ubuntu that was created in VirtualBox using the exact same iso file that was used to install to the problem machine; and when I say that it's the same file, I don't mean that I downloaded it from the same place, I mean I used Unetbootin and my other laptop to burn a thumb drive installation media after choosing the exact file. Thoughts?

---

### Post by hildy-guitar on 2017-08-22
Thankfully, I found a solution to this problem. Or more accurately, I found an article written by someone who experienced this same issue with Ubuntu 17.04 and thankfully had more knowledge than myself.

This gist of it is that it is indeed a DNS issue. The problem is being caused by a service called "systemd-resolved." More specifically, the DNSSEC function of the service is not playing well with resolv.conf. The fix is to either disable that feature (not secure) or replace it with another service called "unbound." In my case, I followed the author's steps to disable DNSSEC, and it fixed the problem immediately. That sufficiently proved to me that it was the issue; so, I then followed his steps to replace systemd-resolved with unbound. I can now browse the internet with abandon. 

Here is a link to the article. If anyone would like to chime in with some in-depth technical explanation, I would enjoy it. Otherwise, thanks for tuning in. 

article:
[http://www.hecticgeek.com/2017/04/ubuntu-17-04-systemd-dns-issues/](http://www.hecticgeek.com/2017/04/ubuntu-17-04-systemd-dns-issues/)

---

