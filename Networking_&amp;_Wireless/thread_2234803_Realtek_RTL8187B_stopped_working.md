---
title: "Realtek RTL8187B stopped working"
date: 2014-07-17
forum: Networking &amp; Wireless
---

### Post by h.hittini on 2014-07-17
Hello there,

I have Ubuntu 13.10 Server running 3.11 kernel, I also have two USB Wireless adapters as follows:
Adapter 1: Realtek RTL8187B chipset [https://www.thinkpenguin.com/gnu-linux/penguin-wireless-g-usb-adapter](https://www.thinkpenguin.com/gnu-linux/penguin-wireless-g-usb-adapter)
Adapter 2: AR7010+AR9280 chipsets [https://www.thinkpenguin.com/gnu-linux/penguin-wireless-n-dual-band-usb-adapter-gnu-linux-tpe-nusbdb](https://www.thinkpenguin.com/gnu-linux/penguin-wireless-n-dual-band-usb-adapter-gnu-linux-tpe-nusbdb)
They claim that they work out of the box and they did, however, Adapter 2 had some limitations on frequency use
So, I recompiled backports 3.15 source files after doing some manipulations to get a more opened driver, these manipulations were only for Atheros drivers
Now, Adapter 1 stopped working, I tested the same adapter on another computer and it works fine
I got the following errors:
```

device descriptor read/64, error -110
device not accepting address 10, error -110
device not acccepting address11, error -110
unable to enumerate USB device on port 1

```
The adapter doesn't even show up in lshw -C network
I recompiled backports and included some Relatek drivers but none of them is for the same chipset, I hoped that another chipset would be using the same driver but still, the adapter doesn't work
And I don't see the errors mentioned earlier anymore
Do you have any suggestions?

Thank you

Update 1----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
I looked at the module in /lib/modules and the module is still there, apparently it wasn't modified recently
Kindly look at the following codes

```
hosam@Robin-05:~$ sudo modprobe rtl8187
ERROR: could not insert 'rtl8187': Invalid argument
```

```
hosam@Robin-05:~$ sudo insmod /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/rtl818x/rtl8187/rtl8187.ko
Error: could not insert module /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/rtl818x/rtl8187/rtl8187.ko: Invalid parameters
```

```
hosam@Robin-05:~$ dmesg | tail
[ 3097.162711] rtl8187: disagrees about version of symbol wiphy_rfkill_start_polling
[ 3097.162716] rtl8187: Unknown symbol wiphy_rfkill_start_polling (err -22)
[ 3097.162739] rtl8187: disagrees about version of symbol ieee80211_unregister_hw
[ 3097.162744] rtl8187: Unknown symbol ieee80211_unregister_hw (err -22)
[ 3097.162757] rtl8187: disagrees about version of symbol ieee80211_beacon_get_tim
[ 3097.162761] rtl8187: Unknown symbol ieee80211_beacon_get_tim (err -22)
[ 3097.162800] rtl8187: disagrees about version of symbol ieee80211_rx_irqsafe
[ 3097.162805] rtl8187: Unknown symbol ieee80211_rx_irqsafe (err -22)
[ 3097.162828] rtl8187: disagrees about version of symbol ieee80211_rts_duration
[ 3097.162833] rtl8187: Unknown symbol ieee80211_rts_duration (err -22)
```

---

### Post by chili555 on 2014-07-17
I believe there is a conflict in the way the 80211 stack is handled between the two methods you used. I suggest you install both drivers using the same method, presumably backports. Did you compile backports or install linux-backports-modules-cw?

---

### Post by h.hittini on 2014-07-17
> **chili555 said:**
> I believe there is a conflict in the way the 80211 stack is handled between the two methods you used. I suggest you install both drivers using the same method, presumably backports. Did you compile backports or install linux-backports-modules-cw?

I compiled backports 3.15 from source files, but the issue is the driver for this specific chipset is not supported by backports
I changed some settings related to the region and regulations if that makes a difference

---

### Post by chili555 on 2014-07-17
Will backports 3.13.2-1 do the job for both?```
Desktop/Forum/backports-3.13.2-1/drivers/net/wireless/rtl818x/rtl8187/[COLOR="#FF0000"]rtl8187.ko[/COLOR]
```By the way, what is the other driver you needed to compile?> I changed some settings related to the region and regulations if that makes a differencePossibly; what did you change?

---

### Post by h.hittini on 2014-07-17
> **chili555 said:**
> Will backports 3.13.2-1 do the job for both?```
Desktop/Forum/backports-3.13.2-1/drivers/net/wireless/rtl818x/rtl8187/[COLOR=#FF0000]rtl8187.ko[/COLOR]
```

I'm not sure I have to test that but I think yes, even the 3.15 version has a folder for rtl8187 driver
I tried to compile backports version 3.12, 3.13, 3.14 and 3.15 using the .config file I got using "make defconfig-rtlwifi" command and none of them created rtl8187.ko
When I used "make menuconfig" and went to *[COLOR=#ff8c00]Wireless LAN > Realtek rtlwifi family of devices[/COLOR]* I didn't find the RTL8187 among them in the four versions
However, if I listed the contents of [COLOR=#ff8c00]drivers/net/wireless/rtl818x/rtl8187[/COLOR] I can see .h and .c files
So, I'm not sure how you managed to compile the driver I need
I wonder if you can help me with that

> **chili555 said:**
> By the way, what is the other driver you needed to compile?Possibly; what did you change?
I needed to recompile the ath9k driver because I didn't have full access to the 5GHz channels
I need to use the AP and Ad-Hoc modes in the 5GHz band and I could get 8 channels of them to work
I enabled the following options from "make menuconfig"
[LIST]
[*]cfg80211 regulatory debugging 
[*]cfg80211 certification onus 
[*]use statically compiled regulatory rules database 
[*]cfg80211 wireless extensions compatibility 
[*]Atheros wireless debugging 
[*]Atheros dynamic user regulatory hints 
[*]Atheros dynamic user regulatory testing 
[*]Atheros ath9k debugging 
[*]Detailed station statistics 
[*]Atheros DFS support for certified platforms 
[*]Atheros ath9k TX99 testing support 
[*]Atheros ath9k rfkill support 
[*]Atheros HTC based wireless cards support 
[*]Atheros ath9k_htc debugging 
[/LIST]

---

### Post by chili555 on 2014-07-17
You can get both ath9k and rtl8187 with:```
make defconfig-wifi
```I suggest you try that.```
  LD [M]  /home/chili/Downloads/backports-3.15.1-1/drivers/net/wireless/ath/ath9k/ath9k.ko
  LD [M]  /home/chili/Downloads/backports-3.15.1-1/drivers/net/wireless/ath/ath9k/ath9k_common.ko
  LD [M]  /home/chili/Downloads/backports-3.15.1-1/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
  LD [M]  /home/chili/Downloads/backports-3.15.1-1/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
  LD [M]  /home/chili/Downloads/backports-3.15.1-1/drivers/net/wireless/ath/carl9170/carl9170.ko
<snip>
  LD [M]  /home/chili/Downloads/backports-3.15.1-1/drivers/net/wireless/rt2x00/rt61pci.ko
  LD [M]  /home/chili/Downloads/backports-3.15.1-1/drivers/net/wireless/rtl818x/rtl8180/rtl8180.ko
  LD [M]  /home/chili/Downloads/backports-3.15.1-1/drivers/net/wireless/rtl818x/rtl8187/rtl8187.ko
  LD [M]  /home/chili/Downloads/backports-3.15.1-1/drivers/net/wireless/rtlwifi/btcoexist/btcoexist.ko
<snip>
```I believe the correct process is:```
cd ~/Desktop/backports-3.15.1-1  [COLOR="#FF0000"]<--or wherever you extracted it[/COLOR]
make clean
make defconfig-wifi
make -j4
sudo make install
```Then I'd reboot.

Backports currently won't compile on the latest Ubuntu kernels so I suggest that, for now, you stick with 13.10. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1342703](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1342703)

---

### Post by h.hittini on 2014-07-18
> **chili555 said:**
> You can get both ath9k and rtl8187 with:```
make defconfig-wifi
```I suggest you try that.```
  LD [M]  /home/chili/Downloads/backports-3.15.1-1/drivers/net/wireless/ath/ath9k/ath9k.ko
  LD [M]  /home/chili/Downloads/backports-3.15.1-1/drivers/net/wireless/ath/ath9k/ath9k_common.ko
  LD [M]  /home/chili/Downloads/backports-3.15.1-1/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
  LD [M]  /home/chili/Downloads/backports-3.15.1-1/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
  LD [M]  /home/chili/Downloads/backports-3.15.1-1/drivers/net/wireless/ath/carl9170/carl9170.ko
<snip>
  LD [M]  /home/chili/Downloads/backports-3.15.1-1/drivers/net/wireless/rt2x00/rt61pci.ko
  LD [M]  /home/chili/Downloads/backports-3.15.1-1/drivers/net/wireless/rtl818x/rtl8180/rtl8180.ko
  LD [M]  /home/chili/Downloads/backports-3.15.1-1/drivers/net/wireless/rtl818x/rtl8187/rtl8187.ko
  LD [M]  /home/chili/Downloads/backports-3.15.1-1/drivers/net/wireless/rtlwifi/btcoexist/btcoexist.ko
<snip>
```I believe the correct process is:```
cd ~/Desktop/backports-3.15.1-1  [COLOR=#FF0000]<--or wherever you extracted it[/COLOR]
make clean
make defconfig-wifi
make -j4
sudo make install
```Then I'd reboot.

Backports currently won't compile on the latest Ubuntu kernels so I suggest that, for now, you stick with 13.10. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1342703](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1342703)

I don't have access to that computer right now, but I tested this on a virtual machine and it works like a charm
Thank you so much!
I'll test in a couple of days and mark the thread as solved later
Thanks again for your time

---

### Post by h.hittini on 2014-07-20
I used the following command to get the default configuration for WiFi drivers
```
make defconfig-wifi
```
And the following command then to change the settings I need ```
make menuconfig
```

After that I did the following
```
make -j4
make install
reboot
```

---

