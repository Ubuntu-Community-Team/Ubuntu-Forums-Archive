---
title: "uml-utilities vs bridge-utils"
date: 2008-11-21
forum: Networking &amp; Wireless
---

### Post by anystupidname on 2008-11-21
Hello. Could somebody please help me comprehend the differences, pros, and cons between bridging interfaces using uml-utilities vs bridge-utils?
Thanks!:)

---

### Post by anystupidname on 2009-04-27
anybody?!?

---

### Post by anystupidname on 2009-05-23
bump

---

### Post by bab1 on 2009-05-23
> **anystupidname said:**
> Hello. Could somebody please help me comprehend the differences, pros, and cons between bridging interfaces using uml-utilities vs bridge-utils?
Thanks!:)

See _[here]("http://linux.about.com/cs/linux101/g/uml-utilities.htm")_ for uml-utities definition.  These are utilities for **user space Linux** kernels.

See _[here]("http://linux.about.com/cs/linux101/g/bridgeutils.htm")_ for bridge-util definition.  These are utilities for **Ethernet** bridging the Linux kernel.

These are for totally different things.  If you have a VM that needs to network connectivity use the bridge-util.

---

### Post by anystupidname on 2009-05-26
Thanks!

---

