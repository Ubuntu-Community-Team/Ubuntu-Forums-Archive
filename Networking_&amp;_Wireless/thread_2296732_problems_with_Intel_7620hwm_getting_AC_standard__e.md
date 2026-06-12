---
title: "problems with Intel 7620hwm getting AC standard / errors during backporting iwlwifi"
date: 2015-09-28
forum: Networking &amp; Wireless
---

### Post by rolandd2 on 2015-09-28
Hello, 
i try to run my Intel 7620HMW on my Tegra K1.
Its running the current version 3.10.40-gdacac96 (armhf).
I also installed the current FW packet for the Intel Wifi Card.
So /lib/firmware# find . | grep  '7260' results:


```
          
[LIST=1]
[*]./iwlwifi-7260-13.ucode 
[*]./iwlwifi-7260-7.ucode 
[*]./iwlwifi-7260-12.ucode 
[*]./iwlwifi-7260-8.ucode 
[*]./iwlwifi-7260-14.ucode 
[*]./iwlwifi-7260-15.ucode 
[*]./iwlwifi-7260-10.ucode 
[*]./iwlwifi-7260-9.ucode 
[*]./LICENSE.iwlwifi-7260-ucode 
[*]./README.iwlwifi-7260-ucode 
[/LIST]
 

```

Here is my iwconfig wlan0, note that there is no ac available     
```


[LIST=1]
[*]wlan0     IEEE 802.11abgn  ESSID:off/any 
[*]          Mode:Managed  Frequency:5.18 GHz  Access Point: Not-Associated 
[*]          Tx-Power=20 dBm 
[*]          Retry  long limit:7   RTS thr:off   Fragment thr:off 
[*]          Encryption key:off 
[*]          Power Management:on 
[/LIST]
 

```
modinfo iwlwifi

