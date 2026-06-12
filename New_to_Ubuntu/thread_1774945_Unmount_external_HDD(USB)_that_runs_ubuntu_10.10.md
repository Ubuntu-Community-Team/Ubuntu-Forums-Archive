---
title: "Unmount external HDD(USB) that runs ubuntu 10.10"
date: 2011-06-04
forum: New to Ubuntu
---

### Post by sriratpuru on 2011-06-04
Hi All,

As my internal HDD had crashed, I started using my external 500 GB Seagate HDD powered by USB  as a boot device installed with ubuntu. However, I started getting errors while trying to boot my system.Even though my system works fine now, I am afraid whether my external HDD is turned off properly. Please advise us me the correct procedure to spin down my external HDD before shut down.

---

### Post by -kg- on 2011-06-04
Since you are booting to your external hard drive, then AFAIK you can't "spin it down" prior to shutdown.  It has to access the drive until shutdown, or it can't properly shut down.  The principles of operation between an external and internal hard drive are basically the same.

Frankly, I'd get another internal hard drive to replace your external as the boot device.  It won't spin down until the shutdown process is completed, either, but it will be faster considering it isn't going through the bottleneck of the speed of the USB port.

---

