---
title: "Disabling wifi power management Dell vostro 14-5480"
date: 2015-11-24
forum: Networking &amp; Wireless
---

### Post by heruvim2 on 2015-11-24
**Problems:**

  1) Power management makes Wifi connection unstable. I need to disable it completely
2) My wifi doesn't automatically turns on after sleep. I should do it myself

  **Info**

  Laptop:      Dell vostro 14-5480
OS:          Ubuntu 15.04
kernel:      3.19.0-30
Wifi-card:   Intel 7265
Wifi-driver: iwlwifi

  **What i've tried**

  "iwconfig wlan0 power off" helps but I should do it every time my  Laptop turns on. I tried to play with /etc/pm. Nothing helped. The only  solution was adding 
  ```

[INDENT]sleep 10
[/INDENT]
[INDENT]  iwconfig wlan0 poweroff
exit 0 
[/INDENT]

```  to /etc/rc.local. Now power management turns off, as I need, but only  when I reboot/switch on laptop. If I turn my wifi on manually after  suspend, I should also manually turn off power management.
  I thought maybe [13.10 suspend kills wifi connection]("http://askubuntu.com/questions/365441/13-10-suspend-kills-wifi-connection")  solution might help, I made a file wakenet.sh, but it doesn't work and  it shouldn't as ubuntu 15.04 doesn't have nmcli nm, so it's impossible  to use 
```
[INDENT]nmcli nm sleep flase
[/INDENT]

``` 
At least I haven't found how to do it with new nmcli.

---

