---
title: "Feisty Fawn vs. D-Link Airplus DWL-G520, ndiswrapper and acx"
date: 2007-03-21
forum: Networking &amp; Wireless
---

### Post by MadeR on 2007-03-21
I always had problem with my D-Link DWL-G520+ Wireless 802.11 b/g PCI card.

```

**output of lspci -vv**
02:07.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
        Subsystem: D-Link System Inc DWL-G520+ Wireless PCI Adapter
        Flags: bus master, medium devsel, latency 32, IRQ 21
        Memory at f1024000 (32-bit, non-prefetchable) [size=8K]
        Memory at f1000000 (32-bit, non-prefetchable) [size=128K]
        Capabilities: [40] Power Management version 2
```

```

**output of dmesg: acx**
[ 1894.898590] acx: Loaded combined PCI/USB driver, firmware_ver=default
[ 1894.898597] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
[ 1894.918677] ACPI: PCI Interrupt 0000:02:07.0[A] -> GSI 22 (level, low) -> IRQ 21
[ 1894.919118] acx: found ACX111-based wireless network card at 0000:02:07.0, irq:21, phymem1:0xF1024000, phymem2:0xF1000000, mem1:0xf8b00000, mem1_size:8192, mem2:0xf8f40000, mem2_size:131072
[ 1894.920727] acx: loading firmware for acx1111 chipset with radio ID 16
[ 1895.568431] NVS_vendor_offs:01CD probe_delay:200 eof_memory:1114112
[ 1895.568439] CCAModes:04 Diversity:01 ShortPreOpt:01 PBCC:01 ChanAgil:00 PHY:05 Temp:01
[ 1895.568447] AntennaID:00 Len:02 Data:01 02
[ 1895.568451] PowerLevelID:01 Len:02 Data:001E 000A
[ 1895.568456] DataRatesID:02 Len:05 Data:02 04 11 22 44
[ 1895.568512] DomainID:03 Len:06 Data:30 20 30 31 32 40
[ 1895.568523] ProductID:04 Len:09 Data:**[color=red]TI ACX100[/color] *Shouldn't it be TI ACX111?***
[ 1895.568527] ManufacturerID:05 Len:07 Data:TI Test
[ 1895.628173] acx: === chipset TNETW1130, radio type 0x16 (Radia), form factor 0x01 ((mini-)PCI / CardBus), EEPROM version 0x05: uploaded firmware 'Rev 1.2.1.34' ===
[ 1895.629450] acx v0.3.36: net device wlan0, driver compiled against wireless extensions 21 and Linux 2.6.20-12-generic
[ 1895.632196] usbcore: registered new interface driver acx_usb
[ 1895.860509] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

```

**output of dmesg: ndiswrapper**
[ 2328.510452] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
[ 2328.615074] usbcore: registered new interface driver ndiswrapper
```

Basicly the acx driver never, ever anyhow worked. No way.
In dapper and edgy (and freebsd) I always used ndiswrapper, but in feisty fawn I can't connect to my AP anymore.
I remember that when ndiswrapper was loaded in Edgy, at least 4-5 more lines appeared in the output of dmesg.

```

**output of (acx::) sudo wpa_supplicant -dd -Dwext -iwlan0 -c /etc/wpa_supplicant/wpa_supplicant.conf**
sudo wpa_supplicant -dd -Dwext -iwlan0 -c /etc/wpa_supplicant/wpa_supplicant.conf
Initializing interface 'wlan0' conf '/etc/wpa_supplicant/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant/wpa_supplicant.conf' -> '/etc/wpa_supplicant/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 3 - start of a new network block
ssid - hexdump_ascii(len=6):
     61 76 61 6c 6f 6e                                 avalon
key_mgmt: 0x2
proto: 0x1
pairwise: 0x8
group: 0x8
PSK (ASCII passphrase) - hexdump_ascii(len=19): [REMOVED]
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='avalon'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=21 WE(source)=9 enc_capa=0x0
  capabilities: key_mgmt 0x0 enc 0x3
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:11:95:47:07:6b
wpa_driver_wext_set_wpa
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 7 value 0x1 - Driver does not support WPA.
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: Operation not supported
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: Operation not supported
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
```
last part cycling, I pressed Ctrl-c


```

**output of (ndiswrapper::) sudo wpa_supplicant -dd -Dndiswrapper -iwlan0 -c /etc/wpa_supplicant/wpa_supplicant.conf **[color=red]**Segmentation fault (core dumped)**[/color]
Initializing interface 'wlan0' conf '/etc/wpa_supplicant/wpa_supplicant.conf' driver 'ndiswrapper' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant/wpa_supplicant.conf' -> '/etc/wpa_supplicant/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 3 - start of a new network block
ssid - hexdump_ascii(len=6):
     61 76 61 6c 6f 6e                                 avalon
