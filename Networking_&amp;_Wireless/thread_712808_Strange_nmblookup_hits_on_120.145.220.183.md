---
title: "Strange nmblookup hits on 120.145.220.183"
date: 2008-03-02
forum: Networking &amp; Wireless
---

### Post by Eiríkr on 2008-03-02
I've been trying to diagnose why my Samba setup won't display properly in my iBook's Network pane, and have been spending some time futzing about with [font=courier]nmblookup[/font].  I'm behind a router, with my home network assigned to the 192.168.x.x space.  I tried the following from my iBook, and am quite disturbed by what I found:
```
user@ibook:~$ nmblookup -U smbserver "*"
querying * on 192.168.10.10
192.168.10.10 *<00>
120.145.220.183 *<00>
user@ibook:~$
```

So I tried again from my smb server:
```
user@smbserver:~$ nmblookup -U smbserver "*"
querying * on 127.0.1.1
192.168.10.10 *<00>
120.145.220.183 *<00>
user@smbserver:~$
```

Meanwhile, running [font=courier]nmblookup "*"[/font] without specifying the "-U" unicast address WINS server query option produces the expected:

```
user@smbserver:~$ nmblookup "*"
querying * on 192.168.10.255
192.168.10.10 *<00>
user@smbserver:~$
```

Anyone have any clue what this means?  I tried whois lookup on this 120.145.220.183 address but came up with zilch.  Traceroute gets one hop away from my ISP and fails.  Have I been rooted, or is this some oddball bogus IP address that Samba's nmbd process is returning as a bug?

Worried,

Eiríkr

---

### Post by SpaceTeddy on 2008-03-02
mhm, have you done a trace to that ip to see if you can acctually find it ? and if it answers... ?
what happens if you assign yourself an ip in that range and try to reach it then ?
also, does your router supply any wins support ?


a guess would be that is it a badly configured computer outside of your network (in the internet) from someone that uses the same isp as you do, and that computer somehow registeres with your router through the wins server... 

But - that is strech to no end :(

sadly, i have no other ideas :(

---

### Post by Eiríkr on 2008-03-02
I physically shut off the worrisome machine last night.  Running traceroute from my iBook produces the following:
```
Traceroute has started ...

traceroute to 120.145.220.183 (120.145.220.183), 64 hops max, 40 byte packets
 1  192.168.10.1 (192.168.10.1)  1.510 ms  1.130 ms  1.092 ms
 2  192.168.0.1 (192.168.0.1)  1.570 ms  1.847 ms  1.485 ms
 3  adsl-75-18-191-254.dsl.pltn13.sbcglobal.net (75.18.191.254)  8.390 ms  8.260 ms  9.705 ms
 4  64.164.107.130 (64.164.107.130)  8.999 ms  8.746 ms  8.527 ms
 5  * * *
 6  * * *
```
... with just lots more * * * entries until traceroute fails out.  Whois gives me a bare lead that the 120.0.0.0 - 120.255.255.255 range is administered by APNIC, but all that tells me is that the IP is ostensibly from somewhere in Asia or the Pacific (incl. Australia).  I can't seem to get any other info about this address.  

I'll futz with my router firewall to block outgoing traffic later today (had previously operated on the assumption that blocking incoming was good enough), then I'll turn the Ubuntu machine back and and see what the router's firewall logs tell me.   

If anyone else has any inklings, by all means please let me know.  

Cheers,

Eiríkr

---

