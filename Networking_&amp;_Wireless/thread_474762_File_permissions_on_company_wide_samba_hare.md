---
title: "File permissions on company wide samba hare"
date: 2007-06-15
forum: Networking &amp; Wireless
---

### Post by stashj on 2007-06-15
I recently moved a network share onto an Ubuntu/Samba box that I joined to my domain and enabled using [this]("http://ubuntuforums.org/showthread.php?t=5409&highlight=samba+domain+users") howto which worked excellently (thanks).

My only problem is that when a domain user saves a file the owner and group are both set to their username (as expected) but the permissions are set so that other users can only read the file. This makes the file unusable to anyone else. As a short-term fix I put a job in the cron that chmod's everything in the share to 777 every 5 minutes but I'm hoping for something a little more elegant which has eluded me so far.

Any ideas anyone?

Thanks in advance

---

