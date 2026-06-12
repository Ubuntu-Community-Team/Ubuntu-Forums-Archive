---
title: "Can't enable Wifi"
date: 2013-09-17
forum: Networking &amp; Wireless
---

### Post by tn88test on 2013-09-17
Hi!

I just installed Ubuntu dual boot. My wireless worked fine on Windows XP but not on Ubuntu. It showed "Wireless is disable by hardware switch", but the wireless led already turned on. Please help me!

---

### Post by varunendra on 2013-09-17
Please open a terminal (Ctrl-Alt-T) and post back the output of following -
```
lspci -nnk | grep -iA2 net
rfkill list all
lsmod
```

While posting the outputs, please use the 'Code' box. Follow the "Using Code Tags" link in my signature to see how.

---

### Post by tn88test on 2013-09-18
I just found out a solution to enable my wifi by using this 
```
rfkill unblock all
```
but I have to do this every time on start up.

---

### Post by jonnyboysmithy on 2013-09-18
To run the command at every startup, add the code to your rc.local file like so:
in a terminal: ```
sudo gedit /etc/rc.local
```
Add the line of code above the "exit 0" and save.
```
rfkill unblock all
```

---

