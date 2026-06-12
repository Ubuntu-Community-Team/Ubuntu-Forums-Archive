---
title: "Lubuntu 14 - Wireless Internet - WLAN"
date: 2015-12-04
forum: Networking &amp; Wireless
---

### Post by LudwigM on 2015-12-04
Hello,
I have installed Lubuntu 14.04.1 on an old laptop. Before this, Windows XP was installed. With this operating system the wireless internet worked.
But with Lubuntu I have got some problems. I have tried already different things some time ago, but I could not solve the problem. Now I want to try it again. 
Could somebody give me a good instruction for this?
Or should I upgrade to Lubuntu 15?

Looking forward to your answers
Ludwig

---

### Post by praseodym on 2015-12-04
Hi,

please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

lspci -nnk
pccardctl info
lsusb
lsmod
rfkill list
```

---

### Post by LudwigM on 2015-12-04
see attachements

---

### Post by praseodym on 2015-12-04
Download this file and save it in your home folder:

[http://media-cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz](http://media-cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz)

Installation:
```

sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/
```
Reboot.

---

### Post by LudwigM on 2015-12-05
Thanks for your answer.
The connection does not work yet. But it changed something: the applet in the bottom-right corner shows now the wireless network, which was not the case before. But it says, that the wireless networks are disabled (see attachments). 

Edit: When I type in "nm-applet" to the terminal, it returned "nm-applet-Message: using fallback from indicator to GtkStatusIcon".

How can I activate it?

---

### Post by praseodym on 2015-12-05
Is there a button, switch, key or key combination (e.g. Fn+F3)?

---

### Post by LudwigM on 2015-12-05
It works now ;)
It is the key combination Fn+F2.

Thanks again for your help, praseodym!

---

