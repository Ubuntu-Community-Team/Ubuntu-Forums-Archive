---
title: "Ubuntu 14.04 LTS x64 on HP Envy 15t q400 laptop shows no wi-fi (Intel)"
date: 2016-01-13
forum: Networking &amp; Wireless
---

### Post by Bill_Pairaktaridis on 2016-01-13
This is a fresh installation and wi-fi has not been working from the get-go. It is an Intel chip and Bluetooth and Ethernet work fine.

Update: Adapter seems to be Intel Dual Band Wireless-AC 3165

---

### Post by Hadaka on 2016-01-13
Hi, from a working wired connection please copy and paste..
```
sudo apt-get update
sudo apt-get dist-upgrade #does NOT upgrade to next load
```
then do..
```
sudo iw reg set GR
sudo sed -i 's/^REG.*=$/&GR/' /etc/default/crda
```
boot,remove wired connection test wireless.
your wireless report also showed..
```
[   14.398788] iwlwifi 0000:08:00.0: Unsupported splx structure
[   14.564966] iwlwifi 0000:08:00.0: Direct firmware load for iwlwifi-3165-12.ucode failed with error -2
[   14.582667] iwlwifi 0000:08:00.0: Direct firmware load for iwlwifi-3165-11.ucode failed with error -2
[   14.582680] iwlwifi 0000:08:00.0: Direct firmware load for iwlwifi-3165-10.ucode failed with error -2
[   14.582682] iwlwifi 0000:08:00.0: request for firmware file 'iwlwifi-3165-10.ucode' failed.
[   14.582689] iwlwifi 0000:08:00.0: Direct firmware load for iwlwifi-3165-9.ucode failed with error -2
[   14.582690] iwlwifi 0000:08:00.0: request for firmware file 'iwlwifi-3165-9.ucode' failed.
[   14.582691] iwlwifi 0000:08:00.0: [COLOR=#ff0000][/COLOR][COLOR=#ff0000]no suitable firmware found ![/COLOR][COLOR=#000000][/COLOR][COLOR=#ff0000][/COLOR]

```
*IF the update/upgrade didnt solve the issue...then go here.
[http://ubuntuforums.org/showthread.php?t=2296254](http://ubuntuforums.org/showthread.php?t=2296254)
Posts #6 & 7
thanks.

---

### Post by jeremy31 on 2016-01-13
Try ```
sudo cp /lib/firmware/iwlwifi-7265D-12.ucode /lib/firmware/iwlwifi-3165-12.ucode
```
Reboot

---

### Post by Bill_Pairaktaridis on 2016-01-15
> **jeremy31 said:**
> Try ```
sudo cp /lib/firmware/iwlwifi-7265D-12.ucode /lib/firmware/iwlwifi-3165-12.ucode
```
Reboot

Jeremy's solution worked for me! Thanks!

---

