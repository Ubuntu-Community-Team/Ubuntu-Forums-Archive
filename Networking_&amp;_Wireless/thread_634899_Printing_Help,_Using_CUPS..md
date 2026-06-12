---
title: "Printing Help, Using CUPS."
date: 2007-12-08
forum: Networking &amp; Wireless
---

### Post by c0reyf on 2007-12-08
I am trying to print to my Ubuntu desktop with my wifes XP laptop. I use the URL to find the printer and it does so. It shows up when I goto the localhost:631 under jobs on my Ubuntu box but never prints. I can print from my Ubuntu laptop and locally on the ubuntu desktop but not from the XP laptop. Any ideas.
.

---

### Post by AndyC_772 on 2007-12-08
I've just been through exactly the same thing with a network printer, and ended up finding a workaround and reporting a bug.

What fixed it in my case, was to replace the name of my printer server in the URL with its IP address. See [https://bugs.launchpad.net/ubuntu/+source/system-config-printer/+bug/174874](https://bugs.launchpad.net/ubuntu/+source/system-config-printer/+bug/174874)

If yours is a local printer, maybe changing 'localhost' to '127.0.0.1' on the Ubuntu box will fix it?

(edit: just noticed, your Ubuntu box is the print server and not the client - maybe worth a go though?)

---

### Post by c0reyf on 2007-12-09
Print jobs are making it  in the CUPS queue and shows as completed on the server but never prints?

---

