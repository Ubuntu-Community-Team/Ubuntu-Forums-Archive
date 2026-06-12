---
title: "Pilot-xfer sync problem (after upgrade?)"
date: 2008-02-04
forum: Networking &amp; Wireless
---

### Post by redthor on 2008-02-04
Hi there,
I've been syncing my PDA quite happily with J-Pilot over bluetooth but today it's stopped working. I noted that there was a new upgrade on the kernel and so I wonder if that's had anything to do with it.

Anyway, when I start bluetooth on the laptop and then go onto my PDA and establish the connection all works well:

```
Feb  5 09:11:56 laptop pppd[6295]: pppd 2.4.4 started by root, uid 0
Feb  5 09:11:56 laptop pppd[6295]: Using interface ppp0
Feb  5 09:11:56 laptop pppd[6295]: Connect: ppp0 <--> /dev/rfcomm0
Feb  5 09:12:00 laptop pppd[6295]: found interface wlan0 for proxy arp
Feb  5 09:12:00 laptop pppd[6295]: local  IP address 192.168.0.60
Feb  5 09:12:00 laptop pppd[6295]: remote IP address 192.168.0.105
```

However when run this:
```
pilot-xfer -p net:any -l
```

All I get is:
```
   Listening for incoming connection on net:any... 
```

And nothing else happens.

Anyone help with debugging or getting to the bottom of it?

Thanks muchly,
r

---

### Post by redthor on 2008-02-06
I haven't had much joy yet so here's some testing I've done.

Confirm bluetooth is ok:
```
> hcitool scan
        00:07:E0:5F:4B:2D       MyTreo

```

Contents of /etc/ppp/peers/dun:
```
115200
  192.168.0.105:192.168.0.202
  local
  ms-dns 192.168.0.1
  noauth
  debug
```

Check to see I can surf the web through pppd (from [http://howto.pilot-link.org/bluesync/ga.htm](http://howto.pilot-link.org/bluesync/ga.htm)l):
```
echo 1 > /proc/sys/net/ipv4/ip_forward
```

Then on the  treo select Prefs->Network->linux Connect and results in /var/log/messages:
```
Feb  7 13:05:43 laptop kernel: [ 9449.316000] PPP generic driver version 2.4.2
Feb  7 13:05:43 laptop pppd[6886]: pppd 2.4.4 started by root, uid 0
Feb  7 13:05:43 laptop pppd[6886]: Using interface ppp0
Feb  7 13:05:43 laptop pppd[6886]: Connect: ppp0 <--> /dev/rfcomm0
Feb  7 13:05:47 laptop kernel: [ 9453.324000] PPP BSD Compression module registered
Feb  7 13:05:47 laptop kernel: [ 9453.384000] PPP Deflate Compression module registered
Feb  7 13:05:47 laptop pppd[6886]: found interface wlan0 for proxy arp
Feb  7 13:05:47 laptop pppd[6886]: local  IP address 192.168.0.105
Feb  7 13:05:47 laptop pppd[6886]: remote IP address 192.168.0.202
```

Looks all good. Now try the web on the treo... no good, it doesn't have a connection.

Try pinging the Treo from the laptop:
```
>ping 192.168.0.202
 PING 192.168.0.202 (192.168.0.202) 56(84) bytes of data.
64 bytes from 192.168.0.202: icmp_seq=1 ttl=255 time=20.8 ms
64 bytes from 192.168.0.202: icmp_seq=2 ttl=255 time=19.9 ms
64 bytes from 192.168.0.202: icmp_seq=3 ttl=255 time=20.0 ms
64 bytes from 192.168.0.202: icmp_seq=4 ttl=255 time=19.9 ms

--- 192.168.0.202 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3000ms
```

That's fine, so it just doesn't seem to get a route out?

I've tried pilot-xfer -p net:any yesterday and it didn't work so I thought I'd try:
```
 pilot-xfer -p net:192.168.0.202 -l
   Unable to bind to port: net:192.168.0.202
   Please use --help for more information
```
But for some reason that doesn't work.

Then I tried the original again:
```
 pilot-xfer -p net:any -l
```
pressed HotSync... and well.. .it worked !!!

The weird thing is I haven't done anything different from yesterday unless it was simply the reboot.

So this post is solved (without knowing the solution) but it's unlikely to help anyone else!

---

