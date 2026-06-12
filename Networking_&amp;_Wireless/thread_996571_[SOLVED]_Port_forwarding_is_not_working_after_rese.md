---
title: "[SOLVED] Port forwarding is not working after reset: WRT54G"
date: 2008-11-29
forum: Networking &amp; Wireless
---

### Post by RavUn on 2008-11-29
I recently flashed my router to DD-WRT but couldn't get it to work well with xbox live so I went back to the linksys firmware.  I've set up the port forwarding the same as it was before but it's not working.  Everything else seems to be the same (pretty sure) but the port forwarding doesn't work.

I'm trying to forward port 80 for apache to my laptop and port 7878 for gnump3d to my desktop.  Neither of them work, and I made sure the checkboxes are checked for "Enable".  Anything else I can check?  Both computers were working fine before I reset the router and so I know it's a router issue.  My WAN (public) IP did change after resetting, if that matters... but typing that takes me to my router and I already changed it in dyndns.

---

### Post by superprash2003 on 2008-11-29
well to access your apache webserver from its dyndns id , you would need to access it from outside your network, not in your house.. You can check if port forwarding is done by using this online port scanner [http://www.t1shopper.com/tools/port-scanner/](http://www.t1shopper.com/tools/port-scanner/)

---

### Post by kevdog on 2008-11-29
Although this is a surrogate, I would scan your external IP address (ie your router) with shields up to see if port 80 appears open from the outside.

---

### Post by RavUn on 2008-11-29
I had everything set the same as before.  I ended up resetting the modem and router and it works now.  I don't know why that fixes it but it seems to fix several issues.  

I reset the router and it changed my LAN IP so the port forwarding still didn't work (since it was different, yet again).  I corrected it and it still didn't work so I had to reset the router again.  For some reason those kinds of changes don't take effect until I completely reset the router (hold reset for 30 seconds which basically restores to factory default).

---

