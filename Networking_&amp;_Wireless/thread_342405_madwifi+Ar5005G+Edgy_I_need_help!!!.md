---
title: "madwifi+Ar5005G+Edgy I need help!!!"
date: 2007-01-20
forum: Networking &amp; Wireless
---

### Post by reyes116 on 2007-01-20
Hi! I have a bi trouble, I have an Acer Aspire 5040, it runs ubuntu, but i can't to configure the wireless card. The wireless card have an Atheros AR5005G Chip, i have installed acer_acpi 0.3. 
This is my trouble:
I have this script:
#! /bin/sh
lsmod | grep ath
rmmod ath_pci
rmmod ath_rate_sample
rmmod ath_hal
rmmod wlan
lsmod | grep ath
modprobe ath_pci
lsmod | grep ath
iwconfig ath0 power on
iwlist ath0 scan
exit

When i run it as root:

root@quentin-ubuntu:/home/quentin/Desktop# ./on
ath_pci               111528  0 
ath_rate_sample        19200  1 ath_pci
wlan                  238560  5 wlan_wep,wlan_scan_sta,ath_pci,ath_rate_sample
ath_hal               220912  3 ath_pci,ath_rate_sample
ERROR: Module wlan is in use by wlan_wep,wlan_scan_sta
ath_pci               111528  0 
ath_rate_sample        19200  1 ath_pci
ath_hal               220912  3 ath_pci,ath_rate_sample
wlan                  238560  5 ath_pci,ath_rate_sample,wlan_wep,wlan_scan_sta

Message from syslogd@quentin-ubuntu at Sat Jan 20 00:58:22 2007 ...
quentin-ubuntu kernel: [ 1284.197737] Disabling IRQ #209
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device ath0 ; Operation not supported.
ath0      Interface doesn't support scanning : Invalid argument

If i run iwconfig:

root@quentin-ubuntu:/home/quentin/Desktop# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11b  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:0 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I can't to power on:

root@quentin-ubuntu:/home/quentin/Desktop# iwconfig ath0 power on
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device ath0 ; Operation not supported.

I can't to scan:

root@quentin-ubuntu:/home/quentin/Desktop# iwlist ath0 scan
ath0      Interface doesn't support scanning : Invalid argument

Please i need your help. Before I I run as root:
modprobe acer_acpi
echo "enabled : 1">/proc/acpi/acer/wireless

In the [web of madwifi]("http://madwifi.org/wiki/Compatibility#AtherosAR5005G") I have read that AR5005G chip runs in Acer Aspire 5040 with madwifi, acer_acpi. I need your help please.

---

### Post by spacetree on 2007-02-14
Ive got a similar problem here.

I also get the infamous SET failed on device ath0; Operation not permitted.

In my case i think i dont need to use de acer_acpi , because i can actually see the device, and even i can see the wireless networks in my range... but i cant connect.....

mi iwconfig has the same output, but instead of Tx-Power:0 i have  9


someone has an idea?

---

