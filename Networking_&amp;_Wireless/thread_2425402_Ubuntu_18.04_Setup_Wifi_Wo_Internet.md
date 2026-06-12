---
title: "Ubuntu 18.04 Setup Wifi W/o Internet"
date: 2019-08-25
forum: Networking &amp; Wireless
---

### Post by dybo on 2019-08-25
I'm trying to configure the WiFi on my new laptop.  It does not have an ethernet port, but I do have a second laptop.  The main problem I have been running into is having to manually download dozens of distributions piecemeal, trying to get Ndiswrapper and Unshield to even install.  My desktop has turned into a mess of unreadable folder names.  I did run the wireless-info script, not sure what parts are relevant though.

---

### Post by him610 on 2019-08-25
> I did run the wireless-info script
You need to rerun it, and when it asks if you want to place in pastebin (or something to that effect), you need to choose *yes* then you copy paste the link to the pastebin contents in this thread so others may inspect it and provide advice.

---

### Post by chili555 on 2019-08-25
> **him610 said:**
> You need to rerun it, and when it asks if you want to place in pastebin (or something to that effect), you need to choose *yes* then you copy paste the link to the pastebin contents in this thread so others may inspect it and provide advice.He won't likely have any way to pastebin the results without any internet access.

Please drag and drop the result onto a USB drive and, using another computer, post is here.

---

### Post by him610 on 2019-08-27
> He won't likely have any way to pastebin the results without any internet access.
@chili555, good catch.

---

### Post by dybo on 2019-08-27
I worked on it a bit more yesterday, I found an appropriate driver but it's not Linux compatible by default.  In trying to install Unshield, I ran into another wall of required distributions.  Is there a way for me to collate all the right downloads from my Windows machine so I don't have to do it piecemeal?

Also, here's the output from wireless-info:

```



########## wireless info START ##########


Report from: 24 Aug 2019 20:02 PDT -0700


Booted last: 24 Aug 2019 00:00 PDT -0700


Script from: 22 Oct 2018 03:34 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 18.04.2 LTS
Release:	18.04
Codename:	bionic


##### kernel ############################


Linux 4.18.0-15-generic #16~18.04.1-Ubuntu SMP Thu Feb 7 14:06:04 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=1


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:b822]
	Subsystem: Hewlett-Packard Company Device [103c:831b]
	Kernel modules: r8822be


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 04f2:0976 Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 0bda:b00b Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 05c8:022a Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 001 Device 006: ID 18a5:0304 Verbatim, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### secure boot #######################


SecureBoot enabled


##### lsmod #############################


hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
mac80211              802816  0
wmi_bmof               16384  0
cfg80211              667648  1 mac80211
wmi                    24576  2 hp_wmi,wmi_bmof


##### interfaces ########################


[/etc/network/interfaces]
auto lo
iface lo inet loopback


##### ifconfig ##########################


1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever


##### iwconfig ##########################


lo        no wireless extensions.


##### route #############################


##### resolv.conf #######################


[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']


nameserver 127.0.0.53
options edns0


##### network managers ##################


Installed:


	NetworkManager


Running:


root       587     1  0 19:13 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


##### NetworkManager config #############


[[/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf]]
[connection]
wifi.powersave = 3


[[/etc/NetworkManager/NetworkManager.conf]]
[main]
plugins=ifupdown,keyfile
[ifupdown]
managed=false
[device]
wifi.scan-rand-mac-address=no


[[/usr/lib/NetworkManager/conf.d/10-dns-resolved.conf]]
[main]
dns=systemd-resolved


[[/usr/lib/NetworkManager/conf.d/10-globally-managed-devices.conf]]
[keyfile]
unmanaged-devices=*,except:type:wifi,except:type:wwan


[[/usr/lib/NetworkManager/conf.d/20-connectivity-ubuntu.conf]]
[connectivity]
uri=http://connectivity-check.ubuntu.com/


[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-mac-addr-change-wifi]
match-device=driver:rtl8723bs,driver:rtl8189es,driver:r8188eu,driver:8188eu,driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no
wifi.cloned-mac-address=preserve
ethernet.cloned-mac-address=preserve


##### NetworkManager profiles ###########


##### Netplan config ####################


[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager


##### iw reg get ########################


Region: America/Los_Angeles (based on set time zone)


global
country 00: DFS-UNSET
	(2402 - 2472 @ 40), (N/A, 20), (N/A)
	(2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
	(2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, PASSIVE-SCAN
	(5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
	(5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, PASSIVE-SCAN
	(5735 - 5835 @ 80), (N/A, 20), (N/A), PASSIVE-SCAN
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)


##### iwlist channels ###################


lo        no frequency information.


##### iwlist scan #######################


lo        Interface doesn't support scanning.


##### module infos ######################


[mac80211]
filename:       /lib/modules/4.18.0-15-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     C5D73328CD704BB6E363074
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       4.18.0-15-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.18.0-15-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     BFB309EF7C6C321F605D36E
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.18.0-15-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500


[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


##### modprobe options ##################


[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode


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


[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


##### rc.local ##########################


grep: /etc/rc.local: No such file or directory


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


########## wireless info END ############

```

