---
title: "nm-applet for networkmanager not working after Edgy update"
date: 2006-10-26
forum: Networking &amp; Wireless
---

### Post by MattW on 2006-10-26
I just upgraded to Edgy and it seems rather nice. A couple of particular niggles though, one of which I'll address here and another one I might post about later once I've done some more diagnostics (it's a completely different issue).

I had NetworkManager working perfectly before the update. Now it doesn't - well, it works fine with wired connections, but the nm-applet itself doesn't work, which in turns means the daemon can't get the key for my wireless network.

When trying to start nm-applet from the console I get this:

> ** (nm-applet:7730): WARNING **: <WARNING>       nma_dbus_init (): nma_dbus_init() could not acquire its service.  dbus_bus_acquire_service() says: 'Connection ":1.20" is not allowed to own the service "org.freedesktop.NetworkManagerInfo" due to security policies in the configuration file'

I've not done anything to any part of this sort of config file on this system, and this is definitely new since Edgy update.

Google was little help, and only showed me someone with the same problem on the NetworkManager list quite some time ago with no solution being posted. Does anybody have any ideas?

---

### Post by jUser on 2006-10-27
> **MattW said:**
> When trying to start nm-applet from the console

I think it requires the user to be root. Try

```
sudo nm-applet
```

and see if you get any different results.

---

### Post by MattW on 2006-10-27
That allows me to start the applet and use it, but because it was always running as me before, it can't access the keyring for my network keys etc.

So this lets me use the wireless, but it's not what it should be still.

---

### Post by MattW on 2006-10-27
It seems to be working properly now. No idea why.

Confused, but happy :-)

---

