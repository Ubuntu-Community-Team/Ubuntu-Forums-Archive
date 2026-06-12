---
title: "Wireless button on keyboard does not turn on"
date: 2014-06-28
forum: Networking &amp; Wireless
---

### Post by James720 on 2014-06-28
Hi,

I recently installed Wubi on my hp Pavilion dv4 which was previously running Windows 7. The installation went fine and I was able to choose a wireless network without a problem. Yesterday, though, I moved out of the area of the wireless network and now I cannot view any wi-fi connections that are available. The wi-fi button on my keyboard(f12) will not go from orange to blue. When I boot into Windows 7 it works perfectly. 

I've been looking for an answer all day but nothing posted seems to work. I've tried to use rfkill list all to help solve the problem, but the command doesn't return anything for me.

Any ideas? Thanks in advance!

---

### Post by Vladlenin5000 on 2014-06-28
Hi, welcome.

Sorry, WUBI is no longer supported -> [http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

---

### Post by bobnn on 2014-06-28
I have sometimes had luck with this opening a terminal and using:

```
sudo nmcli nm wifi on
```

---

