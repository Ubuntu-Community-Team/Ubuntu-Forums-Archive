---
title: "Upstart on a laptop"
date: 2015-10-10
forum: Networking &amp; Wireless
---

### Post by MrMe01 on 2015-10-10
Hi folks,

I'm having an issue with Upstart on boot, it takes ~2 minutes to boot as it's waiting for eth0. As it's a laptop, I'm more likely to be using wireless, any way to reduce the waiting time?

---

### Post by MrMe01 on 2015-10-10
Fixed it, [http://tech.pedersen-live.com/2012/05/disable-waiting-for-network-configuration-messages-on-ubuntu-boot/](http://tech.pedersen-live.com/2012/05/disable-waiting-for-network-configuration-messages-on-ubuntu-boot/)

---

### Post by v3.xx on 2015-10-10
Open up /etc/network/interfaces and comment out the last two lines.

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
[COLOR="#FF0000"]#[/COLOR]auto eth0
[COLOR="#FF0000"]#[/COLOR]iface eth0 inet dhcp
```

That will stop the wait at boot.

---

### Post by MrMe01 on 2015-10-10
> **v3.xx said:**
> Open up /etc/network/interfaces and comment out the last two lines.

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
[COLOR=#FF0000]#[/COLOR]auto eth0
[COLOR=#FF0000]#[/COLOR]iface eth0 inet dhcp
```

That will stop the wait at boot.

Would you recommend this fix over the one I posted? I haven't had any issues on either interface, wireless or wired so far.

The link I used to fix it, [http://tech.pedersen-live.com/2012/05/disable-waiting-for-network-configuration-messages-on-ubuntu-boot/](http://tech.pedersen-live.com/2012/05/disable-waiting-for-network-configuration-messages-on-ubuntu-boot/)

I have a copy of the original file to go back to.

---

### Post by v3.xx on 2015-10-10
> Would you recommend this fix over the one I posted?

No

Just was no reply when I marked your thread.  Should of refreshed my screen first :)

---

