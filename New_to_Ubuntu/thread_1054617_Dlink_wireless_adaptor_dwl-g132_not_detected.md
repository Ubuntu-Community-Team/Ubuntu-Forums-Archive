---
title: "Dlink wireless adaptor dwl-g132 not detected"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by jsmakkar on 2009-01-29
I am a newbie and just downloaded Ubuntu and installed on my PC.
I am disappointed because my **Dlink Wireless Adaptor DWL-G132 is not detected**. I do have the driver but that is useless until my device is detected.
Could anybody help me with that please!

Thank you.

---

### Post by Crafty Kisses on 2009-01-29
First you may want to grab these packages first:
```
sudo apt-get install ndiswrapper
sudo apt-get install build-essential
```
Once you have those packages installed, grab the driver right here: [ftp://ftp.dlink.com/Wireless/dwlg132/Driver/dwlg132_drivers_121.zip](ftp://ftp.dlink.com/Wireless/dwlg132/Driver/dwlg132_drivers_121.zip). Once you have downloaded that, save it to your desktop than extract it to your desktop:
```
tar zxvf /home/username/Desktop/drivername
```
Once it's extracted, navigate to the "Drivers" folders, make sure everything is in there that's needed including the .inf file, and run these commands:
```
sudo ndiswrapper -i athfmwdl.inf
sudo ndiswrapper -i NetA5AGU.inf
sudo depmod -a
sudo modprobe ndiswrapper
```
Then from there you need to edit this file to make sure the kernel loads the ndiswrapper module at the start:
```
sudo gedit /etc/modules
```
Just add the following line at the bottom:
```
ndiswrapper
```
Then save it, then you should be set and your card should work.

---

### Post by jsmakkar on 2009-01-29
[COLOR="Blue"][B][I][B]Thanks a lot for the detailed information.
Well as I said I am a beginner, could you tell me where would I type the above codes. I really want to use Ubuntu.

Thanks[/B][/I][/B][/COLOR]

---

### Post by Crafty Kisses on 2009-01-30
You would type these commands in the Terminal. **Applications->Accessories->Terminal.** For more information on the Terminal please read the following: [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal).

---

