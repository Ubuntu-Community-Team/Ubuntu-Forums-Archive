---
title: "How do I specify essid dynamically?"
date: 2006-08-01
forum: Networking &amp; Wireless
---

### Post by vayu on 2006-08-01
Using the command line, how can I specify the essid when there are several available?

My interfaces file has a line like this:
iface hotspot inet dhcp

Then when I'm wanting to connect at a cafe I do this:
sudo ifup eth2=hotspot
sudo dhclient eth2

I want to include the essid in the above.  I can do it in the intefaces file by adding a line with:
        wireless-essid <essid>
but I want to do it in the above command line.  Is it possible?


(I'm not sure about using network manager.  I'm leary of GUI programs that I don't know what they are doing.  I had a hard time getting several different connections working; wired static, wireless static with WPA and wireless DHCP. I don't want to mess that up and I want to keep the command line understanding I've struggled to gain.)

---

### Post by stormblue on 2006-08-02
Here is what I do to connect:

Bring up your interface:

```
sudo ifconfig eth2 up
```
Specify Network Name
```

sudo iwconfig eth2 essid network_name
```
Pass the key if need be
```

sudo iwconfig eth2 key wep_key_here
```
Pull up the DHCP stuff
```
sudo dhclient eth2
```

Replace eth2 with whatever yours maybe ethx, wlanx, athx, etc, etc.

---

### Post by vayu on 2006-08-02
> **stormblue said:**
> Here is what I do to connect:

Bring up your interface:
sudo ifconfig eth2 up

Specify Network Name
sudo iwconfig eth2 essid network_name

Pass the key if need be
sudo iwconfig eth2 key wep_key_here

Pull up the DHCP stuff
sudo dhclient eth2

Replace eth2 with whatever yours maybe ethx, wlanx, athx, etc, etc.


Thanks, just what I wanted.

---

