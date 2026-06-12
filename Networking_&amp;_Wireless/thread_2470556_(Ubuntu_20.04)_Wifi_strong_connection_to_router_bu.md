---
title: "(Ubuntu 20.04) Wifi: strong connection to router but no internet after suspend/boot"
date: 2022-01-03
forum: Networking &amp; Wireless
---

### Post by MaccyDG on 2022-01-03
Hello,

My wifi has stopped working reliably. When I wake up my laptop from a suspend state or do a fresh boot, I get a strong connection to my router, but frequently no connection to the internet.

What _does_ work:
* Internet access via ethernet cable direct to router
* Turn the wifi off, then on again (usually several times)
* Same laptop, but booting into Windows 10.
* Wifi access on my partner's Apple smartphone/laptop

What does _not_ work:
* Wifi on my Ubuntu Touch smartphone: stopped working the very same day I got problems with my laptop. Possible coincidence; happy to treat as separate unless likely to have a common cause.

This is not a fresh install - I have had many months of normal wifi behaviour prior. Router has been in use for several years.

Possible red herring: when I have no internet access, the output from ```
sudo dhclient -v
``` ends with the line ```
bound to 192.168.1.134 -- renewal in 30 seconds.

``` It is always a max. of 30 seconds. When I run the same command _with_ internet access through my wifi, I get this ```
Internet Systems Consortium DHCP Client 4.4.1
Copyright 2004-2018 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

/var/lib/dhcp/dhclient.leases line 51: numeric hour expected.
  renew 2 2022/01/04 05lease 
                      ^
/var/lib/dhcp/dhclient.leases line 51: semicolon expected.
  renew 2 2022/01/04 05lease {
                              ^
Corrupt lease file - possible data loss!
Corrupt lease file - possible data loss!
Corrupt lease file - possible data loss!
Corrupt lease file - possible data loss!
Corrupt lease file - possible data loss!
Corrupt lease file - possible data loss!
Corrupt lease file - possible data loss!
Corrupt lease file - possible data loss!
Corrupt lease file - possible data loss!
Corrupt lease file - possible data loss!
Corrupt lease file - possible data loss!
Corrupt lease file - possible data loss!
Corrupt lease file - possible data loss!
Listening on LPF/docker0/02:42:23:07:69:11
Sending on   LPF/docker0/02:42:23:07:69:11
Listening on LPF/wlp1s0/b0:35:9f:af:f5:78
Sending on   LPF/wlp1s0/b0:35:9f:af:f5:78
Listening on LPF/enp0s31f6/a4:4c:c8:49:3d:09
Sending on   LPF/enp0s31f6/a4:4c:c8:49:3d:09
Sending on   Socket/fallback
DHCPDISCOVER on docker0 to 255.255.255.255 port 67 interval 3 (xid=0x53245324)
DHCPREQUEST for 192.168.1.134 on wlp1s0 to 255.255.255.255 port 67 (xid=0x1d18f5a1)
DHCPDISCOVER on enp0s31f6 to 255.255.255.255 port 67 interval 3 (xid=0x61c6dd29)
DHCPACK of 192.168.1.134 from 192.168.1.254 (xid=0xa1f5181d)
bound to 192.168.1.134 -- renewal in 33412 seconds.

```

System:
[LIST]
[*]Ubuntu 20.04 
[*]Dell Latitude 5580 
[*]Intel Wireless 8265 / 8275 
[*]All Ubuntu updates applied 
[*]No 3rd-party wireless drivers installed 
[*]BT SmartHub - Type A 
[/LIST]

Any guidance gratefully received.

---

### Post by TheFu on 2022-01-05
Something is corrupting the dhcp run file.

Have you tried deleting the dhcp.leases file?

Another guess, but if the storage block where the lease run file is stored is failing, then that corruption can happen.  Run smartctl to check for any bad disk areas that need remapping ... or use badblocks, if you like.  If there are more than a few relocated sectors, time to replace the storage device.

Of course, this is just 1 idea.

---

### Post by MaccyDG on 2022-01-08
TheFu: many thanks for your help. After several days of experiencing the problem, it seemed to resolve by itself. Your suggestion makes sense to me - I will try it if I get the same issue again and report back here for the benefit of others with the same issue.

I have left the thread as unsolved because I can't be sure that TheFu's suggestion is the solution (though it might well be).

If you are dealing with this issue yourself: it might be helpful to know that now that my wifi is working as expected, the output of ```
sudo dhclient -v
``` looks like this:
```
Internet Systems Consortium DHCP Client 4.4.1
Copyright 2004-2018 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/docker0/02:42:30:06:92:10
Sending on   LPF/docker0/02:42:30:06:92:10
Listening on LPF/wlp1s0/b0:35:9f:af:f5:78
Sending on   LPF/wlp1s0/b0:35:9f:af:f5:78
Listening on LPF/enp0s31f6/a4:4c:c8:49:3d:09
Sending on   LPF/enp0s31f6/a4:4c:c8:49:3d:09
Sending on   Socket/fallback
DHCPDISCOVER on docker0 to 255.255.255.255 port 67 interval 3 (xid=0xa6158a46)
DHCPDISCOVER on wlp1s0 to 255.255.255.255 port 67 interval 3 (xid=0x910e497c)
DHCPDISCOVER on enp0s31f6 to 255.255.255.255 port 67 interval 3 (xid=0x39965c5d)
DHCPOFFER of 192.168.1.134 from 192.168.1.254
DHCPREQUEST for 192.168.1.134 on wlp1s0 to 255.255.255.255 port 67 (xid=0x7c490e91)
DHCPACK of 192.168.1.134 from 192.168.1.254 (xid=0x910e497c)
bound to 192.168.1.134 -- renewal in 34801 seconds.

```

The dhclient.leases file that TheFu refers to can be found in /var/lib/dhcp/dhclient.leases.

---

