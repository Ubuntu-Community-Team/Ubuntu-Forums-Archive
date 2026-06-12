---
title: "Losing wireless connection - automatically changing to hidden but cannot connect"
date: 2016-03-16
forum: Networking &amp; Wireless
---

### Post by zac13 on 2016-03-16
Hi all. New here. 

I'm having a problem with my wireless connection. Connection intermittently fails, and my current (not hidden) network drops out, and does not show up in the list of wireless connections in the menu bar, though when I check hidden networks, it can be found there, though I cannot connect to it. 

Currently running 14.04 64 bit with the following hardware:

```
~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108M [GeForce GT 550M] (rev ff)
03:00.0 Network controller: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
04:00.0 USB controller: Fresco Logic FL1000G USB 3.0 Host Controller (rev 04)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
```

nmcli nm dispays the following when the connection is active:
```
~$ nmcli nm
RUNNING         STATE           WIFI-HARDWARE   WIFI       WWAN-HARDWARE   WWAN      
running         connected       enabled         enabled    enabled         disabled  



```

And nmcli nm displays the following after the connection to home wifi is disabled:
```
~$ nmcli nm
RUNNING         STATE           WIFI-HARDWARE   WIFI       WWAN-HARDWARE   WWAN      
running      disconnected       enabled         enabled    enabled         disabled  



```

No other devices (android phone, iPhone, Win7 desktop) are having connection issues with the wifi network, nor is the SSID hidden.

The only solution I have found thus far, is to reboot, though this is a temporary solution, as the connection will invariably drop and become hidden and unable to be connected to again. 

Interestingly, I've been able to reproduce this error by pausing Youtube videos, though this is not the only catalyst, as it seems to drop out at random.

Thanks for your consideration, and sorry for the long post. I've searched the forums a bit, though I have found no obvious solution to this problem.

---

### Post by jeremy31 on 2016-03-16
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info
```

Post the contents of the wireless-info.txt file

I would suspect your issues are due to the use of TKIP encryption as I had similar struggles when I had TKIP enabled

---

### Post by zac13 on 2016-03-16
[ATTACH]267845[/ATTACH]

---

### Post by jeremy31 on 2016-03-16
As I suspected, your wireless is
```
Cell 01 - Address: <MAC 'ATT696' [AC1]>                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"ATT696"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001e710eb939
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
```

I would recommend you change encryption to WPA2 only without WEP or TKIP

---

### Post by zac13 on 2016-03-16
I will try this, though I am curious as to why it has only been an issue for the last week or so. I haven't changed wireless network settings since the network was installed. These problems didn't start until I added tlp for some extra battery life, though after purging tlp (probably should add it back then) i have still been losing my connection.

Will let you know if your solution doesn't work. Thanks for your assistance!

---

### Post by zac13 on 2016-03-16
Changing to WPA2 only with CCMP seems to have solved the issue. You've saved me hours of frustration. Thanks for the solution!

---

### Post by jeremy31 on 2016-03-16
I have a couple Atheros wifi cards and TKIP may work for some time but getting rid of it is better

---

### Post by zac13 on 2016-03-17
Sadly, I have been having the same problem as before. I changed the security settings on the home modem/router to WPA2,and have still been losing my wifi connection. It is doing the same as before--dropping connection and disappearing from local visible connections--and I am unable to discover it again until a reboot. 

Interestingly, this happened after reinstalling tlp, which i purged again to see if the automated power settings were disabling my wireless adapter, though the problem persisted after reboot. The connection will actively drop out on occasion, even while streaming media.

My connection information no longer displays TKIP as being active.

[ATTACH]267855[/ATTACH]

Unfortunately, I'm at a bit of a loss here. This sort of thing hasn't happened for the previous 6 months of running 14.04 on my home wifi, which has remained unchanged. Has there been some wifi breaking update that has been passed to this version?

---

### Post by jeremy31 on 2016-03-17
```
sudo iw reg set US
```
Then see if changing the router to channel 9 helps as the channel it is on has some other access points

---

### Post by zac13 on 2016-03-17
For some reason, purging tlp has prevented any further issues with dropped connections. After a restart, I've not had further issues. For reasons that I cannot fully understand, this issue seems to revolve around tlp, as it is the only common thread surrounding the lost connectivity. If anyone has input toward their experiences with tlp causing errors, I would be curious to know.

---

### Post by zac13 on 2016-03-19
Still losing connection, I got a wild hare and deleted my home network connection and set it up again, choosing WPA2 as the encryption. The combination of WPA2 in the modem/router wireless settings, as well as recreating the home connection from scratch seems to have done the trick thus far. Don't know why I didn't think of that earlier...

Many thanks to jeremy31 for assistance!

---

### Post by zac13 on 2016-03-20
And after waking my laptop up from suspend this morning, the issue promptly repeated itself. Wireless connection drops, and disabling and re-enabling networking does nothing. Only rebooting the computer seems to solve this issue, temporarily.

I have seen the issue where wireless connection is dropped from suspend, but per the output of nmcli nm I posted earlier, my loss of connection is not quite the same.

Anyone have any other hints at solving this?

---

