---
title: "intel 7260AC hard blocked on startup but not after suspend"
date: 2018-05-06
forum: Networking &amp; Wireless
---

### Post by rmbq on 2018-05-06
Hi all.
I've got a HP pavillion g6 and i changed my wifi card to a Intel 7260AC.
it's hard blocked on startup but it works fine after a suspend and a resume.
I noticed strage lines about ACPI in dmesg.

wifi script: [https://pastebin.com/CcvVV5Qa](https://pastebin.com/CcvVV5Qa)
dmesg on startup: [https://pastebin.com/x2eyBN9r](https://pastebin.com/x2eyBN9r)
dmesg after resume: [https://pastebin.com/xtdypqGx](https://pastebin.com/xtdypqGx)
lsmod on startup: [https://pastebin.com/AxHxY5Q4](https://pastebin.com/AxHxY5Q4)
lsmod after resume: [https://pastebin.com/2Bc6Rpci](https://pastebin.com/2Bc6Rpci)

i tried to blacklist hp_wmi module (from similar thread suggestion) but it didn't work.

EDIT: also tried to block hp_wireless and restore BIOS default

---

### Post by rmbq on 2018-05-06
Solved putting tape on pin 20 and 51 [https://communities.intel.com/thread/51030](https://communities.intel.com/thread/51030)

---

