---
title: "Wifi with Intel N6235 stopping to work after a while"
date: 2019-01-14
forum: Networking &amp; Wireless
---

### Post by stefano-fornari on 2019-01-14
Hi all,

I hope somebody can help with this. I do not know what else to do after trying many things read on the net. I have an intel NUC with a miniPCI wifi card N6235. After boot the wifi works for a while until it suddenly stops working. When it happens, ifconfig does not even show the wireless device. If I reboot it works again... :(

Result of the info script:

[http://paste.ubuntu.com/p/7RqyZ6nx3c/](http://paste.ubuntu.com/p/7RqyZ6nx3c/)

Thank in advance,
Stefano

---

### Post by jeremy31 on 2019-01-14
See chili555's advice at [https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520](https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520)
I think the first command will fix the issue, read more on that post for some tweaks

---

### Post by stefano-fornari on 2019-01-14
thanks for the quick reply. I have done what stated in the post, but nothing changed. it still goes away after a while and I have to reboot.

any help is very appreciated.

stefano

---

### Post by jeremy31 on 2019-01-14
Open a terminal, enter ```
tail -f /var/log/syslog
```
See what is happening when the issue occurs

---

### Post by stefano-fornari on 2019-01-15
Here is what I grabbed in the console. I think there is something interesting, but let me know if you need more past log.

[https://paste.ubuntu.com/p/GTRsxnmV34/](https://paste.ubuntu.com/p/GTRsxnmV34/)

Ste

---

### Post by jeremy31 on 2019-01-16
See if there are any options for ASPM in BIOS

---

### Post by stefano-fornari on 2019-01-18
Yes, it was enabled. shall I try disabling it?

---

### Post by jeremy31 on 2019-01-18
I would try it

---

### Post by stefano-fornari on 2019-01-18
Cool! it seems to work! Thank you very much!

ste

---

