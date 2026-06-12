---
title: "samba share won't show up -- Feisty"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by dberg on 2007-04-25
I have setup Samba and everything was working great, then after a reboot...

When I go to Places --> Network --> dberg

there used to be a folder called 'MyFiles' which was my shared location, but now after rebooting it no longer shows up. Nothing else has been changed. How can I troubleshoot this?

Thanks.

---

### Post by dberg on 2007-04-26
bump

---

### Post by podfish on 2007-04-26
Try this:

sudo /etc/init.d/samba restart

or reboot, or just wait a few minutes.  It will cause samba to restart and reload the config file with the new share in it.

---

### Post by dberg on 2007-04-26
> **podfish said:**
> Try this:

sudo /etc/init.d/samba restart

or reboot, or just wait a few minutes.  It will cause samba to restart and reload the config file with the new share in it.

I've done all of these options several times and it never solves the problem.  It showed up after I had initially worked fine. Then after the restart it quit showing up.

---

### Post by dberg on 2007-04-27
bump

---

### Post by jdunn on 2007-04-29
Try the advice in this error report.  Its worked for alot of people.  Of course, it didn't work for me

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/95460](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/95460)

---

### Post by dberg on 2007-05-02
> **jdunn said:**
> Try the advice in this error report.  Its worked for alot of people.  Of course, it didn't work for me

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/95460](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/95460)

For me, my smb.conf did not have a "msdfs proxy" line. So I guess is other words this didn't work for me either.

---

