---
title: "Broadcom STA Driver Caused Kernal Panic..."
date: 2009-11-23
forum: New to Ubuntu
---

### Post by kamitsukai on 2009-11-23
Quick rundown of what happened: 


[LIST]
[*]Installed Ubuntu 9.10 via the LiveCD and noticed that there was an option to install the Broadcom STA wireless driver in the Restricted Hardware window
[/LIST]


[LIST]
[*]After I had  installed Ubuntu I went to install the Broadcom STA wireless driver but it didn't find any so I updated Ubuntu and restarted the laptop
[/LIST]


[LIST]
[*]After restart Restricted Hardware managed to find and install the STA driver however about 20sec later the screen went blank with a stuck cursor and the caps lock light and the one next to it started to flash
[/LIST]


[LIST]
[*]Turned the laptop off and it restarted fine however there was still no internet, Restricted Hardware stated that "The Driver was Installed but not currently active (flipping useless statement with no solution....)
[/LIST]


[LIST]
[*]Reinstalled the driver and the blank screen happened again but after another reboot this time I was greeted with a blank screen with some wtext about a kernal panic and sync errors (see below)
[/LIST]

My laptop is a Dell Inspiron 1525 with the Broadcom BCM4312 14e4:4315 card which isn't supported by b43 driver....



```
[      1.601897] kernal panic - not syncing: VFS: Unable to mount root fs on unk
nown-block(0.0)
```Thanks for any help!



Also as a side note I installed the RC1 of Mint 8 and managed to get my wirless installed and running in under 5min very strange;)

---

### Post by ukripper on 2009-11-23
check this thread - [http://ubuntuforums.org/showthread.php?t=1309760](http://ubuntuforums.org/showthread.php?t=1309760)

---

### Post by kamitsukai on 2009-11-23
> **ukripper said:**
> check this thread - [http://ubuntuforums.org/showthread.php?t=1309760](http://ubuntuforums.org/showthread.php?t=1309760)

Thanks but in the end I just reinstalled and then followed this post: [http://ubuntuforums.org/showthread.php?t=1266620](http://ubuntuforums.org/showthread.php?t=1266620)

---

