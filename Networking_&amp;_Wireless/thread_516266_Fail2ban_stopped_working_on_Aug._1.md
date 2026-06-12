---
title: "Fail2ban stopped working on Aug. 1 ???"
date: 2007-08-03
forum: Networking &amp; Wireless
---

### Post by steve457 on 2007-08-03
Ok, this is really strange.  I've been running fail2ban and its been blocking attempts to my ftp server (vsftp) great.. up until yesterday August 1st.  I just happened to check my logs, and I noticed that starting on August 1st, there are many failed entries that are no longer being blocked.  Nothing has changed with my system, so I am not sure what happened.

/etc/init.d/fail2ban status
shows that it is running.

Any ideas on what is causing fail2ban to no longer work?

---

### Post by steve457 on 2007-08-03
I got it working again, but am not sure why I needed to make the change.  For some reason fail2ban was no longer reading my /var/log/vsftpd.log correctly, although I haven't changed that program or logfile location at all.  I changed the /etc/fail2ban/jail.local entry for vsftp to look at /var/log/auth.log instead and now it seems to be banning succesfully. 

I'm confused as to why fail2ban suddenly stopped working yesterday though, and why this change was necessary.

---

