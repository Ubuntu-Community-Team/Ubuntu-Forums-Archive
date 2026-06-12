---
title: "fresh install of 16.04 LTS - inexperienced user - wireless does not turn on"
date: 2017-12-13
forum: Networking &amp; Wireless
---

### Post by coolhube on 2017-12-13
Hello,
I have just installed 16.04 LTS on a VAIO with an Intel WIFI 5100 wireless adapter (miniPCI) installed.  I cannot turn on the wireless.  Ran wireless-info per the sticky note.  wireless-info.tar.gz attached.

Please help if possible.
Thanks!

---

### Post by chili555 on 2017-12-14
We see this in your results:> 2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yesHard blocked, in this context, means HARDware blocked. That is, there is a switch or key combination somewhere on that VIAO that is now set to turn off the wireless radio. Sometimes, it is called Airplane Mode.

Please find the switch and switch it. Then check from the terminal:```
rfkill list all
```

In some cases, the switch doesn't work to change the hard block and we'll need to try other steps.

---

### Post by coolhube on 2017-12-14
Solved!  Found the wireless switch...instant success.

---

