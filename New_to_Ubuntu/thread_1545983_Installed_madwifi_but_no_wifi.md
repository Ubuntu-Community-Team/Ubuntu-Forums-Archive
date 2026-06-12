---
title: "Installed madwifi but no wifi"
date: 2010-08-04
forum: New to Ubuntu
---

### Post by danman33 on 2010-08-04
I followed this guide to install madwifi on my laptop 
[http://ubuntuforums.org/showthread.php?t=1163380](http://ubuntuforums.org/showthread.php?t=1163380)
everything went fine until I finished, rebooted and no i have no wifi
when i run ```
iwconfig
``` i get ```
lo        no wireless extensions.

eth0      no wireless extensions.


```
but when i go system-Administartion-Hardware Drivers it says I have madwifi installed and currently in use 

Please help me
btw im running and atheros AR5001 wifi card

---

### Post by lkraemer on 2010-08-06
We need a little more information:

Just use "copy & paste" for the commands.
And, there is a difference in LSPCI and lspci.
```

uname -r
lspci
lspci -nn
lsusb
lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist.conf
iwconfig
ifconfig

```
Just copy & paste the commands in a Terminal window,
one at a time, and post the results.
(If you are using versions earlier than 9.10, or 9.04 use:
cat /etc/modprobe.d/blacklist)

lk

---

### Post by k3lt01 on 2010-08-06
We really need to know what version of Ubuntu you are using. I was under the impression, from experience with my fathers laptop, that manually installing madwifi isn't actually needed from 9.10 onwards as the required drivers are part of the kernel. I may be wrong but the last version of Ubuntu I used anything madwifi was 9.04 since then wireless has run out of the box.

EDIT: also just check it isn't something simple like the wireless button being accidentally bumped off.

---

### Post by killboymota on 2010-12-28
im having the very same problem with my Acer 5735Z using 10.10. Just got this problem After doing what [this thread]("http://ubuntuforums.org/showthread.php?t=1484242") says. The atheros driver looks gone.

to bring it back just use this command:
modprobe ath9k 

if that one doesnt work just try ath5k. depends of your wifi card driver.

---

