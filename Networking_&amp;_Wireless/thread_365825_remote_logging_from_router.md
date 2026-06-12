---
title: "remote logging from router"
date: 2007-02-20
forum: Networking &amp; Wireless
---

### Post by mizar001 on 2007-02-20
Hi. I have a dlink dsl 504t installed at home. I know, not the best choice. However among its features i discovered the 'remote logging'.

When i setup this i put the correct IP address where to send logs. 

But my question is: What is the used protocol in doing this ? the manual and the updated guides of this router never mention the 'remote logging' feature, and i'm scared that could be only a smoky feature.

I setted the sysklogd with '-r' option like seen in the /etc/init.d/sysklogd configuration suggestions (even in /etc/default/sysklogd). But no packets is grabbed from the device.


Maybe i need some other package to receive and read network devices logs ?

---

### Post by gradedcheese on 2007-02-21
They could have implemented any number of protocols, probably their own proprietary one that they made up,  Search around on google and, if there's info, post it here and we'll see if there's any reasonable way to get the logs.

---

### Post by mizar001 on 2007-02-21
No way. I searched many times in internet. I think it uses SNMP protocol, but no sure of that because the log feature is never mentioned on router manuals, and no one on internet talk about this feature on this router.

I think SNMP 'cause it's the first protocol a router developer can think when implementing message logging to an auditing server.

Any suggest to listen to snmp packets ?

---

### Post by gradedcheese on 2007-02-21
sure.  look up what port that's on (and if it's udp or tcp, my guess is TCP?) and then point it at your PC via the router config, and turn logging on.  On your PC, fire up tcpdump and tell it to listen to that port.  This will dump the packets to your screen.  For example if your network interface is eth0,

```

sudo tcpdump -i eth0 port 1234

```

---

### Post by mizar001 on 2007-02-23
Wow i was amazed by the tcpdump command. It's a real packet sniffer. But anyway i see many things, even from my dlink router, but never sure if could be its log.

Can i see the packet content ? maybe the tcpdump read only the header ?

---

### Post by gugliasky on 2007-12-24
> **mizar001 said:**
> Hi. I have a dlink dsl 504t installed at home. I know, not the best choice. However among its features i discovered the 'remote logging'.

When i setup this i put the correct IP address where to send logs. 

But my question is: What is the used protocol in doing this ? the manual and the updated guides of this router never mention the 'remote logging' feature, and i'm scared that could be only a smoky feature.

I setted the sysklogd with '-r' option like seen in the /etc/init.d/sysklogd configuration suggestions (even in /etc/default/sysklogd). But no packets is grabbed from the device.


Maybe i need some other package to receive and read network devices logs ?

I think that i found the solution.

You must set appropiate options in the router so that your computer IP is one of the destinatons for the log messages.
That computer IP can be an address behind the NAT (so only for the local network) or an address of the global internet.
Then you can start recieving packet on port UDP 514, wich is known as "syslog" and is an industry standard for remote logs.

How can you listen to UDP port 514?

The simplest mode is using the freeware "netdemon" and start listening to udp port 514.
Anyway i found a smal freeware named KLog ([http://kin.klever.net/klog/](http://kin.klever.net/klog/)) that is specifically designed to listen to syslog events, does a little work on analyzing the text recieved, and can even save the recieved data to a log file or route them to another host.

Anyway, it's true that d-link doesn't explain this feature in their manual nor in their website, and i really tried many times to find information about this feature but never succeded.

So how I found it?

I chose my ip as the log destination and I set the log level to debug, so as to recieve as many packet as possible, then I saved the new settings. So i started Whireshark (aka Etherreal) that is a packet sniffer, and i restarted the router. When the reboot of the router started, i found a small packet on udp port 514 telling me that the connection was reset. Then I looked on the internet for which protocol uses udp port 514 and i found "syslog". Then I looked for some freeware client for the syslog messages and I found KLog.
That's all! 5 minutes! Why dindn't I think at it before? :popcorn:

---

