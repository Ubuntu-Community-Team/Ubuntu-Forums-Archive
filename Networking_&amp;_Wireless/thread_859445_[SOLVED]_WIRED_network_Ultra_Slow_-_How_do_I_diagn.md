---
title: "[SOLVED] WIRED network Ultra Slow - How do I diagnose?"
date: 2008-07-14
forum: Networking &amp; Wireless
---

### Post by Grandma_DOG on 2008-07-14
I've been fighting an ultra slow WIRED connection since I upgraded to Hardy Heron a month ago. Its on a dual boot machine, the Windoz side has great connection. No special hardware, its worked fine in other Ubuntu installs.

Here are the symptoms that have stumped me:
1. slow connection - about 1/4 dialup speed for about 2-4kb/s
2. Probably Not DNS based - when I make it static IP with dns servers, it still crawls
3. Local ping to local router is fast at 0.40 ms, but html connection to router at 192.168.0.1 is so slow it takes 4 minutes to pull up the router control panel!!
4. Web ping to mit.edu is normal at 55.0 ms, but html connection takes 2-5 minutes to pull up a page.
5. I've put in another NIC and eth1 is just as slow as eth0.
6. Sometimes the connection stops entirely then resumes
7. Sometimes the ping will stop and nothing happens then it resumes 1-2 minutes later. While pinging, the pings are normal latency.

I've blacklisted IP6 in my modprobe, and shutdown IP6 in firefox:config.

I've used iftop tool to try to diagnose the problem without seeing anything odd.

I've used traceroute and have seen no problems.

I've tried to use wireshark (as root) but it crashes when I select eth0 or eth1.

Contents of interfaces:
auto lo
iface lo inet loopback


#iface eth0 inet static
#address 192.168.0.8
#netmask 255.255.255.0
#gateway 192.168.0.1



iface eth1 inet dhcp

auto eth1
------------------


I'm fresh out of Ideas-
Any Ideas out there to diagnose?

---

### Post by fdesign on 2008-07-14
I think this sounds like a problem with some conflicting modules. If I were you, that's where I would start investigating.

---

### Post by jrasmussen0 on 2008-07-14
You sound like you are having duplexing issues -- weird non-consistant speed issues.

[http://www.cyberciti.biz/faq/howto-setup-linux-lan-card-find-out-full-duplex-half-speed-or-mode/]("http://www.cyberciti.biz/faq/howto-setup-linux-lan-card-find-out-full-duplex-half-speed-or-mode/")

---

### Post by Grandma_DOG on 2008-07-14
> **jrasmussen0 said:**
> You sound like you are having duplexing issues -- weird non-consistant speed issues.

[http://www.cyberciti.biz/faq/howto-setup-linux-lan-card-find-out-full-duplex-half-speed-or-mode/]("http://www.cyberciti.biz/faq/howto-setup-linux-lan-card-find-out-full-duplex-half-speed-or-mode/")

An interesting theory, I'll look into when I get home.  However, while here at my work, I found our big data server is set to half duplex. So I fixed it with ethtool and may have dodged a future bullet on that.

---

### Post by Grandma_DOG on 2008-07-14
got the NIC running full duplex 100.

but when i do a sudo /etc/init.d/network restart I get :

Listening on LPF/eth0/00:01:6c:d0:3b:af
Sending on   LPF/eth0/00:01:6c:d0:3b:af
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER of 192.168.0.8 from 192.168.0.1
DHCPREQUEST of 192.168.0.8 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.0.8 from 192.168.0.1
addr=192.168.0.8,		 name=
Updating databases ...
Reading configuration from /etc/mail/sendmail.conf.
Validating configuration.
Creating /etc/mail/databases...
Updating Makefile ...
Reading configuration from /etc/mail/sendmail.conf.
Validating configuration.
Creating /etc/mail/Makefile...
Updating sendmail.cf ...
*** ERROR: FEATURE() should be before MAILER()
*** ERROR: FEATURE() should be before MAILER()
*** ERROR: FEATURE() should be before MAILER()
*** ERROR: FEATURE() should be before MAILER()
*** FEATURE(smrsh) must occur before MAILER(local)
*** ERROR: MAILER(local) already included
*** ERROR: MAILER(smtp) already included
Updating auth ...
sasl2-bin not installed, not configuring sendmail support.

To enable sendmail SASL2 support at a later date, invoke "/usr/share/sendmail/update_auth"

Creating /etc/mail/relay-domains
# Optional file...
A forced reload...
** ** You should issue `/etc/init.d/sendmail reload` ** **
Mail Transport Agent: sendmail is not running
bound to 192.168.0.8 -- renewal in 229384 seconds.
 * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...done.
Updating sendmail.cf ...
*** ERROR: FEATURE() should be before MAILER()
*** ERROR: FEATURE() should be before MAILER()
*** ERROR: FEATURE() should be before MAILER()
*** ERROR: FEATURE() should be before MAILER()
*** FEATURE(smrsh) must occur before MAILER(local)
*** ERROR: MAILER(local) already included
*** ERROR: MAILER(smtp) already included
Updating auth ...
sasl2-bin not installed, not configuring sendmail support.

To enable sendmail SASL2 support at a later date, invoke "/usr/share/sendmail/update_auth"

Creating /etc/mail/relay-domains
# Optional file...
A forced reload...
** ** You should issue `/etc/init.d/sendmail reload` ** **


Now I've removed and purged sendmail.  I can't seem to figure out why all this crap about sendmail keeps popping up and if it has something to do with the slow wired connection.

Any ideas?

---

### Post by Grandma_DOG on 2008-07-23
Solved it. Set card from 100MB/s to 10MB/s

Culprit - 30 meter run of cat5 cable that was a tad too long for a 100 Full duplex card that didn't seem to autonegotiate to a cleaner 10 FD speed.  It was able to get 100MB/s at a cost of 25% packet loss which rendered my effective speed to almost a 1200 Baud modem.  Once i set the speed to 10MB/s all the problems went away. When I switched back to 100MB/s they returned. Case closed.

Tools needed:
ethtool
dmesg | grep eth  (to notice corrupt packets)
ntop (for network load history)
ifconfig

---

