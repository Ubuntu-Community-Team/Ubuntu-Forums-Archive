---
title: "Ndiswrapper won't autostart"
date: 2007-10-18
forum: Networking &amp; Wireless
---

### Post by CDNdevil on 2007-10-18
I can't get ndiswrapper to auto start on boot, I blacklisted the open source driver, installed  ndiswrapper & my driver, ran the command ndiswrapper -m, and I have to modprobe ndiswrapper everytime I start my laptop. Oh yeah running gusty.

---

### Post by Oraclegol on 2007-10-18
Once everything works fine you can write the correct modprobe settings to load ndiswrapper automatically when the wlan0 interface is used, by running ndiswrapper -m Note that this doesn’t automatically load ndiswrapper module at boot time. If you want the module to be loaded automatically at boot time, you should configure your module setup, which depends on the distribution. Most distributions will load all modules listed in /etc/modules at boot time

```
sudo gedit /etc/modules
```
and add the word ndiswrapper to the end of this file and save it.
/!\ It is strongly recommended that you make a backup copy of the /etc/modules file before manually editing it.

all with the wonderful help of google :)

---

### Post by dmizer on 2007-10-18
try this:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?#head-6a606ccd9c2c4db72ac726891bd5d7cbaf8097de](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?#head-6a606ccd9c2c4db72ac726891bd5d7cbaf8097de)

---

### Post by CDNdevil on 2007-10-18
Thanks guys, one problem down one more to go.

---

