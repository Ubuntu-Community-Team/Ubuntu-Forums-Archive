---
title: "Calling all wpasupplicant experts"
date: 2006-11-03
forum: Networking &amp; Wireless
---

### Post by cookfromfrozen on 2006-11-03
Hi

I have WPA working just fine with wpasupplicant.  However, I've noticed something strange.

If I ifdown the interface, stop and start it through the GUI or run /etc/init.d/networking restart, the interface comes back up and wpasupplicant starts, but it keeps disconnecting (no, there's nothing wrong with the wireless since it works fine unless you mess with it).

At first I thought the wpasupplicant process was terminating, but it is.  I also tried deleting the /var/run/wpa_supplicant/ath0 lock file, but it still won't reconnect after an ifdown.

Here is how I start and kill wpasupplicant in /etc/network/interfaces:

```

pre-up wpasupplicant -Bw -Dmadwifi -iath0 -c/etc/wpa_supplicant.conf
post-down kilall -q wpa_supplicant

```

Is there any reason for this?

---

### Post by cookfromfrozen on 2006-11-04
bump

---

### Post by cookfromfrozen on 2006-11-06
No one?  wpasupplicant works the first time, but subsequent attempts to restart it or stop and start it fail.  Come on, there has to be a simple-ish explanation for this?

Is there a process being left over or something?

---

