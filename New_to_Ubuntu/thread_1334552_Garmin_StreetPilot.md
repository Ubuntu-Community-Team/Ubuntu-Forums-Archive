---
title: "Garmin StreetPilot"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by my2009ch on 2009-11-22
I would like to use Garmin Web Update on Ubuntu (I have the software running on WINE already), but when I plug my StreetPilot c580 into the USB port on my computer, Ubuntu does not do anything in terms of recognising or even acknowledging that I plugged it into my computer. Is there any way i can get the GPS unit recognised? I'm running Ubuntu 9.10.

---

### Post by cariboo on 2009-11-28
Inserting the garmin module dtects my gps:

```
sudo modprobe garmin_gps
```

---

