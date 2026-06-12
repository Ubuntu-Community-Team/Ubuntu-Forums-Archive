---
title: "Partial Network failure"
date: 2007-03-22
forum: Networking &amp; Wireless
---

### Post by revelation.now on 2007-03-22
Hi everyone.
  I have a gruby little problem with a fresh install of Ubuntu and I'm running out of ideas.

I have no issues with the other computers plugged into the router connecting to the net

I have swapped out a number of different (working) ethernet cards

My network card is cabled and detects. 

my IP is static and is pingable from other PCs

I can ping other network pcs from the Ubuntu PC

I can ping google from the Ubuntu PC (so DNS is working)

I can connect to google sometimes, but usually I get "Unable to Connect" from firefox

Most other web pages fail unless I've just visited them on another PC

All of the updates fail. eg. trying to install file sharing fails. Trying to get updates from the repository fails.

So my guess is its some lame network timeout setting but I don't know how to configure this. Anyone?

---

### Post by chili555 on 2007-03-22
Please sudo gedit /etc/modprobe.d/blacklist to add:```
blacklist  ipv6
```Reboot and let us know.

---

### Post by thingy on 2007-03-22
Please paste the output of "ifconfig -a"

Also your /etc/network/interfaces file.

---

### Post by revelation.now on 2007-03-22
out of ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:40:95:0B:F7:4C  
          inet addr:192.168.1.120  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:874938 errors:0 dropped:0 overruns:0 frame:0
          TX packets:883613 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:56874957 (54.2 MiB)  TX bytes:400981106 (382.4 MiB)
          Interrupt:201 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:20:ED:54:A1:BC  
          inet addr:192.168.1.121  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:209 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

Interfaces:

iface eth1 inet static
address 192.168.1.121
netmask 255.255.255.0
gateway 192.168.1.1

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto eth0

auto eth1

---------------

I have also applied blacklist ipv6, and now appear to be able to view the web, but i don't seem to be able to download anything from the repositories. Does this require me to have a particular port open?

---

### Post by Mr. C. on 2007-03-22
You have to NICs on the same physical network.  This is a no-no.

Disable one of them.

MrC

---

### Post by chili555 on 2007-03-22
You seem to have two interfaces with IP addresses fighting each other for world domination instead of serving the Master downloading torrents. ```
eth0 Link encap:Ethernet HWaddr 00:40:95:0B:F7:4C
inet addr:**192.168.1.120** Bcast:192.168.1.255 Mask:255.255.255.0

eth1 Link encap:Ethernet HWaddr 00:20:ED:54:A1:BC
inet addr:**192.168.1.121** Bcast:192.168.1.255 Mask:255.255.255.0

```I suggest disabling eth1 and see if things drastically improve. May take a reboot.

PS - Yeah, what Mr.C said!!

---

### Post by revelation.now on 2007-03-22
okay, I've disabled one (eth1 -> 192.168.1.121)
I should explain that eth1 was not actually connected to an ethernet cable

I'm performing a reboot but after disabling the adapter I was still unable to access the repository

---

### Post by Mr. C. on 2007-03-22
What's in youre /etc/resolv.conf file ?  Your router's IP or your ISP's DNS servers?

---

### Post by revelation.now on 2007-03-22
nameserver 192.168.1.1 <router
nameserver 210.15.254.240 <-isp

descriptions obviously omitted

---

### Post by Mr. C. on 2007-03-22
Delete the router's nameserver.  You can use a text editor.  If you used the GUI, you can use the DNS tab in System->Adminisitration->Network.

Commodity router caching-DNS implementations are very poor, and don't have enough memory to do justice to a DNS server.  Use your ISPs.

If you can disable the caching DNS server in your router, do so.  Your ISP likely gave you two IPs; place the fastest, most responsive one first.  You can have up to 3 nameserver lines.

No reboot necessary - effects are immediate.

MrC

---

### Post by revelation.now on 2007-03-23
Thank you very much Mr.C. That seems to have solved the problem exactly. I don't understand why my Router's DNS wasn't good enough, but there you go.

---

### Post by Mr. C. on 2007-03-23
You're welcome.

As I mentioned, the implementations of many caching-DNS servers in cheap, commodity routers  are very poor, and do not have enough memory to do justice to a DNS server.  A cachng DNS server requires a fair amount of RAM.  In addition, your routers DNS server relies on your ISPs anyway, but the additional layer of caching leads to stale results.  If your ISPs name server does not respond quickly enough, the router may cache a negative answer for too long, causing many more temporary look up failures.  That matches your problem description and experience.

ISPs have very large, robust, standalone DNS servers with enormous caches; they are usually very fast.

Windows has its own built in cache, so many people using these routers do not experience the problems; they are essentially hidden.

MrC

---

