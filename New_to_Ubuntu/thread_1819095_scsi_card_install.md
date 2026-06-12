---
title: "scsi card install"
date: 2011-08-05
forum: New to Ubuntu
---

### Post by antmast on 2011-08-05
Hi,  Ubuntu 11.04 installed & running. Have a Advansys scsi card that I need to configure for my scanner. I came up with the following webpage that has the driver needed.
[http://manpages.ubuntu.com/manpages/hardy/man4/adv.4.html](http://manpages.ubuntu.com/manpages/hardy/man4/adv.4.html)

Being a noob with Ubuntu I need step by step instructions on how to get the driver installed. TIA for any help.

---

### Post by cariboo on 2011-08-06
The driver should be automgically installed when you boot your system. Do you get any output, if you open a terminal and type:

```
sudo lshw | grep scsi
```

---

