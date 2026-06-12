---
title: "VPN down since upgrade to 8.10"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by brutaltruth on 2008-11-07
Hi all,

I upgrade my 8.04 to 8.10, and since, my pptp VPN connection doesn't work anymore. I checked the config files, nothing was changed by the upgrade except some rights/ownership:

drwxr-xr-x 2 root root  4096 2008-11-06 22:27 ip-up.d
drwxr-s--- 2 root dip   4096 2008-11-06 22:27 peers


I get this in the logs:

==> /var/log/syslog <==
Nov  7 15:05:31 yogsothoth pptp[10890]: anon log[ctrlp_disp:pptp_ctrl.c:788]: Received Stop Control Connection Request.
Nov  7 15:05:31 yogsothoth pptp[10890]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 4 'Stop-Control-Connection-Reply' 
Nov  7 15:05:31 yogsothoth pptp[10890]: anon log[callmgr_main:pptp_callmgr.c:258]: Closing connection (shutdown)
Nov  7 15:05:31 yogsothoth pptp[10890]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request' 
Nov  7 15:05:31 yogsothoth pppd[10881]: Modem hangup
Nov  7 15:05:31 yogsothoth pppd[10881]: Connection terminated.
Nov  7 15:05:31 yogsothoth pptp[10890]: anon log[ctrlp_disp:pptp_ctrl.c:929]: Call disconnect notification received (call id 0)
Nov  7 15:05:31 yogsothoth pptp[10890]: anon log[ctrlp_error:pptp_ctrl.c:199]: Result code is 3 'Administrative Shutdown'. Error code is 0, Cause code is 0
Nov  7 15:05:31 yogsothoth pptp[10890]: anon log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Nov  7 15:05:31 yogsothoth pppd[10881]: Exit.

Did I miss something ?

Regards,
JC

---

### Post by brutaltruth on 2008-11-08
Hi all,

I've corrected the options.pptp file, require-mppe-128 was commented out by the upgrade, it seems...

Thanks for the no-help to the n00b ;)

---

