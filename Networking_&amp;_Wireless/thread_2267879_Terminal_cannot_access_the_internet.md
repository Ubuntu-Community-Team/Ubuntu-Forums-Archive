---
title: "Terminal cannot access the internet"
date: 2015-03-04
forum: Networking &amp; Wireless
---

### Post by director84 on 2015-03-04
I have a somewhat weird problem:

The WIFi is connected, I can surf the internet without any problems, e.g. firefox has full internet access.
But in a terminal (MATE Terminal 1.8.1), using apt-key, I cannot download keys from any keyserver I tried, and I have tried different keys, too. When I tried to ping the servers entering the URL (e.g. subkeys.pgp.net) the IP was resolved and shown correctly (so the DNS seems to work), but there is no response from the server. The same goes for websites which work fine in my browser. However when I ping a local IP in my home network it works. Asseemingly only WAN cannot be accessed from the terminal.

My distribution is UberStudent 4.1 Epicurus (based on Ubuntu 14.04 with an XFCE Desktop).

Any idea what could cause this, and how I can fix it?

---

### Post by ajgreeny on 2015-03-04
Does wget work downloading a file from somewhere?

---

### Post by steeldriver on 2015-03-04
Is your brower perhaps using a proxy that is not set system wide?

---

### Post by ewenss on 2015-03-05
I'm Stephen Ewen, UberStudent's lead developer.

apt-key is working just fine on my end in 4.1 inside MATE terminal.

[ATTACH=CONFIG]260459[/ATTACH]

Note that apt-key will not add the key if it already exists on your system.

---

