---
title: "No DHCPOFFERS received"
date: 2007-01-30
forum: Networking &amp; Wireless
---

### Post by trancending on 2007-01-30
I installed Ubuntu onto my machine after getting frazzled with windows. Booting in with the Edgy Live CD and using it to install/reformat the original HD. My internet worked to begin with and I was able to get updates and software and packages.

Today I no longer get internet though. Cruised the forums and tried most things I found from IPv6 fixes to 

sudo dhclient eth0.

There is already a pid file /var/run/dhclient.pid with pid 6490
killed old client process, removed PID file
...

...
wmaster0: unknown hardware address type 801 (I'm trying to get a wired connection, is this wireless?)
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:13:d4:81:79:44
Sending on LPF/eth0/00:13:d4:81:79:44
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


When I check ifconfig I get

eth0    Link encap:Ethernet HWaddr 00:13:D4:81:79:44
          inet6 addr: fe80::213::d4ff:fe81::7944/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
          RX packets:283 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:30834 (30.1 KiB)    TX bytes:0 (0.0b)
          interupt:98

lo       Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING MTU:16436 Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:700 (700.0 b)    TX bytes:700 (700.0b)


Writing this all in by hand :confused: 

Also have a wlan0 and wmaster0

Any and all help would be appreciated.

---

### Post by theavier on 2007-02-01
Writing  by hand! That's .. so primitive ;)
Anyway have you controlled /etc/resolv.conf so that you have a valid dns address. 
Your ifconfig seems to lack an ipaddress, so that's where I'd start looking
It should look something like this, with your dns at 192.x.x.x
----resolv.conf----
search localdomain
nameserver 192.168.1.1
----eof----

---

### Post by usererror on 2007-02-01
is the resolve.conf file something that is changing all the time?  is it similar to the "hosts" file on a windows box?

---

### Post by mips on 2007-02-01
First try a static config so you can eliminate any lower level problems.

---

### Post by koenn on 2007-02-01
> **theavier said:**
> Writing  by hand! That's .. so primitive ;)
Anyway have you controlled /etc/resolv.conf so that you have a valid dns address. 
Your ifconfig seems to lack an ipaddress, so that's where I'd start looking
It should look something like this, with your dns at 192.x.x.x
----resolv.conf----
search localdomain
nameserver 192.168.1.1
----eof----
Ignore this post. 
not getting dhcp offers has nothing to do with dns ;
and ifconfig does not show an ip address because you depend on dhcpoffers to get one 

As mips said, static network configuration could be a place to start and find out what's really causing this.

---

### Post by koenn on 2007-02-01
On a side note:> is the resolve.conf file something that is changing all the time? is it similar to the "hosts" file on a windows box?

/etc/hosts is wat "the hosts file" is on a windows box.
/etc/resolv.conf is a list of dns servers. It can be created manually (with a text editor), or modified automaitcally, eg when dhcp tells you computer which DNS servers it should use. (so it *can* change 'all the time')

---

### Post by chili555 on 2007-02-01
No DHCPOFFERS received sometimes means a problem with encryption. Are you using WEP or WPA? Have you tried, temporarily, with encryption turned off in the router?

Let us know; we'll get it going.

---

### Post by usererror on 2007-02-02
> **koenn said:**
> On a side note:
/etc/hosts is wat "the hosts file" is on a windows box.
/etc/resolv.conf is a list of dns servers. It can be created manually (with a text editor), or modified automaitcally, eg when dhcp tells you computer which DNS servers it should use. (so it *can* change 'all the time')

Thanks for the explanation!

to Chili555:  his interface is eth0 so I am assuming he's got a wired NIC and no encryption is taking place here.  unless of course he only has a wifi card then maybe ubuntu put it in as eth0 during install.

to the original poster: have you tried using a static IP yet?

---

### Post by checho on 2007-02-07
Hi, I used to have the same problem, all you gotta do is run in console "dhclient eth0", then restart your router ( better if you unplug it and wait a minute) and then run the command again (dhclient eth0). eth0 you may replace it with the name of the device you are trying to connect with.

---

