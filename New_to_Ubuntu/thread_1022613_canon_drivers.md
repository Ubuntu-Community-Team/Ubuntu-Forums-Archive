---
title: "canon drivers"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by illusionbuster on 2008-12-27
I have a canon pixma ip2600 and I followed the instructions other had success with  using  similiar system (ubuntu-Intrepid)8.10. The problem is when I run the package installer on cnijfilter-common_2.90-1_i386.deb, it tells me it requires installation of 1 pkg - libcupsys2. So I find libcupsys2 on us.debian and i package install it and installer says I need libgnutls13. Ok so now what? I am new to linux and want to learn it but why am I or are packages missing key components and what is my solution. How many libs am i going o need and where and how do i get them? I am 1 real green coffee bean here, so go easy!:)

---

### Post by cariboo on 2008-12-27
If you are installing from a .deb, all you need to do is double-click the file. Gdebi should take care of the dependencies for you.

From the gdebi man page:

> gdebi  lets you install local deb packages resolving and installing its dependencies. apt does the  same,  but  only  for  remote  (http,  ftp)   located packages.

Jim

---

### Post by RomanIvanov on 2008-12-27
use this, but put your printer name: [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900)

---

