---
title: "No Wireless extension WMWare"
date: 2016-01-30
forum: Networking &amp; Wireless
---

### Post by Diaconescu on 2016-01-30
Hello,

I`m begginer in use the system operation Ubuntu.
I install this system on the virtual machine (WMWare) and I open a terminal and I write the next command.
```
iwconfig
```
After running this command following message

```
eth0      no wireless extensions
lo          no wireless extensions
```

Can you please tell me where it came from this error and how can I solve it?
I installed Windows and are connected via wireless internet

Thanks in advance!

---

### Post by jeremy31 on 2016-01-30
If Ubuntu is the guest OS, then you should set up the virtual machine to use the virtual ethernet connection to use the wifi from the host.  Check the WMWare documentation for details

---

