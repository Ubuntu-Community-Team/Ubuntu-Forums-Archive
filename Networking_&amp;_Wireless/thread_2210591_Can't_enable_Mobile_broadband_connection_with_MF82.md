---
title: "Can't enable Mobile broadband connection with MF820D"
date: 2014-03-11
forum: Networking &amp; Wireless
---

### Post by stuf99 on 2014-03-11
Hi
I have installed Ubuntu 12.04 LTS and trying to use MF820D LTE USB Modem. I can see the connection under my mobile connections, but is disabled. I cannot change that.
I have tried several recipes on the subject among those are these

[http://ubuntuforums.org/showthread.php?t=1601355](http://ubuntuforums.org/showthread.php?t=1601355) , 
and
[http://ubuntuforums.org/showthread.php?t=2074518](http://ubuntuforums.org/showthread.php?t=2074518)

but I haven't had any luck.

Can anyone please help?

Thanks

---

### Post by varunendra on 2014-03-14
Welcome to the forums stuf99 !

Please unplug the modem (if is already plugged in) > wait approx. 10 seconds > plug it in > wait about 30 seconds > open a terminal (Ctrl-Alt-T) and post back the outputs of -
```
uname -mr
lsb_release -d
lsusb
dmesg | tail -40
nm-tool
cat /var/lib/NetworkManager/NetworkManager.state
```

---