```


[LIST=1]
[*]filename:       /lib/modules/3.10.40-gdacac96/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko 
[*]license:        GPL 
[*]author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com> 
[*]version:        in-tree: 
[*]description:    Intel(R) Wireless WiFi driver for Linux 
[*]firmware:       iwlwifi-100-5.ucode 
[*]firmware:       iwlwifi-1000-5.ucode 
[*]firmware:       iwlwifi-135-6.ucode 
[*]firmware:       iwlwifi-105-6.ucode 
[*]firmware:       iwlwifi-2030-6.ucode 
[*]firmware:       iwlwifi-2000-6.ucode 
[*]firmware:       iwlwifi-5150-2.ucode 
[*]firmware:       iwlwifi-5000-5.ucode 
[*]firmware:       iwlwifi-6000g2b-6.ucode 
[*]firmware:       iwlwifi-6000g2a-5.ucode 
[*]firmware:       iwlwifi-6050-5.ucode 
[*]firmware:       iwlwifi-6000-4.ucode 
[*]firmware:       iwlwifi-3160-7.ucode 
[*]firmware:       iwlwifi-7260-7.ucode 
[*]srcversion:     F5654BE9F9C3C64A4666DE1 
[*]alias:          pci:v00008086d000008B3sv*sd00008570bc*sc*i* 
[*]alias:          pci:v00008086d000008B3sv*sd00008470bc*sc*i* 
[*]alias:          pci:v00008086d000008B4sv*sd00008270bc*sc*i* 
[*]alias:          pci:v00008086d000008B3sv*sd00008062bc*sc*i* 
[*]alias:          pci:v00008086d000008B3sv*sd00008060bc*sc*i* 
[*]alias:          pci:v00008086d000008B3sv*sd00008172bc*sc*i* 
[*]alias:          pci:v00008086d000008B3sv*sd00008170bc*sc*i* 
[*]alias:          pci:v00008086d000008B3sv*sd00008072bc*sc*i* 
[*]alias:          pci:v00008086d000008B3sv*sd00008070bc*sc*i* 
[*]alias:          pci:v00008086d000008B4sv*sd00000370bc*sc*i* 
[*]alias:          pci:v00008086d000008B3sv*sd00000472bc*sc*i* 
[*]alias:          pci:v00008086d000008B3sv*sd00000470bc*sc*i* 
[*]alias:          pci:v00008086d000008B4sv*sd00000272bc*sc*i* 
[*]alias:          pci:v00008086d000008B4sv*sd00000270bc*sc*i* 
[*]alias:          pci:v00008086d000008B3sv*sd00000062bc*sc*i* 
[*]alias:          pci:v00008086d000008B3sv*sd00000060bc*sc*i* 
[*]alias:          pci:v00008086d000008B3sv*sd00000172bc*sc*i* 
[*]alias:          pci:v00008086d000008B3sv*sd00000170bc*sc*i* 
[*]alias:          pci:v00008086d000008B3sv*sd00000072bc*sc*i* 
[*]alias:          pci:v00008086d000008B3sv*sd00000070bc*sc*i* 
[*]alias:          pci:v00008086d000008B1sv*sd0000C420bc*sc*i* 
[*]alias:          pci:v00008086d000008B2sv*sd0000C220bc*sc*i* 
[*]alias:          pci:v00008086d000008B1sv*sd0000C02Abc*sc*i* 
[*]alias:          pci:v00008086d000008B1sv*sd0000C020bc*sc*i* 
[*]alias:          pci:v00008086d000008B1sv*sd0000C360bc*sc*i* 
[*]alias:          pci:v00008086d000008B2sv*sd0000C370bc*sc*i* 
[*]alias:          pci:v00008086d000008B1sv*sd0000C560bc*sc*i* 
[*]alias:          pci:v00008086d000008B1sv*sd0000C570bc*sc*i* 
[*]alias:          pci:v00008086d000008B1sv*sd0000C462bc*sc*i* 
[*]alias:          pci:v00008086d000008B1sv*sd0000C460bc*sc*i* 
[*]alias:          pci:v00008086d000008B1sv*sd0000C472bc*sc*i* 
[*]alias:          pci:v00008086d000008B1sv*sd0000C470bc*sc*i* 
[*]alias:          pci:v00008086d000008B2sv*sd0000C262bc*sc*i* 
[*]alias:          pci:v00008086d000008B2sv*sd0000C26Abc*sc*i* 
[*]alias:          pci:v00008086d000008B2sv*sd0000C260bc*sc*i* 
[*]alias:          pci:v00008086d000008B2sv*sd0000C272bc*sc*i* 
[*]alias:          pci:v00008086d000008B2sv*sd0000C270bc*sc*i* 
[*]alias:          pci:v00008086d000008B1sv*sd0000C760bc*sc*i* 
[*]alias:          pci:v00008086d000008B1sv*sd0000C770bc*sc*i* 
[*]alias:          pci:v00008086d000008B1sv*sd0000C162bc*sc*i* 
[*]alias:          pci:v00008086d000008B1sv*sd0000C062bc*sc*i* 
[*]alias:          pci:v00008086d000008B1sv*sd0000C160bc*sc*i* 
[*]alias:          pci:v00008086d000008B1sv*sd0000C06Abc*sc*i* 
[*]alias:          pci:v00008086d000008B1sv*sd0000C060bc*sc*i* 
[*]alias:          pci:v00008086d000008B1sv*sd0000C170bc*sc*i* 
[*]alias:          pci:v00008086d000008B1sv*sd0000C072bc*sc*i* 
[*]alias:          pci:v00008086d000008B1sv*sd0000C070bc*sc*i* 
[*]alias:          pci:v00008086d000008B1sv*sd00004420bc*sc*i* 
[*]alias:          pci:v00008086d000008B2sv*sd00004220bc*sc*i* 
[*]alias:          pci:v00008086d000008B1sv*sd0000402Abc*sc*i* 
[*]alias:          pci:v00008086d000008B1sv*sd00004020bc*sc*i* 
[*]alias:          pci:v00008086d000008B1sv*sd00005070bc*sc*i* 
[*]alias:          pci:v00008086d000008B2sv*sd00004360bc*sc*i* 
[*]alias:          pci:v00008086d000008B2sv*sd00004370bc*sc*i* 
[*]alias:          pci:v00008086d000008B1sv*sd00004560bc*sc*i* 
[*]alias:          pci:v00008086d000008B1sv*sd00004570bc*sc*i* 
[*]alias:          pci:v00008086d000008B1sv*sd0000486Ebc*sc*i* 
[*]alias:          pci:v00008086d000008B1sv*sd00004870bc*sc*i* 
[*]alias:          pci:v00008086d000008B1sv*sd00004462bc*sc*i* 
[*]alias:          pci:v00008086d000008B1sv*sd0000446Abc*sc*i* 
[*]alias:          pci:v00008086d000008B1sv*sd00004460bc*sc*i* 
[*]alias:          pci:v00008086d000008B1sv*sd00004472bc*sc*i* 
[*]alias:          pci:v00008086d000008B1sv*sd00004470bc*sc*i* 
[*]alias:          pci:v00008086d000008B2sv*sd00004262bc*sc*i* 
[*]alias:          pci:v00008086d000008B2sv*sd0000426Abc*sc*i* 
[*]alias:          pci:v00008086d000008B2sv*sd00004260bc*sc*i* 
[*]alias:          pci:v00008086d000008B2sv*sd00004272bc*sc*i* 
[*]alias:          pci:v00008086d000008B2sv*sd00004270bc*sc*i* 
[*]alias:          pci:v00008086d000008B1sv*sd00004162bc*sc*i* 
[*]alias:          pci:v00008086d000008B1sv*sd00004062bc*sc*i* 
[*]alias:          pci:v00008086d000008B1sv*sd00004160bc*sc*i* 
[*]alias:          pci:v00008086d000008B1sv*sd0000406Abc*sc*i* 
[*]alias:          pci:v00008086d000008B1sv*sd00004060bc*sc*i* 
[*]alias:          pci:v00008086d000008B1sv*sd00004170bc*sc*i* 
[*]alias:          pci:v00008086d000008B1sv*sd00004072bc*sc*i* 
[*]alias:          pci:v00008086d000008B1sv*sd00004070bc*sc*i* 
[*]alias:          pci:v00008086d00000892sv*sd00000462bc*sc*i* 
[*]alias:          pci:v00008086d00000893sv*sd00000262bc*sc*i* 
[*]alias:          pci:v00008086d00000892sv*sd00000062bc*sc*i* 
[*]alias:          pci:v00008086d00000894sv*sd00000822bc*sc*i* 
[*]alias:          pci:v00008086d00000894sv*sd00000422bc*sc*i* 
[*]alias:          pci:v00008086d00000895sv*sd00000222bc*sc*i* 
[*]alias:          pci:v00008086d00000894sv*sd00000022bc*sc*i* 
[*]alias:          pci:v00008086d0000088Fsv*sd00005260bc*sc*i* 
[*]alias:          pci:v00008086d0000088Esv*sd00004860bc*sc*i* 
[*]alias:          pci:v00008086d0000088Esv*sd0000446Abc*sc*i* 
[*]alias:          pci:v00008086d0000088Esv*sd00004460bc*sc*i* 
[*]alias:          pci:v00008086d0000088Fsv*sd0000426Abc*sc*i* 
[*]alias:          pci:v00008086d0000088Fsv*sd00004260bc*sc*i* 
[*]alias:          pci:v00008086d0000088Esv*sd0000406Abc*sc*i* 
[*]alias:          pci:v00008086d0000088Esv*sd00004060bc*sc*i* 
[*]alias:          pci:v00008086d00000887sv*sd00004462bc*sc*i* 
[*]alias:          pci:v00008086d00000888sv*sd00004262bc*sc*i* 
[*]alias:          pci:v00008086d00000887sv*sd00004062bc*sc*i* 
[*]alias:          pci:v00008086d00000890sv*sd00004822bc*sc*i* 
[*]alias:          pci:v00008086d00000890sv*sd00004422bc*sc*i* 
[*]alias:          pci:v00008086d00000891sv*sd00004222bc*sc*i* 
[*]alias:          pci:v00008086d00000890sv*sd00004022bc*sc*i* 
[*]alias:          pci:v00008086d00000896sv*sd00005027bc*sc*i* 
[*]alias:          pci:v00008086d00000896sv*sd00005025bc*sc*i* 
[*]alias:          pci:v00008086d00000897sv*sd00005017bc*sc*i* 
[*]alias:          pci:v00008086d00000897sv*sd00005015bc*sc*i* 
[*]alias:          pci:v00008086d00000896sv*sd00005007bc*sc*i* 
[*]alias:          pci:v00008086d00000896sv*sd00005005bc*sc*i* 
[*]alias:          pci:v00008086d000008AEsv*sd00001027bc*sc*i* 
[*]alias:          pci:v00008086d000008AEsv*sd00001025bc*sc*i* 
[*]alias:          pci:v00008086d000008AFsv*sd00001017bc*sc*i* 
[*]alias:          pci:v00008086d000008AFsv*sd00001015bc*sc*i* 
[*]alias:          pci:v00008086d000008AEsv*sd00001007bc*sc*i* 
[*]alias:          pci:v00008086d000008AEsv*sd00001005bc*sc*i* 
[*]alias:          pci:v00008086d00000084sv*sd00001316bc*sc*i* 
[*]alias:          pci:v00008086d00000084sv*sd00001216bc*sc*i* 
[*]alias:          pci:v00008086d00000083sv*sd00001326bc*sc*i* 
[*]alias:          pci:v00008086d00000083sv*sd00001226bc*sc*i* 
[*]alias:          pci:v00008086d00000083sv*sd00001306bc*sc*i* 
[*]alias:          pci:v00008086d00000083sv*sd00001206bc*sc*i* 
[*]alias:          pci:v00008086d00000084sv*sd00001315bc*sc*i* 
[*]alias:          pci:v00008086d00000084sv*sd00001215bc*sc*i* 
[*]alias:          pci:v00008086d00000083sv*sd00001325bc*sc*i* 
[*]alias:          pci:v00008086d00000083sv*sd00001225bc*sc*i* 
[*]alias:          pci:v00008086d00000083sv*sd00001305bc*sc*i* 
[*]alias:          pci:v00008086d00000083sv*sd00001205bc*sc*i* 
[*]alias:          pci:v00008086d00000886sv*sd00001317bc*sc*i* 
[*]alias:          pci:v00008086d00000886sv*sd00001315bc*sc*i* 
[*]alias:          pci:v00008086d00000885sv*sd00001327bc*sc*i* 
[*]alias:          pci:v00008086d00000885sv*sd00001325bc*sc*i* 
[*]alias:          pci:v00008086d00000885sv*sd00001307bc*sc*i* 
[*]alias:          pci:v00008086d00000885sv*sd00001305bc*sc*i* 
[*]alias:          pci:v00008086d00000089sv*sd00001316bc*sc*i* 
[*]alias:          pci:v00008086d00000089sv*sd00001311bc*sc*i* 
[*]alias:          pci:v00008086d00000087sv*sd00001326bc*sc*i* 
[*]alias:          pci:v00008086d00000087sv*sd00001321bc*sc*i* 
[*]alias:          pci:v00008086d00000087sv*sd00001306bc*sc*i* 
[*]alias:          pci:v00008086d00000087sv*sd00001301bc*sc*i* 
[*]alias:          pci:v00008086d00000091sv*sd00005226bc*sc*i* 
[*]alias:          pci:v00008086d00000091sv*sd00005225bc*sc*i* 
[*]alias:          pci:v00008086d00000091sv*sd00005221bc*sc*i* 
[*]alias:          pci:v00008086d00000091sv*sd00005207bc*sc*i* 
[*]alias:          pci:v00008086d00000091sv*sd00005206bc*sc*i* 
[*]alias:          pci:v00008086d00000091sv*sd00005205bc*sc*i* 
[*]alias:          pci:v00008086d00000091sv*sd00005201bc*sc*i* 
[*]alias:          pci:v00008086d00000090sv*sd00005216bc*sc*i* 
[*]alias:          pci:v00008086d00000090sv*sd00005215bc*sc*i* 
[*]alias:          pci:v00008086d00000090sv*sd00005211bc*sc*i* 
[*]alias:          pci:v00008086d0000008Bsv*sd00005317bc*sc*i* 
[*]alias:          pci:v00008086d0000008Bsv*sd00005315bc*sc*i* 
[*]alias:          pci:v00008086d0000008Asv*sd00005327bc*sc*i* 
[*]alias:          pci:v00008086d0000008Asv*sd00005325bc*sc*i* 
[*]alias:          pci:v00008086d0000008Asv*sd00005307bc*sc*i* 
[*]alias:          pci:v00008086d0000008Asv*sd00005305bc*sc*i* 
[*]alias:          pci:v00008086d00000082sv*sd00001305bc*sc*i* 
[*]alias:          pci:v00008086d00000082sv*sd00001304bc*sc*i* 
[*]alias:          pci:v00008086d00000082sv*sd00004820bc*sc*i* 
[*]alias:          pci:v00008086d00000085sv*sd0000C228bc*sc*i* 
[*]alias:          pci:v00008086d00000085sv*sd0000C220bc*sc*i* 
[*]alias:          pci:v00008086d00000082sv*sd0000C020bc*sc*i* 
[*]alias:          pci:v00008086d00000085sv*sd00001316bc*sc*i* 
[*]alias:          pci:v00008086d00000085sv*sd00001318bc*sc*i* 
[*]alias:          pci:v00008086d00000085sv*sd00001311bc*sc*i* 
[*]alias:          pci:v00008086d00000082sv*sd00001328bc*sc*i* 
[*]alias:          pci:v00008086d00000082sv*sd00001326bc*sc*i* 
[*]alias:          pci:v00008086d00000082sv*sd00001321bc*sc*i* 
[*]alias:          pci:v00008086d00000082sv*sd00001308bc*sc*i* 
[*]alias:          pci:v00008086d00000082sv*sd00001307bc*sc*i* 
[*]alias:          pci:v00008086d00000082sv*sd00001306bc*sc*i* 
[*]alias:          pci:v00008086d00000082sv*sd00001301bc*sc*i* 
[*]alias:          pci:v00008086d00004239sv*sd00001316bc*sc*i* 
[*]alias:          pci:v00008086d00004239sv*sd00001311bc*sc*i* 
[*]alias:          pci:v00008086d00004238sv*sd00001118bc*sc*i* 
[*]alias:          pci:v00008086d00004238sv*sd00001111bc*sc*i* 
[*]alias:          pci:v00008086d0000422Csv*sd00001326bc*sc*i* 
[*]alias:          pci:v00008086d0000422Csv*sd00001321bc*sc*i* 
[*]alias:          pci:v00008086d0000422Csv*sd00001307bc*sc*i* 
[*]alias:          pci:v00008086d0000422Csv*sd00001306bc*sc*i* 
[*]alias:          pci:v00008086d0000422Csv*sd00001301bc*sc*i* 
[*]alias:          pci:v00008086d0000422Bsv*sd00001128bc*sc*i* 
[*]alias:          pci:v00008086d0000422Bsv*sd00001121bc*sc*i* 
[*]alias:          pci:v00008086d0000422Bsv*sd00001108bc*sc*i* 
[*]alias:          pci:v00008086d0000422Bsv*sd00001101bc*sc*i* 
[*]alias:          pci:v00008086d0000423Dsv*sd00001316bc*sc*i* 
[*]alias:          pci:v00008086d0000423Dsv*sd00001216bc*sc*i* 
[*]alias:          pci:v00008086d0000423Dsv*sd00001311bc*sc*i* 
[*]alias:          pci:v00008086d0000423Dsv*sd00001211bc*sc*i* 
[*]alias:          pci:v00008086d0000423Csv*sd00001326bc*sc*i* 
[*]alias:          pci:v00008086d0000423Csv*sd00001321bc*sc*i* 
[*]alias:          pci:v00008086d0000423Csv*sd00001221bc*sc*i* 
[*]alias:          pci:v00008086d0000423Csv*sd00001306bc*sc*i* 
[*]alias:          pci:v00008086d0000423Csv*sd00001206bc*sc*i* 
[*]alias:          pci:v00008086d0000423Csv*sd00001301bc*sc*i* 
[*]alias:          pci:v00008086d0000423Csv*sd00001201bc*sc*i* 
[*]alias:          pci:v00008086d0000423Bsv*sd00001011bc*sc*i* 
[*]alias:          pci:v00008086d0000423Asv*sd00001021bc*sc*i* 
[*]alias:          pci:v00008086d0000423Asv*sd00001001bc*sc*i* 
[*]alias:          pci:v00008086d00004236sv*sd00001114bc*sc*i* 
[*]alias:          pci:v00008086d00004236sv*sd00001014bc*sc*i* 
[*]alias:          pci:v00008086d00004236sv*sd00001111bc*sc*i* 
[*]alias:          pci:v00008086d00004236sv*sd00001011bc*sc*i* 
[*]alias:          pci:v00008086d00004235sv*sd00001104bc*sc*i* 
[*]alias:          pci:v00008086d00004235sv*sd00001004bc*sc*i* 
[*]alias:          pci:v00008086d00004235sv*sd00001101bc*sc*i* 
[*]alias:          pci:v00008086d00004235sv*sd00001001bc*sc*i* 
[*]alias:          pci:v00008086d00004235sv*sd00001124bc*sc*i* 
[*]alias:          pci:v00008086d00004235sv*sd00001024bc*sc*i* 
[*]alias:          pci:v00008086d00004235sv*sd00001121bc*sc*i* 
[*]alias:          pci:v00008086d00004235sv*sd00001021bc*sc*i* 
[*]alias:          pci:v00008086d00004237sv*sd00001316bc*sc*i* 
[*]alias:          pci:v00008086d00004237sv*sd00001216bc*sc*i* 
[*]alias:          pci:v00008086d00004237sv*sd00001315bc*sc*i* 
[*]alias:          pci:v00008086d00004237sv*sd00001215bc*sc*i* 
[*]alias:          pci:v00008086d00004237sv*sd00001314bc*sc*i* 
[*]alias:          pci:v00008086d00004237sv*sd00001214bc*sc*i* 
[*]alias:          pci:v00008086d00004237sv*sd00001311bc*sc*i* 
[*]alias:          pci:v00008086d00004237sv*sd00001211bc*sc*i* 
[*]alias:          pci:v00008086d00004232sv*sd00001326bc*sc*i* 
[*]alias:          pci:v00008086d00004232sv*sd00001226bc*sc*i* 
[*]alias:          pci:v00008086d00004232sv*sd00001325bc*sc*i* 
[*]alias:          pci:v00008086d00004232sv*sd00001225bc*sc*i* 
[*]alias:          pci:v00008086d00004232sv*sd00001324bc*sc*i* 
[*]alias:          pci:v00008086d00004232sv*sd00001224bc*sc*i* 
[*]alias:          pci:v00008086d00004232sv*sd00001321bc*sc*i* 
[*]alias:          pci:v00008086d00004232sv*sd00001221bc*sc*i* 
[*]alias:          pci:v00008086d00004232sv*sd00001306bc*sc*i* 
[*]alias:          pci:v00008086d00004232sv*sd00001206bc*sc*i* 
[*]alias:          pci:v00008086d00004232sv*sd00001305bc*sc*i* 
[*]alias:          pci:v00008086d00004232sv*sd00001205bc*sc*i* 
[*]alias:          pci:v00008086d00004232sv*sd00001304bc*sc*i* 
[*]alias:          pci:v00008086d00004232sv*sd00001204bc*sc*i* 
[*]alias:          pci:v00008086d00004232sv*sd00001301bc*sc*i* 
[*]alias:          pci:v00008086d00004232sv*sd00001201bc*sc*i* 
[*]depends:        cfg80211 
[*]intree:         Y 
[*]vermagic:       3.10.40-gdacac96 SMP preempt mod_unload ARMv7 p2v8 
[*]parm:           swcrypto:using crypto in software (default 0 [hardware]) (int) 
[*]parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint) 
[*]parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int) 
[*]parm:           fw_restart:restart firmware in case of error (default true) (bool) 
[*]parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int) 
[*]parm:           bt_ch_inhibition:Enable BT channel inhibition (default: enable) (bool) 
[*]parm:           plcp_check:Check plcp health (default: 1 [enabled]) (bool) 
[*]parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int) 
[*]parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool) 
[*]parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int) 
[*]parm:           power_save:enable WiFi power management (default: disable) (bool) 
[*]parm:           power_level:default power save level (range from 1 - 5, default: 1) (int) 
[*]parm:           auto_agg:enable agg w/o check traffic load (default: enable) (bool) 
[/LIST]

```

