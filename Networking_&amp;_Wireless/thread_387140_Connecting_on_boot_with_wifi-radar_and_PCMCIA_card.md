---
title: "Connecting on boot with wifi-radar and PCMCIA card"
date: 2007-03-17
forum: Networking &amp; Wireless
---

### Post by afoglia on 2007-03-17
I'm having trouble getting my laptop to connect via wireless automatically upon booting.  I thought it might be because wifi-radar had a lower priority in rc2.d (20) than the pcmcia scripts in rcS (40), but having just turned off the quiet and splash options in /boot/grub/menu.lst and turning on the verbose option in /etc/default/rcS, it looks like that's not the case.  Any ideas?

Could it be related to ifconfig not showing the wireless card until I run wifi-radar manually?  (It is shown in iwconfig and "cardctl status" knows there is a card in the slot.)

---

### Post by Kobalt on 2007-03-18
Can you please post us the outpuf of (remove any ssid or wireless key that might apear befor posting) :
```
cat /etc/network/interfaces
```
It could be just a simple 'auto wlan0' option missing...

---

### Post by afoglia on 2007-03-18
> **Kobalt said:**
> Can you please post us the outpuf of (remove any ssid or wireless key that might apear befor posting) :
```
cat /etc/network/interfaces
```
It could be just a simple 'auto wlan0' option missing...

Well, I've never had a wlan0 device.  My card always looks like either eth0 or eth1.  (Mostly eth0, but I think it's been eth1 in the past.)  Here's my /etc/network/interfaces, omitting the loopback interface lines.

```

# The primary network interface
auto eth1
iface eth1 inet dhcp

# wireless interface
auto eth0
```

I added the "auto eth0" just now in hopes things would work, but no such luck.

For completeness, here's the top lines of my /etc/wifi-radar.conf, omitting the configuration for each AP.

```

[DEFAULT]
ifup_required = False
auto_profile_order = Foglia,PCM,JavaJones,FogliaG
speak_up = False
scan_timeout = 5
interface = eth0
commit_required = False
```

---

### Post by afoglia on 2007-03-21
Well, whatever it was, it fixed itself when I upgraded to Feisty.  Much better.

---

