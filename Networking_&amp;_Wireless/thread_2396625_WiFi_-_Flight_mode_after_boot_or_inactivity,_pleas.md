---
title: "WiFi - Flight mode after boot or inactivity, please help"
date: 2018-07-18
forum: Networking &amp; Wireless
---

### Post by matrix5 on 2018-07-18
Hello, 

After fresh Ubuntu 18.04 installation I have problem with wireless connection. 
After boot flight mode is enabled and when I turn on wireless all is ok until I'll leave computer for about 4 minutes, then it will switch to flight mode again and when it is happening I see such entries in logs:
```
Jul 18 20:38:44 CBA kernel: wlp2s0: deauthenticating from c0:4a:00:be:89:66 by local choice (Reason: 3=DEAUTH_LEAVING)
Jul 18 20:38:44 CBA kernel: EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro,commit=600
Jul 18 20:38:44 CBA kernel: usbcore: deregistering interface driver rtsx_usb

```
Here are my wireless info: [http://paste.ubuntu.com/p/kJCmK9b4wf/](http://paste.ubuntu.com/p/kJCmK9b4wf/) 

Please help me with this issue.

I found solution, or workaround, by myself. Some time ago I installed TLP, later uninstalled and then my problem occurred. I installed it again and all is fine now.

---

