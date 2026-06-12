---
title: "Wireless Not Working, Tried Other Solutions Still Not Working"
date: 2014-01-27
forum: Networking &amp; Wireless
---

### Post by colm2 on 2014-01-27
Hello

I am hoping someone can help me as this issue has been resolved on other thread but it is just not working for me despite trying solutions. I am a new first time Ubunto user so forgive me if I ask silly questions.

My machine is an Acer Extensa 5620Z and runs Windows 7, I have installed Ubunto LTS along side it and all works except for the Wireless, there is nothing found, and in the bar at the top of the screen there is no enable wireless. I have enabled the Boradcom STA Wireless driver but did not seem to do anything for the issue.

Can anyone help me, Im happy to post results of commands if you let me know what to test.

Thanks

---

### Post by praseodym on 2014-01-27
Please open a terminal with CTRL+AL+T and show the outputs of:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```
Does LAN work?

---

