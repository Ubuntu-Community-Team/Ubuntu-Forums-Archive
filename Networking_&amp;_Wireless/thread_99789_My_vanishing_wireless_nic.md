---
title: "My vanishing wireless nic?"
date: 2005-12-06
forum: Networking &amp; Wireless
---

### Post by ravalox on 2005-12-06
Okay, so I installed Ubuntu on my laptop, and everything except the 3d video was working just fine.  I had an active wireless connection until I rebooted this morning and now the wireless card is no longer available in the networking menu.  The Administration->Networking application won't let me add a device, so I'm wondering how do I trick Ubuntu into giving me my wireless networking back?

---

### Post by Lambert on 2005-12-06
If nothing is showing up in networking, that usually means no working driver. So you need to find what [driver]("http://linux-wless.passys.nl/") your device uses.

Then run this command.

```
lsmod
```

to see if the driver is loaded. If not run this command to load it.

```
modprobe <driver>
```

where <driver> =the name of the driver minus the<>

---

### Post by ravalox on 2005-12-06
I ```
lsmod
```'ed and I don't think the wireless driver is there, but I don't know what driver it would have used.  This was working yesterday and today until I rebooted this morning... and then nothing.  I tried looking in the /etc/init.d for a net.* (or in this case ath.*) device I could try to start/restart but I can't find anything like that.

---

### Post by ravalox on 2005-12-06
Okay, so after poking around some more, even the device manager knows what kind of wireless NIC I have.  So it is picked up by lspci and Ubuntu's tools, yet I can no longer access it in the networking menu, nor does Ubuntu have the net.ath0 I'd expect to find in /etc/init.d/, in fact it has no net.* devices in there, so I don't know what diagnostics Ubuntu affords me?

---

