---
title: "Wifi unstable with latest 8.10 kernel"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by Tony Flury on 2009-01-30
I have in the last day or so uploaded 2.6.27-11 (the latest 8.10 kernel)

Coincident with this i have noticed a marked degradation in the stability of my wifi network - including dropping wifi connections,  reprompting for network keys (despite the fact it will mostly always connect automatically on start up - without prompting).

Has anyone else noticed this on 2.6.27-11

---

### Post by avtolle on 2009-01-30
No, I haven't. Which wifi card do you have?

---

### Post by smothpocket on 2009-01-30
I have a broadcom card and had some minor issues using the drivers from the restricted driver manager. I removed those and installed these [http://linuxwireless.org/en/users/Drivers/b43#firmwareinstallation](http://linuxwireless.org/en/users/Drivers/b43#firmwareinstallation) and it's been working great ever since... hope this helps :)

---

### Post by Tony Flury on 2009-01-30
i have a belkin fd50751 ... It is fine under the previous Kernel.

Just very odd that is all.

---

### Post by sandyd on 2009-01-30
many prople have problems with this...

ubuntu has a major problem with is kernel

it uses the highest bitrate possible, which is really unstable....

so ......

adjust the bitrate with this command
```

sudo iwconfig eth2 rate 5.5M fixed
```

you can change the maximum bitrate i set there, but this seems to be the most stable so far.
also, you will have to change the device name from "eth2" to your wirless card name

---

