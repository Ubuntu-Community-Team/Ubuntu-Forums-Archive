---
title: "How to diable IPv6?"
date: 2008-06-13
forum: Networking &amp; Wireless
---

### Post by oleksus on 2008-06-13
I see it active in ifconfig, but my provider dont support it, and I might have problems connecting because of that.

Where do I disable IPv6?

---

### Post by Lostincyberspace on 2008-06-13
you can disable it in firefox by using fasterfox that is where the biggest problem will come in.

---

### Post by oleksus on 2008-06-14
I don't have fastfox.

Can I maybe disable them somewhere in the config files?

---

### Post by bigken on 2008-06-14
in the address bar type **about:config **then ipv6 in the filter  double click to change value

---

### Post by The Cog on 2008-06-14
Edit the file **/etc/modprobe.d/blacklist** and add the line:
**blacklist ipv6**
then reboot. This removes IPv6 from the kernel entirely, not just the browser.

You need to use sudo to edit this file as it's outside your home directory:
**gksudo gedit /etc/modprobe.d/blacklist**

---

### Post by oleksus on 2008-06-15
Thanks a lot! :guitar:

---

