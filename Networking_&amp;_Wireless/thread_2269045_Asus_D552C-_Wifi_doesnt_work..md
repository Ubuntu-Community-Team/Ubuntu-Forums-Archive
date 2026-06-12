---
title: "Asus D552C- Wifi doesnt work."
date: 2015-03-13
forum: Networking &amp; Wireless
---

### Post by ehood2 on 2015-03-13
[SOLVED]
I installed ubuntu on my computer, and the wifi doesn't work at al,
only if connect my phone with usb (and enable the data transfer )I can acsses the Internet.
Any ideas why? and how to fix it?
It's appear that there isn't a driver for my network card.
 
SOLVED USING THAT DRVIVER:[https://github.com/kuba-moo/mt7630e](https://github.com/kuba-moo/mt7630e)

---

### Post by Hulk_Joshua on 2015-03-13
try the answers on this thread [http://askubuntu.com/questions/425155/my-wireless-wifi-connection-does-not-work-what-information-is-needed-to-diagnos](http://askubuntu.com/questions/425155/my-wireless-wifi-connection-does-not-work-what-information-is-needed-to-diagnos)

---

### Post by ehood2 on 2015-03-22
Didnt work, any other ideas?

---

### Post by wildmanne39 on 2015-03-22
You were suppose to run the wireless script in that post and attach the file here so we can look at it.

It is also in my signature and you will find it in the sticky at the top of the networking forum.
Thanks

---

### Post by ehood2 on 2015-03-29
the file -  			 			
thanks

---

### Post by wildmanne39 on 2015-03-29
We need to install a driver coopy and paste one line at a time for accuracy:
```
sudo apt-get install build-essential linux-headers-generic git
git clone https://github.com/lwfinger/mt7630.git
cd mt7630
make
sudo make install
```
Every time there is an update to the kernel you  will have tp rebuild the driver like this:
```
cd ~/mt7630
make clean
make
sudo make install
```
Thanks

---

### Post by ehood2 on 2015-03-29
first, thank you for the help.
but it didnt work.
here if the file after I did the instruction above.

---

### Post by wildmanne39 on 2015-03-29
Reboot and see if the driver loads.
Thanks

---

### Post by ehood2 on 2015-03-30
I rebooted severl times. still doesnt work. 
Any idea?
thanks.

---

### Post by wildmanne39 on 2015-03-30
Did you get any errors when you compiled the driver?

---

### Post by ehood2 on 2015-03-30
I belive so. I dont remember, but there was a few warnings for sure.

---

### Post by wildmanne39 on 2015-03-30
It sounds like the driver failed to compile, warniings are allowed but one error and it failed. 
That is all I know to do.

---

### Post by ehood2 on 2015-03-31
thanks for the help.
Anyway do you know who I can ask more on this subject?

---

### Post by wildmanne39 on 2015-03-31
You really do not need to ask anyone, if someone knows how to get it working they will reply, just bump your thread about once every 24 hours to keep it on the top.

---

### Post by ehood2 on 2015-03-31
how do I "bump" my thread?

---

### Post by wildmanne39 on 2015-03-31
Just reply with bump!

---

### Post by ehood2 on 2015-04-01
I found some drive that should support my NIC. and the new kernel.
I belive that that last driver I installed works only on 3.14.
In here[https://github.com/tobiasBora/MT7630E_3.16](https://github.com/tobiasBora/MT7630E_3.16)
but since I already install the previous drive i get errors that some files already exsits.
I tried unistalling it, with second set of command in comment 6, but it's appears to not work.
any other way to uninstall it?

---

### Post by wildmanne39 on 2015-04-01
Just run these two commands that should remove anything that remains.
```
cd ~/mt7630
make clean
```
I asked the master of wireless to take a look but in all my research I did not find any working devcies that was reproduce by a second person.

---

### Post by ehood2 on 2015-04-01
this what i get when i load the driver:
ehood@ehood-ubuntu:~$ cd /home/ehood/Downloads/MT7630E_3.16-master
ehood@ehood-ubuntu:~/Downloads/MT7630E_3.16-master$ make load
sudo cp firmware/Wi-FI/MT7650E234.bin /lib/firmware/
[sudo] password for ehood: 
cd rt2x00 && make
make[1]: Entering directory `/home/ehood/Downloads/MT7630E_3.16-master/rt2x00'
make -C /lib/modules/3.13.0-48-generic/build M=/home/ehood/Downloads/MT7630E_3.16-master/rt2x00 modules
make[2]: Entering directory `/usr/src/linux-headers-3.13.0-48-generic'
  Building modules, stage 2.
  MODPOST 12 modules
make[2]: Leaving directory `/usr/src/linux-headers-3.13.0-48-generic'
make[1]: Leaving directory `/home/ehood/Downloads/MT7630E_3.16-master/rt2x00'
Wifi driver has been compiled successfully.
cd rt2x00 && sudo ./unload_wifi.sh; true
rmmod: ERROR: Module crc_ccitt is in use by: rt2800lib
rmmod: ERROR: Module mac80211 is in use by: rt2x00lib rt2800lib
rmmod: ERROR: Module cfg80211 is in use by: mac80211 rt2x00lib
rmmod: ERROR: Module rt2800pci is not currently loaded
rmmod: ERROR: Module rt2x00mmio is not currently loaded
rmmod: ERROR: Module rt2x00pci is not currently loaded
Wifi has been successfully unloaded.
cd rt2x00 && sudo ./load_wifi.sh
insmod: ERROR: could not insert module /lib/modules/3.13.0-48-generic/kernel/lib/crc-ccitt.ko: File exists
insmod: ERROR: could not insert module /lib/modules/3.13.0-48-generic/kernel/net/wireless/cfg80211.ko: File exists
insmod: ERROR: could not insert module /lib/modules/3.13.0-48-generic/kernel/net/mac80211/mac80211.ko: File exists
Wifi has been successfully loaded.
sudo cp firmware/BT/mt76x0.bin /lib/firmware/
cd btloader/ && make
make[1]: Entering directory `/home/ehood/Downloads/MT7630E_3.16-master/btloader'
make -C /lib/modules/3.13.0-48-generic/build M=/home/ehood/Downloads/MT7630E_3.16-master/btloader modules
make[2]: Entering directory `/usr/src/linux-headers-3.13.0-48-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-3.13.0-48-generic'
make[1]: Leaving directory `/home/ehood/Downloads/MT7630E_3.16-master/btloader'
Bluetooth driver has been compiled successfully.
cd btloader/ && sudo ./unload_bt.sh; true
Bluetooth has been successfully unloaded.
cd btloader/ && sudo ./load_bt.sh
Bluetooth has been successfully loaded.

this is attached file from the wireless script it has change-
[ATTACH=CONFIG]261028[/ATTACH]

---

### Post by chili555 on 2015-04-01
It looks like it compiled correctly to me:> # PCI device 0x14c3:0x7630 ([COLOR="#FF0000"]rt2800pci[/COLOR])
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
I suggest you detach the USB wireless device and reboot.

Does it scan and see networks?```
sudo iwlist wlan0 scan
```If it scans, it will connect, usually.

---

### Post by ehood2 on 2015-04-05
thanks for the help, I solved the problem using this driver
[https://github.com/kuba-moo/mt7630e](https://github.com/kuba-moo/mt7630e)
and before this It didnt scaned.

---