---

### Post by chili555 on 2019-08-27
It appears that there is aleady a driver on the system that claims your device: r8822be. It is not, however, loaded. Let's load it and see if there are any informative messages, errors, etc.:```
sudo modprobe r8822be
dmesg | grep r88
```Please discontinue all the ndiswrapper, unshield, etc., downloads. Adapting the Windows driver in Ubuntu won't work. Ever.

---

### Post by dybo on 2019-08-28
The first command threw this:

modprobe: Error: could not insert 'r8822be': Operation not permitted

The second one did not appear to do anything.

> Adapting the Windows driver in ubuntu won't work. Ever.

Why is it recommended in the help documentation?  I found that advice through the sticky at the top of this forum...

---

### Post by chili555 on 2019-08-30
> modprobe: Error: could not insert 'r8822be': Operation not permittedIs Secure Boot on or off in the BIOS/EFI. Try turning it off.

What does this report?```
modinfo r8822be | grep -i ver
```> 
Why is it recommended in the help documentation?Because, like a great many things on the internet, it is obsolete. No brave volunteer has stepped forward to devote 2-3 months of his/her life to the project.

---

### Post by dybo on 2019-08-30
Turned off SecureBoot.  Modprobe ran, didn't display anything.  Dmesg threw this:
```

r8822be: module is from the staging direcotry, the quality is unknown, you have been warned
": module verification failed: signature and/or required key missing - tainted kernel
": Using firmware rtlwifi/rtl8822befw.bin
" 0000:02:00.0 wlo1: renamed from wlan0

```
Modinfo threw this:
```

filename: /lib/modules/4.18.0-15-generic/kernel/drivers/staging/rtlwifi/r8822be.ko
descriptiong: PCI basic driver for rtlwifi
srcversion: FCBBD738FC5F4CEEBA19625
vermagic: 4.18.0-15-generic SMP mod_unload

```

---

### Post by chili555 on 2019-08-30
Excellent! Now you have a wireless interface, namely wlo1. Does it scan and see networks?```
sudo iwlist wlo1 scan
```Is the wireless switch or key combination set to to enable the wireless radio?```
rfkill list all
```

---

### Post by dybo on 2019-08-30
iwlist threw: A huge block of text, lots of UNKNOWN.  Will apend

rfkill threw:
```

0: phy0: Wireless LAN
           Soft blocked:  no
           Hard blocked: no
2: hci0:  Bluetooth
          Soft blocked: no
          Hard blocked: no


```

---

### Post by dybo on 2019-08-30
Here's the precise text from iwlist:

```

