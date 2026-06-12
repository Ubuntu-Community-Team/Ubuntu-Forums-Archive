---
title: "How do I startup with Networking/Wi-Fi Disabled by default?"
date: 2013-10-13
forum: Networking &amp; Wireless
---

### Post by Line-X on 2013-10-13
I don't like to have services running if they're unnecessary, since they take up cycles, battery life and can even be security risks. With that in mind, I'd like to have networking and Bluetooth services disabled every time I startup the machine. I know I can disable them via the xfce panel, and that it will remain disabled upon the next startup, but I'd like for it to default to being disabled upon each and every startup. I'd like to easily enable it via the panel when it's needed, but start up disabled. Is there an easy way to do this (or at all)? Also, I welcome suggestions for any other unnecessary services that be disabled.

---

### Post by TheFu on 2013-10-13
Control of any daemons - things that are automatically started - happens with the location of files/settings in the /etc/rc{N}.d/ directories.  **update-rc.d is** the program - **man update-rc.d** to learn more.

I have ZERO idea if the GUI will be able to enable any of these disabled services later or not. I'm a CLI person. However, using the update-rc.d program again will let you enable/disable as desired for anyone with sudo permissions.

I'm trying to "teach you to fish", not hand you "a fish" for today only.

---

