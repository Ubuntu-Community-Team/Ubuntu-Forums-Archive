---
title: "Ubuntu with Broadcom How?"
date: 2008-05-16
forum: Networking &amp; Wireless
---

### Post by robfcobb on 2008-05-16
I have a Presario C714NR which has only wireless.  I would love to use Ubuntu 8.04, but can't get the wireless to work(Broadcom).  I can only hook to the internet wirelessly.  Is there anyway I can download the required driver?

---

### Post by Ayuthia on 2008-05-16
> **robfcobb said:**
> I have a Presario C714NR which has only wireless.  I would love to use Ubuntu 8.04, but can't get the wireless to work(Broadcom).  I can only hook to the internet wirelessly.  Is there anyway I can download the required driver?

You can try this [link]("http://ubuntuforums.org/showthread.php?t=779754").  You will want to check your wireless card (lspci -nn in the Terminal) to determine if your card will work with the current b43/b43legacy modules.

---