I tried to use backports to compile a newer version of iwlwifi for using an higher version of iwlwifi-7260-x.ucode.

However i stuck on the make defconfig-iwlwifi command:
```

[LIST=1]
[*]make[2]: `conf' is up to date. 
[*]boolean symbol HWMON tested for 'm'? test forced to 'n' 
[*]boolean symbol HWMON tested for 'm'? test forced to 'n' 
[*]warning: (MAC80211 && MAC802154) selects BACKPORT_CRYPTO_CCM which has unmet direct dependencies (CRYPTO_AEAD && CRYPTO_CTR) 
[*]warning: (MAC80211 && MAC802154) selects BACKPORT_CRYPTO_CCM which has unmet direct dependencies (CRYPTO_AEAD && CRYPTO_CTR) 
[*]# 
[*]# configuration written to .config 
[*]# 
[/LIST]

```

I'm able to make and make install, but then after reboot, there is no  way to connect to an encrypted network due a 4-way-handshake error.I  used the same wpa_supplicant.conf before the backport install, 
which had worked. 

I used an ASUS RT-AC87U Router which is running an AC-standard Network, which is definitely running on my MacBook.  

Here is the iwllist scan result. Here I miss the VHT entry, I guess thats placed anywhere in IE:Unknown:

```

[LIST]
[*]wlan0     Scan completed : 
[*]          Cell 01 - Address: xx:xx:xx:xx:xx:xx 
[*]                    Channel:36 
[*]                    Frequency:5.18 GHz (Channel 36) 
[*]                    Quality=70/70  Signal level=-21 dBm 
[*]                    Encryption key:on 
[*]                    ESSID:"ASUS" 
[*]                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s 
[*]                              36 Mb/s; 48 Mb/s; 54 Mb/s 
[*]                    Mode:Master 
[*]                    Extra:tsf=00000005cded64ac 
[*]                    Extra: Last beacon: 61ms ago 
[*]                    IE: Unknown: 000441535553 
[*]                    IE: Unknown: 01088C1298243048606C 
[*]                    IE: Unknown: 030124 
[*]                    IE: Unknown: 200100 
[*]                    IE: Unknown: 2D1A4F0017FFFFFFFFFEFFFFFFFF1F000001000000000018E6E71900 
[*]                    IE: Unknown: 3D16240D0400000000000000000000000000000000000000 
[*]                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00 
[*]                    IE: IEEE 802.11i/WPA2 Version 1 
[*]                        Group Cipher : CCMP 
[*]                        Pairwise Ciphers (1) : CCMP 
[*]                        Authentication Suites (1) : PSK 
[*]                    IE: Unknown: DD850050F204104A00011010440001021057000101103B00010310470010E993FF743B945AE1B7232E5CB8F25C49102100044153555310230006526F757465721024000851563836302E30301042000C3038363236363846464142431054000800060050F204000110110006526F75746572100800022108103C0001021049000600372A000120 
[*]                    IE: Unknown: BF0C3258C33FAAFF0000AAFF0000 
[*]                    IE: Unknown: C005012A00FFFC 
[*]                    IE: Unknown: DD0A002686010300DD000000 
[*]          Cell 02 - Address: xx:xx:xx:xx:xx:xx 
[*]                    Channel:1 
[*]                    Frequency:2.412 GHz (Channel 1) 
[*]                    Quality=39/70  Signal level=-71 dBm 
[*]                    Encryption key:on 
[*]                    ESSID:"ASUS" 
[*]                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
[*]                              24 Mb/s; 36 Mb/s; 54 Mb/s 
[*]                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s 
[*]                    Mode:Master 
[*]                    Extra:tsf=000000015c956d63 
[*]                    Extra: Last beacon: 62ms ago 
[*]                    IE: Unknown: 000441535553 
[*]                    IE: Unknown: 010882848B962430486C 
[*]                    IE: Unknown: 030101 
[*]                    IE: Unknown: 2A0100 
[*]                    IE: Unknown: 2F0100 
[*]                    IE: IEEE 802.11i/WPA2 Version 1 
[*]                        Group Cipher : CCMP 
[*]                        Pairwise Ciphers (1) : CCMP 
[*]                        Authentication Suites (1) : PSK 
[*]                    IE: Unknown: 32040C121860 
[*]                    IE: Unknown: 0B050000120000 
[*]                    IE: Unknown: 2D1AEF1917FFFFFF0000000000000000000000000000000000000000 
[*]                    IE: Unknown: 3D16010D0000000000000000000000000000000000000000 
[*]                    IE: Unknown: 4A0E14000A002C01C800140005001900 
[*]                    IE: Unknown: 7F080500080000000040 
[*]                    IE: Unknown: DD9D0050F204104A0001101044000102103B000103104700109F2DF3F1CA19B3605A623359BAF93507102100154153555354654B20436F6D707574657220496E632E1023001C57692D46692050726F74656374656420536574757020526F757465721024000852542D4143383755104200001054000800060050F20400011011000852542D4143383755100800022008103C0001011049000600372A000120 
[*]                    IE: Unknown: DD090010180200001C0000 
[*]                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00 
[*]                    IE: Unknown: 46057208010000 
[*]                    IE: Unknown: DD1F00904C0408BF0CB259820FEAFF0000EAFF0000C0050003000000C303010202 
[/LIST]

