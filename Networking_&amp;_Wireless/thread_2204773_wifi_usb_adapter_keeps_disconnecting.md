---
title: "wifi usb adapter keeps disconnecting"
date: 2014-02-10
forum: Networking &amp; Wireless
---

### Post by cardinalidiego on 2014-02-10
Hello!


with ubuntu 13.10 64bit I'm using a d-link dwl-G132 usb wifi terminal, which works perfectly on windows. on ubuntu it keeps connecting and disconnecting all the time (kind of switching the aeroplane mode on and off in cycles); it takes a lot of cycling to connect to the wifi network, and when it does it doesn't last for more than 2 minutes!


thank you in advance

---

### Post by varunendra on 2014-02-11
Welcome to the forums cardinalidiego!

When your USB adapter seems connected, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by cardinalidiego on 2014-02-12
[COLOR=#000000]here it comes! I managed to run it during one of the few moments when the adapter worked and it managed to connect to the wifi network

thank you anyway!

```
[/COLOR]



*************** info trace ***************


***** uname -a *****


Linux SCROTO-02 3.11.0-15-generic #25-Ubuntu SMP Thu Jan 30 17:22:01 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


***** lsb_release *****


Distributor ID:	Ubuntu
Description:	Ubuntu 13.10
Release:	13.10
Codename:	saucy


***** lspci *****


00:07.0 Bridge [0680]: NVIDIA Corporation MCP61 Ethernet [10de:03ef] (rev a2)
	Subsystem: ASRock Incorporation 939NF6G-VSTA Board [1849:03ef]
	Kernel driver in use: forcedeth


***** lsusb *****


Bus 001 Device 003: ID 0bc2:2300 Seagate RSS LLC Expansion Portable
Bus 001 Device 007: ID 04e8:681d Samsung Electronics Co., Ltd Galaxy Portal/Spica Android Phone
Bus 001 Device 092: ID 2001:3a02 D-Link Corp. DWL-G132 [Atheros AR5523]
Bus 001 Device 002: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 15d9:0a4c Trust International B.V. USB+PS/2 Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


***** PCMCIA Card Info *****




***** iwconfig *****


wlan0     IEEE 802.11bg  ESSID:"WebCubeNew-46B8"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC address removed>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=47/70  Signal level=-63 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:183  Invalid misc:52   Missed beacon:0




***** rfkill *****


224: phy224: Wireless LAN
	Soft blocked: no
	Hard blocked: no


***** lsmod *****




***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: wlan0  [WebCubeNew-46B8] ---------------------------------------------
  Type:              802.11 WiFi
  Driver:            ar5523
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           1 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *WebCubeNew-46B8:Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 51 WPA WPA2
    TP-LINK_CFCEED:  Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 10 WPA2


  IPv4 Settings:
    Address:         192.168.1.163
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off






***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=false
WimaxEnabled=true


***** NetworkManager.conf *****


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


no-auto-default=<MAC address removed>,00:19:66:99:5C:15,D6:80:A2:92:18:A2,1E:61:E3:EA:39:2F,


[ifupdown]
managed=false


***** interfaces *****


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


***** iwlist *****


No way to aquire root rights found.


***** resolv.conf *****


nameserver 127.0.1.1
search huawei.com


***** blacklist *****


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


***** modinfo *****




***** udev rules *****


# PCI device 0x10de:0x03ef (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# USB device 0x:0x (ar5523)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


***** dmesg *****


[ 1879.501778] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1879.502300] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1884.419866] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1884.420431] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1889.341139] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1889.341596] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1894.240786] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1894.241267] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1899.209297] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1899.209774] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1904.113292] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1904.113729] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1908.848780] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1908.849217] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1913.772065] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1913.772557] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1918.711752] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1918.712452] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1923.648435] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1923.648930] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1928.580289] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1928.580856] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1933.505073] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1933.505541] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1938.421992] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1938.422477] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1943.338294] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1943.338772] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1948.256329] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1948.256799] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1953.185884] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1953.186370] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1958.099669] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1958.100171] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1962.984532] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1962.985033] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1967.885338] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1967.885814] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1971.424632] usb 1-8: could not send firmware block data
[ 1990.920223] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1990.920696] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1995.839926] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1995.840414] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2000.751236] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2000.751717] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2005.670815] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2005.671294] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2010.596339] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2010.596818] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2015.515650] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2015.516161] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2020.450563] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2020.451087] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2025.347194] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2025.347734] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2030.253324] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2030.253801] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2035.157993] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2035.158468] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2040.077646] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2040.078150] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2044.991791] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2044.992306] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2049.922222] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2049.922733] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2054.850410] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2054.850928] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2059.763552] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2059.764076] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2064.665126] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2064.665645] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2069.560201] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2069.560684] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2074.467665] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2074.468192] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2079.376442] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2079.376926] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2084.278066] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2084.278490] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2089.207308] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2089.207791] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2094.096675] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2094.097169] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2098.998054] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2098.998528] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2103.908058] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2103.908544] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2108.809680] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2108.810155] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2113.731505] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2113.731996] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2118.638455] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2118.638957] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2123.528462] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2123.528944] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2128.438082] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2128.438573] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2133.330464] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2133.330953] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2138.249734] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2138.250259] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2143.147438] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2143.147918] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2148.035979] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2148.036487] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2152.941305] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2152.941801] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2157.848135] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2157.848612] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2162.750665] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2162.751166] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2183.756269] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2183.756700] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2186.408479] wlan0: authenticate with <MAC address removed>
[ 2186.412747] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2186.414952] wlan0: authenticated
[ 2186.416183] wlan0: associate with <MAC address removed> (try 1/3)
[ 2186.418950] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 2186.420079] wlan0: associated
[ 2186.420108] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


****************** done ******************



[COLOR=#000000]
```[/COLOR]

---

### Post by varunendra on 2014-02-12
Interesting report..

A quick suggestion based on this -
> **cardinalidiego said:**
> ```

  Wireless Access Points (* = current AP)
    ***WebCubeNew-46B8:Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 51 [COLOR="#FF0000"]WPA WPA2[/COLOR]**
    TP-LINK_CFCEED:  Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 10 WPA2
```

Please change the encryption type in your router/access-point to pure WPA2-AES(CCMP). Currently it is set to WPA/WPA2 mixed mode which requires TKIP encryption. Avoid using TKIP or the mixed mode. Reboot the router after making the changes.

If that doesn't solve the problem, please post the outputs of -
```
lsmod
modinfo ar5523
dmesg | grep ar5523
```

---

### Post by cardinalidiego on 2014-02-13
changed the encryption but no results; here's the outputs you asked for. and thank you again for your patience!

```


diego@SCROTO-02:~$ lsmod
Module                  Size  Used by
arc4                   12608  2 
ar5523                 42103  0 
mac80211              597268  1 ar5523
cfg80211              480503  2 mac80211,ar5523
rfcomm                 69130  0 
bnep                   19704  2 
bluetooth             372041  10 bnep,rfcomm
binfmt_misc            17468  1 
snd_hda_codec_hdmi     41117  1 
snd_hda_codec_realtek    55704  1 
ppdev                  17671  0 
kvm_amd                59987  0 
kvm                   431720  1 kvm_amd
radeon               1402995  3 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
ttm                    84169  1 radeon
snd_rawmidi            30095  1 snd_seq_midi
snd_hda_intel          48171  5 
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
psmouse                97655  0 
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
serio_raw              13413  0 
drm_kms_helper         52710  1 radeon
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
edac_core              62342  0 
k8temp                 12978  0 
edac_mce_amd           22617  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_timer              29433  2 snd_pcm,snd_seq
drm                   297056  5 ttm,drm_kms_helper,radeon
snd                    69141  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
i2c_algo_bit           13413  1 radeon
soundcore              12680  1 snd
i2c_nforce2            13221  0 
parport_pc             32701  1 
mac_hid                13205  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 53014  0 
hid                   105858  2 hid_generic,usbhid
usb_storage            62062  1 
pata_acpi              13038  0 
forcedeth              67460  0 
sata_nv                27745  4 


diego@SCROTO-02:~$ modinfo ar5523
filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/ath/ar5523/ar5523.ko
firmware:       ar5523.bin
license:        Dual BSD/GPL
srcversion:     2005E29498631D7DD0C599E
alias:          usb:v1385p5F03d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1385p5F02d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1385p5F01d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1385p5F00d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1385p4251d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1385p4250d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CDEp0013d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CDEp0012d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1435p0829d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1435p0828d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1435p0827d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1435p0826d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v157Ep3007d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v157Ep3006d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v157Ep3206d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v157Ep3205d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v157Ep3007d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v157Ep3006d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p5F01d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p5F00d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p4251d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p4250d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p4301d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p4300d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0D8Ep7803d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0D8Ep7802d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v16ABp7812d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v16ABp7811d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v16ABp7802d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v16ABp7801d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v129Bp160Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v129Bp160Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1690p0711d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1690p0710d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1690p0713d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1690p0712d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3A05d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3A04d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3A03d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3A02d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3A01d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3A00d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0D8Ep7812d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0D8Ep7811d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0D8Ep7802d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0D8Ep7801d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p0006d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p0005d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p0004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p0003d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p0002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p0001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v168Cp0002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v168Cp0001d*dc*dsc*dp*ic*isc*ip*in*
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.11.0-15-generic SMP mod_unload modversions 

diego@SCROTO-02:~$ dmesg | grep ar5523
[  218.181674] usbcore: registered new interface driver ar5523
[  286.456722] usb 1-1: ar5523_data_rx_cb: USB err: -2
[  286.456964] usb 1-1: ar5523_data_rx_cb: USB err: -2
[  286.457213] usb 1-1: ar5523_data_rx_cb: USB err: -2
[  286.457463] usb 1-1: ar5523_data_rx_cb: USB err: -2
[  286.457713] usb 1-1: ar5523_data_rx_cb: USB err: -2
[  286.457963] usb 1-1: ar5523_data_rx_cb: USB err: -2
[  286.458212] usb 1-1: ar5523_data_rx_cb: USB err: -2
[  286.458840] usb 1-1: ar5523_data_rx_cb: USB err: -2
[  286.459086] usb 1-1: ar5523_data_rx_cb: USB err: -2





```

---

### Post by varunendra on 2014-02-14
> **cardinalidiego said:**
> ```

diego@SCROTO-02:~$ dmesg | grep ar5523
[  218.181674] usbcore: registered new interface driver ar5523
[  286.456722] usb 1-1: ar5523_data_rx_cb: **[COLOR="#FF0000"]USB err: -2[/COLOR]**
[  286.456964] usb 1-1: ar5523_data_rx_cb: USB err: -2
```

Haven't seen or worked with this driver before, but I don't like these error messages. Let's try a newer version of this driver to see if we can get rid of these errors -

Install the base packages required to build a module -
```
sudo apt-get install linux-headers-generic build-essential
```

Then,

[INDENT]**1)** Download the "backports-3.12.8-1" package from here : [http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/](http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/)

**2)** Right-click the downloaded package > Extract here.

**3)** Assuming this extracted folder is in the "Downloads" folder in your Home directory, run the following commands in a terminal -
```
cd Downloads/backports-3.12.8-1
make defconfig-ar5523
make
sudo make install
```

**4)** Reboot > Connect and let us know about its performance. Also check "dmesg | grep ar5523" again, are the error messages gone?[/INDENT]

---

