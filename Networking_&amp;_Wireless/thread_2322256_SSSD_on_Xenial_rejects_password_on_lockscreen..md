---
title: "SSSD on Xenial rejects password on lockscreen."
date: 2016-04-27
forum: Networking &amp; Wireless
---

### Post by ksmigrod2 on 2016-04-27
Symptoms:
SSSD configured to login to ActiveDirectory on Trusty and upgraded through Utopic, Vivid and Wily to Xenial.
After upgrade suddenly my password was rejected on lockscreen. I was able to get back to my session via "switch user" and choosing my user.

There was an entry in sssd_DOMAIN_NAME.log file:
```
(Wed Apr 27 08:12:05 2016) [sssd[be[DOMAIN_NAME]]] [ad_gpo_access_done] (0x0040): GPO-based access control failed.
```

I've crancked up logging and got the following messages:
```
(Wed Apr 27 09:50:45 2016) [sssd[be[DOMAIN_NAME]]] [ad_gpo_access_send] (0x0400): using default right
(Wed Apr 27 09:50:45 2016) [sssd[be[DOMAIN_NAME]]] [ad_gpo_access_send] (0x0400): service unity maps to Denied
(Wed Apr 27 09:50:45 2016) [sssd[be[DOMAIN_NAME]]] [ad_gpo_access_done] (0x0040): GPO-based access control failed.
```

I've added the following line to  [FONT=courier new]/etc/sssd/sssd.conf[/FONT] to [domain/DOMAIN_NAME] section:
```
ad_gpo_map_interactive = +unity
```

after sssd restart:
```
sudo systemctl restart sssd
```

My password was accepted in lockscreen.

Please comment if my workaround has know adverse security consequences.

---

