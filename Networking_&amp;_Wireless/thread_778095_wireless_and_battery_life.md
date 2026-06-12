---
title: "wireless and battery life"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by timebomb on 2008-05-01
Quick question: does un-clicking "Enable Wireless" in the Network Manager applet turn off the wireless radio and thus extend the battery time on my notebook?

Running Hardy on Dell Inspiron 600m.

Thanks in advance.

---

### Post by timebomb on 2008-05-02
Anyone? I suppose another question is assuming the applet will not do it, how to I ensure the wireless is off? Would love to boot Ubuntu on airplanes, etc..

---

### Post by timebomb on 2008-05-09
Bump - does no one know? Happy to apologize if I missed an obvious place where this info is recorded.

---

### Post by prshah on 2008-05-09
> **timebomb said:**
> Quick question: does un-clicking "Enable Wireless" in the Network Manager applet turn off the wireless radio and thus extend the battery time on my notebook?


Don't know about the "un-clicking" (unchecking) but you can use ```
sudo iwconfig eth1 txpower off
``` in a terminal to turn off wireless manually. Replace "off" with "auto" or "fixed" to re-enable wireless.

Obviously, replace "eth1" with your actual wireless interface.

---

