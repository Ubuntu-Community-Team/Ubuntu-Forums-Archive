---
title: "usbserial fails to load at startup after kernel update"
date: 2010-07-28
forum: New to Ubuntu
---

### Post by gandaran on 2010-07-28
I'm having this problem after the latest kernel update, I have a mobile broadband dongle permanently attached to the computer, it used to connect at start-up but now its not detected by network manager and usbserial module isn't loaded so I have to remove the dongle and insert it again, then it works okay, I wonder why!
the first file is the modules loaded at start-up and the second is after I reinsert the dongle.
any help welcome.

---

### Post by davidmohammed on 2010-07-28
any error messages concerning your device in your kernel log before and/or after the reboot? (administration - Log file viewer)

---

### Post by gandaran on 2010-07-28
> **davidmohammed said:**
> any error messages concerning your device in your kernel log before and/or after the reboot? (administration - Log file viewer)
well I cant find any error there but check the full kernel log for today

---

### Post by davidmohammed on 2010-07-28
... I don't see any obvious errors - I also couldn't see any evidence of plugging in / unplugging / re-plugging in again...

I presume, if you boot from your previous grub kernel everything is working normally again?  If so, suggest file a bug in launchpad, and in the interim, change your default value in /etc/default/grub to boot with your older kernel that works.

---

### Post by gandaran on 2010-07-28
> **davidmohammed said:**
> ... I don't see any obvious errors - I also couldn't see any evidence of plugging in / unplugging / re-plugging in again...

I presume, if you boot from your previous grub kernel everything is working normally again?  If so, suggest file a bug in launchpad, and in the interim, change your default value in /etc/default/grub to boot with your older kernel that works.
yes no errors, looks like the computer/kernel or network manager is completely ignoring the dongle during boot up.
I have removed all old kernels and I don't want to reinstall one, if I cant fix it I will file a launchpad bug later.
thanks

---