```

As probably helpful for you, my iw reg get:
```

[LIST]
[*]iw reg get 
[*]country AT: 
[*]    (2402 - 2482 @ 40), (N/A, 20) 
[*]    (5170 - 5250 @ 80), (N/A, 20) 
[*]    (5250 - 5330 @ 80), (N/A, 20), DFS 
[*]    (5490 - 5710 @ 160), (N/A, 27), DFS 
[*]    (57000 - 66000 @ 2160), (N/A, 40) 
[/LIST]

```
 
So did anybody have some experience  with the Intel cards including AC or backporting?
If you need more infos, just ask!
Thank you.

---

### Post by rolandd2 on 2015-09-28
```
########## wireless info START ##########

last: /var/log/wtmp: No such file or directory
Perhaps this file was removed by the operator to prevent logging last info.
Report from: 28 Sep 2015 12:30 UTC +0000

Booted last: 28 Sep 2015 00:00 UTC +0000

Script from: 14 Jul 2015 17:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.10.40-grinch-21.3.4 #1 SMP PREEMPT Fri May 1 10:41:09 UTC 2015 armv7l armv7l armv7l GNU/Linux

console=ttyS0,115200n8, console=tty1, no_console_suspend=1, lp0_vec=2064@0xf46ff000, mem=2015M@2048M, memtype=255, ddr_die=2048M@2048M, section=256M, pmuboard=0x0177:0x0000:0x02:0x43:0x00, tsec=32M@3913M, otf_key=c75e5bb91eb3bd947560357b64422f85, usbcore.old_scheme_first=1, core_edp_mv=1150, core_edp_ma=4000, tegraid=40.1.1.0.0, debug_uartport=lsport,3, power_supply=Adapter, audio_codec=rt5640, modem_id=0, android.kerneltype=normal, fbcon=map:1, commchip_id=0, usb_port_owner_info=0, lane_owner_info=6, emc_max_dvfs=0, touch_id=0@0, board_info=0x0177:0x0000:0x02:0x43:0x00, rw, rootwait, tegraboot=sdmmc, gpt

