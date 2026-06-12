---
title: "HP Mini 200 - No Wifi"
date: 2015-09-16
forum: Networking &amp; Wireless
---

### Post by marek21 on 2015-09-16
Hello, recently I installed Ubuntu on my old netbook. Everything works fine but i cant turn on wifi. I tried to install Lubuntu but still theres no wifi. Can you help me please? 
[http://paste.ubuntu.com/12427020/](http://paste.ubuntu.com/12427020/)
[http://paste.ubuntu.com/12418589/](http://paste.ubuntu.com/12418589/)

---

### Post by kerry_s on 2015-09-16
go to "additional drivers" , you need the firmware for the broadcom wifi to work.

when you install, select "third party" & it will install the drivers so when you reboot you will have wifi. install offline, not connected to internet.

i miss my hp-mini 210, it just died on me last week. :(

---

### Post by jeremy31 on 2015-09-16
marek21, the one pastebin link shows network: disabled, can you post the result of ```
rfkill list all
```

---

### Post by MyName_FirstLast on 2015-12-14
(1) Open Terminal (Ctrl-alt-t)
(2) Type: 
sudo modprobe -r b43 ssb wl brcmfmac brcmsmac bcma
[FONT=arial](enter your sudo password when asked)[/FONT]

[FONT=arial](3) Type:
[/FONT]sudo modprobe wl
[FONT=arial]hit enter and enjoy your reactivated wifi chewy goodness. You'll likely have to do this every time you power down and reboot. Might have something to do with the blacklist list.[/FONT]

HP Mini 110-1115CA with Ubuntu 14.04 LTS desktop

---

### Post by Hadaka on 2015-12-14
@MyName_FirstLast...marek21 doesnt have any broadcom cards
please read marek21's printout and the sticky before posting a
suggestion,adding an unusable driver will only create more problems,

---

