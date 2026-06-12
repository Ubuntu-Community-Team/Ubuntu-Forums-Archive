---
title: "LAN/Ethernet doesn't work (Link detected: no)"
date: 2015-11-06
forum: Networking &amp; Wireless
---

### Post by Vijay_Mendiratta on 2015-11-06
Hi

My ethernet connection stopped working today.

My installation (& kernel): Linux VJ 3.2.0-93-generic #133-Ubuntu SMP Fri Oct 23 13:32:16 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
Ethernet driver: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)

This seems to have happened after I installed the following updates today:

Upgrade: libreoffice-help-en-gb:amd64 (3.5.7-0ubuntu8, 3.5.7-0ubuntu9), libreoffice-gnome:amd64 (3.5.7-0ubuntu8, 3.5.7-0ubuntu9), libreoffice-draw:amd64 (3.5.7-0ubuntu8, 3.5.7-0ubuntu9), libreoffice-help-en-us:amd64 (3.5.7-0ubuntu8, 3.5.7-0ubuntu9), libreoffice-style-tango:amd64 (3.5.7-0ubuntu8, 3.5.7-0ubuntu9), libreoffice-impress:amd64 (3.5.7-0ubuntu8, 3.5.7-0ubuntu9), fonts-opensymbol:amd64 (102.2+LibO3.5.7-0ubuntu8, 102.2+LibO3.5.7-0ubuntu9), libreoffice-math:amd64 (3.5.7-0ubuntu8, 3.5.7-0ubuntu9), libreoffice-gtk:amd64 (3.5.7-0ubuntu8, 3.5.7-0ubuntu9), libreoffice-common:amd64 (3.5.7-0ubuntu8, 3.5.7-0ubuntu9), uno-libs3:amd64 (3.5.7-0ubuntu8, 3.5.7-0ubuntu9), python-uno:amd64 (3.5.7-0ubuntu8, 3.5.7-0ubuntu9), libreoffice-style-human:amd64 (3.5.7-0ubuntu8, 3.5.7-0ubuntu9), ure:amd64 (3.5.7-0ubuntu8, 3.5.7-0ubuntu9), libreoffice-base-core:amd64 (3.5.7-0ubuntu8, 3.5.7-0ubuntu9), libreoffice-calc:amd64 (3.5.7-0ubuntu8, 3.5.7-0ubuntu9), libreoffice-emailmerge:amd64 (3.5.7-0ubuntu8, 3.5.7-0ubuntu9), libreoffice-l10n-en-gb:amd64 (3.5.7-0ubuntu8, 3.5.7-0ubuntu9), libreoffice-core:amd64 (3.5.7-0ubuntu8, 3.5.7-0ubuntu9), libreoffice-writer:amd64 (3.5.7-0ubuntu8, 3.5.7-0ubuntu9), libreoffice-l10n-en-za:amd64 (3.5.7-0ubuntu8, 3.5.7-0ubuntu9)

I've tried to google my way through but haven't been able to fix this issue.

Any help will be greatly appreciated.

This is my first post here so pardon me if I've broken any posting rules.

---

### Post by Vladlenin5000 on 2015-11-06
Hi and welcome.

The updates are unrelated. The most probable cause is hardware failure and one simple troubleshooting you should have done already is booting a live session.

---

### Post by Vijay_Mendiratta on 2015-11-06
Thanks for the response. The updates did look unrelated to me too but I wasn't sure.

Do you mean booting using a cd/dvd? I'm sorry I don't have one on me right now. Any other quick test I can run before I declare this as a hardware failure?

Thanks again.

---

### Post by Vladlenin5000 on 2015-11-06
Assuming nothing else has been changed - BIOS settings - the probabilities of it being software/OS related are close to none, because it happened suddenly, but there's always that odd, mind boggling, case.
The only way to test it is change that variable, hence the test in a live session. Yes, an installation or live media is required, either a CD/DVD or USB flash dongle.
Also try another cable. Those fail more often than we realize.

---

### Post by Vijay_Mendiratta on 2015-11-06
Thanks. Yup, no BIOS setting was changed. Tried another cable too - didn't work still. Will test with a live media and update the thread. Thanks for your help.

---