##### desktop ###########################

sed: can't read /root/.dmrc: No such file or directory

Could not be determined.

##### lspci #############################

01:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev bb)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:4070]
    Kernel driver in use: iwlwifi

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0123]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 004: ID 0781:5576 SanDisk Corp. 
Bus 002 Device 003: ID 17ef:6019 Lenovo 
Bus 002 Device 005: ID 05af:0808 Jing-Mold Enterprise Co., Ltd 
Bus 002 Device 002: ID 8564:4000  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:07dc Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwlmvm                 87656  0 
mac80211              351672  1 iwlmvm
iwlwifi                75650  1 iwlmvm
cfg80211              349918  3 iwlwifi,mac80211,iwlmvm
rfkill                  9587  4 cfg80211,bluetooth

##### interfaces ########################

source-directory /etc/network/interfaces.d

auto wlan0
iface wlan0 inet dhcp

##### ifconfig ##########################

dummy0    Link encap:Ethernet  HWaddr <MAC 'dummy0' [IF]>  
          BROADCAST NOARP  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.11.235  Bcast:192.168.11.255  Mask:255.255.252.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:72353 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25413 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24607667 (24.6 MB)  TX bytes:7740319 (7.7 MB)

ip6tnl0   Link encap:UNSPEC  HWaddr <MAC 'ip6tnl0' [IF]>  
          NOARP  MTU:1452  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

