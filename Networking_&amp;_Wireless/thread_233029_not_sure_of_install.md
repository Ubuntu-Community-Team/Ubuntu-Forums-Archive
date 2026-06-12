---
title: "not sure of install"
date: 2006-08-09
forum: Networking &amp; Wireless
---

### Post by tonab on 2006-08-09
ubuntu 5.10
belkin wireless g usb adapter

hi  i have enabled ndiswrper utils in synaptic,also i copied the 2000/xp drivers that comes with this adapter to my home folder,

when i type sudo ndiswrapper -l
i getthe following output,
   installed ndis drivers
rt73 invalid driver (note the original driver file is rt73.sys)
rt73.cat invalid driver
rt73.sys invalid driver

whats my next step to solve this pleas,im new to linux and ubuntu,
and the above note was added by me not by the output.

---

### Post by Jagot on 2006-08-09
You need to find the correct driver.  It is usually a .inf file - do you have anything like that with the Windows drivers?

---

### Post by tonab on 2006-08-09
i think the first rt73 without the extension is the .inf ,i do have a .inf on the adapters cdrom,and i mistakenly posted a note saying .sys , but im not sure if its inf as the output of sudo dosnt say thanks

---

### Post by tonab on 2006-08-09
ps, i ran ndiswrapper -i rt73.inf and the output says that its already installed, ?? but it dosnt show the inf extsion if that means anything.

---

### Post by alecjw on 2006-08-09
Run sudo ndiswrapper -e rt73 first

---

### Post by tonab on 2006-08-10
i have run the  sudo ndiswrapper -e and it uninstalled,also i reinstalled still i get the same invalid driver error,pleas help,thanks

---

### Post by tonab on 2006-08-10
ive uninstalled all the drivers, and reinstalled just the inf,and now i have driver present hardware present so i take it this is a good start,im goin to have a go at configuring it now,keep ye posted thanks

---

### Post by tonab on 2006-08-10
mm its not showing up in the system administration network, and here is some out put i got from it,

$ iwconfig lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

~$ ifconfig lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
 inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:103176 errors:0 dropped:0 overruns:0 frame:0
          TX packets:103176 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:9357646 (8.9 MiB)  TX bytes:9357646 (8.9 MiB)

---

### Post by tonab on 2006-08-11
.

---

