---
title: "Does Ubuntu throttle upload bandwidth by default? Or is this a hardware thing?"
date: 2022-12-08
forum: Networking &amp; Wireless
---

### Post by AwaitingUserInput on 2022-12-08
I've been working on my home network lately and recently installed [iperf3]("https://iperf.fr/iperf-download.php") as a way to check my transfer speeds.

The computer I use the most is connected to the 5GHz wireless band of my router. I have a server on my LAN that is connected to the same router via ethernet cable.

Using iperf3, I notice that I get twice as much bandwidth when receiving data vs. when I send data to the server. Is this configured in Ubuntu somewhere, or is it due to hardware or settings somewhere else in the network chain? Maybe the wireless card, or the router, or something like that? Perhaps consumer wifi cards are built with receive performance prioritized over uploading? I am trying to figure out if there's a way to get faster upload transfer speeds. It seems suspicious to me that my upload speed is exactly half of my download speed.

Wifi chip is Intel Corporation Wireless-AC 9260 and I'm using the iwlwifi drivers.

Thanks for any insight!!!

[SIZE=3]iperf3 output when sending data to the server (Connection chain is client --> 5GHz wireless --> Router --> Ethernet --> Server):[/SIZE]

```
[FONT=monospace][COLOR=#000000]$ iperf3 -c 192.168.1.202[/COLOR]
Connecting to host 192.168.1.202, port 5201
[  5] local 192.168.1.200 port 59128 connected to 192.168.1.202 port 5201
[ ID] Interval           Transfer     Bitrate         Retr  Cwnd
[  5]   0.00-1.00   sec  34.4 MBytes   289 Mbits/sec    0   1.45 MBytes        
[  5]   1.00-2.00   sec  31.2 MBytes   262 Mbits/sec    0   1.88 MBytes        
[  5]   2.00-3.00   sec  31.2 MBytes   262 Mbits/sec    0   2.39 MBytes        
[  5]   3.00-4.00   sec  30.0 MBytes   252 Mbits/sec    0   2.71 MBytes        
[  5]   4.00-5.00   sec  32.5 MBytes   273 Mbits/sec    0   3.05 MBytes        
[  5]   5.00-6.00   sec  31.2 MBytes   262 Mbits/sec    0   3.05 MBytes        
[  5]   6.00-7.00   sec  31.2 MBytes   262 Mbits/sec    0   3.05 MBytes        
[  5]   7.00-8.00   sec  31.2 MBytes   262 Mbits/sec    0   3.05 MBytes        
[  5]   8.00-9.00   sec  32.5 MBytes   273 Mbits/sec    0   3.05 MBytes        
[  5]   9.00-10.00  sec  30.0 MBytes   252 Mbits/sec    0   3.05 MBytes        
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bitrate         Retr
[  5]   0.00-10.00  sec   316 MBytes   265 Mbits/sec    0             sender
[  5]   0.00-10.05  sec   314 MBytes   262 Mbits/sec                  receiver
[/FONT]
```

[SIZE=3]iperf3 output for reverse of the above (receiving data from server):[/SIZE]
```
[FONT=monospace][COLOR=#000000]$ iperf3 -c 192.168.1.202 -R[/COLOR]
Connecting to host 192.168.1.202, port 5201
Reverse mode, remote host 192.168.1.202 is sending
[  5] local 192.168.1.200 port 58316 connected to 192.168.1.202 port 5201
[ ID] Interval           Transfer     Bitrate
[  5]   0.00-1.00   sec  59.4 MBytes   498 Mbits/sec                   
[  5]   1.00-2.00   sec  61.0 MBytes   512 Mbits/sec                   
[  5]   2.00-3.00   sec  63.0 MBytes   529 Mbits/sec                   
[  5]   3.00-4.00   sec  64.1 MBytes   537 Mbits/sec                   
[  5]   4.00-5.00   sec  62.9 MBytes   527 Mbits/sec                   
[  5]   5.00-6.00   sec  67.8 MBytes   569 Mbits/sec                   
[  5]   6.00-7.00   sec  60.5 MBytes   508 Mbits/sec                   
[  5]   7.00-8.00   sec  62.8 MBytes   527 Mbits/sec                   
[  5]   8.00-9.00   sec  64.5 MBytes   541 Mbits/sec                   
[  5]   9.00-10.00  sec  68.6 MBytes   576 Mbits/sec                   
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bitrate         Retr
[  5]   0.00-10.04  sec   636 MBytes   531 Mbits/sec    0             sender
[  5]   0.00-10.00  sec   635 MBytes   532 Mbits/sec                  receiver

iperf Done.

[/FONT]
```

