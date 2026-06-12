---
title: "No Wi-Fi Adapter Found"
date: 2019-01-20
forum: Networking &amp; Wireless
---

### Post by SNaveenMathew on 2019-01-20
I installed Ubuntu recently. The only changes I did were:

1) Initially I used to start with acpi=off in grub because of nvidia driver issue. Now I removed this setting. Other changes: installed nvidia driver and blacklisted nouveau.
2) Upgraded packages.

I tried other solutions such as reinstalling bcmwl, but that did not solve the problem. Currently I'm using wired network, so the problem is localized to Wi-Fi.

---

### Post by wildmanne39 on 2019-01-20
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created.

---

### Post by SNaveenMathew on 2019-01-21
Hello,

The problem persists after sudo apt update and sudo apt dist-upgrade.

Pastebin link: [http://paste.ubuntu.com/p/TT7DF6YGPC/](http://paste.ubuntu.com/p/TT7DF6YGPC/)

---

### Post by jeremy31 on 2019-01-21
What model Lenovo?  For now do ```
echo "blacklist ideapad-laptop" | sudo tee /etc)modprobe.d/ideapad-laptop.conf
```
Reboot

---

### Post by SNaveenMathew on 2019-01-21
> **jeremy31 said:**
> What model Lenovo?  For now do ```
echo "blacklist ideapad-laptop" | sudo tee /etc/modprobe.d/ideapad-laptop.conf
```
Reboot

This worked! Thank you very much.

---

### Post by jeremy31 on 2019-01-21
What model Lenovo?  I do have a better fix

---

