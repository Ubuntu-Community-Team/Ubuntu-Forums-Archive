---
title: "Asus EEE PC 1225c wi-fi adapter hard blocked"
date: 2016-11-22
forum: Networking &amp; Wireless
---

### Post by alexnikolaev94 on 2016-11-22
I've got Asus EEE PC 1225c laptop and I tried to install several Linux distros, among them Ubuntu/Lubuntu 16.04, Arch Linux and Manjaro Linux XFCE 16.07. Every distro returned me the same problem - my wi-fi adapter was blocked and I was unable to unblock it. The output of ```
rfkill list
``` command returned me the following:
```

[COLOR=#000000][FONT=-apple-system]0: asus-wlan: Wireless LAN[/FONT][/COLOR]
[COLOR=#000000][FONT=-apple-system]  Soft blocked: no[/FONT][/COLOR]
[COLOR=#000000][FONT=-apple-system]  Hard blocked: no[/FONT][/COLOR]
[COLOR=#000000][FONT=-apple-system]1: asus-wimax: WiMAX[/FONT][/COLOR]
[COLOR=#000000][FONT=-apple-system]  Soft blocked: no[/FONT][/COLOR]
[COLOR=#000000][FONT=-apple-system]  Hard blocked: no[/FONT][/COLOR]
[COLOR=#000000][FONT=-apple-system]2: phy0: Wireless LAN[/FONT][/COLOR]
[COLOR=#000000][FONT=-apple-system]  Soft blocked: no[/FONT][/COLOR]
[COLOR=#000000][FONT=-apple-system]  Hard blocked: yes[/FONT][/COLOR]

```
Pressing Fn+F2 buttons that are supposed to switch the wi-fi adapter on returned only toggling software block in ```
asus-wlan
``` and ```
phy0
```, but not did no effect on the hardware block of the adapter. After some research in Google on this problem I tried to add command ```
blacklist asus-wmi
``` to ```
/etc/modprobe.d/blacklist.conf
```, but it did no effect either. Currently I'm running Windows 7 on the laptop and the hotkey Fn+F2 works as is expected and toggles wi-fi adapter block both on the hardware and on the software level. The official Asus technical support responded me that they cannot suggest me anything because Asus announced that it stopped to support Linux on their devices in 2008. Is there any way to handle this? Thanks

---

### Post by howefield on 2016-11-22
Thread moved to the "*Networking & Wireless*" forum for a better fit.

---

### Post by chili555 on 2016-11-22
> After some research in Google on this problem I tried to add command
Code:
blacklist asus-wmi
to
Code:
/etc/modprobe.d/blacklist.confI suggest that you undo this. Next, please check here:  [http://askubuntu.com/questions/499881/cant-connect-to-any-wi-fi-on-asus-x550c-in-ubuntu-14-04/499903#499903](http://askubuntu.com/questions/499881/cant-connect-to-any-wi-fi-on-asus-x550c-in-ubuntu-14-04/499903#499903)

---

