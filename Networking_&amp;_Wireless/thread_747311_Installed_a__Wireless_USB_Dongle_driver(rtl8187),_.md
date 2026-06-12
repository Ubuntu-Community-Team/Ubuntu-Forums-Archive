---
title: "Installed a  Wireless USB Dongle driver(rtl8187), now internal ipw2200 doesn't work"
date: 2008-04-06
forum: Networking &amp; Wireless
---

### Post by Dreamlocked on 2008-04-06
Hello, 

I recently acquired a new ALFA Networks AWUS036H (chipset : Realtek 8187), so I proceded installing the latest drivers following what I thought a rather accurate [guide]("http://www.aircrack-ng.org/doku.php?id=r8187&s=r8187").

Taken from that guide : 
```

sudo apt-get install build-essential
sudo apt-get install libssl-dev

sudo rm -rf /lib/modules/2.6.22-14-generic/ubuntu/wireless/rtl818x/rtl8187.ko
sudo rm -rf /lib/modules/2.6.22-14-generic/ubuntu/wireless/rtl8180/rtl_ieee80211/ieee80211-rtl.ko
sudo rm -rf /lib/modules/2.6.22-14-generic/kernel/net/ieee80211/ieee80211.ko
sudo rm -rf /lib/modules/2.6.22-14-generic/kernel/net/ieee80211/ieee80211_crypt.ko
sudo rm -rf /lib/modules/2.6.22-14-generic/kernel/net/ieee80211/ieee80211_crypt_wep.ko
sudo rm -rf /lib/modules/2.6.22-14-generic/kernel/net/ieee80211/ieee80211_crypt_ccmp.ko
sudo rm -rf /lib/modules/2.6.22-14-generic/kernel/net/ieee80211/ieee80211_crypt_tkip.ko

ifconfig wlan0 down	 
rmmod rtl8187

wget http://dl.aircrack-ng.org/drivers/rtl8187_linux_26.1010.zip
unzip rtl8187_linux_26.1010.zip
cd rtl8187_linux_26.1010.0622.2006/
wget http://patches.aircrack-ng.org/rtl8187_2.6.24v3.patch
tar xzf drv.tar.gz
tar xzf stack.tar.gz
patch -Np1 -i rtl8187_2.6.24v3.patch
make
make install


```

Of course, I backed up the 7 files that the guide asks me to delete.

So I rebooted and the driver seems to work somewhat (though I can't seem to be able to connect to WPA) with the ALFA Networks AWUS036H. Regardless, now my eth1 (the internal intel chipset using the ipw2200 driver) is broken.

```

username@dreamlocked::~$ sudo ifconfig eth1 up
eth1: ERROR while getting interface flags: No such device

```

```

username@dreamlocked:~$ dmesg|grep ipw2200
[   16.696000] ipw2200: Unknown symbol ieee80211_wx_get_encodeext
[   16.696000] ipw2200: Unknown symbol ieee80211_wx_set_encode
[   16.696000] ipw2200: Unknown symbol ieee80211_wx_get_encode
[   16.696000] ipw2200: Unknown symbol ieee80211_txb_free
[   16.696000] ipw2200: Unknown symbol ieee80211_wx_set_encodeext
[   16.696000] ipw2200: Unknown symbol ieee80211_wx_get_scan
[   16.696000] ipw2200: Unknown symbol escape_essid
[   16.696000] ipw2200: Unknown symbol ieee80211_freq_to_channel
[   16.696000] ipw2200: Unknown symbol ieee80211_set_geo
[   16.696000] ipw2200: Unknown symbol ieee80211_rx
[   16.696000] ipw2200: Unknown symbol ieee80211_channel_to_index
[   16.696000] ipw2200: Unknown symbol ieee80211_rx_mgt
[   16.696000] ipw2200: Unknown symbol ieee80211_get_geo
[   16.696000] ipw2200: Unknown symbol free_ieee80211
[   16.696000] ipw2200: Unknown symbol ieee80211_is_valid_channel
[   16.696000] ipw2200: Unknown symbol alloc_ieee80211

```

Would anyone know how I can re-enable the Intel ipw2200 driver, short of re-installing Gutsy? I don't mind if it means removing the driver of the new USB dongle.

Thank you in advance, for your time.

- Dreamlocked.

---

### Post by Dreamlocked on 2008-04-06
Managed to fix it.

Inspired from [http://www.aircrack-ng.org/doku.php?id=ipw2200]("http://www.aircrack-ng.org/doku.php?id=ipw2200")
but with latest patches.

Note : I am using Xubuntu Gutsy. No clue if it will work with anything else.

ieee80211-1.2.18 :
```

wget http://puzzle.dl.sourceforge.net/sourceforge/ieee80211/ieee80211-1.2.18.tgz
tar zxvf ieee80211-1.2.18.tgz
cd ieee80211-1.2.18
sudo make
sudo make install

```

Get the Patch and driver :
```

wget http://www.waraey.com/dl/files/ipw2200-1.2.2-inject.patch
wget http://www.waraey.com/dl/files/ipw2200-1.2.2-make.patch
wget http://kent.dl.sourceforge.net/sourceforge/ipw2200/ipw2200-1.2.2.tgz

```

Patch the driver :
```

tar zxvf ipw2200-1.2.2.tgz
patch ipw2200-1.2.2/ipw2200.c ipw2200-1.2.2-inject.patch
patch ipw2200-1.2.2/Makefile ipw2200-1.2.2-make.patch
cd ipw2200-1.2.2
sudo ./remove-old
sudo make
sudo make install

```

Reboot, and it should work. Or at least it did for me.

---

