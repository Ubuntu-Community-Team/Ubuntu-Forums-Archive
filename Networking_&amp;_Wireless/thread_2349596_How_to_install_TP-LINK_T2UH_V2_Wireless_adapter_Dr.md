---
title: "How to install TP-LINK T2UH V2 Wireless adapter Driver"
date: 2017-01-16
forum: Networking &amp; Wireless
---

### Post by lelorien on 2017-01-16
My built in wifi adapter (some Atheros something) not working properly in linux, I recently purchased a USB adapter (TP-Link T2UH V2) for its supposed linux compatibility and I'm having trouble installing it.

I followed the steps of [this]("http://askubuntu.com/questions/674116/how-to-install-tp-link-t2uh-wireless-adapter-driver-ralink-mt7610u") guide to no avail. As the repository specified was marked deprecated, I also tried using [this]("https://github.com/chenhaiq/mt7610u_wifi_sta_v3002_dpo_20130916/blob/master/README.md") repo with the same steps. Still no success.

lsusb shows my adapter:
```
Bus 003 Device 002: ID 148f:761a Ralink Technology, Corp.
```

I am running ubuntu 16.04 with the 4.4.0-59-generic kernel. The original driver on TP-Link's website mentions it is compatible up to kernel version 3.3 but a few users have had success with my version of Ubuntu

But ifconfig doesn't show any new interface.

Also, lsmod doesn't show anything close to mt7610u or starting with rtl.

I'm stumped. How can I validate if it worked?

---