wlo1      Scan completed :
          Cell 01 - Address: 08:36:C9:48:FC:F4
                    Channel:161
                    Frequency:5.805 GHz
                    Quality=52/70  Signal level=-58 dBm 
                    Encryption key:on
                    ESSID:"SPINDRIFT3"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000012ed60abcb
                    Extra: Last beacon: 76ms ago
                    IE: Unknown: 000A5350494E445249465433
                    IE: Unknown: 01088C129824B048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 0B050500030000
                    IE: Unknown: 2D1AEF0917FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D16A10F0400000000000000000000000000000000000000
                    IE: Unknown: 7F080400080000000040
                    IE: Unknown: BF0CB259820FEAFF0000EAFF0000
                    IE: Unknown: C005019B000000
                    IE: Unknown: C30402020202
                    IE: Unknown: DD830050F204104A0001101044000102103B00010310470010D2767E95023BCDC94E90EC9D382F62C8102100074E657467656172102300074E6574676561721024000631323334353610420007303030303030311054000800060050F20400011011000C43363235302D3130304E4153100800022008103C0001031049000600372A000120
                    IE: Unknown: DD090010180205001C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 46057208010000
          Cell 02 - Address: 08:36:C9:48:FC:F3
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=43/70  Signal level=-67 dBm 
                    Encryption key:on
                    ESSID:"Spindrift2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000265971a197
                    Extra: Last beacon: 2932ms ago
                    IE: Unknown: 000A5370696E647269667432
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030107
                    IE: Unknown: 050400020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 0B050000080000
                    IE: Unknown: 2D1AFE191BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D16070F0000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080500080000000040
                    IE: Unknown: DD310050F204104A000110104400010210470010D2767E95023BCDC94E90EC9D382F62C8103C0001031049000600372A000120
                    IE: Unknown: DD090010180200000C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 46057208010000
          Cell 03 - Address: 00:1A:2B:60:94:36
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm 
                    Encryption key:on
                    ESSID:"Starr Seaside"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000e22d5b7d
                    Extra: Last beacon: 76ms ago
                    IE: Unknown: 000D53746172722053656173696465
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 04 - Address: 04:A1:51:AB:9E:0E
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=27/70  Signal level=-83 dBm 
                    Encryption key:on
                    ESSID:"NWS8"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000008cb4369e46
                    Extra: Last beacon: 2700ms ago
                    IE: Unknown: 00044E575338
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030108
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33CC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1ACC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3408080800000000000000000000000000000000000000
                    IE: Unknown: 3D1608080800000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD7C0050F204104A0001101044000102103B000103104700100000000000001000000004A151AB9E0E102100074E65746765617210230008574E445233383030102400025631104200046E6F6E651054000800060050F204000110110015574E44523338303028576972656C65737320415029100800020086103C000103
          Cell 05 - Address: AC:3B:77:3E:4C:DE
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm 
                    Encryption key:on
                    ESSID:"MySpectrumWiFid8-2G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000004efd440ca50
                    Extra: Last beacon: 76ms ago
                    IE: Unknown: 00134D79537065637472756D5769466964382D3247
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 3204B048606C
                    IE: Unknown: 2D1AAD011BFFFFFF0000000000000000000100000000000000000000
                    IE: Unknown: 3D1606080400000000000000000000000000000000000000
                    IE: Unknown: 7F0800000F0000000040
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: B0:B9:8A:7E:1E:6B
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)         
                    Quality=23/70  Signal level=-87 dBm 
                    Encryption key:on
                    ESSID:"NETGEAR76"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003fdad6a274
                    Extra: Last beacon: 2464ms ago
                    IE: Unknown: 00094E4554474541523736
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400020000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 0B050100190000
                    IE: Unknown: 2D1AAD1917FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080500080000000040
                    IE: Unknown: DD310050F204104A00011010440001021047001009EAD02947B8885AA0B76FE9C4F64D15103C0001031049000600372A000120
                    IE: Unknown: DD090010180201001C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 46057208010000
                    IE: Unknown: DD1E00904C0408BF0CB259820FEAFF0000EAFF0000C005000B000000C3020002


```

It seems like its identified some networks, now how do I bridge the gap?  The top two are my networks btw

---

### Post by chili555 on 2019-08-30
> 
now how do I bridge the gap?
Click the Network Manager icon at the top right. NM should see the networks, as well. Click on yours and connect!

PS - Your router appears to be set on auto channel select. A fixed channel is much preferred.

---

### Post by dybo on 2019-08-30
Gap, bridged.  Thanks for the help, internet access really does make everything so much easier

---

### Post by chili555 on 2019-08-30
Please use thread tools at the top to mark the thread Solved. The searchers will appreciate it.

---

