---
title: "Trouble installing PCI wireless card"
date: 2007-09-27
forum: Networking &amp; Wireless
---

### Post by chimerical_brio on 2007-09-27
So to date I've been using Ubuntu Feisty with ndiswrapper so I could use a USB wireless adapter without native support. But I recently picked up a Linksys WMP55AG PCI card, supported by madwifi. So I plugged it in today, started Ubuntu, typed lspci and...it's not recognized. It's seen as some sort of ethernet controller that's an unknown device, and when I run ifconfig, I only have eth0 and lo. Any ideas at all? Would a reinstallation of Ubuntu be best? Thanks.

---

### Post by chimerical_brio on 2007-09-28
Hmm...interesting additional results. I booted into the LiveCD and ran lspci, and again, the device is still "unknown." This time, though, in addition to lo and eth0, there's also eth0:avah. Any ideas at all as to how I can get Ubuntu to recognize my device? Would switching the PCI slot work better?

---

### Post by chimerical_brio on 2007-09-28
..bump..

---

### Post by tgalati4 on 2007-09-28
Post the output of:

>lspci -vv

Post relevant portions of:

>dmesg | more

Do a google search on your card model: Linksys WMP55AG PCI and try to determine the actual chipset that is used.  Then search the forums for that chipset and you may get closer.

---

### Post by chimerical_brio on 2007-09-28
Well...my card is based on the Atheros 5212 chipset, which I googled around for before posting, and unfortunately, everyone else seemed to be able to at least get their card recognized as produced by Atheros, and have an ath0 network device. lspci -vv gives me:
```
Etherent controller: Unknown device 160c:0013 (rev 01)
Subsystem: Linksys Unknown device 0018
``` followed by some other stuff that doesn't seem any different form any of the other listed devices. Nothing in dmesg seemed relevant to this problem.

---

