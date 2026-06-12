---
title: "wireless card not appearing"
date: 2008-08-07
forum: Networking &amp; Wireless
---

### Post by mjavorek on 2008-08-07
Hi,

I tried to run wifi on DELL 1525 (Dell Wireless 1390), running Ubuntu 7.10, 2.6.22-15-generic.

Using several tutorials I have downloaded windows drivers from DELL pages (Dell_multi-device_A17_R174292.exe), unzipped and using ndsgtk installed. 

```

ndiswrapper -l
bcmwl6 : driver installed
        device (14E4:4315) present

```

ndiswrapper is added to modules

But, unfortunately in Network manager (icon in systray) I cannot see anything related to wifi (after system restart). 

in /var/log/daemon I can see only these suspicious lines:

```

 <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  

```

and

```

 <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored..

```

Hardware wifi switch is switched on, bluetooth appeared in systray. I have checked also settings in BIOS, but all is enabled.

Should I prepare some config file for wireless? I supposed that I can scan the air using some interface... ?

Thanks a lot for any ideas.

---

### Post by mjavorek on 2008-08-22
Solved for my self.

Ubuntu (ndiswrapper) is not working with Windows Vista drivers, must download Windows XP drivers ;-)

---

