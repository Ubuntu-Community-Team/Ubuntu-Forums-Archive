---
title: "DansGuardian blocking apt-get at school"
date: 2006-12-11
forum: Networking &amp; Wireless
---

### Post by Lord Illidan on 2006-12-11
Hi guys, currently on school computer.

The technician has set up dansguardian to block certain websites and extensions, among them .gz and .exe

In Windows, we managed to view certain websites which were blocked (no illegal activity, these were legitimate websites like google images) by using Torpark, so no problem.

However, I have an Ubuntu box in the lab which is using Dapper Drake beta and I want to upgrade it. But it seems that dansguardian is not letting it get the .gz for the packages. The technician is also not available almost 100% of the time. Does anyone know a way how I can bypass it with a proxy? I really want to get this box to Edgy, or at least Dapper Final.

---

### Post by bapoumba on 2006-12-11
Hi, being in academia myself, I could only recommend you talk with the network administrator. Bypassing the rules could get you into trouble.

If you cannot get to be able to update Ubuntu from your school network, may be you could consider setting up a [local repository]("http://ubuntuforums.org/showthread.php?t=20217"), if you have an ubuntu computer with a network access (at home for ex).

[http://www.debianadmin.com/create-backup-of-all-packages-using-aptoncd-in-ubuntu.html]("http://www.debianadmin.com/create-backup-of-all-packages-using-aptoncd-in-ubuntu.html")

---

### Post by Lord Illidan on 2006-12-11
I don't think I'll get into trouble for setting up a proxy or anything, as I do have some leverage within the school administration. Does anyone think it's possible to set a VPN between home pc and school pc and use the home pc to upgrade it?

---

