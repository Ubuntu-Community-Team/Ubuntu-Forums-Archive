---
title: "WIFI powermanagement - set to off"
date: 2015-02-17
forum: Networking &amp; Wireless
---

### Post by chihwah_li on 2015-02-17
$ iwconfig
output: wlan0(rt2800usb)    : connected, power management = on

I changed the power management to disble, value 5 means on, value 1 means off.
$                       sudo vim /etc/default/tlp     
WIFI_PWR_ON_AC=1
WIFI_PWR_ON_BAT=1

But after a reboot I can see with iwconfig that wifi powermanagement is on again.
(edit: I guess, as the tlp config file says, not all WIFI adapters support it.)

A possible fix could be: to automatically execute the following command in a script:
   sudo iwconfig wlan0 power off

But is there not a better, cleaner way to solve this?

---

### Post by chili555 on 2015-02-18
>     But is there not a better, cleaner way to solve this? It depends on how you define better and cleaner!

I suggest you open a terminal and do:```
sudo gedit /etc/rc.local
```Use nano or kate or leafpad if you don't have the text editor gedit. Right above exit 0, add a new line:```
iwconfig wlan0 power off
```Proofread carefully, save and close the text editor.

You should be all set.

---

