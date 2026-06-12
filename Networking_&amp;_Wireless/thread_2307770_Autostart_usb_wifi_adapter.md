---
title: "Autostart usb wifi adapter"
date: 2015-12-28
forum: Networking &amp; Wireless
---

### Post by abbobba2 on 2015-12-28
[SIZE=2][FONT=arial narrow]Hi 
I have an usb wifi adapter, its chipset is rtl8188eu. For using this I had to compile the driver that i found on github. 
[/FONT][/SIZE][SIZE=2][FONT=arial narrow][COLOR=#212121]The problem is that when I start the system I have to remove and reinsert the key in usb port to make it work.[/COLOR][/FONT][/SIZE]

---

### Post by abbobba2 on 2015-12-29
resolved with:
[COLOR=#000000][FONT=Ubuntu]
sudo modprobe 8188eu[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]echo '8188eu' | sudo tee -a /etc/modules[/FONT][/COLOR]

---

### Post by slickymaster on 2015-12-29
> **abbobba2 said:**
> resolved with:
[COLOR=#000000][FONT=Ubuntu]
sudo modprobe 8188eu[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]echo '8188eu' | sudo tee -a /etc/modules[/FONT][/COLOR]

being so, please mark your thread as [solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"), so other people searching the forums know that it provides a working solution for the problem.

---

