---
title: "wireless Acess Point: Not-Associated sometime"
date: 2006-12-22
forum: Networking &amp; Wireless
---

### Post by tom_adams on 2006-12-22
Sometimes the wireless configuration boots properly and the Access-point shown by iwconfig correctly names my wireless network.  However, it now has says that the Access-point is "Not-Associated".

Maybe there is a command that will force the configuration to reload?

Any thoughts?

Thanks

---

### Post by n00b@linux on 2006-12-22
The command you're looking for is 'iwconfig'.   Use iwconfig to configure your wireless interfaces.  I suggest you read the man page on it to get the detail about what parameters you can pass to it but please note that the 'key' parameter is WEP only.  To use WPA you need to a bit more (see the thread in my sig).   To configure your nic permanently you need to change the /etc/network/interfaces configuration file.  Again, see the link in my sig for some examples.

---

### Post by tom_adams on 2006-12-22
Thanks for the input

The /etc/network/interfaces file is configured with the correct  wireless-essid and wireless-key values.    

When I get the not-associated info reported by iwconfig I have simply been rebooting and everything usually comes up correctly the next time around.

This is the second wireless thingy on this machine that  is unstable ... the other problem is that networking applet will no longer run ( it causes a bug report app to pop up instead).

---

