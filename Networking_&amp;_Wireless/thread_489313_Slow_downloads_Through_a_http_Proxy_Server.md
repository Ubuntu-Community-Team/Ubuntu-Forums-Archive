---
title: "Slow downloads Through a http Proxy Server"
date: 2007-07-01
forum: Networking &amp; Wireless
---

### Post by ZuluboyRSA on 2007-07-01
Good day to All.

I have partially been successful in installing Ubuntu 7.04 as a Server as well as the desktop version on another PC . The desktop version was successfully setup with a dual boot (Vista and Ubuntu) using help from this forum. Thanks to those who posted the methods. A problem which is giving me grey hairs is as follows:-

Server was temporarily setup with an external public IP address connected directly to my ADSL router. The network gave me the full available bandwidth (up to 50K) when doing updates and package installs etc, using apt-get ....

My network, however needs to run through a HTTP Censornet (Debian based) Authenticating Server. As soon as I configure the Ubuntu Server or the workstation to work through the proxy, the bandwidth drops to a maximum of 3K and actually runs at an average of less than 2K. The Username used on Censornet Proxy Server for this PC has no bandwidth limits set. I have disbled ipV6 in Firefox as well as in aliases. What am I doing wrong ?? Please help.
__________________

---

### Post by ZuluboyRSA on 2007-07-01
I have solved my own problem. I tried all of the tips  that I could find on this forum, Disabling IPV6 and a whole bunch of other network setting tweaks etc.

I have now excluded this PC's IP from the proxy authentication on the Censornet Server and it's now flying. SO... the problem lies with Censornet all along.

---

