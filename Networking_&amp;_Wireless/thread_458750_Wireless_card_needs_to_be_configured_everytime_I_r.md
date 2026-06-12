---
title: "Wireless card needs to be configured everytime I reboot"
date: 2007-05-29
forum: Networking &amp; Wireless
---

### Post by tylerjroach on 2007-05-29
I have successfully installed a linksys wusb11v4 wireless adapter but now every time I reboot I have to put in these two commands for it to work:

```
user@ubuntu:~/WUSB11v4_08272004/Drivers$ sudo depmod -a
```

```
user@ubuntu:~/WUSB11v4_08272004/Drivers$ sudo modprobe ndiswrapper
```

How can i get this to work automatically everytime I start my computer

Thanks

---

### Post by handydan918 on 2007-05-30
one possibility is to add the name of the module to the /etc/modules file. Not sure if that is the best solution for Ubuntu, since I just started using it again for the first time since 5.04....
You might also try ndiswrapper -m after you have it loaded. I know that writes the configuration for the driver ndiwrapper is "wrapping", but I'm not sure if that is pertinant to your issue.

---

### Post by #Reistlehr- on 2007-07-04
if ya find a fix, shoot me a pm, ill do the same. 

got the same problem.

---

