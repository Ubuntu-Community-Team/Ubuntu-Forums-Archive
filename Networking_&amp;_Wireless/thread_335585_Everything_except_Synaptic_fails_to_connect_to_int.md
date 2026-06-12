---
title: "Everything except Synaptic fails to connect to internet"
date: 2007-01-10
forum: Networking &amp; Wireless
---

### Post by Mishal on 2007-01-10
HELP!

I have been trying to browse the internet on Ubuntu for such a long time and I just can't make it work. I can download updates using Synaptic but nothing else related to the internet works. I tried everything that has been mentioned here:
[http://www.ubuntuforums.org/showthread.php?t=282034](http://www.ubuntuforums.org/showthread.php?t=282034)

So PLEASE don't direct me to that thread.

This is what I get when restart my network. Something seems to be wrong.

```
speedo@speedo-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.ath0.pid with pid 3254
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:16:ce:77:77:59
Sending on   LPF/ath0/00:16:ce:77:77:59
Sending on   Socket/fallback
DHCPRELEASE on ath0 to 192.168.2.1 port 67
/usr/bin/poff: No pppd is running.  None stopped.
There is already a pid file /var/run/dhclient.eth1.pid with pid 5798864
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
wifi0: unknown hardware address type 801
Bind socket to interface: No such device
Failed to bring up eth1.
There is already a pid file /var/run/dhclient.eth2.pid with pid 5798864
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
wifi0: unknown hardware address type 801
Bind socket to interface: No such device
Failed to bring up eth2.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 5798864
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
wifi0: unknown hardware address type 801
Bind socket to interface: No such device
Failed to bring up wlan0.
Plugin rp-pppoe.so loaded.
There is already a pid file /var/run/dhclient.ath0.pid with pid 5798864
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:16:ce:77:77:59
Sending on   LPF/ath0/00:16:ce:77:77:59
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.2.1
DHCPREQUEST on ath0 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.10 -- renewal in 2147483648 seconds.
                                                                         [ ok ]
speedo@speedo-laptop:~$ 

```

PLEASE PLEASE help.:(

---

### Post by meldroc on 2007-01-10
If synaptic can fetch updates, your network hardware and interfaces are up.

My guess is that either you have a misconfigured firewall, or you have misconfigured priviledges (in that case, the reason why synaptic is working is because it runs with root 
priviledges.)

Try to rule a few things out.

If it's a DNS problem, you would be able to still use the network, but you'd have to specify IP addresses instead of DNS names.  For example, you could use 82.211.81.186 instead of [www.ubuntuforums.org](www.ubuntuforums.org).  See if that's the case.

You can test if it's a privilege problem by running something else with root privileges (try "kdesu firefox" or "gtksu firefox".)

As far as firewalls go, apt-get install guarddog, and you'll have an easy way to configure the firewall.  That or learn iptables.

---

### Post by Mishal on 2007-01-10
Don't know how to thank you.

You were right. It was a user privilege problem. I am running Firefox using root now and typing this message.

So how do I now get it to work my own user rather than root?

Thanks!!
Mishal :)

EDIT: btw, I tried your other suggestion and I can access ubuntuforums.org using my own user if I type in 82.211.81.186

---

### Post by meldroc on 2007-01-10
For privilege problems:

Fire up a terminal, using your normal user account, and once you have a shell prompt, type "groups".  What do you get back?

---

### Post by Mishal on 2007-01-10
This is what I get:
speedo adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin

---

### Post by meldroc on 2007-01-10
Hmmm.  That's all the normal groups.  I'm guessing that you're running Edgy on this box, correct?  When it installs by default, normal users should have enough privileges to be able to access the internet.

Try some network access from the command line and see what errors you get.  Try ping (though it doesn't work much of the time even when correctly set up because some ISPs block pings.)  Try wget to fetch web pages.  Compare that to running them with sudo to get root privileges.

---

### Post by Mishal on 2007-01-10
Here are the results:

1) ping 192.168.2.1 works
2) wget [www.google.com](www.google.com) doesn't work BUT
3) sudo wget [www.google.com](www.google.com) DOES work
4) wget [http://82.211.81.186](http://82.211.81.186) works

EDIT: I am indeed running Edgy. And a little more info for you: I am running Acer laptop - Aspire 5102WLMi and its a 64-bit Edgy thats running. Hope that helps.

---

### Post by kebes on 2007-01-10
Since it appears that normal users cannot access the DNS settings, check the permissions on your "resolv.conf" file (note that it's usually a symlink so go check the actual file, too). On my system they appear as:

```

kebes@computer:/$ ls -laF /etc/resolv.conf
lrwxrwxrwx 1 root root 31 2006-09-30 21:18 /etc/resolv.conf -> /etc/resolvconf/run/resolv.conf
kebes@computer:/$ ls -laF /etc/resolvconf/run/resolv.conf
-rw-r--r-- 1 root dhcp 174 2006-12-09 18:29 /etc/resolvconf/run/resolv.conf

```

Notice that the file is world-readable (but not writeable). Check that this is the case! If it isn't world-readable then normal users cannot do DNS lookups. To fix it you can go:


```

sudo chmod 644 /etc/resolvconf/run/resolv.conf

```

---

### Post by Mishal on 2007-01-10
PROBLEM SOLVED!! YEEEAAAH!!

You were right. Users other than root did not have access to resolv.conf ....not even read, let alone write to the file.

Changed the permissions, and everythings fine. YEEAAAAH!!!:) :) 

Thanks a lot kebes and meldroc.  I am very grateful.:)

---

