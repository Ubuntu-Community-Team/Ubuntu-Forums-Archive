---
title: "Constant connection reset errors"
date: 2007-08-21
forum: Networking &amp; Wireless
---

### Post by dannemil on 2007-08-21
This is driving me nuts. I am running Feisty with a wireless connection. All of a sudden, every page I try to open in Firefox (and Opera for that matter) gives me 

"The connection to the server was reset while the page was loading."

I can hit the refresh button and get the page to then load, but what is causing this annoying problem. Because it is happening both with Firefox and Opera it can't be specific to the browser (well that's pretty obvious, huh!).

I can also try pinging google.com and sometimes the ping will get returned fine but some times I get "Resource temporarily unavilable." It is a crap shoot which I get. It is as if the connection is intermittent - some times there some times not. There should not really be a signal strength problem because I'm only about 15 feet away from the wireless router.

Any help would be appreciated. It basically makes using the web a horrible experience if you have to reload every page to get it to open.

Here is the output from ifconfig

ath0      Link encap:Ethernet  HWaddr (xxxxxxxblah blah)
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:46ff:fe97:527e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4325 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4575 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3351140 (3.1 MiB)  TX bytes:690382 (674.2 KiB)

[EDIT] Solved the problem. It was a problem with my wireless router. I reset the Transmission rate to 11 Mbps and the Basic rate to All under the advanced Wireless Settings on the router from its webadmin gui and that did the trick.

[EDIT EDIT] I also turned off IPV6 as shown here, and that really solved the flaky wireless connection
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#ipv6]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#ipv6") - I did the system-wide turn-off].

---