### Post by chili555 on 2017-01-16
Please try this: [http://askubuntu.com/questions/865102/tp-link-t2u-ac600-usb-wlan-adapter-driver-on-ubuntu-16-10/865157#865157](http://askubuntu.com/questions/865102/tp-link-t2u-ac600-usb-wlan-adapter-driver-on-ubuntu-16-10/865157#865157)

Please post back any errors, etc., and we'll try to help.

---

### Post by praseodym on 2017-01-16
[http://www.ubuntu-forum.de/artikel/65713/tp-link-ac600-t2uh-usb-adapter-probleme-mit-treiber-installation.html#post387218](http://www.ubuntu-forum.de/artikel/65713/tp-link-ac600-t2uh-usb-adapter-probleme-mit-treiber-installation.html#post387218)

This driver could also work. But with kernel 4.8???

---

### Post by lelorien on 2017-01-16
Thank you for the answers!

> [COLOR=#000000]Please post back any errors, etc., and we'll try to help.
[/COLOR]

When I input "sudo make install", I get: "make: *** No rule to make target 'install'.  Stop."
When I input "[COLOR=#111111][FONT=Consolas]sudo insmod mt7610u.ko", I get: "[/FONT][/COLOR]insmod: ERROR: could not load module mt7610u.ko: No such file or directory"


> [http://www.ubuntu-forum.de/artikel/6...tml#post387218]("http://www.ubuntu-forum.de/artikel/65713/tp-link-ac600-t2uh-usb-adapter-probleme-mit-treiber-installation.html#post387218")

When I try to make, I get this error twice:

```
macro "__DATE__" might prevent reproducible builds [-Werror=date-time]
 intf(extra, size, "Driver version-%s, %s %s\n", STA_DRIVER_VERSION, __DATE__, _
```

Thanks!

---

### Post by chili555 on 2017-01-16
> macro "__DATE__" might prevent reproducible builds [-Werror=date-time]
 intf(extra, size, "Driver version-%s, %s %s\n", STA_DRIVER_VERSION, __DATE__, _Is the time and date set correctly on your computer?```
date
```I get:> Mon Jan 16 16:07:45 EST 2017After you set it correctly, try again:```
cd ~/mt7610u
make clean
make
```Does the 'make' end up here?```
<snip>
Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/chili/Desktop/Forum/mt7610u/mt7610u.mod.o
  LD [M]  /home/chili/Desktop/Forum/mt7610u/mt7610u.ko

```If so, next try:```
sudo insmod mt7610u.ko
```Again, post any errors or funny stuff!

---

### Post by lelorien on 2017-01-16
My date is fine, I had the error only when trying to make the official driver, not yours, chili.


I get these warnings during make:
```
/home/laurent/mt7610u/sta/sta_cfg.c:1580:10: warning: assignment makes pointer from integer without a cast [-Wint-conversion]
     pBuf = mt7610u_read32(pAd, IdAddr);
          ^
/home/laurent/mt7610u/sta/sta_cfg.c:1587:11: warning: assignment makes pointer from integer without a cast [-Wint-conversion]
      pBuf = mt7610u_read32(pAd, IdAddr);
/home/laurent/mt7610u/common/rtmp_init.c: In function ‘NICInitializeAsic.part.1’:
/home/laurent/mt7610u/common/rtmp_init.c:1194:1: warning: the frame size of 2040 bytes is larger than 1024 bytes [-Wframe-larger-than=]
 }
/home/laurent/mt7610u/rate_ctrl/alg_grp.c: In function ‘StaQuickResponeForRateUpExecAdapt’:
/home/laurent/mt7610u/rate_ctrl/alg_grp.c:1079:38: warning: comparison of constant ‘2’ with boolean expression is always false [-Wbool-compare]
   else if (pAd->CommonCfg.TrainUpRule==2 && Rssi<=pAd->CommonCfg.TrainUpRuleRSS
                                      ^
/home/laurent/mt7610u/rate_ctrl/alg_grp.c:1083:38: warning: comparison of constant ‘3’ with boolean expression is always false [-Wbool-compare]
   else if (pAd->CommonCfg.TrainUpRule==3 && Rssi<=pAd->CommonCfg.TrainUpRuleRSS

```            

I have this at the end of the make:  


```

  Building modules, stage 2.
  MODPOST 1 modules
  LD [M]  /home/laurent/mt7610u/mt7610u.ko
make[1]: Leaving directory '/usr/src/linux-headers-4.4.0-59-generic'

```

I get this after [COLOR=#000000][FONT=&quot]sudo insmod mt7610u.ko[/FONT][/COLOR]:
```
insmod: ERROR: could not insert module mt7610u.ko: Required key not available

```

Thanks!

---

### Post by chili555 on 2017-01-16
> insmod: ERROR: could not insert module mt7610u.ko: Required key not availablePlease see: [http://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules](http://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules)

> The easiest way to fix this issue is to disable Secure Boot in UEFI (BIOS) settings.

---

### Post by lelorien on 2017-01-17
It worked! I was finally able to install the driver!

The adapter gives me worse reception than my built in adapter, which is already very bad. I'm not sure I was able to open a web page while being connected through the adapter. I tried blacklisting my built-in module, but it did not change anything. I un-blacklisted it 

I also get a popup saying "Sorry, Ubuntu experienced an internal error" periodically from the modemmanager 1.4.12-1ubuntu1 Package.

---

### Post by chili555 on 2017-01-17
> The adapter gives me worse reception than my built in adapterThen I would absolutely use the internal rather than the tricky, twitchy mt7610u. Perhaps we can tweak a few things for the internal.

---

### Post by lelorien on 2017-01-17
The problem is my internal adapter often drops connections and doesn't see any wifi, even on windows. My reception is also very bad compared to the people around me. It's an Atheros AR9485. Do you think it's worth trying?

---

### Post by chili555 on 2017-01-18
> **lelorien said:**
> The problem is my internal adapter often drops connections and doesn't see any wifi, even on windows. My reception is also very bad compared to the people around me. It's an Atheros AR9485. Do you think it's worth trying?If it is troublesome even on Windows, then it's the device itself. I'd certainly check the antenna connectors: [http://farm4.staticflickr.com/3771/8991456036_baa5dc68e7.jpg](http://farm4.staticflickr.com/3771/8991456036_baa5dc68e7.jpg)

If that doesn't do it, the replacements are US $13 or so on Ebay.

Finally, there are many inexpensive USB devices that work fine in Ubuntu without tricky drivers that need to be compiled after every kernel update; this works well for me: [https://www.amazon.com/TP-Link-N150-Wireless-Adapter-TL-WN722N/dp/B002SZEOLG](https://www.amazon.com/TP-Link-N150-Wireless-Adapter-TL-WN722N/dp/B002SZEOLG) I'd also blacklist the driver for the internal, ath9k.

---

### Post by lelorien on 2017-01-22
I'll open my laptop soon to check things out, thanks for the tip!

Is there an easy way to know which type of inner wifi slot I have and how to know an adapters compatibility? I'd get a better card, ideally well supported in Ubuntu.

Blacklisting the driver did wonders! My adapter looks a lot like that one, in fact, it's the AC600 edition. Do you think a change in version (for the n150) would make such a difference?

Thanks!

---

### Post by chili555 on 2017-01-23
Your AC600 version uses the tricky-in-Linux mt7610u chipset. The N150 that I have and recommend uses the ath9k_htc chipset. It's fully supported right out of the box.

The best way to find out the exact type of wireless card you have and need; that is, mini-pci, half-height, etc. is to Google up the service manual for your exact model of laptop and see what the part numbers are. Then Google the part numbers and you'll see the description listed at Ebay, Newegg, Amazon, etc.

This may help: [http://www.machinaelectronics.com/blog/a-guide-to-mini-pci-laptop-wireless-cards/](http://www.machinaelectronics.com/blog/a-guide-to-mini-pci-laptop-wireless-cards/) You can also simply look and probably tell which version you have.

Some laptop manufacturers, including but not limited to HP and Lenovo, whitelist their wireless cards, meaning that you can't use any card you want; you must use a card listed (hidden) in the BIOS. [http://goughlui.com/2014/08/02/laptop-wireless-card-whitelists-an-upgrade-nightmare/](http://goughlui.com/2014/08/02/laptop-wireless-card-whitelists-an-upgrade-nightmare/)

The Atheros ath9k you have now is generally very reliable. I wouldn't hesitate to get another one if the antenna wires are intact and the card is simply electrically defective.

---

### Post by duruttye on 2017-04-03
Hello, I was fortunate enough to randomly pick up one of these usb adaptors from the store shelf the other day, right after I told my colleagues that I use linux and everything works out of the box. Well, so I thought.

The process and my knowledge stop at the "sudo make install" bit as well, output is the same as one from above:
```
dome@ubvaio:~/mt7610u$ sudo make install
make: *** No rule to make target 'install'. Stop.

```

As you can see, I am in the same folder, I had a few warnings during the make command, but no errors and after "sudo insmod mt7610.ko" I can also see the MediaTek Wifi thingy in the network manager, greyed out, not managed.

And I am also trying to get this adaptor work only because of the 5ghz network which can't be accessed from the built-in wifi card, unfortunately.

Any ideas will be met with joy and tears in my eyes :)

---

### Post by chili555 on 2017-04-05
> The process and my knowledge stop at the "sudo make install" bit as well, output is the same as one from above:
Code:
dome@ubvaio:~/mt7610u$ sudo make install
make: *** No rule to make target 'install'. Stop.That simply means that, for whatever reason, the Makefile doesn't contain the scripts to install the driver in /lib/modules/*/kernel/drivers/wherever. As you have seen, and as is mentioned in the README, you must manually load the module with:```
sudo insmod mt7610.ko
```>  I can also see the MediaTek Wifi thingy in the network manager, greyed out, not managed.Why? Is the switch set to enable or disable wireless?```
rfkill list all
```Have you told Network Manager that it will manage wireless or that you will do so; typically in /etc/network/interfaces?```
cat /etc/NetworkManager/NetworkManager.conf
```Have you placed any spurious entries here?```
cat /etc/network/interfaces
```Are there any clues in the log?```
dmesg | grep mt76
```> And I am also trying to get this adaptor work only because of the 5ghz network which can't be accessed from the built-in wifi card, unfortunately.You picked the trickiest, least likely to succeed device that I can think of, unfortunately. I might have, instead, addressed the internal card. Are you handy with a screwdriver??

[ATTACH=CONFIG]274437[/ATTACH]

---

### Post by SeijiSensei on 2017-04-05
I recommend you take the device back to the store and exchange it for an "N" adapter like this one that works out-of-the-box in Linux: [https://www.amazon.com/TP-Link-N150-Wireless-Adapter-TL-WN722N/dp/B002SZEOLG](https://www.amazon.com/TP-Link-N150-Wireless-Adapter-TL-WN722N/dp/B002SZEOLG).  That little [Edimax device]("https://www.amazon.com/Edimax-EW-7811Un-150Mbps-Raspberry-Supports/dp/B003MTTJOY") works pretty well, too.

I have an AC 1200 adapter that requires compiling the driver.  I got it to work for a while but then had problems with it.  I've decided to go back to that N adapter for the time being until the AC driver is incorporated into the kernel.

---

### Post by duruttye on 2017-04-05
Hi SeijiSensei,

Thank you for your reply!

I will give this one another try and if I can't make it work I will have to return it, no question about it.
As far as I can see, the two adaptors you mentioned can't use the 5ghz channel and that would be the whole point of having a usb adaptor for me.

---

### Post by duruttye on 2017-04-05
Hi chilli555,
Thank you for the reply!

I managed to manually load the kernel, I just wasn't aware that that is what the "sudo make install" command should do, I thought it will place other files in other locations as well.

The "rfkill list all" gives me:

```
0: sony-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: sony-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
4: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

I haven't had a word with the Network Manager yet:

```
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=true

```

All entries from /etc/network/interfaces:

```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback



```

And the dmesg:

```
[   70.508700] ==>mt7610u_chip_onoff(): OnOff:1, Reset= 0, pAd->WlanFunCtrl:0x0, Reg-WlanFunCtrl=0xff000002
[   70.510992] usbcore: registered new interface driver mt7610u

```

Also, when I plug the dongle in, the dmesg shows:

```
[20349.163200] usb 2-1.2: new high-speed USB device number 4 using ehci-pci
[20349.288212] usb 2-1.2: New USB device found, idVendor=148f, idProduct=761a
[20349.288219] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[20349.288223] usb 2-1.2: Product: WiFi
[20349.288227] usb 2-1.2: Manufacturer: MediaTek
[20349.288230] usb 2-1.2: SerialNumber: 1.0
[20349.288732] 
               
               === pAd = ffffaf9401ca1000, size = 893824 ===

[20349.288782] <-- RTMPAllocTxRxRingMemory, Status=0
[20349.288800] <-- RTMPAllocAdapterBlock, Status=0
[20349.288953] ==>mt7610u_chip_onoff(): OnOff:1, Reset= 0, pAd->WlanFunCtrl:0x0, Reg-WlanFunCtrl=0xff000002
[20349.289201] MACVersion = 0x76502000
[20349.289680] MACVersion = 0x76502000
[20349.289937] 80211> RFICType = 3
[20349.289940] 80211> Number of channel = 44
[20349.289942] 80211> Number of rate = 12
[20349.289944] 80211> CurTxPower = 0 dBm
[20349.289947] 80211> TxStream = 0
[20349.290059] crda> requlation requestion by country IE: GB
[20349.290133] 80211> CFG80211_Register
[20349.302275] ModemManager[3749]: segfault at 0 ip 000055a235a40b27 sp 00007ffc3e308650 error 4 in ModemManager[55a235a09000+11e000]

```

Yesterday I blacklisted the module for the normal internal driver and for a short period of time I actually saw the 5ghz network, but it couldn't connect to it.

And yes, changing the internal one was my first option. I have another laptop that I don't use, tested it, I can see the 5ghz channel. I googled both cards and at a visual inspection, they looked more or less the same - may I add: I'm not an expert by far. After taking both laptops apart - my room was full of parts - and when I was trying to put the other on in, I realised that in fact they are not the same. The size is the same, the pins are slightly different. The only problem is that I can't tell what type of card the internal is. This is a not too popular Sony Vaio laptop, using [this card]("http://www.ebay.co.uk/itm/SONY-VAIO-PCG-81313M-WIFI-WIRELESS-CARD-AR5B25-/112092196101"), the only thing I know about it is that it is AR5B25. For me it looks the same as any other, but the pins are different.

Just a few minutes ago, I saw the 5ghz channel again, couldn't connect.

```
[  212.667755] ==>mt7610u_chip_onoff(): OnOff:0, Reset= 0, pAd->WlanFunCtrl:0xff000003, Reg-WlanFunCtrl=0xff000003
[  212.671317] receive cmd msg fail(-2)
[  212.671348] tx_kickout_fail_count = 0
[  212.671350] tx_timeout_fail_count = 0
[  212.671351] rx_receive_fail_count = 0
[  212.671352] alloc_cmd_msg = 141
[  212.671354] free_cmd_msg = 141
[  212.727137] ==>mt7610u_chip_onoff(): OnOff:1, Reset= 0, pAd->WlanFunCtrl:0xff000000, Reg-WlanFunCtrl=0xff000000
[  212.727360] MACVersion = 0x76502000
[  212.727758] MAC[Ver=0x76502000]
[  212.727761] usb 2-1.2: loading firmware mt7610u.bin
[  212.732777] usb 2-1.2: firmware mt7610u.bin loaded
[  212.738569] fw version:0.1.00 build:7640
[  212.738570] build time:ilm length = 68780(bytes)
[  212.738571] dlm length = 11476(bytes)
[  212.820977] #
[  212.827878] loading fw......
[  212.948957] #
[  213.165874] RTMP_TimerListAdd: add timer obj ffffaf3a81902758!
[  213.165875] RTMP_TimerListAdd: add timer obj ffffaf3a819027c8!
[  213.165876] RTMP_TimerListAdd: add timer obj ffffaf3a81902838!
[  213.165877] RTMP_TimerListAdd: add timer obj ffffaf3a819026e8!
[  213.165878] RTMP_TimerListAdd: add timer obj ffffaf3a81902598!
[  213.165879] RTMP_TimerListAdd: add timer obj ffffaf3a81902608!
[  213.165879] RTMP_TimerListAdd: add timer obj ffffaf3a81894a90!
[  213.165880] RTMP_TimerListAdd: add timer obj ffffaf3a81883910!
[  213.165880] RTMP_TimerListAdd: add timer obj ffffaf3a81883988!
[  213.165881] RTMP_TimerListAdd: add timer obj ffffaf3a81894c00!
[  213.165882] RTMP_TimerListAdd: add timer obj ffffaf3a818949b0!
[  213.165883] RTMP_TimerListAdd: add timer obj ffffaf3a81894b90!
[  213.165907] cfg_mode=13
[  213.165909] wmode_band_equal(): Band Not Equal!
[  213.166128] 1. Phy Mode = 61
[  213.166129] 2. Phy Mode = 61
[  213.171664] /home/dome/Desktop/mt7610u/chips/mt76x0.c:1694 assert (pAd->TxPower[choffset].Channel == 36)failed
[  213.181891] ERROR!!! E2PROM: WRONG VERSION 0x2, should be 1
[  213.183855] BT Coexistence word [66] = 0000ffff
[  213.184511] 0x24 = 0xffef, 0x0104 = 0x0033ffef
[  213.184514] EEPROM_NIC_CFG1_OFFSET = 0xfd11
[  213.184984] mt76x0_read_tx_alc_info_from_eeprom: EEPROM_MT76x0_TEMPERATURE_OFFSET (0xD1) = 0xf8
[  213.184996] mt76x0_read_tx_alc_info_from_eeprom: TemperatureOffset = 0xfffffff8
[  213.184997] Temperature Tx ALC not enabled
[  213.188365] 3. Phy Mode = 61
[  213.188380] AntCfgInit: primary/secondary ant 0/1
[  213.193863] TxPath = 1, RxPath = 1, RFIC=17
[  213.193891] RTMPSetPhyMode: channel is out of range, use first channel=1 
[  213.195239] MCS Set = ff 00 00 00 01
[  213.205230] <==== rt28xx_init, Status=0
[  213.205232] 80211> re-init bands...
[  213.205365] 80211> re-init bands...
[  213.205367] 80211> RFICType = 3
[  213.205369] 80211> Number of channel = 44
[  213.205370] 80211> Number of rate = 12
[  213.205372] 80211> CurTxPower = 0 dBm
[  213.205375] 80211> TxStream = 1
[  213.205377] crda> CFG80211_RegRuleApply ==>
[  213.205379] crda> reset chan/power for 2.4GHz
[  213.205382] Chan 001:	power 0 dBm, DFS 0, DFS Type 0
[  213.205384] Chan 002:	power 0 dBm, DFS 0, DFS Type 0
[  213.205387] Chan 003:	power 0 dBm, DFS 0, DFS Type 0
[  213.205389] Chan 004:	power 0 dBm, DFS 0, DFS Type 0
[  213.205391] Chan 005:	power 0 dBm, DFS 0, DFS Type 0
[  213.205393] Chan 006:	power 0 dBm, DFS 0, DFS Type 0
[  213.205395] Chan 007:	power 0 dBm, DFS 0, DFS Type 0
[  213.205397] Chan 008:	power 0 dBm, DFS 0, DFS Type 0
[  213.205399] Chan 009:	power 0 dBm, DFS 0, DFS Type 0
[  213.205401] Chan 010:	power 0 dBm, DFS 0, DFS Type 0
[  213.205403] Chan 011:	power 0 dBm, DFS 0, DFS Type 0
[  213.205405] Chan 012:	power 0 dBm, DFS 0, DFS Type 0
[  213.205407] Chan 013:	power 0 dBm, DFS 0, DFS Type 0
[  213.205409] Chan 014 (frq 2484):	not allowed!
[  213.205428] crda> reset chan/power for 5GHz
[  213.205430] Chan 036:	power 0 dBm, DFS 0, DFS Type 0
[  213.205431] Chan 038:	power 0 dBm, DFS 0, DFS Type 0
[  213.205432] Chan 040:	power 0 dBm, DFS 0, DFS Type 0
[  213.205433] Chan 044:	power 0 dBm, DFS 0, DFS Type 0
[  213.205434] Chan 046:	power 0 dBm, DFS 0, DFS Type 0
[  213.205436] Chan 048:	power 0 dBm, DFS 0, DFS Type 0
[  213.205437] Chan 052:	power 0 dBm, DFS 1, DFS Type 0
[  213.205438] Chan 054:	power 0 dBm, DFS 1, DFS Type 0
[  213.205439] Chan 056:	power 0 dBm, DFS 1, DFS Type 0
[  213.205440] Chan 060:	power 0 dBm, DFS 1, DFS Type 0
[  213.205441] Chan 062:	power 0 dBm, DFS 1, DFS Type 0
[  213.205442] Chan 064:	power 0 dBm, DFS 1, DFS Type 0
[  213.205443] Chan 100:	power 0 dBm, DFS 1, DFS Type 0
[  213.205445] Chan 104:	power 0 dBm, DFS 1, DFS Type 0
[  213.205446] Chan 108:	power 0 dBm, DFS 1, DFS Type 0
[  213.205447] Chan 112:	power 0 dBm, DFS 1, DFS Type 0
[  213.205448] Chan 116:	power 0 dBm, DFS 1, DFS Type 0
[  213.205450] Chan 118:	power 0 dBm, DFS 1, DFS Type 0
[  213.205451] Chan 120:	power 0 dBm, DFS 1, DFS Type 0
[  213.205452] Chan 124:	power 0 dBm, DFS 1, DFS Type 0
[  213.205453] Chan 126:	power 0 dBm, DFS 1, DFS Type 0
[  213.205454] Chan 128:	power 0 dBm, DFS 1, DFS Type 0
[  213.205455] Chan 132:	power 0 dBm, DFS 1, DFS Type 0
[  213.205456] Chan 134:	power 0 dBm, DFS 1, DFS Type 0
[  213.205457] Chan 136:	power 0 dBm, DFS 1, DFS Type 0
[  213.205459] Chan 140:	power 0 dBm, DFS 1, DFS Type 0
[  213.205460] Chan 149 (frq 5745):	not allowed!
[  213.205461] Chan 151 (frq 5755):	not allowed!
[  213.205462] Chan 153 (frq 5765):	not allowed!
[  213.205466] Chan 157 (frq 5785):	not allowed!
[  213.205471] Chan 159 (frq 5795):	not allowed!
[  213.205476] Chan 161 (frq 5805):	not allowed!
[  213.205480] Chan 165 (frq 5825):	not allowed!
[  213.205484] Chan 167 (frq 5835):	not allowed!
[  213.205488] Chan 169 (frq 5845):	not allowed!
[  213.205493] Chan 171 (frq 5855):	not allowed!
[  213.205506] Chan 173 (frq 5865):	not allowed!
[  213.205509] Chan 184 (frq 4920):	not allowed!
[  213.205512] Chan 188 (frq 4940):	not allowed!
[  213.205515] Chan 192 (frq 4960):	not allowed!
[  213.205518] Chan 196 (frq 4980):	not allowed!
[  213.205521] Chan 208 (frq 6040):	not allowed!
[  213.205524] Chan 212 (frq 6060):	not allowed!
[  213.205529] Chan 216 (frq 6080):	not allowed!
[  213.205542] crda> Number of channels = 39
[  213.206609] 0x1300 = 00064300
[  213.206610] RTMPDrvSTAOpen(1):Check if PDMA is idle!
[  213.206730] RTMPDrvSTAOpen(2):Check if PDMA is idle!

```

I even wrote to Sony, asking them to tell me what kind of internal card I have. But I guess they can't be bothered.

Thank you again!!

---

### Post by chili555 on 2017-04-06
Does this help? [http://www.machinaelectronics.com/blog/a-guide-to-mini-pci-laptop-wireless-cards/](http://www.machinaelectronics.com/blog/a-guide-to-mini-pci-laptop-wireless-cards/)

You might Google up the maintenance manual for your exact model of laptop. It should tell you the configuration of the card in your laptop. Also, if you check Google images for "Sony Vaio <your_exact_model>" wireless card, you should be able to find it. If you get stuck, let me know the exact model and I'll try to help.

Research carefully because all replacement cards may or may not have native Linux drivers and, as you've found out, may or may not do 5 Ghz. > [20349.290059] crda> requlation requestion by country IE: GBI don't understand this at all. What do these tell us?```
sudo iw reg get
cat /etc/default/crda | grep REG
```What *should *your country be? [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2)

We don't see anything wrong and therefore fixable in the log, and yet it won't connect. Ugh!

---

### Post by jeremy31 on 2017-04-06
If you actually have an AR5B225 chipset, it is linux friendly as I am using one now.  It uses an AR9485 wireless chipset that uses the ath9k kernel module and has an AR3012 bluetooth device

---

### Post by chili555 on 2017-04-06
> **jeremy31 said:**
> If you actually have an AR5B225 chipset, it is linux friendly as I am using one now.  It uses an AR9485 wireless chipset that uses the ath9k kernel module and has an AR3012 bluetooth deviceI don't believe the chip supports 5 Ghz, does it? That's what he is trying to achieve.

---

### Post by duruttye on 2017-04-06
Hello, country is the UK, so I guess GB should be okay.

I tried the web-page before I got the usb dongle, but it doesn't list this laptop, or I can't find it...

This chipset works fine with the current driver, it just can't see the 5 ghz network. Just to justify my struggle, the 2.4 ghz is limited to around 2-3Mbits/sec, the 5ghz is always on 50Mbits. A proper youtube video is struggling...

Last night I managed to see the network again, but it just can't connect.

If I plug it in now, this is what dmesg shows:

```
[13753.011995] usb 2-1.2: new high-speed USB device number 4 using ehci-pci
[13753.135392] usb 2-1.2: New USB device found, idVendor=148f, idProduct=761a
[13753.135399] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[13753.135403] usb 2-1.2: Product: WiFi
[13753.135407] usb 2-1.2: Manufacturer: MediaTek
[13753.135411] usb 2-1.2: SerialNumber: 1.0
[13753.136154] 
               
               === pAd = ffffc828c1a46000, size = 893824 ===

[13753.136221] <-- RTMPAllocTxRxRingMemory, Status=0
[13753.136247] <-- RTMPAllocAdapterBlock, Status=0
[13753.136448] ==>mt7610u_chip_onoff(): OnOff:1, Reset= 0, pAd->WlanFunCtrl:0x0, Reg-WlanFunCtrl=0xff000002
[13753.136916] MACVersion = 0x76502000
[13753.137598] MACVersion = 0x76502000
[13753.137851] 80211> RFICType = 3
[13753.137852] 80211> Number of channel = 44
[13753.137853] 80211> Number of rate = 12
[13753.137854] 80211> CurTxPower = 0 dBm
[13753.137855] 80211> TxStream = 0
[13753.137918] crda> requlation requestion by country IE: GB
[13753.138032] 80211> CFG80211_Register
[13753.148956] ------------[ cut here ]------------
[13753.148960] kernel BUG at /build/linux-ezBi1T/linux-4.8.0/fs/namei.c:248!
[13753.148962] invalid opcode: 0000 [#1] SMP
[13753.148963] Modules linked in: cmac rfcomm ccm bnep mt7610u(OE) snd_hda_codec_hdmi binfmt_misc mxm_wmi intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm irqbypass crct10dif_pclmul crc32_pclmul arc4 ghash_clmulni_intel aesni_intel aes_x86_64 lrw glue_helper ablk_helper cryptd ath9k ath9k_common ath9k_hw intel_cstate snd_hda_codec_realtek ath snd_hda_codec_generic mac80211 snd_hda_intel uvcvideo snd_hda_codec videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 snd_hda_core snd_hwdep intel_rapl_perf videobuf2_core videodev snd_pcm cfg80211 ath3k btusb media btrtl snd_seq_midi snd_seq_midi_event snd_rawmidi btbcm btintel snd_seq bluetooth snd_seq_device snd_timer snd joydev input_leds serio_raw soundcore nvidia_uvm(POE) mei_me mei lpc_ich shpchp mac_hid sony_laptop wmi ip6t_REJECT
[13753.148995]  nf_reject_ipv6 nf_log_ipv6 xt_hl ip6t_rt nf_conntrack_ipv6 nf_defrag_ipv6 ipt_REJECT nf_reject_ipv4 nf_log_ipv4 nf_log_common xt_LOG xt_limit xt_tcpudp xt_addrtype nf_conntrack_ipv4 nf_defrag_ipv4 xt_conntrack ip6table_filter ip6_tables nf_conntrack_netbios_ns nf_conntrack_broadcast nf_nat_ftp nf_nat nf_conntrack_ftp nf_conntrack parport_pc iptable_filter ppdev lp parport ip_tables x_tables autofs4 uas usb_storage hid_generic usbhid hid nvidia_drm(POE) nvidia_modeset(POE) nvidia(POE) drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops psmouse firewire_ohci ahci drm r8169 libahci firewire_core sdhci_pci mii crc_itu_t sdhci fjes video
[13753.149022] CPU: 4 PID: 1159 Comm: NetworkManager Tainted: P           OE   4.8.0-46-generic #49-Ubuntu
[13753.149023] Hardware name: Sony Corporation VPCF23P1E/VAIO, BIOS R2150V3 07/22/2011
[13753.149025] task: ffff915a1b640000 task.stack: ffff915a214e0000
[13753.149026] RIP: 0010:[<ffffffffa8e440c3>]  [<ffffffffa8e440c3>] putname+0x43/0x60
[13753.149030] RSP: 0018:ffff915a214e3da8  EFLAGS: 00010246
[13753.149031] RAX: 0000000000000000 RBX: 0000000000000000 RCX: ffff915a1b640000
[13753.149033] RDX: 0000000000000000 RSI: ffff915a1fe3d820 RDI: ffff915a1d982880
[13753.149034] RBP: ffff915a214e3eb8 R08: 000000000001c700 R09: ffffffffa8e5d94e
[13753.149035] R10: ffffea0008766000 R11: ffff915898b3e3f8 R12: ffff915a1d982880
[13753.149036] R13: 0000000000000001 R14: ffff915a214e3f08 R15: ffff915a1ba30cc0
[13753.149038] FS:  00007f01c5fdfe00(0000) GS:ffff915a26b00000(0000) knlGS:0000000000000000
[13753.149039] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[13753.149040] CR2: 00007fa90eb09810 CR3: 00000002215e8000 CR4: 00000000000406e0
[13753.149041] Stack:
[13753.149043]  ffffffffa8e44571 0000000000000000 0000000000000000 000000075e5ccf8a
[13753.149045]  ffff915a1d982044 0000000000000000 ffff915a1f5d60c0 ffff915a21049bc0
[13753.149047]  0000000000000001 000000000000269a 0000000100000000 ffff915a214e3e08
[13753.149050] Call Trace:
[13753.149053]  [<ffffffffa8e44571>] ? filename_lookup+0xf1/0x180
[13753.149056]  [<ffffffffa8e5d940>] ? simple_attr_release+0x20/0x20
[13753.149059]  [<ffffffffa8e0b713>] ? kmem_cache_alloc+0xd3/0x1a0
[13753.149060]  [<ffffffffa8e4412f>] ? getname_flags+0x4f/0x1f0
[13753.149062]  [<ffffffffa8e446d6>] user_path_at_empty+0x36/0x40
[13753.149064]  [<ffffffffa8e314c4>] SyS_access+0xb4/0x220
[13753.149068]  [<ffffffffa949f536>] entry_SYSCALL_64_fastpath+0x1e/0xa8
[13753.149069] Code: 48 8d 47 1c 48 89 e5 53 48 8b 37 48 89 fb 48 39 c6 74 1a 48 8b 3d 7e e8 d1 00 e8 29 7e fc ff 48 89 df e8 d1 7a fc ff 5b 5d f3 c3 <0f> 0b 48 89 fe 48 8b 3d 61 e8 d1 00 e8 0c 7e fc ff 5b 5d eb e9 
[13753.149091] RIP  [<ffffffffa8e440c3>] putname+0x43/0x60
[13753.149093]  RSP <ffff915a214e3da8>
[13753.149095] ---[ end trace 06f8df06b7dd84a1 ]---
[13753.152624] ModemManager[1123]: segfault at 0 ip 00005556c4588b27 sp 00007ffed508cc80 error 4 in ModemManager[5556c4551000+11e000]

```

There is a kernel bug in there. Also, the moment I plug it in, the modem manager show an error. No details, just a report button.

---

### Post by duruttye on 2017-04-06
As far as I know this wireless card doesn't support 5ghz network, but I only know because I can't see it.

Jeremy31, any chance you know what type it is, so maybe I can get one that supports 5 ghz, stick it in instead of this one and be done with it?? :)

---

### Post by jeremy31 on 2017-04-06
The AR9485 doesn't support 5 GHz but Intel has some nice wifi cards that do as long as your computer doesn't have a BIOS whitelist like my Lenovo

---

### Post by duruttye on 2017-04-06
It just doesn't get any easier, right?
What type is it? Cause I took out one from a different laptop, looked the same, but the pins were just not matching up. I didn't know that there are so many different types... I thought it was like with the RAM, ddr2, 3 and so on...

---

### Post by jeremy31 on 2017-04-06
The pins don't really matter, it is the size and placement of the cutout between the pins.  A mini PCIe is a mini PCIe and the ebay link you posted [http://www.ebay.co.uk/itm/SONY-VAIO-PCG-81313M-WIFI-WIRELESS-CARD-AR5B25-/112092196101](http://www.ebay.co.uk/itm/SONY-VAIO-PCG-81313M-WIFI-WIRELESS-CARD-AR5B25-/112092196101) shows a mini PCIe card and something like [img]http://www.legitreviews.com/wp-content/uploads/2014/02/intel-7260-wireless-cards-645x269.jpg[/img]
 will work as long as a BIOS whitelist isn't in place
You might have a M.2 card
[img]http://www.intel.com/content/dam/www/public/us/en/images/product/RWD/wireless-n-7260-rwd.jpg.rendition.intel.web.416.234.jpg[/img]
The M.2 card is on the right and the mini PCIe is the card on the left

---

### Post by duruttye on 2017-04-06
I'll just buy one tomorrow and I'll make it fit with a hammer :)

---

### Post by jeremy31 on 2017-04-06
I have swapped quite a few different mini PCIe wireless cards in the laptops I have without a whitelist and they work, Intel, Broadcom, Realtek, and Atheros

---

### Post by chili555 on 2017-04-07
> Just to justify my struggle, the 2.4 ghz is limited to around 2-3Mbits/sec, This is the *real *problem, isn't it? Jeremy and I often see questions about how to solve an issue involving several increasingly complicated steps until finally, a step doesn't work to band-aid the underlying, real problem.

Frankly, before we proceed further, I'd rather work on the real problem.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Then set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

If these changes do not help, please try:```
sudo modprobe -r ath9k
sudo modprobe ath9k nohwcrypt=1
```If it helps, make it permanent:```
sudo -i
echo "options ath9k nohwcrypt=1"  >>  /etc/modprobe.d/ath9k.conf
exit
```Reboot and let us see your speed test: [http://fast.com](http://fast.com) or else: [http://www.dslreports.com/speedtest](http://www.dslreports.com/speedtest)

---

### Post by duruttye on 2017-04-18
Hello,
Thank you for the detailed guide.
So, here is what I've done:
- Wifi Channel set to 1 - that's no too crowded
- Authentication set to WPA2 - that's the only option, no other option with WPA2
- Regdomain set to GB - that's where I am. (
- I'm using gnome so the IPv6 setting is not active, I think that means that it's ignored.

What I noticed:
- after the changes made to the router, I noticed an improvement on the laptop, but on my phone and tablet as well. It's not the same as the 5ghz band, but as long as it reached 20-25 mbps (and it did), I'm completely satisfied.
- unfortunately I upgraded to 17.04 - with gnome shell (from 16.10). After the upgrade it is probably even worse than before. It drops the connection very often, sometimes it doesn't even see the wifi network, I have the restart the wifi card (by turning wifi on and off). During the upgrade, at one point it asked me if I want to replace the changed network configuration file with the one coming with the original ubuntu and I said yes. In the mean time I am measuring 30-35 mbps with the phone and tablet from the 2.4 Ghz band. The other one is almost constantly stuck at 50 Mbps.

Dmesg is completely full of lines like this:

```
[ 4963.793580] wlp2s0: authenticate with 88:a6:c6:34:f4:5a
[ 4963.814453] wlp2s0: send auth to 88:a6:c6:34:f4:5a (try 1/3)
[ 4963.816390] wlp2s0: authenticated
[ 4963.816811] wlp2s0: associate with 88:a6:c6:34:f4:5a (try 1/3)
[ 4963.820575] wlp2s0: RX AssocResp from 88:a6:c6:34:f4:5a (capab=0x411 status=0 aid=2)
[ 4963.820714] wlp2s0: associated
[ 4963.824764] ath: EEPROM regdomain: 0x833a
[ 4963.824805] ath: EEPROM indicates we should expect a country code
[ 4963.824807] ath: doing EEPROM country->regdmn map search
[ 4963.824808] ath: country maps to regdmn code: 0x37
[ 4963.824809] ath: Country alpha2 being used: GB
[ 4963.824810] ath: Regpair used: 0x37
[ 4963.824811] ath: regdomain 0x833a dynamically updated by country IE

```

```
gksudo gedit /etc/default/crda
```

has in it:

```
REGDOMAIN=GB
```


I am not an expert by far, but is it possible that there is something wrong either with the wifi card or maybe the driver is not fully compatible?

Thank you!!
(and I was away for a couple of days, hence the late reply)

---

### Post by chili555 on 2017-04-18
> [ 4963.824808] ath: country maps to regdmn code: 0x37
[ 4963.824809] ath: Country alpha2 being used: GB
[ 4963.824810] ath: Regpair used: 0x37
[ 4963.824811] ath: regdomain 0x833a dynamically updated by country [COLOR="#FF0000"]IE[/COLOR]

Is it possible that you are in Ireland, which has its own country code? Is connectivity improved if you try:

```
sudo iw reg set IE
```

 > I'm using gnome so the IPv6 setting is not active, I think that means that it's ignored.

Other than changing an obscure file deep in the warp core, the only place I am aware that it is done is in Network Manager: [https://digitizor.com/wp-content/uploads/2009/11/disable-ipv6-network.png](https://digitizor.com/wp-content/uploads/2009/11/disable-ipv6-network.png) This is for ethernet but the same is true of wireless. Please check and revise if needed.

> unfortunately I upgraded to 17.04 - with gnome shell (from 16.10). After the upgrade it is probably even worse than before. It drops the connection very often, sometimes it doesn't even see the wifi network, I have the restart the wifi card (by turning wifi on and off). 

There is a bug in Network Manager in 17.04 that reputedly affects USB and some Atheros devices. Please try the fix here: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1681513](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1681513) See response #1.

Reboot and let us hear the result.

---

### Post by duruttye on 2017-04-18
Hi chili555,

I'm almost in the heart of London, so I'm pretty confident it's not Ireland :)

I checked the network manager bug and applied the fix from the comments and now the speed is up to almost 4 mbps, before it measured it in kbps - it was so slow. I used it for a half an hour, at least it didn't disconnect as before, also the dmesg has no messages like before, probably because pthe connection is not breaking up all the time.

I'll leave it like this for a couple of days, let's see how it goes.

Although, I'm also seeing speeds like 330 kbps, when at the same time (after the test finished), same band, same network, the android tablet measures 20-25 mbps.

Thank you again!

---

