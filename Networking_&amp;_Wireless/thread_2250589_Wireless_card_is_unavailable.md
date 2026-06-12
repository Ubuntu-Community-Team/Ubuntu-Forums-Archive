---
title: "Wireless card is unavailable"
date: 2014-10-29
forum: Networking &amp; Wireless
---

### Post by Robert_Holden on 2014-10-29
i recently installed ubuntu and i can not get a wireless connectiong due to the card being in "state: unavailable"

---

### Post by jeremy31 on 2014-10-29
Please run the wireless script and post results, details [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by Robert_Holden on 2014-10-29
here is the info
   
```

########## wireless info START ########## 

Report from: 29 Oct 2014 20:13 EDT -0400 

Booted last: 29 Oct 2014 18:43 EDT -0400 

Script from: 20 Sep 2014 23:04 UTC +0000 

##### release ########################### 

Distributor ID:    Ubuntu Description:    Ubuntu 14.04.1 LTS Release:    14.04 Codename:    trusty 

##### kernel ############################ 

Linux 3.13.0-32-generic #57-Ubuntu SMP Tue Jul
15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux 

Parameters: ro, quiet, splash, vt.handoff=7 

##### desktop ########################### 

Ubuntu 

##### lspci ############################# 

02:00.0 Network controller [0280]: Qualcomm
Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev
01)     Subsystem: Lenovo Device [17aa:4026]     Kernel driver in use: ath9k 

03:00.0 Ethernet controller [0200]: Realtek
Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit
Ethernet Controller [10ec:8168] (rev 10)     Subsystem: Lenovo Device [17aa:3816]     Kernel driver in use: r8169 

##### lsusb ############################# 

Bus 002 Device 001: ID 1d6b:0003 Linux
Foundation 3.0 root hub Bus 001 Device 009: ID 0cf3:3004 Atheros
Communications, Inc. 
Bus 001 Device 005: ID 0bda:0129 Realtek
Semiconductor Corp. RTS5129 Card Reader Controller Bus 001 Device 004: ID 5986:014f Acer, Inc 
Bus 001 Device 003: ID 05e3:0608 Genesys Logic,
Inc. USB-2.0 4-Port HUB Bus 001 Device 001: ID 1d6b:0002 Linux
Foundation 2.0 root hub 

##### PCMCIA card info ################## 

##### rfkill ############################ 

0: ideapad_wlan: Wireless LAN     Soft blocked: no     Hard blocked: yes 1: ideapad_bluetooth: Bluetooth     Soft blocked: no     Hard blocked: yes 2: phy0: Wireless LAN     Soft blocked: no     Hard blocked: no 4: hci0: Bluetooth     Soft blocked: no     Hard blocked: no 

##### lsmod ############################# 

ath9k                 164164  0 
ath9k_common           13551  1 ath9k ath9k_hw              453856  2
ath9k_common,ath9k ath                    28698  3
ath9k_common,ath9k,ath9k_hw mac80211              630653  1 ath9k ath3k                  13318  0 
bluetooth             391196  25
bnep,ath3k,btusb,rfcomm cfg80211              484040  3
ath,ath9k,mac80211 ideapad_laptop         18216  0 
sparse_keymap          13948  1 ideapad_laptop 

##### interfaces ######################## 

auto lo iface lo inet loopback 

##### ifconfig ########################## 

bnep0     Link encap:Ethernet  HWaddr <MAC
'bnep0' [IF]>  
          inet addr:172.20.10.2 
Bcast:172.20.10.15  Mask:255.255.255.240           inet6 addr:
fe80::1acf:5eff:fe18:a518/64 Scope:Link           UP BROADCAST RUNNING MULTICAST 
MTU:1500  Metric:1           RX packets:694 errors:0 dropped:0
overruns:0 frame:0           TX packets:760 errors:0 dropped:0
overruns:0 carrier:0           collisions:0 txqueuelen:1000 
          RX bytes:401088 (401.0 KB)  TX
bytes:110520 (110.5 KB) 

eth0      Link encap:Ethernet  HWaddr <MAC
'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500 
Metric:1           RX packets:0 errors:0 dropped:0
overruns:0 frame:0           TX packets:0 errors:0 dropped:0
overruns:0 carrier:0           collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

wlan0     Link encap:Ethernet  HWaddr <MAC
'wlan0' [IF]>  
          BROADCAST MULTICAST  MTU:1500 
Metric:1           RX packets:0 errors:0 dropped:0
overruns:0 frame:0           TX packets:0 errors:0 dropped:0
overruns:0 carrier:0           collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

##### iwconfig ########################## 

bnep0     no wireless extensions. 

eth0      no wireless extensions. 

lo        no wireless extensions. 

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point:
Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off  
Fragment thr:off           Power Management:off           


##### route ############################# 

Kernel IP routing table Destination     Gateway         Genmask        
Flags Metric Ref    Use Iface 0.0.0.0         172.20.10.1     0.0.0.0        
UG    0      0        0 bnep0 172.20.10.0     0.0.0.0         255.255.255.240
U     11     0        0 bnep0 

##### resolv.conf ####################### 

nameserver 127.0.1.1 

##### nm-tool ########################### 

NetworkManager Tool 

State: connected (global) 

- Device: <MAC address>  [You can't see me
Network] ------------------------   Type:              Bluetooth   Driver:            bluez   State:             connected   Default:           yes 

  Capabilities: 

  IPv4 Settings:     Address:         172.20.10.2     Prefix:          28 (255.255.255.240)     Gateway:         172.20.10.1 

    DNS:             172.20.10.1 

- Device: eth0
-----------------------------------------------------------------   Type:              Wired   Driver:            r8169   State:             unavailable   Default:           no   HW Address:        <MAC 'eth0' [IF]> 

  Capabilities:     Carrier Detect:  yes 

  Wired Properties     Carrier:         off 

- Device: wlan0
----------------------------------------------------------------   Type:              802.11 WiFi   Driver:            ath9k   State:             unavailable   Default:           no   HW Address:        <MAC 'wlan0' [IF]> 

  Capabilities: 

  Wireless Properties     WEP Encryption:  yes     WPA Encryption:  yes     WPA2 Encryption: yes 

  Wireless Access Points 


##### NetworkManager.state ############## 

[main] NetworkingEnabled=true WirelessEnabled=true WWANEnabled=true WimaxEnabled=true 

##### NetworkManager.conf ############### 

[main] plugins=ifupdown,keyfile,ofono dns=dnsmasq 

[ifupdown] managed=false 

##### NetworkManager profiles ########### 

##### iw reg get ######################## 

Region: America/New_York (based on set time
zone) 

country 00:     (2402 - 2472 @ 40), (3, 20)     (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN,
NO-IBSS     (2474 - 2494 @ 20), (3, 20), NO-OFDM,
PASSIVE-SCAN, NO-IBSS     (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN,
NO-IBSS     (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN,
NO-IBSS 

##### iwlist channels ################### 

bnep0     no frequency information. 

eth0      no frequency information. 

lo        no frequency information. 

wlan0     13 channels in total; available
frequencies :           Channel 01 : 2.412 GHz           Channel 02 : 2.417 GHz           Channel 03 : 2.422 GHz           Channel 04 : 2.427 GHz           Channel 05 : 2.432 GHz           Channel 06 : 2.437 GHz           Channel 07 : 2.442 GHz           Channel 08 : 2.447 GHz           Channel 09 : 2.452 GHz           Channel 10 : 2.457 GHz           Channel 11 : 2.462 GHz           Channel 12 : 2.467 GHz           Channel 13 : 2.472 GHz 

##### iwlist scan ####################### 

bnep0     Interface doesn't support scanning. 

eth0      Interface doesn't support scanning. 

lo        Interface doesn't support scanning. 

wlan0     Interface doesn't support scanning :
Network is down 

##### module infos ###################### 

[ath9k] filename:      
/lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko license:        Dual BSD/GPL description:    Support for Atheros 802.11n
wireless LAN cards. author:         Atheros Communications srcversion:     7EAAD420ADF6B9354F0C8C1 depends:       
ath9k_hw,mac80211,ath9k_common,cfg80211,ath intree:         Y vermagic:       3.13.0-32-generic SMP mod_unload
modversions 
signer:         Magrathea: Glacier signing key sig_key:       
5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7 sig_hashalgo:   sha512 parm:           debug:Debugging mask (uint) parm:           nohwcrypt:Disable hardware
encryption (int) parm:           blink:Enable LED blink on
activity (int) parm:           btcoex_enable:Enable wifi-BT
coexistence (int) parm:           bt_ant_diversity:Enable WLAN/BT
RX antenna diversity (int) parm:           ps_enable:Enable WLAN PowerSave
(int) 

[ath9k_common] filename:      
/lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko license:        Dual BSD/GPL description:    Shared library for Atheros
wireless 802.11n LAN cards. author:         Atheros Communications srcversion:     696B00A6C59713EC0966997 depends:        ath,ath9k_hw intree:         Y vermagic:       3.13.0-32-generic SMP mod_unload
modversions 
signer:         Magrathea: Glacier signing key sig_key:       
5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7 sig_hashalgo:   sha512 

[ath9k_hw] filename:      
/lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko license:        Dual BSD/GPL description:    Support for Atheros 802.11n
wireless LAN cards. author:         Atheros Communications srcversion:     4809F3842A0542CD6B556D3 depends:        ath intree:         Y vermagic:       3.13.0-32-generic SMP mod_unload
modversions 
signer:         Magrathea: Glacier signing key sig_key:       
5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7 sig_hashalgo:   sha512 

[ath] filename:      
/lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath.ko license:        Dual BSD/GPL description:    Shared library for Atheros
wireless LAN cards. author:         Atheros Communications srcversion:     88A67C5359B02C5A710AFCF depends:        cfg80211 intree:         Y vermagic:       3.13.0-32-generic SMP mod_unload
modversions 
signer:         Magrathea: Glacier signing key sig_key:       
5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7 sig_hashalgo:   sha512 

[mac80211] filename:      
/lib/modules/3.13.0-32-generic/kernel/net/mac80211/mac80211.ko license:        GPL description:    IEEE 802.11 subsystem srcversion:     8ADA881D348148A3358334C depends:        cfg80211 intree:         Y vermagic:       3.13.0-32-generic SMP mod_unload
modversions 
signer:         Magrathea: Glacier signing key sig_key:       
5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7 sig_hashalgo:   sha512 parm:           max_nullfunc_tries:Maximum
nullfunc tx tries before disconnecting (reason 4). (int) parm:           max_probe_tries:Maximum probe
tries before disconnecting (reason 4). (int) parm:           beacon_loss_count:Number of
beacon intervals before we decide beacon was lost. (int) parm:           probe_wait_ms:Maximum time(ms)
to wait for probe response before disconnecting (reason 4). (int) parm:          
ieee80211_default_rc_algo:Default rate control algorithm for mac80211
to use (charp) 

[ath3k] filename:      
/lib/modules/3.13.0-32-generic/kernel/drivers/bluetooth/ath3k.ko firmware:       ath3k-1.fw license:        GPL version:        1.0 description:    Atheros AR30xx firmware driver author:         Atheros Communications srcversion:     98A5245588C09E5E41690D0 depends:        bluetooth intree:         Y vermagic:       3.13.0-32-generic SMP mod_unload
modversions 
signer:         Magrathea: Glacier signing key sig_key:       
5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7 sig_hashalgo:   sha512 

[cfg80211] filename:      
/lib/modules/3.13.0-32-generic/kernel/net/wireless/cfg80211.ko description:    wireless configuration support license:        GPL author:         Johannes Berg srcversion:     E786D076B61F97809B04B64 depends:        
intree:         Y vermagic:       3.13.0-32-generic SMP mod_unload
modversions 
signer:         Magrathea: Glacier signing key sig_key:       
5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7 sig_hashalgo:   sha512 parm:           ieee80211_regdom:IEEE 802.11
regulatory domain code (charp) parm:          
cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band
(bool) 

##### module parameters ################# 

[ath9k] blink: 0 bt_ant_diversity: 0 btcoex_enable: 0 nohwcrypt: 0 ps_enable: 0 

[mac80211] beacon_loss_count: 7 ieee80211_default_rc_algo: minstrel_ht max_nullfunc_tries: 2 max_probe_tries: 5 probe_wait_ms: 500 

[cfg80211] cfg80211_disable_40mhz_24ghz: N ieee80211_regdom: 00 

##### /etc/modules ###################### 

lp rtc 

##### modprobe options ################## 

[/etc/modprobe.d/ath5k.conf] options ath5k nowcrypt=1 

[/etc/modprobe.d/blacklist-ath_pci.conf] blacklist ath_pci 

[/etc/modprobe.d/blacklist.conf] blacklist evbug blacklist usbmouse blacklist usbkbd blacklist eepro100 blacklist de4x5 blacklist eth1394 blacklist snd_intel8x0m blacklist snd_aw2 blacklist i2c_i801 blacklist prism54 blacklist bcm43xx blacklist garmin_gps blacklist asus_acpi blacklist snd_pcsp blacklist pcspkr blacklist amd76x_edac 

[/etc/modprobe.d/blacklist-rare-network.conf] alias net-pf-3 off alias net-pf-6 off alias net-pf-9 off alias net-pf-11 off alias net-pf-12 off alias net-pf-19 off alias net-pf-21 off alias net-pf-36 off 

[/etc/modprobe.d/iwlwifi.conf] remove iwlwifi \ (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e
^iwlwifi | xargs /sbin/rmmod) \ && /sbin/modprobe -r mac80211 

[/etc/modprobe.d/mlx4.conf] softdep mlx4_core post: mlx4_en 

##### rc.local ########################## 

exit 0 

##### pm-utils ########################## 

##### udev rules ######################## 

[/etc/udev/rules.d/70-persistent-net.rules] # PCI device 0x10ec:0x8168 (r8169) SUBSYSTEM=="net", ACTION=="add",
DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>",
ATTR{dev_id}=="0x0", ATTR{type}=="1",
KERNEL=="eth*", NAME="eth0" # PCI device 0x168c:0x0036 (ath9k) SUBSYSTEM=="net", ACTION=="add",
DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>",
ATTR{dev_id}=="0x0", ATTR{type}=="1",
KERNEL=="wlan*", NAME="wlan0" 

##### dmesg ############################# 

[ 1948.074885] ath: phy0: ASPM enabled: 0x43 [ 1948.864372] usb 1-4.3: device firmware
changed 

########## wireless info END ############

```

---

### Post by jeremy31 on 2014-10-29
Is there a switch somewhere to enable wifi or is wifi disabled in BIOS?
Please use code tags when pasting from terminal as it helps with formatting and keeping things from turning into smilies.  Just use [ code ] before the paste and [ /code ] after without the spaces between the [] and code and there is the # option in the advanced reply that will place the tags and you just paste

---

### Post by Robert_Holden on 2014-10-29
there is an airplane mode button and the wifi worked before while i was in windows however i can not figure out how to access the BIOS i tried delete, f2, and f12 none worked
*Edit* i found it and it says wireless enabled

---

### Post by Robert_Holden on 2014-10-29
i do however remember having an option when i set up to connect to an internet device but it asked for a password for my card so i figured i'd skip it and set it up later.

---

### Post by jeremy31 on 2014-10-29
What is the model of the computer if the following doesn't work?
```
sudo modprobe -r ideapad_laptop
```
```
sudo rfkill unblock all
```
Then tell me if any results from the following are yes, or post it
```
rfkill list
```

---

### Post by Robert_Holden on 2014-10-29
it worked thanks

---

### Post by jeremy31 on 2014-10-29
> **Robert_Holden said:**
> it worked thanks

Just one last thing to do or you will have this issue after a restart ```
echo "blacklist ideapad_laptop" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
And use the forum tools at the top of the page to mark as solved if it works after a reboot

---

