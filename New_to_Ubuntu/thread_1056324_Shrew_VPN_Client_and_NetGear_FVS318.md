---
title: "Shrew VPN Client and NetGear FVS318"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by CharlesJ on 2009-01-31
I have beet trying to use the Shrew VPN client to connect to a Netgear FVS318. I am able to make a connection to the tunnel

config loaded for site 'xx.xx.xx.xx'
attached to key daemon ...
peer configured
iskamp proposal configured
esp proposal configured
client configured
local id configured
remote id configured
pre-shared key configured
bringing up tunnel ...
virtual network device configured
virtual network device enabled
tunnel enabled

But the Security Associations does not seem to be connecting 
Established -0
Expired -0
Failed -0

I can ping my remote gateway but not computers behind it.
When I try to ping computers on my remote network the Failed # increases

My local network is 192.168.10.0 255.255.255.0 and the remote network is 192.168.0.0 55.255.255.0
 
Any idea what I should try next?

---

### Post by CharlesJ on 2009-02-08
After playing for a week I have been able to establish a tunnel and ping computers on the other side of the tunnel in both Windows and Ubuntu

I would like to thank Matthew Grooms from Shrew software for his help.

For those reading my post - Some pointers / observations

Early versions of FW on the FVS318 have an issue sending a delete messages when you ping computers behind it. I upgraded from V16 to V27 and this corrected the issue.

The Shrew VPN client bundled with Ubuntu Hardy appears to has an issue correctly identifying the parameters for the "Remote Host" when DNS is disabled. This is fixed in the latest version (2.1.4) you can download from their web site.

Closed:D

---

### Post by fcigoi on 2009-06-14
Hi Charles,

Having the same issue here, but with a 338. Would you be so kind as to mail me your configs so that I can try and figure out what's wrong with mine ?
I get to the point of bringing the tunnel up, but then it times out with no further progress. Also, it used to hang completely my previous 114 router...big mess.

---

### Post by luckyluke994 on 2009-10-06
I have the same config (shrew VPN 2.1.4 and NetGear FVS318). I succeeded to connect to the rooter:
attached to key daemon ...
peer configured
iskamp proposal configured
esp proposal configured
client configured
local id configured
remote id configured
pre-shared key configured
bringing up tunnel ...
network device configured
tunnel enabled

but cannot ping any hosts (ping doesn't answer)

Could you post your config?

Thanks

LL

---

