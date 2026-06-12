---
title: "How to restart a wireless connection?"
date: 2008-06-01
forum: Networking &amp; Wireless
---

### Post by peterballard on 2008-06-01
Using Ubuntu 8.04 I connect through device wlan0. Sometimes connection drops out, or doesn't come up when I boot. What should I be doing to restart it? One poster recommended "sudo ifup --f wlan0", but that doesn't always work. What else should I try? 

I have a D-Link DWA-110 USB wireless adapter, and I'm using the RT73 driver from [http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz) , and I configure wlan0 in /etc/network/interfaces. (Full details at this thread: [http://ubuntuforums.org/showthread.php?t=806355](http://ubuntuforums.org/showthread.php?t=806355) ).

I know it's not a hardware problem because when I boot into Windows XP it connects 100% reliably.

---

### Post by issih on 2008-06-01
You could try:

sudo /etc/init.d/networking restart

which should restart the networking daemons...

Might work

---

### Post by peterballard on 2008-06-01
> **issih said:**
> You could try:

sudo /etc/init.d/networking restart

which should restart the networking daemons...

Might work

Thanks for that. Due to the fact that my connection dies intermittently, it may be a few days before I get to try it.

---

### Post by peterballard on 2008-06-02
> **issih said:**
> You could try:

sudo /etc/init.d/networking restart

which should restart the networking daemons...

Might work

Didn't work. A long post of logs follows. If anyone can suggest what's going wrong, I'd appreciate it.

```

pballard@sirboris:~$ ping yahoo.com
  C-c C-c
pballard@sirboris:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.wlan0.pid with pid 7797
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:1c:f0:0a:55:91
Sending on   LPF/wlan0/00:1c:f0:0a:55:91
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.0.1 port 67
addr=192.168.0.156,		 name=
Updating databases ...
Reading configuration from /etc/mail/sendmail.conf.
Validating configuration.
Creating /etc/mail/databases...
Updating Makefile ...
Reading configuration from /etc/mail/sendmail.conf.
Validating configuration.
Creating /etc/mail/Makefile...
Updating sendmail.cf ...
Updating auth ...
sasl2-bin not installed, not configuring sendmail support.

To enable sendmail SASL2 support at a later date, invoke "/usr/share/sendmail/update_auth"

Creating /etc/mail/relay-domains
# Optional file...
The following file(s) have changed:
  /etc/mail/sendmail.cf
** ** You should issue `/etc/init.d/sendmail reload` ** **
 * Reloading Mail Transport Agent (MTA) sendmail
   ...done.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:1c:f0:0a:55:91
Sending on   LPF/wlan0/00:1c:f0:0a:55:91
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPOFFER of 192.168.0.156 from 192.168.0.1
DHCPREQUEST of 192.168.0.156 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.0.156 from 192.168.0.1
bound to 192.168.0.156 -- renewal in 33 seconds.
   ...done.

```

... but I still had no connectivity. If you look back you'll see that it asked me to run "/etc/init.d/sendmail reload", so...

```

sirboris:~$ sudo /etc/init.d/sendmail reload
[sudo] password for pballard: 
 * Reloading Mail Transport Agent (MTA) sendmail
   ...done.

```

But it made no difference:

```

pballard@sirboris:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.wlan0.pid with pid 8686
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:1c:f0:0a:55:91
Sending on   LPF/wlan0/00:1c:f0:0a:55:91
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.0.1 port 67
addr=192.168.0.156,		 name=
Updating databases ...
Reading configuration from /etc/mail/sendmail.conf.
Validating configuration.
Creating /etc/mail/databases...
Updating Makefile ...
Reading configuration from /etc/mail/sendmail.conf.
Validating configuration.
Creating /etc/mail/Makefile...
Updating sendmail.cf ...
Updating auth ...
sasl2-bin not installed, not configuring sendmail support.

To enable sendmail SASL2 support at a later date, invoke "/usr/share/sendmail/update_auth"

Creating /etc/mail/relay-domains
# Optional file...
The following file(s) have changed:
  /etc/mail/sendmail.cf
** ** You should issue `/etc/init.d/sendmail reload` ** **
 * Reloading Mail Transport Agent (MTA) sendmail
   ...done.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:1c:f0:0a:55:91
Sending on   LPF/wlan0/00:1c:f0:0a:55:91
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPOFFER of 192.168.0.156 from 192.168.0.1
DHCPREQUEST of 192.168.0.156 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.0.156 from 192.168.0.1
bound to 192.168.0.156 -- renewal in 32 seconds.
   ...done.

```

... still no internet connectivity.

