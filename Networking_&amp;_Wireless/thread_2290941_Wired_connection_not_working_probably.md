---
title: "Wired connection not working probably"
date: 2015-08-16
forum: Networking &amp; Wireless
---

### Post by malthe122 on 2015-08-16
[COLOR=#141823][FONT=helvetica]When i plug in my ethernetcable, it says that it is connected and i have a VERY slow connection (takes like 5 min to open google, when it doesen't give up), then there was an update that fixed the problem, and i was able to use my ethernet for gaming. Then a new update was released and the problem occured again. I've tested the Ethernetcable on a windows laptop, and it works perfectly, also worked on my laptop before installing Ubuntu. The wireless internet in my house is very weak, and its almost impossible to play Counter Strike [/FONT][/COLOR][COLOR=#141823][FONT=helvetica]without the ethernet. I'm very new to Ubuntu and the terminal and all that, so if you need some information, please tell me what to input in the terminal :)

EDIT: Issue is fixed after replacing my Zyxel router[/FONT][/COLOR]

---

### Post by praseodym on 2015-08-18
Hi,

please show the terminal outputs of these commands
```

uname -a
lspci -nnk
lsmod
ifconfig -a
cat /etc/network/interfaces
cat /etc/resolv.conf
route -n
```

---

### Post by malthe122 on 2015-08-18
Hi, thanks, but the problem is fixed. Tip: Don't use Zyxel router

---