---

### Post by TheFu on 2022-12-08
Nope.  Transmission and reception are just different with your hardware, it appears.

Wifi is always subject to local conditions, which are constantly changing.  There used to be an app for Android that would help to map the wifi connectivity around a house. Just a few feet in any direction can make a huge difference in connectivity and performance.

About 20 yrs ago, I was part of a team designing and deploying wifi across 1200+ corporate locations.  That taught me much, but mainly to avoid wifi if you want a stable, solid, connection.  Use wired ethernet, even if you need to get a $20 USB3-to-GigE adapter, like most thin laptops require the last 7+ yrs.  

Lacking the ability to use ethernet, use either MoCA or PowerLine ethernet. 

Powerline can have massive drop offs based on the house wiring. In my home, going from the wiring closet to a different floor with a 600Mbps powerline setup drops the speed from 220Mbps in the same room to 62Mbps.  OTOH, that 62Mbps is solid, stable, and works fine for streaming videos.  Wifi, OTOH, was constantly changing from 0 to 300 Mbps erratically.  That's using a dual band wifi router with 2.4 and 5.8Ghz channels.  5.8 Ghz doesn't like it when there's anything between the two antennas.  2.4Ghz works better between walls, but concrete can stop it completely.

Both 5.8Ghz and 2.4Ghz channels are unlicensed, so any devices can use those and muck up the bands, which slows total performance.

MoCA comes in different speeds, but the current $120 kits are 2.5Gbps.  They provide this.  I've not used it, but I would next deployment to replace the Powerline setup, should that stop working.  A relative uses MoCA to connect his home with a disconnected garage about 20m from the house. He's getting 2.5Gbps connections, which is beyond what his GigE LAN in the house can handle.  It negotiates down to 1 Gbps connectivity, so he sees 940 Mbps real-world bandwidth.

Wifi is convenient.  You can try to tweak some driver settings or you can live with the current performance or you can replace wifi with some wired solution which avoids all the interference that is part of using wifi.

---

### Post by AwaitingUserInput on 2022-12-08
Thanks a bunch for sharing your experience. I had never heard of MoCA before but I'll look around and see if I have any coax cables that are already run and that I can re-purpose. I'll consider powerline also.

My speeds seem pretty consistent so far at 260 Mbps up and 530 down, so Powerline may be a step backwards vs. my current wireless. The computer in question is a desktop that doesn't move around. I may just learn to live with it.

The MOCA sounds good if I can find a wire already run, otherwise, I would just run an ethernet cable. But because of the layout of the house, I don't want to run any new wiring. But thanks for giving me some things to look into more deeply.

---

### Post by TheFu on 2022-12-08
Don't think that my 600 Mbps powerline is the end.  Last time I looked there were 1200Mbps versions and the connection is STABLE. Your wifi isn't not stable.  You can't see it, but the computer definitely does.

Another option is to get a better quality wifi-AP.  Those are hard to get thanks to the pandemic, but there is a huge difference in what the normal "home wifi" can do and what an enterprise wifi-AP does.  Take a look at Ubiquiti APs.  these can be placed were you need them using an ethernet cable that also provides power to the AP.  A tiny hole into the attic and a 50ft CAT5e cable up there is all you need.  Then a hole in the ceiling that looks like a fire alarm over the place you want it mounted.  My house is well covered by 2 of those devices, if I used wifi (which I avoid). ;)  Before deploying wifi at a client's location, I did setup everything at my house to see how well it worked. I was impressed.  I'd deployed some outdoor wifi-APs for a compound overseas which was all cement and brick. Basically, to get wifi, the systems needed to be at the window with less than 3 walls in the way.

[https://www.smallnetbuilder.com/basics/lanwan-basics/#](https://www.smallnetbuilder.com/basics/lanwan-basics/#) will be useful, assuming you don't try to tweak the driver options first.  

If it were me, I'd test with MS-Windows and the same wifi adapter, see if the performance is actually better.  If it is, then go into the detailed settings to see what the default option are. There should be 20-50 options in there somewhere.  Companies spend 1000x more effort getting their Windows stuff working well.  With those options known, you just need to see what the defaults are for the Linux drivers.
If the performance isn't any better, then I'd move towards some wired option.

---

