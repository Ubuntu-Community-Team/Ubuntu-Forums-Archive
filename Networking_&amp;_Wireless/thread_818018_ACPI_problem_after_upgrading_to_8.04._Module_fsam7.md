---
title: "ACPI problem after upgrading to 8.04. Module fsam7400."
date: 2008-06-04
forum: Networking &amp; Wireless
---

### Post by ph1721 on 2008-06-04
Problem with FJS AMILO PRO v2000D notebook. Wifi card (with ipw2200) works fine, but only after using SW RF Kill switch module (fsam7400). There was some problem in gusty (the wifi was not working after ACPI resume) - I solved it simply by adding

> modprobe -r ipw2200
modprobe -r fsam7400

to /etc/acpi/sleep.sh and /etc/acpi/hibernate.sh and

> modprobe fsam7400 radio=1
modprobe ipw2200 led=1

to /etc/acpi/resume.sh. It worked well (I had to turn the wifi off manually when I was not using it). The 8.04 upgrade seems to let my acpi scripts as they were - but it doesn’t work anymore.

syslog:
> ipw2200: Radio Frequency Kill Switch is On:
Kill switch must be turned off for wireless networking to work.

In short, I cannot understand why the fsam7400 does not load. If I try it manually (sudo modprobe fsam7400 radio=1), it is OK.

syslog:
> fsam7400: SW RF kill switch for Fujitsu Siemens Amilo M 7400, v0.4.0
fsam7400: Copyright(c) 2004 zwobbl ;)
... and so on, as it should be.

Any ideas? Thanks a lot..

---

### Post by kakao on 2008-07-26
have you filed a bug report at launchpad.net, yet?

Cheers.

---

