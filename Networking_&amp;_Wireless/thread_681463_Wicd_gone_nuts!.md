---
title: "Wicd gone nuts!"
date: 2008-01-29
forum: Networking &amp; Wireless
---

### Post by Jamson on 2008-01-29
Hey,

I have a copy of Wicd installed on my Ubuntu 7.04 installation, and got rid of network manager since they both won't work together according to what the .deb said.

Now, i am trying to setup my wireless network adapter (wg111v2) and i've gotten it to the point where the blue light works now. :O Yay!

_I need my wireless adapter to connect to the internet._

However, Wicd doesn't want to co-operate anymore and it is defaulting to incorrect settings (a simple typo!). I change it, it still uses it. I am using WEP encryption and it thinks i need WPA... when i don't. I use DHCP, and it just uses incorrect settings.

I've tried uninstalling and reinstalling it, and it still uses the old settings.

Help me!

---

### Post by vikrant82 on 2008-01-29
Config files most probably are at /opt/wicd/data.

Try deleting that directory and run wicd again.

---

### Post by erfahren on 2008-01-29
make sure your /etc/network/interfaces file only has what's below (other commented out lines are ok).
```

# The loopback network interface
auto lo
iface lo inet loopback

```

---

### Post by Jamson on 2008-01-29
Going to the beta one worked fine, but i still couldn't get my device to work in it so i gave up. All the tutorials in the forum didn't work, going to Mandriva 2008 didn't work either.

Ah well, back to Windows Vista. :(

---

### Post by imdano on 2008-01-29
> **vikrant82 said:**
> Config files most probably are at /opt/wicd/data.

Try deleting that directory and run wicd again.In case anyone with a similar problem sees this post, you don't want to delete this whole directory!  Just delete the .conf files (wireless-settings, wired-settings, manager-settings), otherwise wicd won't work anymore.

---

