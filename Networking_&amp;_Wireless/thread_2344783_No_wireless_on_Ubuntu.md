---
title: "No wireless on Ubuntu"
date: 2016-11-28
forum: Networking &amp; Wireless
---

### Post by mbolman on 2016-11-28
Hello,

I'm new to Linux, I'd like to give it a try.
I can't connect to a wireless network. Clicking on the network icon (top-right) there's no option for wireless, just the wired network.
There is also no "Enable wireless" button.
If I click "Edit connections" the wireless network is visible though.
Chipset: RTL 8192cu
Ubuntu: 16.10
(It works fine with Windows and other mobile devices).

---

### Post by jeremy31 on 2016-11-28
Welcome to the forums
Please see the wireless script link in my signature and post your results

---

### Post by mbolman on 2016-11-28
> **jeremy31 said:**
> Welcome to the forums
Please see the wireless script link in my signature and post your results

Thanks for the quick reply, I've added the file.

---

### Post by mbolman on 2016-11-29
Update:
After reboot, I suddenly have connection to wifi, although it is painfully slow.

---

### Post by jeremy31 on 2016-11-29
Run ```
./wireless-info
```
when the wireless is working.  Did you get this code from [https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes)

---

### Post by mbolman on 2016-12-02
> **jeremy31 said:**
> Run ```
./wireless-info
```
when the wireless is working.  Did you get this code from [https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes)

./wireless-info : No such file or directory.

I did follow the instructions in the readme from the above link, not much difference. Still realy slow, up to the point where there is no connection at all.

---

### Post by jeremy31 on 2016-12-02
Just use the wireless script link in my signature again.  It might be power management related

---

### Post by mbolman on 2016-12-05
> **jeremy31 said:**
> Just use the wireless script link in my signature again.  It might be power management related

I ran the script again, here&#347; the result:
[ATTACH=CONFIG]272556[/ATTACH]

---

### Post by jeremy31 on 2016-12-05
Do you have secure boot enabled as it doesn't appear that a driver loaded for the wifi?

---

