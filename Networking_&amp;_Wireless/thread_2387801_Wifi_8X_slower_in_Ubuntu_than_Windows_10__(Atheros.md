---
title: "Wifi 8X slower in Ubuntu than Windows 10  (Atheros 802.11AC)"
date: 2018-03-23
forum: Networking &amp; Wireless
---

### Post by Henry_Methorst on 2018-03-23
iPerf3 tests to a LAN server result in 8X slower speeds in Ubuntu than in Windows 10.   

```
~$ uname -a

Linux CQF-MSI 4.13.0-37-generic #42~16.04.1-Ubuntu SMP Wed Mar 7 16:03:28 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

```

```
[COLOR=#000000][FONT=Arial]lspci | awk '/[Nn]et/ {print $1}' | xargs -i% lspci -ks %
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]04:00.0 Network controller: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter (rev 20)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]Subsystem: Bigfoot Networks, Inc. Killer N1525 Wireless-AC[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]Kernel driver in use: ath10k_pci[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]Kernel modules: ath10k_pci[/FONT][/COLOR]

```


Windows 10 iPerf3 tests:

[IMG]http://i64.tinypic.com/f02i55.jpg[/IMG]

Ubuntu Mate:

[IMG]http://i67.tinypic.com/2m6a29z.png[/IMG]


 Ubuntu setup is 8X crappier than the first crap. What gives.

---

### Post by praseodym on 2018-03-25
Please check
```

sudo modprobe -rfv ath10k_pci
sudo modprobe -v ath10k_pci nohwcrypt=1
```

---

### Post by Henry_Methorst on 2018-03-27
> **praseodym said:**
> Please check
```

sudo modprobe -rfv ath10k_pci
sudo modprobe -v ath10k_pci nohwcrypt=1
```


here's the output:

```
rmmod ath10k_pcirmmod ath10k_core
rmmod mac80211
rmmod ath
rmmod cfg80211

```



```

henry@CQF-MSI:~$ sudo modprobe -v ath10k_pci nohwcrypt=1
insmod /lib/modules/4.13.0-37-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/4.13.0-37-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/4.13.0-37-generic/kernel/drivers/net/wireless/ath/ath.ko 
insmod /lib/modules/4.13.0-37-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_core.ko 
insmod /lib/modules/4.13.0-37-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko nohwcrypt=1

```

Seems like the Ubuntu driver of this AC wireless card is awful.  :/

---

### Post by Henry_Methorst on 2018-03-27
I will run the speed tests tonight after remove/reinstalling as you suggested and post the results. 

Thanks

---

### Post by Henry_Methorst on 2018-03-28
> **praseodym said:**
> Please check
```

sudo modprobe -rfv ath10k_pci
sudo modprobe -v ath10k_pci nohwcrypt=1
```



The top is 2.4Ghz, the top is 5Ghz.  As bad or even worse. ;( 

How do I reverse the modprobe command? 


[IMG]http://i67.tinypic.com/w0kkn6.png[/IMG]

---

### Post by wildmanne39 on 2018-03-28
Just Reboot.

---

### Post by praseodym on 2018-03-28
Try updating the firmware:

```
sudo apt-get install git
git clone git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git
cd linux-firmware
sudo cp -r * /lib/firmware
```
Reboot

---

### Post by Henry_Methorst on 2018-03-28
> **praseodym said:**
> Try updating the firmware:

```
sudo apt-get install git
git clone git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git
cd linux-firmware
sudo cp -r * /lib/firmware
```
Reboot

I'll give it a shot... 

Before I do, look at this:   

First image = a VM machine running FreeBSD:  290MBits  average
Second image = Ubuntu Mate 16.04.1:  6.97 MBits average....

 

[IMG]http://i68.tinypic.com/k0rki0.png[/IMG]


And now Ubuntu's awfulperformance:

[IMG]http://i65.tinypic.com/ekgmcz.png[/IMG]

Wow...

---

### Post by Henry_Methorst on 2018-03-28
No change.  After updating firmware still averaging 7Mbits. 


Ugh

---

### Post by Henry_Methorst on 2018-03-29
FreeBSD gives me 300Mbps  while Ubuntu  7?    wth. 

[IMG]http://i63.tinypic.com/23m7ta8.png[/IMG]

---

### Post by jeremy31 on 2018-03-29
See if disabling wifi power management fixes
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
systemctl restart network-manager.service
```

---

### Post by Henry_Methorst on 2018-03-29
> **jeremy31 said:**
> See if disabling wifi power management fixes
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
systemctl restart network-manager.service
```


No dice bro.   Thanks for trying but it looks like this might have something to do with it:

[https://wireless.wiki.kernel.org/en/users/drivers/ath10k]("http://tx rate is reported as 6mbps due to firmware limitation (no tx rate information in tx completions); instead see /sys/kernel/debug/ieee80211/phyX/ath10k/fw_stats")

> [COLOR=#333333][FONT=Arial]tx rate is reported as 6mbps due to firmware limitation (no tx rate information in tx completions); instead see /sys/kernel/debug/ieee80211/phyX/ath10k/fw_stats[/FONT][/COLOR]

But it says its only "reported", but I am sure the reported speed is accurate...

---

### Post by Henry_Methorst on 2018-03-29
This is what /sys/kernel/debug/ieee80211/phy0/ath10k/fw_stats  says at the bottom. 

If 351000 is a bit count, then its rougly 43k/sec... scratching my head.   


```
    ath10k PEERstats (3)
             =================

              Peer MAC address x
                     Peer RSSI 0
                  Peer TX rate 351000
                  Peer RX rate 0
              Peer RX duration 0

              Peer MAC address x
                     Peer RSSI 0
                  Peer TX rate 351000
                  Peer RX rate 0
              Peer RX duration 0

              Peer MAC address x
                     Peer RSSI 51
                  Peer TX rate 351000
                  Peer RX rate 0
              Peer RX duration 0
```

---

### Post by Henry_Methorst on 2018-03-30
> **jeremy31 said:**
> See if disabling wifi power management fixes
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
systemctl restart network-manager.service
```

Since applying this my connection is intermittently dropping.   Can you toss me the code to re-enable it. 
Thanks

---

### Post by wildmanne39 on 2018-03-30
This will turn power management back on but I doubt running the previous command caused the disconnects.
```
sudo sed -i 's/wifi.powersave = 2/wifi.powersave = 3/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
systemctl restart network-manager.service
```

---

### Post by kerry_s on 2018-03-30
are you by any chance using a hidden ssid?

cause there seems to be a issue of slowness for hidden networks.

---

### Post by Henry_Methorst on 2018-04-02
> **kerry_s said:**
> are you by any chance using a hidden ssid?

cause there seems to be a issue of slowness for hidden networks.


Negative.  It seems this  card is a known lemon in certain distros

[https://forum.manjaro.org/t/qca6174-slow-lan-transfers/35942/10](https://forum.manjaro.org/t/qca6174-slow-lan-transfers/35942/10)

---

### Post by cherrotluo on 2018-08-15
According to #69 of [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1670041](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1670041) :
> [COLOR=#333333][FONT=monospace]The low throughput with transmit TCP streams on ath10k should be fixed with this mac80211 commit:[/FONT][/COLOR][COLOR=#333333][FONT=monospace]mac80211: Adjust TSQ pacing shift[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace][https://git.kernel.org/linus/36148c2bbfbe50c50206b6f61d072203c80161e0](https://git.kernel.org/linus/36148c2bbfbe50c50206b6f61d072203c80161e0)[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]Apparently v4.16-rc5 was the first release to have that commit.[/FONT][/COLOR]

Upgrade kernel to a newer version (4.17.14 in my case) could fix this.

---

