---
title: "[SOLVED] Intel Pro/Wireless Iwl-4965agn works but..."
date: 2008-10-09
forum: Networking &amp; Wireless
---

### Post by jheaton5 on 2008-10-09
I got the right driver and the right firmware installed in the right directory.  After boot, I have to enable the driver with System>Administration>Hardware Drivers.  When I do that the wireless card's led turns blue, meaning it is running as it should. I then have to manually link the card to the network with network manager.  Once this is done the connection is fine.

I'd like for it to connect automatically and I think I'm almost there.  I would like some assistance at this point, however.

Here is the results of iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"linksysn"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1E:E5:50:55:CF   
          Bit Rate=1 Mb/s   Tx-Power=14 dBm   
          Retry min limit:7   RTS thr: off   Fragment thr=2352 B   
          Power Management: off
          Link Quality=100/100  Signal level:-25 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

and here is demesg | grep -i iwl
[  127.394788] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[  127.394797] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[  127.394950] iwlagn: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[  127.441150] iwlagn: Tunable channels: 11 802.11bg, 13 802.11a channels
[  127.442589] phy0: Selected rate control algorithm 'iwl-agn-rs'
[  127.687051] iwlagn: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[  127.723223] iwlagn: Tunable channels: 11 802.11bg, 13 802.11a channels
[  127.726018] phy1: Selected rate control algorithm 'iwl-agn-rs'
[  128.011034] Registered led device: iwl-phy1:radio
[  128.011057] Registered led device: iwl-phy1:assoc
[  128.011079] Registered led device: iwl-phy1:RX
[  128.011098] Registered led device: iwl-phy1:TX
[  177.189708] Registered led device: iwl-phy1:radio
[  177.189730] Registered led device: iwl-phy1:assoc
[  177.189755] Registered led device: iwl-phy1:RX
[  177.189772] Registered led device: iwl-phy1:TX
[  325.567611] Registered led device: iwl-phy1:radio
[  325.567633] Registered led device: iwl-phy1:assoc
[  325.567651] Registered led device: iwl-phy1:RX
[  325.567669] Registered led device: iwl-phy1:TX
[  329.661950] Registered led device: iwl-phy1:radio
[  329.661987] Registered led device: iwl-phy1:assoc
[  329.662017] Registered led device: iwl-phy1:RX
[  329.662045] Registered led device: iwl-phy1:TX

and here is lshw -C Network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 61
       serial: 00:13:e8:46:c9:75
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.100 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:24:67:18:57
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=0 module=r8169 multicast=yes

---

### Post by jheaton5 on 2008-10-09
I ran the following command in terminal:
sudo iwconfig wlan0 txpower auto

Now when I manually enable my driver it automatically connects to the network.

Still looking for automatic enabling.

---

### Post by jheaton5 on 2008-10-10
Update.

Driver is iwlagn

joel@joels-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 61
       serial: 00:13:e8:46:c9:75
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.100 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn

using the command

> modprobe -v iwlagn

The driver activates the card and connects to the internet.

On reboot, the card is seen by System>Administration>Hardware Drivers and the status is "enabled" "not used."  The card is off and no internet connection.

In the directory /etc/modprobe.d/"uname -r" the aliases file shows iwlagn but there is no file for iwlagn or iwl-4965agn-2 (which is the actual name of the driver).

How do I get the kernel to automatically load iwlagn?

---

### Post by jheaton5 on 2008-10-10
another update...

> joel@joels-laptop:~$ modprobe -l "iwl*"
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/iwlwifi/iwlcore.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/iwlwifi/iwlagn.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/iwlwifi/iwl3945.ko
/lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl4965.ko
/lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/mac80211/compatible/net/mac80211/iwlwifi_rc80211_simple.ko
/lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/mac80211/compatible/net/mac80211/iwlwifi_mac80211.ko

joel@joels-laptop:~$ dmesg | grep -i iwl
[  322.048114] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[  322.048122] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[  322.048286] iwlagn: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[  322.094366] iwlagn: Tunable channels: 11 802.11bg, 13 802.11a channels
[  322.095276] phy0: Selected rate control algorithm 'iwl-agn-rs'
[  322.313917] iwlagn: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[  322.350354] iwlagn: Tunable channels: 11 802.11bg, 13 802.11a channels
[  322.354194] phy1: Selected rate control algorithm 'iwl-agn-rs'
[  322.628494] Registered led device: iwl-phy1:radio
[  322.628521] Registered led device: iwl-phy1:assoc
[  322.628541] Registered led device: iwl-phy1:RX
[  322.628559] Registered led device: iwl-phy1:TX



Could I have a conflict between drivers iwlagn and iwl4965?  If so, the iwlagn is the driver that works.  Should I > sudo modprobe -r iwl4965

---

### Post by jheaton5 on 2008-10-10
OK, I added blacklist iwl4965 to the /etc/modprobe.d/blacklist file. There is no change in operation.  I still have to manually tell the kernel to use iwlagn and when I do it works.

Still trying...I'll bet I solve it before you do.:lolflag:

---

### Post by jheaton5 on 2008-10-10
> sudo modprobe -r iwl4965 

No visable effect.

---

### Post by jheaton5 on 2008-10-10
Let me clarify.  Earlier I posted this:
> On reboot, the card is seen by System>Administration>Hardware Drivers and the status is "enabled" "not used." The card is off and no internet connection.

When I first boot, I have no wireless.  System>Administration>Hardware Drivers shows a wireless driver.  The "enabled" box is checked and the "status" field says "not used."  I uncheck the "enabled" box and a dialogue box comes up asking if I want to disable.  I click disable.  Then I re-click the "enabled" box.  Another dialogue box comes up asking if I want to enable.  I click enable.  Now the "enable" box is checked and the "status" field says "In Use"  Then the card automatically connects to the network.

---

### Post by jheaton5 on 2008-10-10
I knew that the fix would be something simple.  I just had to learn more about how linux>debian>ubuntu works.  What I learned is that there is a file, /etc/modules, that stores the names of the modules that get loaded on every boot.  See post No. 3 above.  I found that using modprobe to insert the driver iwlagn into the kernel solved the problem.  I encountered another problem, however, nameley that this command had to be issued manually after each boot.  By putting the driver name in /etc/modules I ensured that each time I boot ubuntu my driver gets loaded automatically.

Thanks to all you readers out there for believing I could find the solution for myself.

---

