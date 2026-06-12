---
title: "Thunderbird won't check mail."
date: 2006-10-08
forum: Networking &amp; Wireless
---

### Post by Squrdel on 2006-10-08
I installed Thunderbirds latest version and set up mail boxes as per my setup in Windows XP. I share a profile with the XP Thunderbird on a vfat drive, no problem there. I cannot get Thunderbird to check my mail in Dapper, it times out on every mailbox. Any suggestions?

---

### Post by timetunnel on 2006-10-08
You're not able to share the same Thunderbird profile between Windows and  Linux. Reason is that paths to the folders that contain your emails are stored as *absolute* paths in the Thunderbird settings file "prefs.js". As these are never the same for Windows and Linux, Thunderbird will work only on the system that Thunderbird was set up first.

Maybe there are solutions and workarounds out there that explain how to really share a profile between Windows and Linux, but for a standard installation, it just won't work.

---

### Post by Squrdel on 2006-10-09
Thanks for that. I had tried editing prefs.js but could see no obvious way of making the paths compatible. There are a few threads on the forum ithe methoof sharig these proles.They workine for Firefox but obviously ot for Thundbird.

---

