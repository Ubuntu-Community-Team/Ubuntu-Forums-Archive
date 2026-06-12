---
title: "Modprobe Ndiswrapper HELP!!!!!!"
date: 2005-07-26
forum: Networking &amp; Wireless
---

### Post by jordanj1969 on 2005-07-26
jjordan@ubuntujj:~$ modprobe ndiswrapper
FATAL: Could not open '/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko': No such file or directory
jjordan@ubuntujj:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5a driver present, hardware present
jjordan@ubuntujj:~$

---

### Post by ssck on 2005-07-26
[QUOTE=jordanj1969]jjordan@ubuntujj:~$ modprobe ndiswrapper
FATAL: Could not open '/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko': No such file or directory
jjordan@ubuntujj:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5a driver present, hardware present
jjordan@ubuntujj:~$[/QUOTE]

maybe you could try this command : sudo modprobe ndiswrapper

---

### Post by jordanj1969 on 2005-07-27
I tried the sudo command also and got the same output

---

