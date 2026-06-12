---
title: "Cups Won't print from Lubuntu"
date: 2018-05-11
forum: Networking &amp; Wireless
---

### Post by antricos88 on 2018-05-11
Hello all!

I have installed cups print server in an OrangePi a while ago and my Windows 7 and Windows 10 PCs prints fine without any problem!
Yesterday I decided to use Lubuntu on my laptop and I cannot print from it.
The laptop connects to the cups server and install drivers normally however I get the below error message and the print job stops.

This is from Lubuntu side:
```

Processing - File "/usr/lib/cups/filter/epson_inkjet_printer_filter" not available: No such file or directory

```

This is from Server side:
```
E [11/May/2018:21:55:19 +0300] EPSON_L310_Series: File \"/usr/lib/cups/filter/epson_inkjet_printer_filter\" not available: No such file or directory
E [11/May/2018:21:55:19 +0300] [Job 159] Unable to start filter "/usr/lib/cups/filter/epson_inkjet_printer_filter" - Success.
E [11/May/2018:21:55:19 +0300] [Job 159] Stopping job because the scheduler could not execute a filter.
```

Any advice ?

---

### Post by antricos88 on 2018-05-12
Solved by executing the below on server side:

```
sudo apt-get install printer-driver-gutenprint
```

After that Epson L210 drivers showed up in cups and worked fine with my Epson L310.

---

