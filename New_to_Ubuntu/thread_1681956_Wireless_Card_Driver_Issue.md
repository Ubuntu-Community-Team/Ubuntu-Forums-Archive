---
title: "Wireless Card Driver Issue"
date: 2011-02-05
forum: New to Ubuntu
---

### Post by shoaibi on 2011-02-05
I recently bought HP Pavilion DV6 4001. I have attached the detailed outputs of lsmod, lspci and lshw.

My OS details:

```

Linux eagle 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 x86_64 GNU/Linux

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.10
Release:	10.10
Codename:	maverick


```

The best i could find was downloading "RT5390PCIe" (ya, its not exactly same as mine) from [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2) and install it as per [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73). However that hasn't helped either. I am a bit lost at what should i do next. will really appreciate any hints at this point.

---

### Post by I&#9829;HTML5 on 2011-02-10
*Try* going to System | Administration | Additional Drivers to check for proprietary/restricted drivers.

---

