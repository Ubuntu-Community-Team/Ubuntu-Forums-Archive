---
title: "Ubuntu 17.10 HP Envy Realtek RALINK RT3290 WiFi/BT not working after upgrade"
date: 2018-03-24
forum: Networking &amp; Wireless
---

### Post by Anool on 2018-03-24
I upgraded from Ubuntu 16.04 to 17.10 on HP Envy with Core i5 64-bit arch.
Secure Boot is disabled in the BIOS.
I've tried various solutions offered, including the one which seems to have worked for many :

in 
/etc/NetworkManager/NetworkManager.conf
[device]
wifi.scan-rand-mac-address=0

and in
/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
[connection]
wifi.powersave = 2

but without success.

I ran the Wireless debugger script from this thread : [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108) and results are posted at this link :
[http://paste.ubuntu.com/p/7DnKgDrxmT/](http://paste.ubuntu.com/p/7DnKgDrxmT/)

Current status is that under SETTINGS > WIFI , I have a WiFi On/Off button, but it shows as "Firmware Missing".
[ATTACH=CONFIG]279060[/ATTACH]

Any help to get my WiFi/BT up and running is much appreciated.

---

### Post by jeremy31 on 2018-03-24
To get the firmware
```
cd /lib/firmware
sudo wget https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/rt3290.bin
```

Reboot

---

### Post by Anool on 2018-03-24
Thanks a ton!
That was quick and works, although I need to do run the below command after reboot / boot to activate the WiFi. 

```
sudo modprobe rt2800pci nohwcrypt=Y
```


Any way to automate that ?

---

### Post by jeremy31 on 2018-03-24
```
echo "options rt2800pci nohwcrypt=Y" | sudo tee /etc/modprobe.d/rt2800pci.conf
```
Should automate it

---

### Post by Anool on 2018-03-26
That doesn't work. Does the rt2800pci.conf file run automatically upon startup ?
And is there a missing modprobe in it?

PS : I tried both versions with no success
options rt2800pci nohwcrypt=Y
and
options modprobe rt2800pci nohwcrypt=Y

in the rt2800pci.conf file

---

### Post by jeremy31 on 2018-03-26
You need to edit /etc/modprobe.d/blacklist.conf and remove the blacklist rt2800pci and blacklist rt2x00pci

---

### Post by Anool on 2018-03-26
Thanks, works !
Appreciate your help.

---

