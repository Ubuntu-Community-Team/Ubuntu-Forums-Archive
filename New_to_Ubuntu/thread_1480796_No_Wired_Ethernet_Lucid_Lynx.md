---
title: "No Wired Ethernet Lucid Lynx"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by SVC XPRT on 2010-05-11
Thanks in advance to everyone involved in making Ubuntu a household name.

I have Lucid Lynx running on a Toshiba Satellite Laptop.
The Lynx does not see the wired NIC and will only do Ethernet with the wireless radio (and does very well)

I dl the Device Manager and it shows a Marvell Yukon controller and everything looks good (To a N00b :-)

Any suggestions? Not everywhere has wireless and sooner or later I will be stuck.

This same hardware worked on Jaunty and Koala but not with the Lynx.....Yet :-)

No Dual Boot here.....:KS

---

### Post by consindo on 2010-05-15
This issue affects me as well... Sometimes booting with noapic acpi=off works.

---

### Post by 98174 on 2010-08-06
Can you give the output of -lspci?

I have a Toshiba Satellite as well, and its running Atheros AR8152 for the wired NIC.  

If you're running a AR81xx driver, you fix this by downloading this driver: [http://partner.atheros.com/Download.aspx?id=125]("http://partner.atheros.com/Download.aspx?id=125")

If it's downloaded as .html, remove this ending (i.e. change it to end in tar.gz)

Then follow the instructions here: [http://ubuntuforums.org/showthread.php?t=1476231#6]("http://ubuntuforums.org/showthread.php?t=1476231#6")

You may get a "FATAL" error when running the modprobe line.  Ignore that and restart.  Enable/disable your networking once, and your wired should show up.

---

### Post by abrax on 2011-03-04
The page of the Atheros Driver download ( [http://partner.atheros.com/Download.aspx?id=125](http://partner.atheros.com/Download.aspx?id=125) ) is not working... does anyone has any other site that has the driver? pleeeese! :)

---

### Post by davidmohammed on 2011-03-04
try [here]("http://partner.atheros.com/Drivers.aspx").

---

