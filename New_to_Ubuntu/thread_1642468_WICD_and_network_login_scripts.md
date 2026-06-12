---
title: "WICD and network login scripts"
date: 2010-12-10
forum: New to Ubuntu
---

### Post by mikeserv on 2010-12-10
Ok, so I've installed WICD from the repos and uninstalled Network Manager. I did this because the network specific script functionality is very desirable for me, also I used it a few years ago and had good results. I'm running Ubuntu 10.10 with a WiFi connection to a home network. I've got some network shares on various machines, but there are some on my media drive that I would specifically like to access. The shares I need are located on a Windows 7 machine.

I'm able to mount and unmount the shared folders in the terminal with this script (run with sudo):
```
#!/bin/sh
notify-send "Connecting" "network drives at desktop.lan" 
mount -t cifs //share1/path1 /target1/path1 -o password=,iocharset=utf8,file_mode=0777,dir_mode=0777 
mount -t cifs //share2/path2 /target2/path2 -o password=,iocharset=utf8,file_mode=0777,dir_mode=0777
```
And the unmount script (again, run with sudo):
```
#!/bin/sh
notify-send "Disconnecting" "network drives at desktop.lan"
umount /target1/path1 
umount /target2/path2
```

I put these scripts in $HOME/.script/ and pointed WICD at them in the post-connect and pre-disconnect fields of my home WiFi SSID. Still I get nothing. Not even the notification (which works when I run the scripts myself). I don't think WICD is even trying to run them.

I thought that maybe it was a permissions problem so I tried altering the script command by adding a "gksudo" to the beginning of it, but I don't even get prompted for my admin password. And besides, the notify-send should still work before the script runs into the mount command, right?

Is there anyone out there that successfully mounts network shares with scripting on WiFi connect? I would really like the function to be automatic, especially when leaving a network.

Thanks for any help anyone can offer.

-Mike

---

