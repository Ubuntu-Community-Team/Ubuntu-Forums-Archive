---
title: "Penn State network configuration"
date: 2006-08-16
forum: Networking &amp; Wireless
---

### Post by mengfei on 2006-08-16
Hi there, I'm going up to Penn State, and they require that I register my Ethernet adapter address, as well as change my IP, I believe.

[http://www.rescom.psu.edu/settingup/default.htm](http://www.rescom.psu.edu/settingup/default.htm)

Those are the instructions.

If I were to follow these instructions on the Windows portion of my computer, when I dual-boot into Ubuntu, would it already be ready to go? Or would I have to do this as well in Ubuntu?

And how should I go about doing this?

Thanks.

---

### Post by meng on 2006-08-16
Looks like they want the adapter's MAC address, which will remain the same in Windows or Linux, so you only have to do it the once. If you want to do it in Linux _instead_ of Windows, the command is ifconfig (not ipconfig) from the terminal.

Either 
ifconfig

or
ifconfig eth0
(if eth0 is the device in question)

---

