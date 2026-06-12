---
title: "deb file cleanup"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by cve009 on 2011-02-28
I am curious if it is standard practice to remove the *.deb files after an installation.
I have a few .deb files in my home, and many in /var/cache/apt/archives.
I understand they are for installing packages.  I don't know if there is any use for them after the installation is complete.  I assume the "synaptic Package Manager" would still know about the packages without the .deb files.  If I wanted to install the package again, I would get the latest, new installation files.

So,
1. Can *.deb files be safely removed?
2. If there is a reason to keep them, does it make sense to put them all in /var/cache/apt/archives?
3. Am I the only one that takes housekeeping to such an extent?  ;-)

Thanks from the newbee.
Running on Ubuntu 10.10.

---

### Post by zenwalker on 2011-02-28
It comes to helpful if your installation is corrupted and needs to be re-installed. Then you dont have to download again. It can use the cache. Also to check the versions installed and needs updation or not stuffs.

---

### Post by Blutkoete on 2011-02-28
By the way: The /var/cache/apt/archives/ folder is cleaned on a regular basis by a cron job (a job that runs [insert time span here, e.g. every day]).

You'll find a cron labeled *apt* in the folder */etc/cron.daily* (meaning it's run every day) which you can configure via the (plain text, no GUI) configuration file in */etc/apt/apt.conf.d/02periodic*.

You can configure it to delete old packages earlier, **but don't change anything if you don't know what you are doing**. Read through APTs documentation first as you'll be messing around with the configuration of a standard system maintenance script.

Best regards,

Blutkoete

---

### Post by cve009 on 2011-02-28
Thank you for the experienced advice.  I will move the .deb files from my home to the standard /var/cache/apt/archives and let crontab eventually remove them.

And I appreciate the intro to crontab.

---

