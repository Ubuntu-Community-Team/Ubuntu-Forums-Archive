---
title: "[SOLVED] HELP Juniper"
date: 2007-10-18
forum: Networking &amp; Wireless
---

### Post by Marinodimare on 2007-10-18
Hi,

My work uses Juniper to allow us to use the wireless network in-house, and after starting up firefox the Juniper package was installed and I was able to browse all I wanted. No problems there (I use my IBM laptop with (K)Ubuntu 6.06). That same evening, I hooked up my laptop on my home LAN line, and guess what: I can browse the network without any trouble, but I cannot get onto the internet (as you may guess, this message was written from my desktop pc). I removed the .juniper_networks folder from my home directory, but: no luck. Please help me, this is very annoying!

Marino

---

### Post by Dark Hornet on 2007-10-18
Hello...can you be more specific...when you say Juniper, are you talking about the Router company...Juniper Networks, or something else.  In addition, you may want to check you network settings on your  laptop at the house, as chances are they are different than at work...

---

### Post by Marinodimare on 2007-10-19
Hi,

first, it is the Juniper Networks ncscv client, the java application, that was installed on my laptop, and used for secure login.

Then, I did check all my network settings, and they were unchanged. This is not suprising as I use my ra0 interface at work for the wireless network, with automatic dhcp and dns, and my eth0 interface for the wired home network, with fixed dhcp, dns, gateway and subnet. Furthermore, the default interface is eth0, so whenever I plugin a network cable, I should be able to make a connection. So, the network settings of both interfaces have not interfered, this is not the problem (as indicated by the fact that there is no problem browsing the home network).

I hope I've clarified the situation enough like this?

M.


p.s. I just checked with my windows machine at work, and internet explorer indicates that the name of the programme is dsSetupApplet. Is this of ay help?

---

