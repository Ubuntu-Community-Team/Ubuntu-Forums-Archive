---
title: "clock not keeping correct time"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by foxinabox on 2009-07-01
I found an archived post about this but that "solution" won't work for me since I have no Windows partition on which to change the time.  The time showing on the task bar is consistently wrong.  If I reset it it eventually goes back to the wrong time again.  The timezone is set correctly and if I sudo hwclock -r it gives the correct time.  It seems the system clock is keeping correct time but the display in the task bar is always about 20 min behind.  Any clues? Thanks.

---

### Post by linuxmagick on 2009-07-01
You may want to set up NTP to keep the time synced with Internet time servers.  Here's a link that may help point you in the right direction:
[https://help.ubuntu.com/community/UbuntuTime?action=show&redirect=NTPTimeSynchronisation]("https://help.ubuntu.com/community/UbuntuTime?action=show&redirect=NTPTimeSynchronisation")

---

