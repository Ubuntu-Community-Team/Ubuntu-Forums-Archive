---
title: "WiFi issues with Ralink RT3290LE on HP Notebook"
date: 2016-01-07
forum: Networking &amp; Wireless
---

### Post by nicotra-davide-5 on 2016-01-07
Hi,
I'm not new to linux but I'm new to this forum so I would like to thank everyone for the excellent job you are doing here.

Let me explain my problem... I'm having problems with my notebook **HP Envy 15 j100sl** bought a year ago.
With ANY linux distro I've tried I have the same annoying problem: firstly it seems that my wifi mpcie card **RT3290LE **
works perfectly fine with no 3th parts drivers required but suddenly it stops working and I need to shutdown and reboot
my notebook. Googling the problem I've found many people experiencing similar problems with this card; they often solve
the problem installing the "officials" ralink drivers that had been removed (nobody knows why) from mediatek website.
However I manage to install it and it seems to work but, as before, my wifi card go down after a while and it is unpredictable
when it would happen. It seems related to if my power adapter is connected or not (?).

I'm currently running Debian but same issues here.

Here the dmesg output when ralink driver is failing:
```
Jan  7 14:17:04 Deadpool kernel: [  828.027059] RT3290_AsicTxAlcGetAutoAgcOffset: Incorrect desired TSSI or current TSSI
Jan  7 14:17:12 Deadpool kernel: [  836.033510] RT3290_AsicTxAlcGetAutoAgcOffset: Incorrect desired TSSI or current TSSI
Jan  7 14:17:20 Deadpool kernel: [  844.040026] RT3290_AsicTxAlcGetAutoAgcOffset: Incorrect desired TSSI or current TSSI
Jan  7 14:17:32 Deadpool kernel: [  856.049724] RT3290_AsicTxAlcGetAutoAgcOffset: Incorrect desired TSSI or current TSSI
Jan  7 14:17:52 Deadpool kernel: [  876.069798] RT3290_AsicTxAlcGetAutoAgcOffset: Incorrect desired TSSI or current TSSI
Jan  7 14:18:00 Deadpool kernel: [  884.076234] RT3290_AsicTxAlcGetAutoAgcOffset: Incorrect desired TSSI or current TSSI
Jan  7 14:18:04 Deadpool kernel: [  888.079461] RT3290_AsicTxAlcGetAutoAgcOffset: Incorrect desired TSSI or current TSSI
Jan  7 14:18:11 Deadpool kernel: [  895.086378] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 1449
Jan  7 14:18:20 Deadpool kernel: [  904.112460] RT3290_AsicTxAlcGetAutoAgcOffset: Incorrect desired TSSI or current TSSI
Jan  7 14:18:32 Deadpool kernel: [  916.122157] RT3290_AsicTxAlcGetAutoAgcOffset: Incorrect desired TSSI or current TSSI
Jan  7 14:19:00 Deadpool kernel: [  944.144669] RT3290_AsicTxAlcGetAutoAgcOffset: Incorrect desired TSSI or current TSSI
Jan  7 14:19:04 Deadpool kernel: [  948.147914] RT3290_AsicTxAlcGetAutoAgcOffset: Incorrect desired TSSI or current TSSI
Jan  7 14:19:12 Deadpool kernel: [  956.154350] RT3290_AsicTxAlcGetAutoAgcOffset: Incorrect desired TSSI or current TSSI
Jan  7 14:19:32 Deadpool kernel: [  976.170567] RT3290_AsicTxAlcGetAutoAgcOffset: Incorrect desired TSSI or current TSSI
Jan  7 14:19:47 Deadpool kernel: [  991.182657] ERROR!!! RTMP_PCIE_PS_L3_BBP_IO_READ8(viaMCU=1) read R66 fail(reason:clk=0,busy=1)
Jan  7 14:19:47 Deadpool kernel: [  991.182745] ERROR!!! RF read R49=0xFFFFFFFF fail, i[100], k[0]
Jan  7 14:19:47 Deadpool kernel: [  991.182815] Retry count exhausted or device removed!!!
Jan  7 14:19:47 Deadpool kernel: [  991.182881] ERROR!!! RTMP_PCIE_PS_L3_BBP_IO_READ8(viaMCU=1) read R1 fail(reason:clk=0,busy=1)
Jan  7 14:19:47 Deadpool kernel: [  991.183236] ERROR!!! H2M_MAILBOX still hold by MCU. command fail(2]
```

The row about TSSI is floodding my dmesg even when the wifi card is correctly working.

Any ideas?
Feel free to ask my any details you want.

ps. sorry for my poor english

---

### Post by slickymaster on 2016-01-07
*Moved to the ***Networking & Wireless*** sub-forum*

Please download and run the [wireless info script]("https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info"), which will gather information to help diagnose your system. It will create the file "wireless-info.txt" at the location it is run from, and depending on its size, an additional archive called "wireless-info.tar.gz", for attaching on the forums

---

### Post by nicotra-davide-5 on 2016-01-07
[ATTACH]266585[/ATTACH] wireless info script with rt2800pci module (the wifi seems to work at the moment I'm waiting for the "disaster")
[ATTACH]266586[/ATTACH] wireless info script with rt3290sta from ralink

```
[12010.509768] ieee80211 phy1: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
```
With the rt2800pci driver I get flooded with this message before my card stop working,
And trying to reset the card I get
```
[12367.197558] ieee80211 phy1: rt2800_wait_csr_ready: Error - Unstable hardware
```
any ideas?

---

### Post by chili555 on 2016-01-07
> Unstable hardwareIf you've had the problem with several drivers and several Linux distros and see 'Unstable hardware,' I'd take it at face value and get a different device. If you don't want to try to thread the whitelist gauntlet, and I wouldn't, why not try a USB?

One possible example: [http://www.amazon.com/gp/product/B002SZEOLG?keywords=tplink%20722&qid=1452199476&ref_=sr_1_1&sr=8-1](http://www.amazon.com/gp/product/B002SZEOLG?keywords=tplink%20722&qid=1452199476&ref_=sr_1_1&sr=8-1)

If you go this route, don't forget to blacklist the internal.

---

### Post by nicotra-davide-5 on 2016-01-08
> **chili555 said:**
> If you've had the problem with several drivers and several Linux distros and see 'Unstable hardware,' I'd take it at face value and get a different device. If you don't want to try to thread the whitelist gauntlet, and I wouldn't, why not try a USB?

One possible example: [http://www.amazon.com/gp/product/B002SZEOLG?keywords=tplink%20722&qid=1452199476&ref_=sr_1_1&sr=8-1](http://www.amazon.com/gp/product/B002SZEOLG?keywords=tplink%20722&qid=1452199476&ref_=sr_1_1&sr=8-1)

If you go this route, don't forget to blacklist the internal.
An usb wifi dongle is not that handy. Consider that I'm currently using a wireless usb mouse so a usb port is permanently busy, my rt3290 is a combo wifi bluetooth and bluetooth is not working too so I'd need another usb bluetooth adapter and this would mean another busy usb port. It would become difficult even moving files between two usb storage becouse I'd be out of usb ports...I'm gonna look for clear information about bios hardware restrictions on my laptop...

Finally "solved" the problem buying a new Wifi-BT combo card.
Today I got an Intel Wireless AC 7260 WIFI-BT, and it worked fine with last BIOS update on my HP Envy 15 j104. 
Thank you and good posting

---

