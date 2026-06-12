---
title: "&quot;Starting Mail Transport Agent (MTA) sendmail&quot; -- HUGE DELAY at Start-up"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by drkameleon on 2009-06-12
Well, Another issue of mine...

I don't know what I've changed, but suddenly my boot-time has gone from 15secs to... >1.5 min.

I then noticed that it throws me back to the terminal screen, waiting for the following "step" to be completed (with an "[   OK   ]")

```
Starting Mail Transport Agent (MTA) sendmail
```

Do you know if there is anything I could do in order to avoid this?

Thanks a lot.... ;)

Dr.Kameleon

---

### Post by drkameleon on 2009-06-12
Up ^

---

### Post by drkameleon on 2009-06-12
Anybody? :confused:

---

### Post by drkameleon on 2009-06-12
UP ^ (for the last time...)

---

### Post by Rubicon_82 on 2009-06-12
Hi drkameleon,

It appears that sendmail is timing out on start up.  In the past, I have experienced a similar issue due to iptables rules I had in place.  Have you altered the default iptables configuration (either directly, or through a frontend such as [g]ufw or firestarter)?

Please post the output of:
```

sudo iptables -L -nv

```

The above command will display the iptables (firewall) configuration of your system.

---

### Post by Rubicon_82 on 2009-06-13
I've done some iptables logging on my system and I think I can explain what is happening:      

In short, you should ensure that you can send any traffic across your loopback interface, especially DNS requests and ICMP Destination Port Unreachable packets.  The following iptables rules will do this.  You may need to modify them depending on your setup:                                                                                                

(Rules given iptables-save format)
```
                            
-A INPUT -i lo -j ACCEPT          
-A OUTPUT -o lo -j ACCEPT         

```                           

If you have never modified the default iptables (or other firewall frontend) setup, you won't need these rules, and your problem may be something else.  If you have modified iptables, and the above rules don't resolve your problem, please post your iptables configuration.  This will assist in solving your problem.


An explanation for why this is the case follows:

On my system Exim4 (which provides sendmail in Jaunty) is configured for local delivery only.  Despite this, exim4 will still preform DNS lookup on startup and delivery.  There is no DNS service present on my system and my wireless connection is only configured by Network Manager upon login to KDE, so I have no network connectivity during startup.  This results in the following entries in my iptables log:

Exim4 sends a DNS request to localhost
```

[21.836910] IN= OUT=lo SRC=127.0.0.1 DST=127.0.0.1 PROTO=UDP SPT=49351 DPT=53 LEN=32 
```

It then receives a Destination Port Unreachable ICMP reply
```

[21.836969] IN= OUT=lo SRC=127.0.0.1 DST=127.0.0.1 PROTO=ICMP TYPE=3 CODE=3 [SRC=127.0.0.1 DST=127.0.0.1 PROTO=UDP SPT=49351 DPT=53 LEN=32 ]
```

This repeats 7 times, until exim4 stops sending DNS requests.

My previous iptables configuration was blocking all outgoing ICMP packets (other than Echo Request) on all interfaces. This resulted in exim4 not receiving a reply to its DNS request, leading to exim4 delaying the bootup process by up to 2 minutes.

Permitting all traffic on the loopback interface resulted in a much faster bootup time.

---

### Post by anoopjohn on 2009-08-23
This delay is caused by the incorrect hosts configuration. You can see a solution for this problem at [http://www.zyxware.com/articles/641/fixed-ubuntu-startup-slows-down-at-starting-mail-transport-agent-mta-sendmail](http://www.zyxware.com/articles/641/fixed-ubuntu-startup-slows-down-at-starting-mail-transport-agent-mta-sendmail)

---

