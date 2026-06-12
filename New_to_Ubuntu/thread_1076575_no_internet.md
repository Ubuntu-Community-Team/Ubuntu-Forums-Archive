---
title: "no internet"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by Mitch9654 on 2009-02-21
well, actually internet is working, but ubuntu isn't quite noticing my eth0 adapter


mitch9654

---

### Post by yeats on 2009-02-21
Could you please open a terminal window and type:

```
ifconfig
```

and paste the output here?  That will give folks a good starting point :-).

---

### Post by Mitch9654 on 2009-02-21
eth0      Link encap:Ethernet  HWaddr 00:07:e9:4c:31:64  
          inet addr:192.168.2.101  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::207:e9ff:fe4c:3164/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:46333 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47741 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:37729625 (35.9 MB)  TX bytes:4658488 (4.4 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1446 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1446 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:72592 (70.8 KB)  TX bytes:72592 (70.8 KB)


you see, if I go to system/administrator/network tools, and then go to the devices tab, click on the drop-down, go to eth0, and click configure, it says "The interface does not exist Check that it is correctly typed and that it is correctly supported by your system."

---

### Post by yeats on 2009-02-21
> eth0 Link encap:Ethernet HWaddr 00:07:e9:4c:31:64
**inet addr:192.168.2.101 Bcast:192.168.2.255 Mask:255.255.255.0**

Well, you've got an IP, so Ubuntu is seeing eth0 fine.  In the terminal, type:

```
ping google.com
```

(you can hit Ctrl-C to stop)

Your output should look something like this:

```
PING google.com (74.125.67.100) 56(84) bytes of data.
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=1 ttl=243 time=13.0 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=2 ttl=243 time=12.6 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=3 ttl=243 time=12.5 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=4 ttl=243 time=13.0 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=5 ttl=243 time=13.7 ms

--- google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3997ms
rtt min/avg/max/mdev = 12.516/13.004/13.718/0.430 ms

```

If it doesn't, post back what it DOES say.

---

### Post by abyssius on 2009-02-21
Mitch9654

Your ifconfig output indicates that you're connected to a network and have transmitted and received quite a bit of data. You have an IP address I'll assume came from your router. It could be that your DNS servers aren't configured properly. Try looking at this file:

```
cat /etc/resolv.conf
```

This should list your DNS servers. If it is empty, all you would need to do is add the nameservers. This is what my resolv.conf looks like.

```
nameserver 192.168.1.1
```

In my case, I'm simply allowing my router to provide the DNS servers.

You can actually edit the file and follow the form shown (nameserver *<your_DNS_server>*) to list any DNS server(s) you'd like to use.

---

### Post by Mitch9654 on 2009-02-21
Chrissharp
my ping turned up almost the exact same as yours:
rootuser@DEN-PC:~$ ping google.com
PING google.com (209.85.171.100) 56(84) bytes of data.
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=1 ttl=243 time=39.4 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=2 ttl=243 time=33.2 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=3 ttl=243 time=43.1 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=4 ttl=243 time=43.0 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=5 ttl=243 time=38.0 ms

--- google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4001ms
rtt min/avg/max/mdev = 33.209/39.396/43.173/3.691 ms


Abyssius

I have the exact same nameserver as you except I am 192.168.**2**.1

Ya

mitch9654

---

### Post by kestrel1 on 2009-02-21
Do you have Firestarter installed?
If so run it & go to Firewall & run the wizard to setup your firewall correctly.
I had a similar problem with a laptop & firestarter was blocking the eth1 (wireless) connection. 
Firestarter is only a gui for iptables & not the firewall itself.

---

### Post by Mitch9654 on 2009-02-21
yes I tried firestarter _many_ times before.

---

### Post by abyssius on 2009-02-21
> **Mitch9654 said:**
> well, actually internet is working, but ubuntu isn't quite noticing my eth0 adapter


mitch9654

Mitch

If you can access the Internet, your adapter _must_ be being noticed. We were all assuming that you couldn't accesss the Internet. Obviously, you have Internet access if you can ping Google, etc. Maybe, what you're saying is that the Network Tools application isn't recognizing your adapter? That's not exactly the same as saying Ubuntu is not noticing your adapter, if you know what I mean. In any case, if you don't have a problem accessing the internet - don't worry about it. I got so annoyed with the NetworkManager application, I simply uninstalled it. Now, I'm accessing the Internet no problem - and I'm using an infamous wireless interface. Go figure!

---

### Post by Mitch9654 on 2009-02-21
ha,   ha,   ha


**hilarious...**



Well, news to me!


the thing is now is that frostwire, my beautiful limewire for ubuntu is pretending that it can't find an internet connection 


(grumble grumble)

mitch9654

---