key_mgmt: 0x2
proto: 0x1
pairwise: 0x8
group: 0x8
PSK (ASCII passphrase) - hexdump_ascii(len=19): [REMOVED]
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='avalon'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
ioctl[SIOCSIWPMKSA]: No such device
ioctl[SIOCSIWMODE]: No such device
Could not configure driver to use managed mode
ioctl[SIOCGIFFLAGS]: No such device
Could not set interface 'wlan0' UP
ioctl[SIOCGIWRANGE]: No such device
WEXT: Operstate: linkmode=1, operstate=5
ioctl[SIOCGIFINDEX]: No such device
Failed to add interface wlan0
State: DISCONNECTED -> DISCONNECTED
[color=red]**Segmentation fault (core dumped)**[/color]

```

```

**output of (ndiswrapper::) sudo wpa_supplicant -dd -Dwext -iwlan0 -c /etc/wpa_supplicant/wpa_supplicant.conf **[color=red]**Segmentation fault (core dumped)**[/color]
Initializing interface 'wlan0' conf '/etc/wpa_supplicant/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant/wpa_supplicant.conf' -> '/etc/wpa_supplicant/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 3 - start of a new network block
ssid - hexdump_ascii(len=6):
     61 76 61 6c 6f 6e                                 avalon
key_mgmt: 0x2
proto: 0x1
pairwise: 0x8
group: 0x8
PSK (ASCII passphrase) - hexdump_ascii(len=19): [REMOVED]
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='avalon'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
ioctl[SIOCSIWPMKSA]: No such device
ioctl[SIOCSIWMODE]: No such device
Could not configure driver to use managed mode
ioctl[SIOCGIFFLAGS]: No such device
Could not set interface 'wlan0' UP
ioctl[SIOCGIWRANGE]: No such device
WEXT: Operstate: linkmode=1, operstate=5
ioctl[SIOCGIFINDEX]: No such device
Failed to add interface wlan0
State: DISCONNECTED -> DISCONNECTED
[color=red]**Segmentation fault (core dumped)**[/color]

```

```

**cat /etc/wpa_supplicant/wpa_supplicant.conf**
ctrl_interface=/var/run/wpa_supplicant

network={
        ssid="avalon"
        key_mgmt=WPA-PSK
        proto=WPA
        pairwise=TKIP
        group=TKIP
        psk=[color="purple"]password[/color]
}

```


Can you help me?

---

### Post by MadeR on 2007-03-21
solution:
acx, as usual, is useless.
I had to install ndiswrapper-utils-1.**9**
The problem is that ndiswrapper-utils-1.8 used in Feisty Fawn Herd 5 is **NOT** compatible with kernel, ndisbackend or whatever it is.
I took a while to understand and discover this, because I really could *NOT* believe that Herd *n*, even though an alpha release, had kernel space and userland frontends not syncronized... unbelievable.

---

### Post by MadeR on 2007-03-21
What I really do not understand is why apt-get upgrade did not upgrade ndiswrapper-utils from version 1.8 to version 1.9.

Has someone a clue?

---

### Post by karachuonyo on 2007-03-22
I have a card with the acx 111 chipset and it worked well out of the box with the latest kernel on kubuntu edgy when connecting to a WEP network. However i have just my router encryption to the more secure WPA-PSK and i cannot connect. Is it possible this card does not support WPA under linux or its just my inexperience showing. When i use the same card under XP thru the same WPA encrypted router i have no problems.

---

### Post by MadeR on 2007-03-22
> **karachuonyo said:**
> I have a card with the acx 111 chipset and it worked well out of the box with the latest kernel on kubuntu edgy when connecting to a WEP network. However i have just my router encryption to the more secure WPA-PSK and i cannot connect. Is it possible this card does not support WPA under linux or its just my inexperience showing. When i use the same card under XP thru the same WPA encrypted router i have no problems.

try upgrading ndiswrapper-utils to version 1.9, blacklist acx, ndiswrapper -m and if you configure correctly wpa_supplicant you will connect using WPA.

wep sucks. too easy to crack, never use it any longer.

---

### Post by musicpont on 2007-03-31
> **MadeR said:**
> solution:
acx, as usual, is useless.
I had to install ndiswrapper-utils-1.**9**
The problem is that ndiswrapper-utils-1.8 used in Feisty Fawn Herd 5 is **NOT** compatible with kernel, ndisbackend or whatever it is.
I took a while to understand and discover this, because I really could *NOT* believe that Herd *n*, even though an alpha release, had kernel space and userland frontends not syncronized... unbelievable.

My card also uses acx111 but after a couple of hours struggling with iwconfig,iwlist and ifcpnfig it worked....

But as soon as i rebooted the machine it never got back to life again. The main problem seems to be to associate the card with the AP...eventually i get it to connect to the AP and access the local devices, but still no internet browsing!!!

---

### Post by dpm on 2007-04-07
> **karachuonyo said:**
> Is it possible this card does not support WPA under linux or its just my inexperience showing. 

It is not your inexperience. The acx100 driver does not yet support WPA:

[http://acx100.sourceforge.net/wiki/WPA](http://acx100.sourceforge.net/wiki/WPA)

Cheers.

---

