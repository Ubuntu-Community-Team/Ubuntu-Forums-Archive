---
title: "Cards works but no connection"
date: 2007-04-04
forum: Networking &amp; Wireless
---

### Post by skotreed on 2007-04-04
So i've just installed feisty beta and my wireless card and it's working but i have no connection.  I can run the restart for networking "sudo /etc/init.d/networking restart" and it works fine.  The problem i'm having is that i have to run the command on every restart.  Is there any fix for this problem, or is there anyone who can explain getting the commaond to run automatically.

Thanks for the help>>>

---

### Post by chili555 on 2007-04-04
Sometimes, amending */etc/network/interfaces* to add auto <interface> works, something like this:```
**auto wlan0**
iface wlan0 inet dhcp
```Please try it, reboot and let us know.

---

### Post by skotreed on 2007-04-04
The file already contains that information, and at restart had the same issue. Any other thoughts

---

### Post by chili555 on 2007-04-04
Try System -> Administration -> Network; put an X next to your wireless interface. Close and let us know.

I have been struggling with Feisty vs. NetworkManager vs. chili myself!

---

### Post by skotreed on 2007-04-04
That didn't seem to make a difference, other than every time I de-select ra1 i end up having to run the networking restart codes in terminal. If I had to guess, it seem like every time that ra1 has to reconnect it's not connecting to my router (which is also working correctly).

---

