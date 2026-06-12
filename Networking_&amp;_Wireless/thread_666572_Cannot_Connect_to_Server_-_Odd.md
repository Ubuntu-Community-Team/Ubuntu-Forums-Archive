---
title: "Cannot Connect to Server - Odd"
date: 2008-01-13
forum: Networking &amp; Wireless
---

### Post by cujo on 2008-01-13
Here is the situation:

I have a server running Ubuntu Server 7.10.  I also have 2 laptops.  One is running Ubuntu 7.10 and the other is running OS X.  There is a wireless network stringing them all together with the server having a ip of 192.168.0.5, the Ubuntu laptop at 192.168.0.2, and the OS X laptop at 192.168.0.3.

On the server, sshd, apache2, and samba are all running.  Each machine on the network can access the internet.  Each machine can ssh to itself by specifying the address as localhost or as their own 192.x.x.x address.

The problem is that nothing can connect to the server machine.  I can't ping it, ssh to it, print to it, see the samba shares, nothing.  The odd part is that occasionally I can.  The trick I've found is to ping it for about 20 seconds.  Ping returns "host unreachable" for about that long, but then it will start to pick it up.  After that everything works.  The secondary problem to that is that the trick doesn't work very often.  I haven't been able to get it to work for the past 3 hours.

So there is my problem.  Now, does anyone know what is going on or how I can fix it?  It is driving me crazy.

---

### Post by evanchu on 2008-01-14
Before we jump to any conclusion, let us collect some basic diagnostic information.  Get you run ifconfig on all three machines and post their outputs?

---

### Post by cujo on 2008-01-21
Sorry for the delay.  Apparently I didn't "subscribe" to this thread to get updates.

Anyway, let's focus on the ubuntu laptop and server.  I don't really care about the mac.  It rarely gets used these days.

So ifconfig and iwconfig for the laptop:
wlan0     Link encap:Ethernet  HWaddr 00:1D:E0:41:42:13  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:e0ff:fe41:4213/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:89285 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52921 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:120144313 (114.5 MB)  TX bytes:10541426 (10.0 MB)

wlan0     IEEE 802.11g  ESSID:"DontBuyNetgear"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:09:5B:DF:77:0A   
          Bit Rate=54 Mb/s   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=85/100  Signal level=-42 dBm  Noise level=-80 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Since I can't copy-paste from the server machine, I've tried to copy it as best i could for ifconfig and iwconfig:
wlan0     Link encap:Ethernet  HWaddr 00:1C:10:E7:2F:40  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:10ff:fee7:2f40/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3461 (3.3 KB)  TX bytes:6860 (6.6 KB)

wlan0     IEEE 802.11g  ESSID:"DontBuyNetgear"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:09:5B:DF:77:0A   
          Bit Rate=48 Mb/s Tx-Power:32 dBm
          RTS thr:2347 B  Fragment thr:2346 B
          Power Management:off
          Link Quality:60/100 Signal level:-57dBm noise level:-96dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

But, like I said, both of these machines can get to the outside world (i.e. google.com) and both can ssh to themselves at the 192.x.x.x address (not just 127.0.0.1).

---

### Post by cujo on 2008-01-21
For what it's worth, I was just able to do the "ping tick" mentioned in the first post to get it working for the time being.  It is the first time it has worked in a week.

---

### Post by evanchu on 2008-01-22
The output of ifconfig looks normal.

Go to the Linux server and run the following and post the result:
route -n
ping -W 10 -c 6 192.168.0.2

Go to the Linux laptop and run the following and post the result:
route -n
ping -W 10 -c 6 192.168.0.5

These ping commands increase the timeout period for each ping-request to 10 seconds instead of 1 second.  I wonder if you are experiencing radio frequency interference.

---

### Post by cujo on 2008-01-23
for the server:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 wlan0

PING 192.168.0.2 (192.168.0.2) 56(84) bytes of data.
64 bytes from 192.168.0.2: icmp_seq=1 ttl=64 time=2.79 ms
64 bytes from 192.168.0.2: icmp_seq=2 ttl=64 time=2.53 ms
.
.
.
---------------------------------------------------------

for the lappy

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0

PING 192.168.0.5 (192.168.0.5) 56(84) bytes of data.
64 bytes from 192.168.0.5: icmp_seq=1 ttl=64 time=2.35 ms
64 bytes from 192.168.0.5: icmp_seq=2 ttl=64 time=2.37 ms
.
.
.

---

### Post by cujo on 2008-01-24
Here is another fun twist...

I use dyn-dns so I can ssh home or potentially use a machine as a web server to the outside world.  Currently I only have the ssh port open to the outside world.  Anyway, I can ssh to my dyn-dns address even when I cannot do it to the local ip.  How's that for fun?

My gut is starting to tell me the router is the problem.  Sigh.

---

### Post by evanchu on 2008-01-25
From the "route -n" output, I assume that your wireless access point is 192.168.0.1, which is a router on your home network and connects to the internet via a wire.

The routing table and ping outputs all look normal.  Now I recommend running the following commands when you experience the problem you described in your first message.

Go to the Linux server; open a command line window; switch to root account and run
```
tcpdump -i wlan0 icmp
```
The above command shows network traffic flowing through wlan0.

Go to the laptop, also run the above tcpdump command.

On the laptop, open a second command line window. Run
```
ping -c 6 192.168.0.5
```

Post the output of all three windows.  This diagnostic will show whether the ping requests from the laptop actually go out of the laptop's wlan0 and arrive at the server's wlan0.

---

