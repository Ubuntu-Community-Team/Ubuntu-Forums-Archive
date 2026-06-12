---
title: "MTU Change"
date: 2006-10-30
forum: Networking &amp; Wireless
---

### Post by shannon.cummins on 2006-10-30
I am trying to change the default MTU on interface eth0 to 1492 vice 1500.  I am running Kubuntu EdgyEft 6.10.  How do I go about doing this other than opening a terminal after startup and doing it manually?  I have written a script called MTU as the following:
```
#!/bin/bash
sudo ifconfig eth0 mtu 1492
```

I have executed this in a terminal with the command

```
sh MTU
```

It executes fine and changes the MTU size but I had to open a terminal and type the sh MTU command manually.  Is there a way to have this script execute automatically at login or is there an area that I can change the default 1500?  Thanks

---

### Post by s[_]spect on 2007-08-31
See this thread.. [http://ubuntuforums.org/showthread.php?t=3985&highlight=mtu+size]("http://ubuntuforums.org/showthread.php?t=3985&highlight=mtu+size")

---

