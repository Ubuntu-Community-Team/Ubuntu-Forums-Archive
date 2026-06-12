---
title: "Samba 4 + Windows 7 EXTREMELY SLOW"
date: 2014-03-05
forum: Networking &amp; Wireless
---

### Post by schneida on 2014-03-05
Hi guys,

I urgently need your help. I deployed a Samba 4 Active Directory (SerNet packages latest version) in my companies network (changing over from Windows Server 2003), everything seemed to work fine at the beginning, however my colleagues now report abysmal download / upload speeds to our shared network locations. When copying over a folder with 50 files that has a total size of 11 MB, it takes on Windows 7 clients roughly 20 minutes (!!!!) to complete the process. I then tried copying the same folder onto the old Windows Server 2003 and the copy process was finished in merly an eyeblink (like 3-5 seconds tops).

I searched the internet for days now, finding all kind of problem reports for Windows 7, however most people are complaining about slow speeds in general (no matter if ftp or smb), and are still getting like 5-10 Mb/s where they would expect 20-30 Mb/s. I tried all kinds of suggestions like turning off Remote Differential Compression or setting the autotune setting (netsh) to restricted or disabled but had no success so far.

PLEASE give me some suggestions on how to solve this issue!

Thanks a lot in advance,

schneida

---

