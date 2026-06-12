---
title: "how do i know if i have an eth0 or an eth1 please??"
date: 2011-01-26
forum: New to Ubuntu
---

### Post by cheekymonky2010 on 2011-01-26
Could anyone please tell me how to recognise the type of eth connection I have so that I can attempt to configure Ushare correctly for the Xbox to work through my tv please???

---

### Post by Frogs Hair on 2011-01-26
Mine is displayed when I select the computer icon from the notification area applet on Gnome panel .
It can also be found by using the nework icon on the menu.

---

### Post by cjazz on 2011-01-26
Or, from the commandline, you can get this and other information using either the command "tpconfig" (from the package tpconfig), "iwconfig" (from the package wireless-tools) or "ifconfig" (from the package "net-tools, which was installed by default on my desktop system).

---

### Post by cheekymonky2010 on 2011-01-26
Cool thanks a lot! I,m guessing that is what I need to configure the Xbox?

---

### Post by amsterdamharu on 2011-01-26
To see your active network connections you can use the following command:

```
ifconfig
```

To execute the command(s) you can press alt + F2, type gnome-terminal  and click run. Then copy one command and paste it in the terminal (black  screen that showed up after you clicked run). Use the mouse to paste  commands in the terminal.
I have no experience with streaming video and or music to xbox but found some sites:

[http://www.themanfromdelmonte.co.uk/2010/02/09/stream-video-to-xbox-360-from-ubuntu-with-ushare/](http://www.themanfromdelmonte.co.uk/2010/02/09/stream-video-to-xbox-360-from-ubuntu-with-ushare/)

Basically you need to install ushare with the following command:
```
sudo apt-get install ushare
```

To edit the config files I'd recommand doing it the following way: press alt + F2 and type "gksu gedit /etc/ushare.conf" (no quotes) then click run.

---

