---
title: "Ubuntu 17.10 connects to network but can't ping router or connect to Internet."
date: 2017-11-05
forum: Networking &amp; Wireless
---

### Post by yamnick on 2017-11-05
I recently installed ubuntu 17.10 on my PC and it seems to have a problem with network connection. It connects to network however I can't reach Internet or even router. Windows on the same PC and Ubuntu 16.04 which was installed before worked without a hitch, but with 17.10 the issue appeared already during installation from USB stick. It also doesn't work when launching from USB stick. To make it more more frustrating sometimes it does connect properly but stops working again after reboot.

So far I tried some solutions (DNS change to 8.8.8.8, wifi.scan-rand-mac-address=no)I found for similiar problems, but so far nothing helped. I wanted to give you guys my output from wireless-info but it seems I'm doing something wrong as it's not working and all I get is:

```
: No such file or directoryinfo: line 1: &#271;»&#380;#!/bin/bash
/home/jan/Desktop/wireless-info: line 27: $'\r': command not found
/home/jan/Desktop/wireless-info: line 32: $'\r': command not found
/home/jan/Desktop/wireless-info: line 38: $'\r': command not found
/home/jan/Desktop/wireless-info: line 43: $'\r': command not found
/home/jan/Desktop/wireless-info: line 48: $'\r': command not found
/home/jan/Desktop/wireless-info: line 52: $'\r': command not found
/home/jan/Desktop/wireless-info: line 57: syntax error near unexpected token `elif'
'home/jan/Desktop/wireless-info: line 57: `elif [ -x /usr/bin/zenity ]; then

``` 

Any help would be appreciated.

---

### Post by yamnick on 2017-11-06
Bump.

---