rmnetctl  Link encap:IPIP Tunnel  HWaddr   
          NOARP  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'rmnetctl' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr <MAC 'rmnetctl' [IF]>  
          inet addr:169.254.9.145  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

##### iwconfig ##########################

rmnetctl  no wireless extensions.

sit0      no wireless extensions.

dummy0    no wireless extensions.

lo        no wireless extensions.

eth0      no wireless extensions.

ip6tnl0   no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.11.1    0.0.0.0         UG    0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     1007   0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 wlan0
192.168.8.0     0.0.0.0         255.255.252.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search surfnet

##### network managers ##################

Installed:

    NetworkManager

Running:

root      2400     1  0 07:12 ?        00:00:04 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.11.235
    Prefix:          22 (255.255.252.0)
    Gateway:         192.168.11.1

    DNS:             192.168.11.1

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             unmanaged
  Default:           no
  HW Address:        <MAC 'rmnetctl' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/ASUS]] (600 root)
[connection] id=ASUS | type=802-11-wireless
[802-11-wireless] ssid=ASUS | mac-address=<MAC 'rmnetctl' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Etc/UTC (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (N/A, 20)
    (2457 - 2482 @ 40), (N/A, 20), PASSIVE-SCAN
    (2474 - 2494 @ 20), (N/A, 20), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 80), (N/A, 20), PASSIVE-SCAN
    (5250 - 5330 @ 80), (N/A, 20), DFS, PASSIVE-SCAN
    (5490 - 5730 @ 160), (N/A, 20), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (N/A, 20), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0)

