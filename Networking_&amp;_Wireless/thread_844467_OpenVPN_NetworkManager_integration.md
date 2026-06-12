---
title: "OpenVPN NetworkManager integration"
date: 2008-06-29
forum: Networking &amp; Wireless
---

### Post by insomniacity on 2008-06-29
I've got OpenVPN configured and working, and I noticed that the network manager applet has some built-in OpenVPN stuff.

However, it doesn't do all the options I'm using in my config file - I either need [FONT="Courier New"]pull[/FONT] or [FONT="Courier New"]redirect-gateway[/FONT]... is there any way I can achieve this, and still use the applet integration?

Thanks!

---

### Post by forezt on 2008-07-03
Here, you can benefit from my hours and hours of messing with OpenVPN:

Redirect-gateway seems just to be a server-side option, so as long as you have it set there you're fine.

And if it's  just DNS names you want to pull, then you're also fine. On my Network-manager client it automatically added the server to the nameserver list. You can check by going Manual configuration --> DNS and checking for your server's IP.

---

