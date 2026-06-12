---
title: "Saving partitions and data while upgrading to 10.10"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by abhishek_sharma on 2010-10-10
Hi,
I need to upgrade to Ubuntu 10.10 but also want to save my data on hard disk as it is very time consuming to transfer and backup.
Here is my system partitions:
1. /dev/sda1          dierctory is /
2. /dev/sda6          directory is /home
3. /dev/sda7          directory is /usr
4. swap space

Thank you in advance:)

---

### Post by Locke_99GS on 2010-10-10
The simplest solution would be to perform the dist-upgrade offered through the Update Manager. This will leave your things in-tact.

Another method, since you have a seperate /home partition, would be to install the new Ubuntu over / (sda1) and either add sda6 to your fstab, mounted at /home - OR - have the installer do it but having it use sda6 for /home, but NOT formatting the partition.

A more time consuming method would be to just back up /home, reinstall, then move your backup back to /home.

---

