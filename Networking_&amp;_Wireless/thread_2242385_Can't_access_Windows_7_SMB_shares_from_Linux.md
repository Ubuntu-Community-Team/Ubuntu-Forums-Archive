---
title: "Can't access Windows 7 SMB shares from Linux"
date: 2014-09-01
forum: Networking &amp; Wireless
---

### Post by halfbeing on 2014-09-01
I am having trouble accessing a Samba share on a Windows 7 machine from Linux. Sharing from Linux to Windows works fine.

When I try to access the share through either Thunar or Gnome Commander I get asked for a domain name. Since I have configured both the Windows box and the Linux box to be part of a workgroup, there oughtn't to be a domain name (although in the advanced system settings in Windows for some reason it says that the domain is DOUGAL, which is actually the name of the machine and not the workgroup). However, no matter what I try to put in the domain name field, including leaving it blank (which is possible in Gnome Commander but not in Thunar), I get an error ("Access not permitted" in Gnome Commander, "Password required for dougal" in Thunar (even though I have entered a password). What am I doing wrong?

---

