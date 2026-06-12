---
title: "nm-applet not showing ( Ubuntu 8.10)"
date: 2008-11-23
forum: Networking &amp; Wireless
---

### Post by somu76 on 2008-11-23
Hi,
  I am trying to troubleshoot my wireless card problem, but am not able to see the Network Manager applet on the SysTray.. When I looked at the list of processes, I do see it in there, with a status of sleeping. I tried to kill it and restart it, but it seems to hang without any response... 

```
somu@somu-ubuntu:~$ sudo nm-applet --sm-disable

** (nm-applet:8871): WARNING **: No connections defined

```

Any ideas on how to get it out of this state... or bring the UI upfront.

Thanks,
somu.

---

### Post by shanix on 2008-11-23
if you restart the dbus?

sudo /etc/init.d/dbus restart

---