##### iwlist channels ###################

rmnetctl  no frequency information.

sit0      no frequency information.

dummy0    no frequency information.

lo        no frequency information.

eth0      no frequency information.

ip6tnl0   no frequency information.

wlan0     32 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz

##### iwlist scan #######################

rmnetctl  Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

dummy0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ip6tnl0   Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.24 GHz (Channel 48)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'ASUS' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-18 dBm  
                    Encryption key:on
                    ESSID:"ASUS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000002cedba5f
                    Extra: Last beacon: 30ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'ZyXEL' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"ZyXEL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000006f5523d1d
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'NETGEAR' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-36 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000006f5ffbd94
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'ASUS' [AC4]>
                    Channel:48
                    Frequency:5.24 GHz (Channel 48)
                    Quality=70/70  Signal level=-22 dBm  
                    Encryption key:on
                    ESSID:"ASUS"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000006f027b445
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/3.10.40-grinch-21.3.4/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     B4770FC2C84528FCDBECAFB
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.10.40-grinch-21.3.4 SMP preempt mod_unload ARMv7 p2v8 
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)

[mac80211]
filename:       /lib/modules/3.10.40-grinch-21.3.4/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
depends:        cfg80211
intree:         Y
vermagic:       3.10.40-grinch-21.3.4 SMP preempt mod_unload ARMv7 p2v8 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.10.40-grinch-21.3.4/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     F5654BE9F9C3C64A4666DE1
depends:        cfg80211
intree:         Y
vermagic:       3.10.40-grinch-21.3.4 SMP preempt mod_unload ARMv7 p2v8 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           bt_ch_inhibition:Enable BT channel inhibition (default: enable) (bool)
parm:           plcp_check:Check plcp health (default: 1 [enabled]) (bool)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           auto_agg:enable agg w/o check traffic load (default: enable) (bool)

[cfg80211]
filename:       /lib/modules/3.10.40-grinch-21.3.4/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
depends:        rfkill
intree:         Y
vermagic:       3.10.40-grinch-21.3.4 SMP preempt mod_unload ARMv7 p2v8 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwlmvm]
init_dbg: N
power_scheme: 2

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[iwlwifi]
11n_disable: 0
amsdu_size_8K: 0
antenna_coupling: 0
auto_agg: Y
bt_ch_inhibition: Y
bt_coex_active: Y
fw_restart: Y
led_mode: 0
plcp_check: Y
power_level: 0
power_save: N
swcrypto: 0
wd_disable: 1

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

bluedroid_pm
nvhost_vi

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x08b1 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'rmnetctl' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   12.792839] iwlwifi 0000:01:00.0: NVM section 0 read completed
[   12.792956] iwlwifi 0000:01:00.0: NVM section 1 read completed
[   12.793149] iwlwifi 0000:01:00.0: NVM section 4 read completed
[   12.793274] iwlwifi 0000:01:00.0: NVM section 5 read completed
[   12.986044] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   13.900868] iwlwifi 0000:01:00.0: L1 Enabled; Disabling L0S (repeated 2 times)
[   14.016742] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

########## wireless info END ############

```

---

