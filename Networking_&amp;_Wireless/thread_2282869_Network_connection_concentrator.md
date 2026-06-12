---
title: "Network connection concentrator"
date: 2015-06-17
forum: Networking &amp; Wireless
---

### Post by Rico_Wang on 2015-06-17
Hi Guys,

I'm formulating a solution to use stunnel to connect multiple devices into a Ubuntu communication concentration server, and forward the client connections to a host through multiple vpn modems(VM1, VM2, VM3).

[FONT=courier new].........................|-------------------|   
Client 1  --- stunnel --\ | PC-Server-Ubuntu..|
Client 2  --- stunnel ---\| stunnel...........|
Client 3  --- stunnel ----|eth0 eth1 eth2 eth3|
                          .........................|-------------------|
................................|....|....| 
...............................VM1..VM2..VM3
................................\....|..../
.................................\...|.../
..................................\..|../
...................................\.|./
.................................|------|
.................................| HOST |
.................................|------|[/FONT]

All the VPN modems are configured with same gateway address 192.168.15.1, and its firewall limits only traffic from 192.168.15.2 can pass through. That's I have to configure eth1/2/3 with same ip/gateway. In the same time, I have to forward communication from client1 through VM1 to port1 on HOST, and client2 through VM2 to port2 on HOST, and client3 through VM3 on port3 on HOST. Potentially, the number of clients could grow to dozens, but I have to maintain the fixed mapping always. I really hate the VPN modems, but we can not touch it.


Looks like bonding is an option, but with bonding I would not be able to set a routing correctly, as it suggests not to have any physical device routing, not mention I have to use port based routing.
"When bonding is configured, it is important that the slave devices not have routes that supercede routes of the master (or, generally, not have routes at all). "
[http://www.linuxfoundation.org/collaborate/workgroups/networking/bonding](http://www.linuxfoundation.org/collaborate/workgroups/networking/bonding)


Any thoughts?

---

### Post by wildmanne39 on 2015-06-17
Please use normal fonts.
> Use color and font properties for highlighting portions of your text, and not for all of the text in your post. Please use the default font color and properties unless you need to highlight or draw attention to a part of your post. ALL CAPS is interpreted as screaming. Funky non-uniform font size/color is difficult for those who are visually impaired. If you are having problems with reading the font, please adjust your browser.
Do not cross post, or post the same thing in multiple locations.
[http://ubuntuforums.org/showthread.php?t=2158945](http://ubuntuforums.org/showthread.php?t=2158945)
Thanks

---

### Post by Rico_Wang on 2015-06-17
Thanks, I have changed font of part of the content so that it looks like a diagram.

---

