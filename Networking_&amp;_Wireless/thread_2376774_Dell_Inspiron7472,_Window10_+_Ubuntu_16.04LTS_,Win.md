---
title: "Dell Inspiron7472, Window10 + Ubuntu 16.04LTS ,Windows can connect to Wi-Fi, U cannot"
date: 2017-11-06
forum: Networking &amp; Wireless
---

### Post by so1itary on 2017-11-06
in my Ubuntu, there is always "Devices not Ready" below my Wi-Fi network,
I have searched a lot these days but the ways are the same as "checking the alternative drivers " 
but my alternative devices don't contain the wireless section. 
Please help me , I've confused by this for a few days...[ATTACH=CONFIG]277430[/ATTACH]

---

### Post by vasa1 on 2017-11-06
Please read [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108) and provide the information required to help you.

---

### Post by oldfred on 2017-11-06
I show an unknown, unknown device.
Mine was not a wireless issue, but I have Skylake and installed Intel driver.

 Skylake Best to have newest microcode from Intel version 3.20160714.1 or later
grep microcode /proc/cpuinfo 

fred@Z170N:~$  dpkg-query -W intel-microcode
intel-microcode    3.20170707.1~ubuntu16.04.0

Above is in Synaptic or Ubuntu  repository with 16.04.
If you have the latest microcode then back to vasa1 suggestion on running the wireless script.

---

