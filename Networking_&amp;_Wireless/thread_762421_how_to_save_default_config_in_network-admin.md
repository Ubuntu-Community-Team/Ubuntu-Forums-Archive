---
title: "how to save default config in network-admin?"
date: 2008-04-22
forum: Networking &amp; Wireless
---

### Post by justin_acklin on 2008-04-22
Just installed 8.04RC on gateway p-6831fx.  Used network-admin to setup my wireless connection.  Initially set it up as WPA, didn't work, realized I am using WPA2, entered password and interface came up fine.

Now every time I restart, it has changed back to WPA, so it won't bring up the interface.  It keeps the SSID and password, it's just changed the password type that changes back.  If I change it to WPA2 it brings it up.  I have tried saving this as a "Location" and that works fine - I just don't want to have to go in and switch locations every time I start.  Is there a way to fix the default to use WPA2, or tell it to use my "Home" location as the default?
thanks...

---

### Post by Kylibar on 2008-11-20
i dont deal with wireless much, but look into the /etc/network/interfaces file? :) worth a shot, u can run scripts from it, so u might be able to "make the cpu remember"

---

### Post by Iowan on 2008-11-21
Not trying to be negative, but after 7 months, **justin_acklin** either found the answer or looked elsewhere. Since he hasn't posted since April 27, I doubt he'll notice your reply. Keep offering the help, though. :!:

---

