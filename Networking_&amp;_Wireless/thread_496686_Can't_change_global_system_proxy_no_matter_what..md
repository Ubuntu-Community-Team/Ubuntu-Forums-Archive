---
title: "Can't change global system proxy no matter what."
date: 2007-07-09
forum: Networking &amp; Wireless
---

### Post by sunksullen on 2007-07-09
I need to change my 7.04 system proxy settings...and am having issues.  I've tried changing $http_proxy by typing:

http_proxy='http://127.0.0.1:8080"

That works temporarily and for some programs...but then it changes back to the old settings...I've then tried to export the variable by using :

export http_proxy='http://127.0.0.1:8080" 

I also have tried using the program gnome-network-preferences which in the gnome menu is under "System-Preferences-Network Proxy....Again it changes the proxy successfully and works for some programs but whenever I try and run anything that uses the internet from the command line(such as lynx and curl)..it changes back to the old proxy setting...It also changes back when I use synaptic..

Any ideas?? I've been completely stumped. THANKS!

---

