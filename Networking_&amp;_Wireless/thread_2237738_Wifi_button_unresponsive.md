---
title: "Wifi button unresponsive"
date: 2014-08-03
forum: Networking &amp; Wireless
---

### Post by nisargshah on 2014-08-03
I recently installed Ubuntu 14.04 64-bit on my HP 15-r022TX laptop. I have a Wifi hardware switch (which is combined with the F12 key). It worked for some time but recently it has been unresponsive. Last thing I seem to have done is to install updates. Now it seems I cannot enable wireless as it has been disabled by the hardware switch and the key is not working. I looked at [this]("http://ubuntuforums.org/showthread.php?t=2231243") thread and pressing the F12 key after running "acpi_listen" in the terminal brings the following output -
```
nisarg@nisarg-HP-15-Notebook-PC:~$ acpi_listen
 PNP0C14:01 00000080 00000000

```
Can anyone help me with this?

---

### Post by kc1di on 2014-08-03
Try this and see if it works:
in a terminal type:
```
rfkill unblock all
```

if that works you can make it permanent with this command:
```
systemctl enable rfkill-unblock@all
```

Good luck

---

### Post by nisargshah on 2014-08-04
No. It did not work.

---

