---
title: "Broadband very slow on ubuntu 10.04, works fine with Windows XP"
date: 2014-06-04
forum: Networking &amp; Wireless
---

### Post by Sania_Wagle on 2014-06-04
I have MTNL broadband connection on my pc which is dual boot with Windows XP and Ubuntu 10.04. Using ADSL+Wifi router+modem (broadband connection is _wired_ for my pc and wireless for other devices). So this wired broadband gives me promised speed of 1Mbps on Windows but becomes tremendously slow on Ubuntu :icon_frown:.... that is 256kpbs only :mad:... So I don't think the problem is from MTNL's side... Do I need to change configuration? Or is any driver installation required on Ubuntu for the same? Waiting for your suggestions....

Thanks

---

### Post by Bucky Ball on 2014-06-04
Unless you're using the server version, 10.04 LTS has not been supported since April 2013. I suggest you upgrade to 12.04 LTS or clean install 14.04 LTS (or upgrade to 12.04 then 14.04 via the update manager, but that is a long, and possibly problematic, route). 

10.04 would not be getting updates, and that includes security updates, so unwise to go online with this machine.

---

### Post by varunendra on 2014-06-05
+1 to upgrading to 12.04 or 14.04, and +2 to a 'Clean Install', since upgrades are prone to errors as BB already pointed out above.

For wireless troubleshooting, a diagnostics report can help a lot to find/guess/solve the problem. So if the problem persists even with the newer, supported versions of Ubuntu, or if there is some really strong reason to stick with 10.04, please follow the instructions in this post to download and run 'wireless_script' (experimental version), and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

