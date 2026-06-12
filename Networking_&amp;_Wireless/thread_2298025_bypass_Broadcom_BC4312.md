---
title: "bypass Broadcom BC4312"
date: 2015-10-08
forum: Networking &amp; Wireless
---

### Post by s9032g@comcast.net on 2015-10-08
Although I am not using my Broadcom card to do anything at all it always pops up briefly during the boot process as requiring attention. Can I stop this boot referencing perhaps by blacklisting the device? If so, then how do I do that?

---

### Post by tgalati4 on 2015-10-08
Perhaps you can turn it off in BIOS.  Otherwise put the following in /etc/modprobe.d/blacklist.conf:

```
blacklist b43
```

Right after the following stanza:

> # replaced by b43 and ssb.
blacklist bcm43xx


Reboot.

---

### Post by s9032g@comcast.net on 2015-10-08
I would like to try that. How do I reach  /etc/modprobe.d/blacklist.conf:

Thanks

---

### Post by tgalati4 on 2015-10-08
Open a terminal, perhaps Control-Alt-T.

```
sudo nano -B /etc/modprobe.d/blacklist.conf
```

Make your changes, Control-o (return), Control-x

Reboot.

---

### Post by s9032g@comcast.net on 2015-10-09
tgalati4

Thanks for your patience and good advice. I now get a cleaner, faster, boot without reference to my unused Broadcom card.

Kudos

---

### Post by tgalati4 on 2015-10-09
Everything is fixable in Linux, it just takes patience.

---

