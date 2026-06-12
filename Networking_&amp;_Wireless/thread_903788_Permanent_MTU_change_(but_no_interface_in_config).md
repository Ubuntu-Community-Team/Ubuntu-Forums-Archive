---
title: "Permanent MTU change (but no interface in config)"
date: 2008-08-28
forum: Networking &amp; Wireless
---

### Post by zackiv31 on 2008-08-28
Ubuntu Hardy with gigabit lan..  I can set the mtu manually by:

sudo ifconfig eth0 mtu 9000

And this works fine, but I want it to always start with that default mtu.

I've been told to add mtu 9000 to the /etc/network/interfaces file, but mine doesn't have any values for eth0 in there!  Here is the contents of my file, what else must I put in to get eth0 to default to mtu 9000?

```

auto lo
iface lo inet loopback

```

My network is setup through DHCP if this matters...

---

### Post by caljohnsmith on 2008-08-28
How did you originally configure your eth0 interface? If you used Network Manager, it should have saved its settings for eth0 in your /etc/network/interfaces file. Did you set it up entirely manually maybe? 

You could try adding eth0 to your interfaces file manually with:
```
iface eth0 inet dhcp
mtu 9000
auto eth0
```
If you then do:
```
sudo ifdown eth0
sudo ifup eth0
```
Then it should be using your new MTU value, because ifdown/ifup use that interface file. And having eth0 in your interfaces file should make the new MTU value stick on a reboot.

P.S. "Gigabit LAN"??? I'm envious. :)

---

### Post by redmk2 on 2008-08-28
I have a question.  How do you throttle back to 1500 MTU for internet destinations?  Do you need to?  I know that 10/100 Ethernet has a max of 1500 MTU.  How is that compatibility maintained?

I ask because my next network will be gig Ethernet.  Can you point me towards some information please.

Thanks in advance,

Red

---

### Post by zackiv31 on 2008-08-29
I've tried adding

```

auto eth0
mtu 9000

```

and this just hangs the bootup process... so I have to delete those lines.  How can I get this accomplished?  I don't see any way to do it through network manager...

---

### Post by zackiv31 on 2009-07-12
Decided to update this post as I ran into the problem a year later...

Solution:

Create a file, I called it mtu in /etc/network/if-up.d/ :
```

sudo gedit /etc/network/if-up.d/mtu

```

Add the following to it (Set the mtu to your desired, I enabled jumbo frames):
```

#!/bin/sh
ifconfig eth1 mtu 9000

```

Make the file executable:
```

sudo chmod 755 /etc/network/if-up.d/mtu

```

Reboot, and all should be well.

---

### Post by lswb on 2009-07-12
> **caljohnsmith said:**
> How did you originally configure your eth0 interface? If you used Network Manager, it should have saved its settings for eth0 in your /etc/network/interfaces file. Did you set it up entirely manually maybe? 


With what version did Network Manager start using the /etc/network/interfaces file? That is a big change and I haven't seen any documentation of it anywhere.

---

