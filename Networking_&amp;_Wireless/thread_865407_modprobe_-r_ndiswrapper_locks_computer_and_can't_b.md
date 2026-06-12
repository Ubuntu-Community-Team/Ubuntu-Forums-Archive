---
title: "modprobe -r ndiswrapper locks computer and can't be killed"
date: 2008-07-20
forum: Networking &amp; Wireless
---

### Post by malfist on 2008-07-20
I have a NetGear WG111v2 and it used to work fine, but every now and then it will kick me off the internet and say that wlan0 doesn't support scanning. I generally fix this by doing 
```
modprobe -r ndiswrapper
modprobe ndiswrapper
iwlist wlan0 scan
```

And then NetworkManager will pick up on it and reconnect me. However, lately modprobe locks up with trying to remove ndiswrapper. It asks for my root password and then nothing. When I try to kill the process with Ctrl+C or kill or using htop, the CPU usage shoots to 100% and it doesn't die. 
The only way to kill it is to restart, and ubuntu hangs on shutting down because it can't kill modprobe so I have to manually press the reset switch.

Does anyone know how I can fix this?

---

### Post by aimwin on 2008-07-25
I have the same problems.

I just unplug and replug my wg111v2, and it works again.
look at my thread, to see if you can try something else, or ask phytheas22.

[http://ubuntuforums.org/showthread.php?t=850120&highlight=wg111v2](http://ubuntuforums.org/showthread.php?t=850120&highlight=wg111v2)

---

