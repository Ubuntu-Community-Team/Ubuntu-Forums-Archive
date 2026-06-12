---
title: "Bluetooth GUI switch does not work after upgrade to 17.10"
date: 2017-12-03
forum: Networking &amp; Wireless
---

### Post by safire on 2017-12-03
I've recently upgraded from 17.04 to 17.10. On my HP Spectre x360 bluetooth used to work without any issues under 17.04.

After the upgrade i see the following:
1. the bluetooth switch in UI settings is not working. I switch it on, but nothing happens. When i reopen the bluetooth settings window, it shows OFF again
2. i run 
```
root@chirkov-f:/home/andrey# rfkill list
0: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

``` 
3. then i do unblock
```

root@chirkov-f:/home/andrey# rfkill unblock 0
root@chirkov-f:/home/andrey# rfkill list
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```
4. i check the UI - now it's ok, it works
5. i try to turn bluetooth off in UI - it does not

I know i can put rfkill unblock into rc.local, but is there any better option to fix this?

---

