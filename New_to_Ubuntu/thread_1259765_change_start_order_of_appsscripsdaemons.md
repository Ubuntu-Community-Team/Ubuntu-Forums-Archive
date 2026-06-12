---
title: "change start order of apps/scrips/daemons"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by LeChacal on 2009-09-06
OK so I just bought and installed an APC UPS so I also installed apcupsd to manage it, the UPS is connected to my PC via USB. Problem starts because I have to run a scrip to get my mouse drives loaded properly or it wont work and my USB keyboard also wont work. The script that loads my mouse driver is:

```
#!/bin/bash
sudo rmmod usbhid
sudo rmmod lmpcm_usb
sudo modprobe lmpcm_usb
sudo modprobe usbhid
numlockx on
```

The whole point of this script is so that "lmpcm_usb" (special mouse driver) is loaded before "usbhid" (general USB driver need for keyboard and also by apcupsd), and to turn number lock on but that isn't the problem right now. Apcupsd starts under run levels 2,3,4,5 and when it starts it locks the "usbhid" module so that my script can't unloaded it and since it starts before I run my script my script runs unsuccessfully. I currentaly have my script started by "Startup Applications" in the preferences menu. My question is how do make my script run before apcupsd or what can I do to fix my problem? I have tried have my script stop apcupsd and then restart it at the end of the script but that didn't work.

---

### Post by LeChacal on 2009-09-07
OK so I had the idea that I would just add my script to the default run levels and have it positioned to start before apcupsd. After doing this my mouse works but now it looks like the apcupsd is not working properly.

---

