---
title: "Network Sharing - but not MS sites?"
date: 2008-10-04
forum: Networking &amp; Wireless
---

### Post by Prism on 2008-10-04
Hi there,

I have two computers. The first one is running the stable version of Ubuntu. The second one is running WinXP.

The Ubuntu machine is connected to the Internet via ADSL. I'm using a cross network cable to share the internet access to my Win machine as well. It works fine most of the time, but I have a strange problem with microsoft sites and services: I cannot surf to MS sites (like [www.microsoft.com](www.microsoft.com) or Windows Update site) or login to MS services (like Windows Live Messenger) from the windows machine. However, they are reachable from the Ubuntu machine.

This problem solves itself when I reset my Internet connection from the Ubuntu machine, by typing [FONT="Courier New"]sudo poff -a[/FONT] and [FONT="Courier New"]pon dsl-provider[/FONT].

The windows machine IP is 168.192.0.2, and the DNS server is defined to be my provider's DNS server address.

What is the problem and how can I fix it without resetting the connection every now and then?

Thanks!

---

### Post by Prism on 2008-10-05
Bump! :)

---

