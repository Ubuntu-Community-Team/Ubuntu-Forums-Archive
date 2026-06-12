---
title: "wlan0 not assigned"
date: 2006-08-05
forum: Networking &amp; Wireless
---

### Post by The Shadow on 2006-08-05
I have a Broadcom wireless network card in my HP dv8000. I made it through all of the ndiswrapper stuff and finally have the driver installed ndiswrapper -l returns "driver present, hardware present"

However when I bring up the network settings tool under the System/applications menu, I only have my standard ethernet card (eth0) and the modem. my wirelss card does not appear. 

Is there a file that I need to edit to identify the wireless card with wlan0? 

lspci does show the Broadcom card.

any suggestions?

---

### Post by Jagot on 2006-08-05
What happens if you run this from terminal:

```
sudo modprobe ndiswrapper
```

---

### Post by The Shadow on 2006-08-05
nothing as far as I can tell. It simply came back to the command line and noting has changed.

I even rebooted the computer afterword

---

### Post by The Shadow on 2006-08-05
x

---

### Post by The Shadow on 2006-08-05
y

---

