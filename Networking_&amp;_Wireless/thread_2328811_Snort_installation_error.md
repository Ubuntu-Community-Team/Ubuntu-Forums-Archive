---
title: "Snort installation error"
date: 2016-06-24
forum: Networking &amp; Wireless
---

### Post by jake-swensen on 2016-06-24
During Snort installation on a new Ubuntu 16.04 virtual server, the installer asks "Address range for local network?" with default of 192.168.0.0/16, which I accept.

After installing several packages, the following error is displayed.  The default IP address may need to be changed to something else but I'm not sure.  I tried pinging the server's broadcast IP address but that failed.  Can someone help me with troubleshooting this Snort installation error?

Setting up libdaq2 (2.0.4-3) ...
Setting up snort (2.9.7.0-5) ...
Job for snort.service failed because the control process exited with error code. See "systemctl status snort.service" and "journalctl -xe" for details.
invoke-rc.d: initscript snort, action "start" failed.
dpkg: error processing package snort (--configure):
 subprocess installed post-installation script returned error exit status 1

---

