---
title: "Lan eth problem Ubuntu Router"
date: 2015-03-23
forum: Networking &amp; Wireless
---

### Post by otto7 on 2015-03-23
Hi!

I need an expert :)

My problem is that when I'm connected trough cable to my ubuntu server/router I get 0,1Mbit in up speed. ([www.tptest.se](www.tptest.se)) (speedtest.net)
But if I use wifi I get > 50Mbit.

The network on the ubuntu server eth2 and wlan0 is bridged (br0) and eth1 is the Internet.

What I have tried so far.

1. Another computer same issue
2. Connected direct to Internet >50Mbit up speed
3. Switched eth2 on server (hardware) 0,1Mbit up speed
4. Connected computer direct to eth on server = 0.1Mbit up speed
5. Tested speedtest.net on server >50Mbit up speed
6. Changed switch after eth2 same issue

I use shorewall as firewall maby somthing is wrong there? But the network is bridged (br0) so why is only cable not working but wifi is? :confused:

I have run the network script and here is the output [http://paste.ubuntu.com/10660295/](http://paste.ubuntu.com/10660295/)

---

### Post by Tsepo_Joshua on 2015-03-24
[LIST=1]
[*]Disconnect from Internet
[*]Open your Terminal and execute the line:
  sudo tee /proc/sys/net/ipv6/conf/all/disable_ipv6 <<<"1"

[*]Connect to the Internet again, and see if the problem still exists.
[/LIST]

---

