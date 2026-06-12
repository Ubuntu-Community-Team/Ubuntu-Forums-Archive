---
title: "Turn off wireless permanently?"
date: 2007-10-27
forum: Networking &amp; Wireless
---

### Post by chaeron on 2007-10-27
Anyone know of an easy way to disable wireless permanently, that is, so that it stays disabled across a reboot?

The Wireless applet lets you turn off wireless, but it re-enables if you reboot.

I don't want to uninstall the drivers...just disable it permanently till I decide to enable it again.

This should be easy...but I can't find a method that does this.

Thx!

---

### Post by Lambert on 2007-10-28
I'm not knowledgeable on exactly how network manager works and if this will solve your problem but you can try this.

If you look in your file /etc/network/interfaces, you might see a line like this.

```

auto wlan0
iface wlan0 inet dhcp

```

remove the line auto wlan0 as this used to be the method debian based distros started a device at boot.

I don't have this and using network manager mine starts at boot so not sure if this is a solution. I need to understand networkmanager a little better.

---

