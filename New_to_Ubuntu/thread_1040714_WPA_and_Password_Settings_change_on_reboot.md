---
title: "WPA and Password Settings change on reboot"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by BlakeM on 2009-01-15
I have a pretty basic/stupid problem that I've been unable to solve since day one. Sorry if this is a really dumb question.

I'm trying to set up a static IP in Ubuntu Hardy. I can set up the static IP ok, but every time I reboot, my internet connection is down. To get it working again, I have to re-input my WPA and password settings into nm-applet. After re-applying these settings the internet is ok again.

I've tried manually editing the /etc/network/interfaces file to no avail.

Is it possible that the Keyring program in Ubuntu keeps interfering with my settings? I've tried deleting the Wireless passphrase entry to no avail.

Any ideas would be greatly appreciated. Thanks for your time and effort.

---

### Post by zvacet on 2009-01-16
Under sysrem>admin>network did you add your nameservers?After that try

```
pppoeconf
```

---

### Post by BlakeM on 2009-01-18
> **zvacet said:**
> Under sysrem>admin>network did you add your nameservers?After that try

```
pppoeconf
```

Thanks for your reply. I've given up on setting the static IP in Ubuntu. I just got my router to assign reserve an IP for it.

---

