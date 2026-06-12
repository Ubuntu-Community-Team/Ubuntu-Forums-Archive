---
title: "SE W890i works on Jaunty, not on Hardy"
date: 2009-10-04
forum: New to Ubuntu
---

### Post by PocketDog on 2009-10-04
I can use my Sony Ericsson W890i as a modem on my desktop (Jaunty) which is nice, but not entirely useful, being my home PC.
When I'm out and about with my laptop, running Hardy Heron, I'd like to be able to plug in my phone and get online anywhere - but Heron doesn't recognise the phone at all.
I assume this is because 8.10 and later versions use a different network manager, am I right? If so, can I get the later versions' network manager installed in Hardy? 

Both machines are fully up to date, and I'd rather not re-install or dist-upgrade the laptop for now.

Thanks.

---

### Post by t0p on 2009-10-04
The network manager in Jaunty is called network-manager.  I don't know if it's the same name in Hardy (I'm not on my Hardy machine right now).  You could do a Synaptic search for "network-manager" to see what's what.

---

### Post by PocketDog on 2009-10-05
Yeah, I have network-manager (daemon) and network-manager-gnome (frontend).
Both latest versions apparently.

lsusb gives
```

Bus 001 Device 004: ID 0fce:d0b3 Sony Ericsson Mobile Communications AB 

```

so the kernel sees the phone, but the network manager doesn't. Puzzling.

---

### Post by wildman4god on 2009-10-05
it works in jaunty and not in hardy because hardy is an older version and didn't have as good device support, jaunty had phenominal hardware support. So is is a driver issue. the only way to get it to work is to upgrade from hardy to jaunty or wait intill karmic later this month and upgrade to that, hardy didn't have very good device support, I know it is the last LTS but device support stunk, please upgrade.

---

