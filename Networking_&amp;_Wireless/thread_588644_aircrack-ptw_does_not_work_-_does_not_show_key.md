---
title: "aircrack-ptw does not work - does not show key"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by letmein on 2007-10-23
When i run aircrack-ptw, it doesn't output the web key, I've tried serveral different .cap files...(used airodump to get them)

Here is my output:

home@administrator:~$ aircrack-ptw crack-01.cap
This is aircrack-ptw 1.0.0
For more informations see [http://www.cdc.informatik.tu-darmstadt.de/aircrack-ptw/](http://www.cdc.informatik.tu-darmstadt.de/aircrack-ptw/)
allocating a new table
bssid = 00:12:17:29:C7:A7  keyindex=0
stats for bssid 00:12:17:29:C7:A7  keyindex=0 packets=230463

And that's it....what gives?

---

### Post by wieman01 on 2007-11-09
How many IVs have you collected? You would need at least 20K.

---

