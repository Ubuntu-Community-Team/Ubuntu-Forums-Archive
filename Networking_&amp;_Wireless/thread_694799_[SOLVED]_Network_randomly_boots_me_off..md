---
title: "[SOLVED] Network randomly boots me off."
date: 2008-02-12
forum: Networking &amp; Wireless
---

### Post by Nero147 on 2008-02-12
Ok, so I've been having this problem recently, my network connection will just stop working. It still shows me connected with an IP address, but if I try to renew my IP it gives me errors.

A little bit of background, I'm using gutsy 64 with fakeraid 0. This started happening after I installed fakeraid, but a while after, so I'm not sure if that's it. This is what I get when I try to renew my IP

nero@nero-desktop:~$ sudo ifdown eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 4801
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1a:a0:3e:53:b4
Sending on   LPF/eth0/00:1a:a0:3e:53:b4
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
nero@nero-desktop:~$ sudo ifup eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1a:a0:3e:53:b4
Sending on   LPF/eth0/00:1a:a0:3e:53:b4
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I tried to reset my dhcp leases to max out on my router (wired btw) and that didn't help. My windows partition is having no problems, and the other computers on my network are having no problems. the weirdest thing is that the kickoff is completely random and the moment that I reboot it works, and it doesn't have problems in Windows, although to be fair I spend very little time booted into Windows; I only have it on here for my brother to use.

Any ideas from anyone, or links to posts that I might have missed, or need for further logs?

Also please forgive the crudeness of my post, but I've never actually had to post a question in the forums before.

---

### Post by Nero147 on 2008-02-21
I just completely wiped and reinstalled without fakeraid and I am going to see if it fixes the issue.

---

### Post by Nero147 on 2008-02-24
ok, so I finished reformatting and redoing everything. Apparently it was either my raid 0 setup, or something else that I had done and forgot about. Either way a reformat and no raid :( later it's working.

---

