---
title: "Feisty doesn't go the Internet distance!"
date: 2007-09-08
forum: Networking &amp; Wireless
---

### Post by chilisastry on 2007-09-08
Whether booted up from the Live CD or from the hard disk, when I enter [www.yahoo.com](www.yahoo.com) in the Firefox browser, it cannot find the server. But if I enter the IP address 209.131.36.158, the correct yahoo page is loaded.

The network card is configured using DHCP - the DNS settings are correct.  Seems like the DNS lookup is not working right.

The version is Feisty Fawn, 7.04.  That is about the limit of my Linuxness.

__________________

---

### Post by noob12 on 2007-09-08
Can you post the output of the command
```

cat /etc/resolv.conf

```

Try pinging each nameserver address listed there.  Can you reach them?

You might also try the OpenDNS section in the  HOWTO here [http://ubuntuforums.org/showthread.php?t=543659](http://ubuntuforums.org/showthread.php?t=543659) .  See if that helps.

---

### Post by chilisastry on 2007-09-08
1.  Here's the DNS list:
> cat /etc/resolv.conf

nameserver 206.13.28.11
nameserver 206.13.28.12



2.  Can ping both nameserver IP addresses with no problems (100%).



3.  Here's the result of the restart after adding the OpenDNS server IP addresses:
> sudo /etc/init.d/networking restart

There is already a pid file /var/run/dhclient.eth0.pid with pid 5376
killed old client process, removed pid file
Internet Systems Consortium DHCP Client 3.0.4
etc.

Listening on LPF/eth0/00:d0:b7:b5:3c:67
Sending on  LPF/eth0/00:d0:b7:b5:3c:67
Sending on /socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
killed old client process, removed pid file
Internet Systems Consortium DHCP Client 3.0.4
etc.

Listening on LPF/eth0/00:d0:b7:b5:3c:67
Sending on  LPF/eth0/00:d0:b7:b5:3c:67
Sending on /socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.100 -- renewal in 37001 seconds.
eth1: ERROR while getting interface flags: no such device
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client 3.0.4
etc.

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: no such device
eth1: ERROR while getting interface flags: no such device
Bind socket to interface: No such device
Failed to bring up eth1.
eth2: ERROR while getting interface flags: no such device
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client 3.0.4
etc.

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: no such device
eth2: ERROR while getting interface flags: no such device
Bind socket to interface: No such device
Failed to bring up eth2.
ath0: ERROR while getting interface flags: no such device
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client 3.0.4
etc.

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: no such device
ath0: ERROR while getting interface flags: no such device
Bind socket to interface: No such device
Failed to bring up ath0.
wlan0: ERROR while getting interface flags: no such device
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client 3.0.4
etc.

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: no such device
wlan0: ERROR while getting interface flags: no such device
Bind socket to interface: No such device
Failed to bring up wlan0.


Hope this is informative enough to solve the problem.

---

### Post by noob12 on 2007-09-08
The error messages just indicate that you have several interfaces:  eth1, eth2, ath0, and wlan0 listed in your /etc/network/interfaces file that you do not actually have on your system.

Another thing to check is that in Firefox under Preferences | Network | Connection | Settings ...  you should have Direct connection to the Internet checked.

---

### Post by chilisastry on 2007-09-09
Looks like the restart after adding the OpenDNS IP addresses works.  I did not do a reboot yesterday, only a networking restart.

However, it is strange that DNS (from the ISP) servers that work for Windows do not work for Ubuntu.  This has to be a bug.  Should it be reported somewhere?

Thanks for your help.  I will post one more message from Ubuntu (this one and all prior ones are from Windows).

---

### Post by chilisastry on 2007-09-09
Noon12, Thank you (from Ubutu).  Chili

---

### Post by chilisastry on 2007-09-09
Noob12, Thank you (from Ubutu).  Chili

---

### Post by noob12 on 2007-09-09
I wouldn't say this is an Ubuntu bug.  Lots of ISPs have unreliable or slow DNS servers.  Windows XP does do more caching of DNS lookups by default than Ubuntu, which can mask this unreliability in the XP case.  You can probably also use a local cache and your ISP's DNS servers and do ok in your situation too.  The referenced thread also has a pointer to someone's blog entry that shows you how to do that and even combine both methods.

---