Figuring perhaps sendmail was my problem, I uninstalled sendmail, rebooted and tried again...

```

pballard@sirboris:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.wlan0.pid with pid 6026
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:1c:f0:0a:55:91
Sending on   LPF/wlan0/00:1c:f0:0a:55:91
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.0.1 port 67
/etc/dhcp3/dhclient-exit-hooks.d/sendmail: line 28: /usr/share/sendmail/dynamic: No such file or directory
/etc/dhcp3/dhclient-exit-hooks.d/sendmail: line 31: update_interface: command not found
/etc/dhcp3/dhclient-exit-hooks.d/sendmail: line 46: update_sendmail: command not found
.: 44: Can't open /usr/share/sendmail/dynamic
run-parts: /etc/network/if-up.d/sendmail exited with return code 2
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:1c:f0:0a:55:91
Sending on   LPF/wlan0/00:1c:f0:0a:55:91
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPOFFER of 192.168.0.156 from 192.168.0.1
DHCPREQUEST of 192.168.0.156 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.0.156 from 192.168.0.1
/etc/dhcp3/dhclient-exit-hooks.d/sendmail: line 28: /usr/share/sendmail/dynamic: No such file or directory
/etc/dhcp3/dhclient-exit-hooks.d/sendmail: line 31: update_interface: command not found
/etc/dhcp3/dhclient-exit-hooks.d/sendmail: line 40: update_host: command not found
/etc/dhcp3/dhclient-exit-hooks.d/sendmail: line 46: update_sendmail: command not found
bound to 192.168.0.156 -- renewal in 34 seconds.
.: 44: Can't open /usr/share/sendmail/dynamic
run-parts: /etc/network/if-up.d/sendmail exited with return code 2
   ...done.

```

So uninstall of sendmail didn't work properly. It's hard to tell if my problem is because Ubuntu screwed up the uninstall of sendmail, or whether that screwup is unrelated to the fact that it can't connect to the internet reliably.

---

### Post by chili555 on 2008-06-02
In all three cases, you associated with the access point and received an IP address:```
DHCPACK of 192.168.0.156 from 192.168.0.1
bound to 192.168.0.156 -- renewal in 33 seconds.
```However, 33 seconds is not much time to surf the web!

Usually, the lease time is given out by the router or access point. I would trouble-shoot that first.

---

### Post by braganfamily on 2008-06-02
I have the same problem with my D-Link DWL G122 ver. A2

It is a problem with every distro I have tried it on.  From experience and observation I believe my problem relates to using ndiswrapper, that is just an observation.

I have a thread in this forum asking for help but no responses.  Linux distro's just seem to "drop" the connection to the usb wireless antenna.  All lights go off.  It is probably not relates to the access point at all, as I have tried several.  I'll keep watching this thread to see if any more responses.

Good luck.

bobby

---

### Post by braganfamily on 2008-06-02
Just discovered something.  After my last post, my wireless disconnected again.  I was also trying to print and found my printer disconnected, also.

This might be a USB issue.  Could you try other usb hardware when your connections fails?  

bobby

---

### Post by braganfamily on 2008-06-02
I have reproduced the problem 3 times now, seems I lose all usb not just wireless

bobby

---

### Post by peterballard on 2008-06-04
> **chili555 said:**
> In all three cases, you associated with the access point and received an IP address:```
DHCPACK of 192.168.0.156 from 192.168.0.1
bound to 192.168.0.156 -- renewal in 33 seconds.
```However, 33 seconds is not much time to surf the web!

Usually, the lease time is given out by the router or access point. I would trouble-shoot that first.

How? (Bearing in mind that it works perfectly in Windows XP)

---

### Post by peterballard on 2008-06-07
A friend offered this (rather depressing) advice:

> 
Apparently the driver for that wireless chip is still in the experimental stage:

[http://www.linux.com/feature/132701](http://www.linux.com/feature/132701)

If you want to save head-banging, I'd just wait until the version included with the kernel has stabilised. Once that has happened, then everything should just be automatic. I guess this means you're stuck with Windows in the meantime. 


By "the wireless chip" he means the ralink chipset used in my DLink wireless adaptor (DWA-110). A kind of sad situation, that Linux can't reliably handle a major chipset.

---

### Post by rated_emman on 2008-06-07
can anybody please tell me how to configure the wireless connection? i have HP pavilion dv2000 that is currently running windows vista and linux 8.04 hardy heron....

i have a built in wireless card on my laptop but i dont know how to even connect to the internet wirelessly in linux...

im super new to linux... anybody can help?

thanks gusy!

---

