---
title: "Wireless network disconnections: No ProbeResp"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by howlsmoving on 2007-10-23
I am using an intel4965AGN mini-pci wireless card and a  WRT54G router.  My problem is: I am randomly disconnect from the router.  The last line of dmesg says: "wlan0: No ProbeResp from current AP 00:1c:10:04:5f:be assume out of range"  Now, I can restart my computer and it (normally) reconnects to the router no problem.  Also, another laptop using the connection in the house doesn't lose connectivity at all (and its running Vista).

When I try to reconnect, no access points (router) are discovered.

The disconnections occur when the network connection isn't in use.  But this can be anywhere from a half hour idle, to 1 or 2 minutes.  This only started happening a couple of days ago.  Since then I've had to reboot my computer over half a dozen times just to get wireless to work again.

Any ideas, or insights would be greatly appreciated.

---

### Post by howlsmoving on 2007-10-23
Okay, so I tried "modprobe -r iwl4965", then "modprobe iwl4965," after that, scanning for an open network works and I am able to connect.

Is there another way to solve this problem? Can this be fixed?  Is it maybe a problem with the iwl4965 module? I would really like to know.

Thanks.

---

### Post by konti on 2007-10-27
I have the same problem. Did you find a sollution to this problem?

i'm using Ubuntu 7.10 32 bit installed from live dvd. Other messages are:

ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
ADDRCONF(NETDEV_UP): wlan0: link is not ready

doesn't change after that last message.
Trying to connect to wpa1 aes encryption

---

### Post by fbn on 2008-03-10
any news on this? I have the same problem here.

---

### Post by blankthemuffin on 2008-03-12
I'm having this problem too on a fresh install of Ubuntu 7.10 on a Dell Inspiron 1520 with a Intel Corporation PRO/Wireless 4965 AGN.

This is a dump of what happened and shortly after as it reconnects, I presume most of the latter would be meaningless.

```

Mar 12 16:56:03 blankthelappy kernel: [ 3869.844000] wlan0: No ProbeResp from current AP 00:08:a1:a1:00:56 - assume out of range
Mar 12 16:56:04 blankthelappy kernel: [ 3871.556000] wlan0: No STA entry for own AP 00:08:a1:a1:00:56
Mar 12 16:56:11 blankthelappy kernel: [ 3878.156000] wlan0: No STA entry for own AP 00:08:a1:a1:00:56
Mar 12 16:56:18 blankthelappy kernel: [ 3884.760000] wlan0: No STA entry for own AP 00:08:a1:a1:00:56
Mar 12 16:56:23 blankthelappy NetworkManager: <info>  wlan0: link timed out. 
Mar 12 16:56:23 blankthelappy NetworkManager: <info>  SWITCH: found better connection 'wlan0/blankthewifi' than current connection 'wlan0/blankthewifi'.  same_ssid=1, have_link=0 
Mar 12 16:56:23 blankthelappy NetworkManager: <info>  Will activate connection 'wlan0/blankthewifi'. 
Mar 12 16:56:23 blankthelappy NetworkManager: <info>  Device wlan0 activation scheduled... 
Mar 12 16:56:23 blankthelappy NetworkManager: <info>  Deactivating device wlan0. 
Mar 12 16:56:23 blankthelappy dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 14049
Mar 12 16:56:23 blankthelappy dhclient: killed old client process, removed PID file
Mar 12 16:56:23 blankthelappy dhclient: wmaster0: unknown hardware address type 801
Mar 12 16:56:23 blankthelappy dhclient: wmaster0: unknown hardware address type 801
Mar 12 16:56:23 blankthelappy dhclient: DHCPRELEASE on wlan0 to 192.168.1.254 port 67
Mar 12 16:56:23 blankthelappy avahi-daemon[5640]: Withdrawing address record for 192.168.1.2 on wlan0.
Mar 12 16:56:23 blankthelappy avahi-daemon[5640]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.2.
Mar 12 16:56:23 blankthelappy avahi-daemon[5640]: Interface wlan0.IPv4 no longer relevant for mDNS.
Mar 12 16:56:24 blankthelappy avahi-daemon[5640]: Withdrawing address record for fe80::21d:e0ff:fe79:e1b7 on wlan0.
Mar 12 16:56:24 blankthelappy NetworkManager: <info>  Activation (wlan0) started... 

```

The problem seems to show itself when I let the connection idle.

---

