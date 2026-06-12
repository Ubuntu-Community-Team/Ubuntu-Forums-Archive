---
title: "[SOLVED] Intrepid PPTP VPN fails on all but tiny data request"
date: 2008-11-11
forum: Networking &amp; Wireless
---

### Post by Jayock on 2008-11-11
Howdy.  I recently upgraded to Intreipd, and have been struggling to get my PPTP VPN running that worked fine on Hardy.  Using the PPTP plugin on NetworkManager.

I have found numerous threads that I have used, and finally got my connection working, but only on small datasets (Several Bytes).  I can use SSH, and see very small webpages (like the default "It Works" apache page).  But anything larger, including google.com will timeout.  Even running a MySQL show slave status; or cat(ing) a file from command line in SSH will show a few lines, then stop sending anymore information.  I find two possibly relevant entries in syslogs.  The first happens on connect to the VPN.

> 
Nov 11 14:26:55 boulder nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1. 


Ive narrowed it down to this line in the file 01ifupdown: 

> 
    *)
	echo "$0: called with unknown action \`$2'" 1>&2
	exit 1
	;;


and, more probably this message which occurs when it is dropping packets on the larger datasets:

> 
Nov 11 14:29:07 boulder pptp[17906]: nm-pptp-service-17883 log[decaps_gre:pptp_gre.c:414]: buffering packet 122 (expecting 121, lost or reordered)
Nov 11 14:29:07 boulder pptp[17906]: nm-pptp-service-17883 log[decaps_gre:pptp_gre.c:414]: buffering packet 123 (expecting 121, lost or reordered)
Nov 11 14:29:15 boulder pptp[17906]: nm-pptp-service-17883 log[decaps_gre:pptp_gre.c:414]: buffering packet 129 (expecting 128, lost or reordered)
Nov 11 14:29:18 boulder pptp[17906]: nm-pptp-service-17883 log[decaps_gre:pptp_gre.c:414]: buffering packet 132 (expecting 130, lost or reordered)
Nov 11 14:29:18 boulder pptp[17906]: nm-pptp-service-17883 log[decaps_gre:pptp_gre.c:414]: buffering packet 133 (expecting 130, lost or reordered)


Any ideas where to start?

---

### Post by john_navarro on 2008-11-11
The issue is the new Network Manager 0.7 setting the MTU too high by default. And there is no way to set it within the settings GUI. There are bug reports about this already. Anyhow, the fix is easy but must be done each time you connect via PPTP.

1) Establish your PPTP tunnel.
2) Then do a: sudo ifconfig ppp0 mtu 1416

you may have to change ppp0 to whatever name you need. Anyhow, this should fix it for you.

John


PS. The errors you're seeing are due to packets being dropped/lost. The stack is attempting to recover and reorder to packs to no avail.

---

### Post by Jayock on 2008-11-12
Indeed that did fix the issue.  Wouldn't have thought that MTU from 1500 to 1416 would make such a big difference.  Any elegant way to script this action, or modify with config files or gconf to get this automated on connect?

---

### Post by zayoo on 2008-11-12
> **Jayock said:**
> Any elegant way to script this action, or modify with config files or gconf to get this automated on connect?

In directory /etc/ppp/ip-up.d create script and write this two line of code
Allow executing this new script as program!!!

```

#!/bin/sh
ifconfig ppp0 mtu 1416

```


I use vpn connection for 10 months. And I have this dropping packets for long time. My MTU is set to 1460. This is maximum for me. When I lower this number their are same problem with dropping packets. I don't now where is problem in my settings.

---

### Post by Jayock on 2008-11-13
I knew there was somewhere I could put such a script, thanks for the location.

---

### Post by theNthDoctor on 2010-08-22
What's amazing to me is that it's been 2 years since this problem was solved, and yet it's still happening (in Fedora).  I've been struggling with random periods where my quad core is spending most of its CPU cycles adding "lost or reordered" messages to /var/log/messages ... and it took hours to find a solution.  The very second I followed your advice, I saw instant results.

I'm switching from Fedora to Ubuntu ASAP, I'm so sick of terribad bugs from ancient history showing up in my supposedly-modern OS.

Anyway, thanks zayoo!

---

