---
title: "Terrible network transfer performance"
date: 2014-03-09
forum: Networking &amp; Wireless
---

### Post by cromestant on 2014-03-09
Hello on Ubunto 13.10, just installed on a 2 year old toshiba laptop, I'm getting terrible network performance
My setup is airport extreme ( not current generation but previous), laptop is connected through LAN, and originating laptop is connected through wifi.

Transfering files through SCP yields very unstable results (2 mb/s -> 100 kb/s) it jumps up and down constantly. eventually finishing the transfer.
on the same network, I use to have a 1st gen apple tv and achieved transfer rates of up to 4mb/s stable).

What can I do to help diagnose the issue, I have no idea where to start.
thank you in advance
charles

---

### Post by mörgæs on 2014-03-09
> **cromestant said:**
> 
What can I do to help diagnose the issue, I have no idea where to start.


Please read the sticky note in the forum. It lists a number of commands to run.

---

### Post by tgalati4 on 2014-03-09
Run *iperf* on a client and server and measure raw throughput.  Collect some statistics for each link.

```
sudo apt-get install iperf
man iperf
```

[http://askubuntu.com/questions/7976/how-do-you-test-the-network-speed-betwen-two-boxes](http://askubuntu.com/questions/7976/how-do-you-test-the-network-speed-betwen-two-boxes)

There are a lot of things that can affect network performance.  A fair amount of testing is usually needed to find the bottleneck.

---

### Post by cromestant on 2014-03-10
Hello, 
I tried the Iperf and got nothign as close as what you have, here is the ouput:
```
Charles-Romestant-MacBook-Air:~ cromestant$ iperf -s
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size:  128 KByte (default)
------------------------------------------------------------
[  4] local 10.0.1.7 port 5001 connected with 10.0.1.2 port 60722
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-10.2 sec  20.6 MBytes  16.9 Mbits/sec
[  4] local 10.0.1.7 port 5001 connected with 10.0.1.2 port 60723
[  4]  0.0-10.4 sec  21.9 MBytes  17.7 Mbits/sec
^CCharles-Romestant-MacBook-Air:~ cromestant$ iperf -c 10.0.1.2
```

I then tried it with the hosts reversed and got
```
Client connecting to 10.0.1.2, TCP port 5001
TCP window size:  129 KByte (default)
------------------------------------------------------------
[  4] local 10.0.1.7 port 49353 connected with 10.0.1.2 port 5001
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-10.0 sec  10.6 MBytes  8.91 Mbits/sec
Charles-Romestant-MacBook-Air:~ cromestant$ iperf -c 10.0.1.2
------------------------------------------------------------
Client connecting to 10.0.1.2, TCP port 5001
TCP window size:  129 KByte (default)
------------------------------------------------------------
[  4] local 10.0.1.7 port 49368 connected with 10.0.1.2 port 5001
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-10.1 sec  15.5 MBytes  12.9 Mbits/sec
```

---

### Post by cromestant on 2014-03-10
as for the stickies, I found one for wireless, this is not the issue here, and for ndiswrapper, my driver seems to work ok, ( default loaded by ubuntu) just that the performance is not good/stable.

---

### Post by cromestant on 2014-03-15
more information.
after an update I rebooted and was getting 9mb/s transfers which was awesome..
now back to 1 - 2 mb/s
weird..
have no idea how to diagnose issues like these..

---

