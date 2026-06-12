---
title: "Set critical power level?"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by JohnnyCbad on 2009-07-24
Hi,
I'm using Xubuntu 9.04 and would like to change my critical power level to something like 10% as currently the laptop is running out of power before it shuts down, how can I do this?
Thanks in advance!

---

### Post by swoll1980 on 2009-07-25
```
sudo gedit /etc/laptop-mode/laptop-mode.conf
```


"Disable all data loss sensitive features"-option when the battery level to 10%

just change the 10% to whatever you want. If you're using Xbuntu it might not have gedit, so try ```
sudo mousepad /etc/laptop-mode/laptop-mode.conf
``` instead I think xubuntu uses mousepad.

---

