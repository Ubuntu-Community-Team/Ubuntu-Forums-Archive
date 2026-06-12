---
title: "Intel 4965AGN not good enough anymore?"
date: 2008-02-17
forum: Networking &amp; Wireless
---

### Post by lgdahl on 2008-02-17
First of all; sorry for broken English - I'm Norwegian.

I have an Acer Aspire 5720ZG with an Intel 4965AGN mini PCI-e wireless adapter. It has been working like a charm for several months, but is now "acting up" - Ubuntu 7.10 don't seem to find any functional wireless adapter.

I'm not very good at reading logs, but in "daemon.log", I find this line:

NetworkManager: <WARN>  request_and_convert_scan_results(): card took too much time scanning.  Get a better one.

Why is suddenly my WIFI card not good enough for Ubuntu?

I tried to run the live CD, but that didn't work, either. So then I of course thought "hardware failure" - but I am now writing this in Windows from the same machine - connected through the wireless interface ...

I'm lost. And I don't like it here in Windows. Anybody got an idea to help me get the wifi card working? I'd be happy to post any further information and relevant logs, just let me know what is needed.

---

### Post by RaZer0r on 2008-02-17
have you tried installing your wireless device through ndiswrapper?
there are lots of howto's and guides that will help you though the instalation...
just google a bit for ndiswrapper ;)

---

### Post by lgdahl on 2008-02-17
No, I haven't tried NDISWrapper. Actually,  I ordered the PC *because of* the Intel NIC, since it is *(**supposed **to be?)* natively supported in Ubuntu 7.10.

And it wouldn't answer the big question: Why did it suddenly stop functioning, after several months?

---

