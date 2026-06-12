---
title: "Wireless Switch does nothing"
date: 2008-08-15
forum: Networking &amp; Wireless
---

### Post by niccholaspage on 2008-08-15
First of all,I used ndiswrapper to get my wireless connection working with Ubuntu.Whenever I switch off my wireless switch,Nothing happens at all.I can still connect to networks.I don't know if this will still happen if I reboot the computer,Haven't tried.

---

### Post by olejorgen on 2008-08-16
No idea if this works with all cards, but this is my note on how do kill wlan:
```

## kill wlan completely
# kill
for i in `find /sys -name "rf_kill" ; do echo 1 > $i ; done
# resurrect
for i in `find /sys -name "rf_kill" ; do echo 0 > $i ; done

```

That the switch doesn't work might be some strange hardware detection problem. If you want to investigate further you could run
```

dbus-monitor

``` and ```
 dbus-monitor --system 
```
press the kill switch and see if get any sensible output

---

### Post by niccholaspage on 2008-08-20
BUMP

This is VERY strange.Ubuntu Detects that I switch it to the right but NOT to the left.

---

