---
title: "Upgrade to 18.04 Caused Qualcomm Atheros AR9285 Wi-Fi to Cease Working"
date: 2019-02-17
forum: Networking &amp; Wireless
---

### Post by billosaur on 2019-02-17
Upgraded my machine from 16.04 to 18.04. Worked fine for three days. Now, my Wi-Fi will no longer connect. I have tried several things I found on-line regarding my Qualcomm Atheros AR9285 Newtwork Adapter, but to no avail. Networking is not my specialty, so any assistance would be appreciated.

My machine is an HP G60 laptop.

wireless-info output: [http://paste.ubuntu.com/p/rCqJ5sZs4H/](http://paste.ubuntu.com/p/rCqJ5sZs4H/)

---

### Post by solisas on 2019-02-18
I have an Advanced-N 6205 with iwlwifi, so not the same. My wifi ceased  working after upgrading to the *.45 kernel. After going back to   4.15.0-44 it is fine again. Perhaps give it a shot.

---

### Post by billosaur on 2019-02-18
Thanks for the tip. Unfortunately, a rollback simply caused my Wi-Fi to disappear altogether. From what I've seen, this is a common problem with no good unitary solution.

---

