---
title: "Ubuntu no Wifi adapter found - suddenly stopped recognising - Acer Aspire F 15"
date: 2019-08-10
forum: Networking &amp; Wireless
---

### Post by lemonymelon on 2019-08-10
Hey folks! I'm running Ubuntu 18.04.2 on an Acer Aspire F 15 - F5-573G-58GV. The wifi was working fine earlier; it was in standby and then when I booted it back up, the wifi adapter was no longer recognised. I've rebooted AND tried running

sudo apt-get install --reinstall bcmwl-kernel-source

then

sudo modprobe wl

as per this thread: [https://ubuntuforums.org/showthread.php?t=1967515](https://ubuntuforums.org/showthread.php?t=1967515)

...to no avail.

Can anyone help?

**EDIT: I've just noticed it's not recognising that I have a bluetooth adapter installed either. I was definitely using wifi and bluetooth this afternoon.**

---

### Post by chili555 on 2019-08-10
Are you quite certain that you have the same Broadcom device? Please run and post:

```
lspci -nnk | grep 0280 -A3
rfkill list all
```

---

### Post by lemonymelon on 2019-08-10
Neither of those yielded anything. :/

But no, I don't think I do, actually. I'm very much noobing my way through this. Apparently this model comes with [COLOR=#444444][FONT=arial]Qualcomm Atheros [/FONT][/COLOR][COLOR=#444444][FONT=arial]NFA435A, if that helps.

[/FONT][/COLOR][https://www.technoworld.com/acer-aspire-f5-573g-58gv-2-5ghz-i5-7200u-15-6-1920-x-1080pixels-black-nx-gd6ek-009](https://www.technoworld.com/acer-aspire-f5-573g-58gv-2-5ghz-i5-7200u-15-6-1920-x-1080pixels-black-nx-gd6ek-009)

---

### Post by jeremy31 on 2019-08-10
If those commands reveal nothing I would recommend shutting it down, remove bottom panel, and remove and reinsert wifi card and see if it works again

---

### Post by lemonymelon on 2019-08-10
OK, cool, shall do. Cheers!

---

### Post by lemonymelon on 2019-08-10
Well, I took the bottom panel, couldn't find it, took the rest off, still couldn't see it, put everything back and now it works. Win?

Cheers, folks! Much appreciated.

---

