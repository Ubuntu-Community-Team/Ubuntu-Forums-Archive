---
title: "wifi disabled by hardware switch after suspend ubuntu 15.10"
date: 2016-04-25
forum: Networking &amp; Wireless
---

### Post by tim153 on 2016-04-25
Hi all,
I have recently installed dual boot ubuntu 15.10 with windows 10 on a HP pavillion laptop. I know there are similar threads on this but my issue seems to be a little different.

Everything works fine when i boot up. When the laptop goes to suspend (when I close it and open it) the wifi is disabled by a hardware switch. the option to enable it is greyed out.

the output of 

```
sudo rfkill list all 
``` is 
```
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```
I have tried 
```
sudo rfkill unblock all
and
sudo rfkill unblock wifi
```
neither work.
I have run the script in this thread [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)[COLOR=#000000] 
[/COLOR]and got this output:
[ATTACH]268628[/ATTACH]

A few more points:
after a restart everything works fine
bluetooth does not work either after a suspend but works fine after a restart.
there are no issues whatsoever with windows
There is NO hardware wifi switch on my machine

Any help would be greatly appreciated!
Tim

---

### Post by lauricat on 2016-04-26
All I can think of, is there some sort of setting in BIOS, and perhaps upgrade BIOS?

HTH

~L

---

### Post by matt198 on 2016-04-26
Tim,

Is there an "Airplane Mode" icon on the HP's F12 key?

Matt

> **tim153 said:**
> Hi all,

There is NO hardware wifi switch on my machine

Tim

---

### Post by tim153 on 2016-04-26
yes there is

---

### Post by tim153 on 2016-04-26
yes there is, i didnt really think of that!
it turns the wifi on and off all right
but it does't work after a suspend

---

