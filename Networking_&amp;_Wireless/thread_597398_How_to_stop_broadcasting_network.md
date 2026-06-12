---
title: "How to stop broadcasting network?"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by KevLeviathan on 2007-10-30
Hey guys, this is a little silly BUT yesterday I messed around with creating an ad hoc network by right clicking on the network icon in the tray and hitting "Create new network". Well I have since rebooted and apparently it is still visible. I am in a highly public place and I would really like to stop broadcasting this network but I can't seem to figure it out
Help would be appreciated!

---

### Post by spd106 on 2007-10-30
Are you sure it's still in ad hoc mode?

Try opening a terminal and enter the following command.
```
iwconfig
```
If the wireless card says managed mode, then it's not in ad hoc mode any more. You can force it to switch to managed mode with the following command (assuming it's eth1).
```
sudo iwconfig eth1 mode managed
```

---

