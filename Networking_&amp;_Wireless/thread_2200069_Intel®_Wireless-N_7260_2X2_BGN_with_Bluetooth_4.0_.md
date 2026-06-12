---
title: "Intel® Wireless-N 7260 2X2 BGN with Bluetooth 4.0 drivers for ubuntu or Kubuntu"
date: 2014-01-17
forum: Networking &amp; Wireless
---

### Post by Thaitransit on 2014-01-17
I have a Lenovo Thinkpad Edge E540 (20C6002SAU) notebook that has wifi and bluetooth problems after installing Ubuntu 12.04 LTS. 

The issue is after installing ubuntu or Kubuntu on this machine I could not connect to my wifi network. It appears ubuntu could not see my Intel® Wireless-N 7260 2X2 BGN with Bluetooth 4.0 wifi card that is installed inside my notebook. Only the Wired Lan was working.

The question I ask is this problem related to no current Ubuntu / Kubuntu drivers for this hardware?

If so where would I be able to locate drivers for the Intel® Wireless-N 7260 2X2 BGN with Bluetooth 4.0 card?

If they do exisit how would i install the drivers onto my notebook?

Thanks for the help

---

### Post by chili555 on 2014-01-17
Please get a temporary wired ethernet connection. Open a terminal and install the prerequisites:```
sudo apt-get install linux-headers-generic build-essential
```Download this file to your desktop: [http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.12/backports-3.12-1.tar.bz2](http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.12/backports-3.12-1.tar.bz2) Right-click it and select 'Extract Here.' Now back to the terminal:```
cd ~/Desktop/backports-3.12/
make defconfig-iwlwifi
make
sudo make install
```Now you need the latest firmware package:```
cd /lib/firmware
sudo wget https://git.kernel.org/cgit/linux/kernel/git/egrumbach/linux-firmware.git/plain/iwlwifi-7260-7.ucode
```Reboot and tell us if your device is working as expected.

---

### Post by Leslie Viljoen on 2014-06-03
Any news on this? Did you get it working?
Does the network card work properly with Ubuntu 14.04?

---

### Post by chili555 on 2014-06-03
The driver and firmware are installed by default in 14.04. There are some reports of dropping. Whether this is a large or small percentage of users is unknown to me.

---

### Post by Leslie Viljoen on 2014-06-05
The very friendly folks at Eden Terrace [http://www.justlaptops.net.nz](http://www.justlaptops.net.nz) in Auckland let me boot Ubuntu Gnome on this laptop in their shop to try it out. 
This is for the Lenovo Thinkpad Edge E540 (20C6002SAU).

In my basic tests everything worked fine:
[FONT=arial]- Basic VGA (didn't try external monitors or verify which GPU was running)[/FONT]
[FONT=arial]- Microphone[/FONT]
[FONT=arial]- Camera[/FONT]
[FONT=arial]- Keyboard special keys (nice expanded keyboard layout)[/FONT]
[FONT=arial]- Wifi (could see other networks, so likely works)[/FONT]
[FONT=arial]- Sound[/FONT]
[FONT=arial]
There's a known issue there the fan doesn't slow down again after it has spun up for a high CPU load. I stressed the 8 cores and got the fan up to speed. Once I took the load off the fan didn't seem to slow. So the fan problem does seem to be there - though the fan is very quiet so I would not be annoyed by it running continually. I suppose that's a small power drain, I don't know.[/FONT]
[FONT=arial]
That was as far as I could go with a live CD in the shop.

[/FONT]

---

