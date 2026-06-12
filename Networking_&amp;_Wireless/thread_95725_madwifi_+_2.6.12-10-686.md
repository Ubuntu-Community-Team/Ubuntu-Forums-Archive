---
title: "madwifi + 2.6.12-10-686"
date: 2005-11-27
forum: Networking &amp; Wireless
---

### Post by squeezer on 2005-11-27
Hello

I am using madwifi on the new 2.6.12-10-686 kernel, but it seems to me that the problem i describe is also present in older kernel version, well:
I installed the madwifi driver as described in the Ubuntu Wiki ([https://wiki.ubuntu.com/MoreRecentMadwifiHowto](https://wiki.ubuntu.com/MoreRecentMadwifiHowto)) and the driver works, but
when I connect to my wlan (even though sitting next to the access point) the bit rates vary a lot.
> 
ath0      IEEE 802.11g  ESSID:"GioKL"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:04:0E:1B:88:4C
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:...  Security mode:restricted


I once get 1Mb/s a second later 54Mbit then 12 aso... So while i am downloading I get rates from 90kb/s down to 12 up to 50 aso...

Here is an extract of my Modules
> 
#root@vaio:/home/marc# lsmod | grep ath
ath_pci                80956  0
ath_rate_sample        16584  1 ath_pci
wlan                  145916  4 wlan_wep,ath_pci,ath_rate_sample
ath_hal               148304  3 ath_pci,ath_rate_sample


My laptop is a Sony Vaio PCG-GRT916Z

I do not exactely know which information are necessary to detect the problem, but if you need some, just post and I´ll add them to this thread afap.

Thanks a lot

Marc

---

### Post by Lambert on 2005-11-27
Most cards adjust bit rate depending on channel noise. The more channel noise, it adjusts the bit rate lower. The 2.4 ghz range which is used on wireless is a very busy frequency.

You can try to change channels you're using or try this command

sudo iwconfig ath0 rate xxM

where xx = a rate 54, 11 etc....

This command locks the rate on the device. You can always change back to auto by ....ath0 rate auto

---

### Post by squeezer on 2005-11-27
hello

thanks a lot for this quick answer, i turned it down to 18M and i also scanned the available frequences using iwlist scan but the problem is still there.

are there maybe other constraints? i ve seen something like DB setting ans power settings?
or might this be due to the kernel version? i am a newbie to linux so i do not exactely know where the problems might be.

thanks

marc

---

