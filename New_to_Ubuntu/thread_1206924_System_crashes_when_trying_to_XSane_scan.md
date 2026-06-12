---
title: "System crashes when trying to XSane scan"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by haydemon on 2009-07-07
I've recently acquired an HP Scanjet 5300C scanner that I've connected to my box via USB, but even though XSane recognizes it, whenever I try to scan, the system crashes and reboots. How can I fix this problem?

I am running Ubuntu 8.04 Hardy Heron.

---

### Post by Sef on 2009-07-07
Applications > Accessories > Terminal

then type in ```
xsane
``` Post any error messages that you get here.

---

### Post by haydemon on 2009-07-08
No code returns. It tries to scan devices, but just hangs & turns gray. I tried uninstalling and reinstalling, but no dice.

---

### Post by carml on 2009-07-08
Maybe here is the solution to your problem [HTML]http://www.sane-project.org/man/sane-avision.5.html[/HTML] but it's possibly old .

---

### Post by haydemon on 2009-07-08
Thanks. Looked at the info, informative, but still doesn't solve my problem. Now when I open SDane, it doesn't detect the device, even though it's plugged in and on.

---

### Post by Untitled_No4 on 2009-08-17
I've just had the same problem with Kubuntu 9.04 -- Xsane finds the scanner, opens and then the whole thing freezes and I need to reboot.

Previously (on 9.04) this worked well for me, but I've recently installed the 64bit version and it's stopped working. I don't know if it's related but it's the only thing I can think of.

My solution was to remove xsane and xsane-common and then install skanlite which is a KDE4 scanning application based on sane and I can scan again.

For non-KDE4 users there is a list of other frontends to sane at here: [http://www.sane-project.org/sane-frontends.html](http://www.sane-project.org/sane-frontends.html)

---

