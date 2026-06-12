---
title: "Wierdest error - can ping, DNS OK, DHCP OK, no connectivity in Gnome"
date: 2008-01-08
forum: Networking &amp; Wireless
---

### Post by magozoom on 2008-01-08
Hi,
at home everything works fine with Ubuntu / Gutsy. At work I can not access the net Firefox 
Firefox sends the request, then waits for response forever...


**From a console I can ping**, and DHCP works fine, both wired and wireless. 
**wget does not work**

This is a wired Gigabit connection from my Amilo pi1556 laptop connecting trough a Linux openBSD router.

Here is the google ping
```

PING www.l.google.com (216.239.59.147) 56(84) bytes of data.
64 bytes from gv-in-f147.google.com (216.239.59.147): icmp_seq=1 ttl=239 time=49.3 ms
64 bytes from gv-in-f147.google.com (216.239.59.147): icmp_seq=2 ttl=239 time=49.1 ms

```


Here is output from wget - Connection is reset

```

magnus@mlaptop:~$ wget -d www.modernafilmer.se
DEBUG output created by Wget 1.10.2 on linux-gnu.

--15:44:06--  http://www.modernafilmer.se/
           => `index.html'
Resolving www.modernafilmer.se... 213.80.101.97
Caching www.modernafilmer.se => 213.80.101.97
Connecting to www.modernafilmer.se|213.80.101.97|:80... connected.
Created socket 3.
Releasing 0x08089650 (new refcount 1).

---request begin---
GET / HTTP/1.0
User-Agent: Wget/1.10.2
Accept: */*
Host: www.modernafilmer.se
Connection: Keep-Alive

---request end---
HTTP request sent, awaiting response... Read error (Connection reset by peer) in headers.
Closed fd 3

```


I also generated some other suggested debug information... here is ifconifg
```

eth0      Link encap:Ethernet  HWaddr 00:03:0D:47:F7:AD  
          inet addr:192.168.10.71  Bcast:192.168.10.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1896 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1792 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:248280 (242.4 KB)  TX bytes:259500 (253.4 KB)
          Interrupt:20 Base address:0xc800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:400 (400.0 b)  TX bytes:400 (400.0 b)

```

and some more...

```

magnus@mlaptop:~$ lspci | grep Eth
05:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)

```

```


magnus@mlaptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.10.1    0.0.0.0         UG    0      0        0 eth0


```

```



magnus@mlaptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


```

```

magnus@mlaptop:~$ cat /etc/dhcp3/dhclient.conf
send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
timeout 30;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}


```

If anyone can point me in the right direction it would be greatly appreciated -  I will show Ubuntu / Compiz at our next all-staff meeting.... goodbye Vista upgrade...

/magnus

---

### Post by domer on 2008-01-08
I am having the same problem**!!!!!!!**

Firefox, Opera does not work, but pinging works 

I recently changed my ISP and now I cannot connect to the internet using Firefox or Opera and Gaim Internet Messenger does not work either. I am using Ubuntu Dapper on this machine. Everything works fine using Windows. 

This is the weird part

When I open terminal and type "**ping [www.yahoo.com](www.yahoo.com)**" or any other server, I get 0% data loss and Weather Report works too. I have tried releasing/renewing my ip address using the following commands, 

**sudo dhclient -r** (for release) 
**sudo dhclient **(for renew)

but still cannot view any webpage or use Gaim (not that I can't live without gaim). 

ssh does not work either.

---

### Post by domer on 2008-01-11
Hi Magozoom, if you have already resolved the issue, please let me know. I am still stuck.

---

