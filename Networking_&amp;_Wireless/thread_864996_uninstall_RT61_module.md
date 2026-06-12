---
title: "uninstall RT61 module"
date: 2008-07-20
forum: Networking &amp; Wireless
---

### Post by rashwan on 2008-07-20
Hi,
i've installed ubuntu 8.04 and my wLan D-Link DWL-G510 that uses RaLink (RT61) chipset Driver installed Automatically and working well.
i was trying to use the "aircrack-ng" suite and i've installed the rt61 module as shown here [http://www.aircrack-ng.org/doku.php?id=rt61]("http://www.aircrack-ng.org/doku.php?id=rt61")
it works at first but when i reboot everything goes bad and i cant either use the aircrack-ng suite or use the Device in normal mode and cant get connected to "secured" networks anymore do i have to remove the new driver module i've installed ?? and how ?

Thanks for helping newbie.

---

### Post by Ayuthia on 2008-07-20
According to the link that you provided, they tell you to remove rt61pci and then load rt61.  That command only works for that session.  If you want to keep using that driver (rt61), you will need to blacklist rt61pci:
```
echo blacklist rt61pci|sudo tee -a /etc/modprobe.d/blacklist
```
Since nothing is working, I am guessing that both drivers are being used.  You can check this by:
```
lsmod|grep rt61
```
This will list out all drivers with that have rt61 in it.  You should see rt61pci and rt61.  If you do, you can restart rt61 by:
```
sudo modprobe -r rt61pci rt61
sudo modprobe rt61
```If rt61 is not there, you can still load the driver by doing the modprobe commands.  To have it always automatically load:
```
echo rt61|sudo tee -a /etc/modules
```

Hope that helps.

---

### Post by rashwan on 2008-07-20
Yeah that works both drivers are actually being used i blacklisted the rt61pci and use the rt61 and monitor mode works well

Thank You

---

