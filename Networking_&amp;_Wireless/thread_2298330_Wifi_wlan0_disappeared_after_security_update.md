---
title: "Wifi wlan0 disappeared after security update"
date: 2015-10-10
forum: Networking &amp; Wireless
---

### Post by dofin on 2015-10-10
Hi,

After an automatic update, my WiFi has disappeared. No more icon in the system bar (next to the clock), no Wireless item anymore in the GUI for network settings and nothing listed with iwconfig (in a terminal).
Several reboots later, the system bar icon came back, but it said WiFi disabled. Typing Fn+F2 (the shortcut for physical wifi (de-)activation on my laptop) didn't help.

I've been able to solve it thanks to @chili555 's posts in a related thread: [http://ubuntuforums.org/showthread.php?t=2239747](http://ubuntuforums.org/showthread.php?t=2239747)

For me, [FONT=courier new]rfkill list all[/FONT] (in a terminal) gave[INDENT]0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
[/INDENT]
and after activating the "hardware" (i.e. keyboard Fn+F2) switch, it gave[INDENT]0: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
[/INDENT]
So soft and hard blocking somehow went out of sync.

The solution was to run [FONT=courier new]rfkill unblock wlan[/FONT] when Hard block is "no". Wifi was then available again.

Hope this can help someone else

---

### Post by jeremy31 on 2015-10-10
What Brand and model computer?

---

### Post by dofin on 2015-10-13
On a Dell XPS laptop (14", model from 2013)

In between, I totally lost the wifi again (no results on [FONT=courier new]rfkill list all[/FONT]). Seems linked with a kernel update to 3.13.0-65.106 last week.
I'll ask for some help in another thread

---

### Post by kenneth20 on 2016-03-02
I will be performing steps tonight I will let you know if I have issues. Thanks

---

