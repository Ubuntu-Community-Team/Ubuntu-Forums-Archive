---
title: "HP 14Q CS0009TU, fresh ubuntu 16.04 install wifi not available"
date: 2019-04-13
forum: Networking &amp; Wireless
---

### Post by ngrbrd on 2019-04-13
Wifi option is not available

---

### Post by jeremy31 on 2019-04-13
See the wireless script link in my signature and post results

---

### Post by ngrbrd on 2019-04-13
[http://paste.ubuntu.com/p/xhdznQWzfS/](http://paste.ubuntu.com/p/xhdznQWzfS/)

---

### Post by jeremy31 on 2019-04-13
Go into BIOS and restore the factory Secure Boot keys, likely in system config
Then you can do ```
sudo apt-get install dkms git build-essential
git clone -b extended https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
sudo cp -r rtlwifi_new/firmware/rtlwifi/ /lib/firmware/rtlwifi/
echo "options rtl8723de ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723de.conf
```
Reboot

---

### Post by ngrbrd on 2019-04-13
What does it mean to restore the factory secure boot keys ?

---

### Post by jeremy31 on 2019-04-13
You might have deleted the Secure Boot keys in BIOS instead of just disabling Secure Boot.  My HP has the options in BIOS to delete or restore those keys, the dkms build will likely fail if those keys are missing

---

### Post by ngrbrd on 2019-04-13
There is a 'Load HP Factory Default Keys' option in BIOS but it is disabled. Should i execute the code above ?

---

### Post by jeremy31 on 2019-04-13
Try enabling Secure Boot, then Load HP factory keys, reboot, go into BIOS and disable Secure Boot only, then run the code if results for ```
mokutil --sb-state
```
shows just Secure Boot is disabled, if it also shows platform is in setup mode, dkms might not work

---

### Post by ngrbrd on 2019-04-14
I loaded hp factory keys,
"mokutil --sb-state" shows platform is in setup mode.

I ran dkms commands above. Now Wifi networks appear in Top bar, but it says 'device not ready'

---

