---
title: "A-link wl54usb card not setting correct channel"
date: 2006-08-12
forum: Networking &amp; Wireless
---

### Post by shemyak on 2006-08-12
I have an A-link wl54usb wireless USB adapter. Drivers installed from [http://zd1211.ath.cx/](http://zd1211.ath.cx/). Modprobe gives the following in /var/log/messages:

Aug 12 10:35:16 localhost kernel: [204479.648524] ZD1211B - [http://zd1211.ath.cx/](http://zd1211.ath.cx/)
Aug 12 10:35:16 localhost kernel: [204479.649025] Based on [www.zydas.com.tw](www.zydas.com.tw) driver version 2.0.0.0
Aug 12 10:35:16 localhost kernel: [204479.701274] usb 2-6: reset high speed USB device using ehci_hcd and address 18
Aug 12 10:35:16 localhost kernel: [204479.770595] Release Ver = 4810
Aug 12 10:35:16 localhost kernel: [204479.770637] EEPORM Ver = 4810
Aug 12 10:35:17 localhost kernel: [204479.832601] AllowedChannel = 00010000
Aug 12 10:35:17 localhost kernel: [204479.832605] Region:48
Aug 12 10:35:17 localhost kernel: [204479.945242] usbcore: registered new driver zd1211b
Aug 12 10:35:17 localhost kernel: [204480.103691] ADDRCONF(NETDEV_UP): wlan0: link is not ready

After that, the device wlan0 comes up, but can't see the access point. Encryption is turned off at both AP and card. 

The card works fine in the neighbour Windows machine, using channel 1. Here is the output of iwlist:

# iwlist wlan0 frequency
wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Current Frequency:3.32084 GHz

The last line makes me think that something is wrong at the radio level. Changing frequency in managed mode is impossible; I switch to ad-hoc mode and try to switch the channel. Command succeeds, but the frequency is not being set:

# iwconfig wlan0 mode ad-hoc
# iwconfig wlan0 channel 1
(or, with the same result - iwconfig wlan0 freq 2.412G)
# iwconfig wlan0
wlan0     802.11b/g NIC  ESSID:"<my correct ESSID>"
          Mode:Ad-Hoc  Frequency=3.32084 GHz  Cell: Not-Associated
          Bit Rate:1 Mb/s
          Retry:off   RTS thr=2432 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:161
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

There is still that suspicious frequency.
Thanks in advance for any pointers.

---

