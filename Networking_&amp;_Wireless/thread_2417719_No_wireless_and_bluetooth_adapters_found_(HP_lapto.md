---
title: "No wireless and bluetooth adapters found (HP laptop)"
date: 2019-04-26
forum: Networking &amp; Wireless
---

### Post by lammer1t00 on 2019-04-26
Hi everyone.

I use Ubuntu 18.04.1 LTS on a laptop HP Envy-x360.

It was broken at february (water damage of motherboard). Yesterday I picked it up from computer service (Sales man told that it's working).
After comng home I realized that Wi-Fi settings menu says "No Wi-Fi Adapter Found"... the same with Bluetooth.

Whole day I spent  trying to find appropriate adapters... unfortunatelly i didn't.

'sudo lshw -C network ' command isn't listing that drivers (looks like they aren't set on machine).
Because I haven't any network connection, it's not possible to make update and upgrade of system and its kernel.

I followed this [https://ubuntuforums.org/showthread.php?t=2082305&p=12350385&viewfull=1#post12350385](https://ubuntuforums.org/showthread.php?t=2082305&p=12350385&viewfull=1#post12350385) post and find out it helpfull. The thread is already closed, but still actual.
Here [https://pastebin.ubuntu.com/p/5fgGv9w9j2/](https://pastebin.ubuntu.com/p/5fgGv9w9j2/) is my output wireless-info. txt file.

Please if you can say any helpful information based on that output text file - tell me what is the core of problem, and maybe how to fix it.

Thank You.

---

### Post by praseodym on 2019-04-27
Please show

```
lspci -nnk
cat /sys/bus/sdio/devices/*
cat /sys/bus/sdio/devices/*/uevent
```

---

### Post by lammer1t00 on 2019-04-27
Thank you. 
Sure, here [https://pastebin.ubuntu.com/p/QKStQ65Gjw/](https://pastebin.ubuntu.com/p/QKStQ65Gjw/)

---

### Post by jeremy31 on 2019-04-27
I think you need to complain to the service about the wifi not working

---

### Post by lammer1t00 on 2019-05-02
Thank You. Done... I wish they will fix it fast

---

