---
title: "Can't log into network-admin"
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by lightinggod on 2008-04-29
I was trying to log into network-admin to change dns servers, and get the following message

(network-admin:6441): Gtk-WARNING **: Unknown property: GtkComboBox.items


** (network-admin:6441): CRITICAL **: Unable to lookup session information for process '6441'

I'm using 8.04 and Firefox

I'm fairly new to Ubuntu and any help would be appreciated. 

Thanks,
Warren

---

### Post by GeoMX on 2008-04-30
Run it without using sudo/gksudo, just use network-admin. You'll find a new button named "Unlock", this is the "new security" feature in Hardy.

---

