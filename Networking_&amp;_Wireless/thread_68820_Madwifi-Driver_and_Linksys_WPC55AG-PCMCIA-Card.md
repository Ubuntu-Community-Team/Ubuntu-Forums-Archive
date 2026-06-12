---
title: "Madwifi-Driver and Linksys WPC55AG-PCMCIA-Card"
date: 2005-09-24
forum: Networking &amp; Wireless
---

### Post by h0bi on 2005-09-24
Madwifi-Driver and Linksys WPC55AG-PCMCIA-Card

Hello,

my Linksys WPC55AG doesn't work with the madwifi-driver module.

As I can see, the necessary modules are loaded  

lsmod | grep ath

ath_pci 55584 0
ath_rate_onoe 8840 1 ath_pci
wlan 106588 4 wlan_wep,ath_pci,ath_rate_onoe
ath_hal 133328 2 ath_pci

The card is configured for networking  (ifconfig ath0)

ath0 Protokoll Ethernet Hardware Adresse xx xx xx xx FF 5F
inet Adresse 192.168.2.198 Bcast 192.168.2.255 Maske 255.255.255.0
inet6 Adresse  fe80  212 17ff fe78 df5f/64 Gültigkeitsbereich Verbindung
UP BROADCAST RUNNING MULTICAST MTU 1500 Metric 1
RX packets 0 errors 489 dropped 0 overruns 0 frame 489
TX packets 12 errors 0 dropped 0 overruns 0 carrier 0
Kollisionen 0 Sendewarteschlangenlänge 199
RX bytes 0 (0.0 b) TX bytes 720 (720.0 b)
Interrupt 11 Speicher e0aa0000-e0ab0000

The card ist configured for wifi  (iwconfig ath0)

ath0 IEEE 802.11b ESSID "myNet"
Mode Managed Frequency 2.437 GHz Access Point  xx xx xx D4 70 37
Bit Rate=11 Mb/s Tx-Power 50 dBm Sensitivity=0/3
Retry off RTS thr off Fragment thr off
Encryption key off
Power Management off
Link Quality=53/94 Signal level=-42 dBm Noise level=-95 dBm
Rx invalid nwid 72 Rx invalid crypt 0 Rx invalid frag 0
Tx excessive retries 0 Invalid misc 0 Missed beacon 0

The router (Linksys WRT54G) is configured with IP 192.168.2.1 and channel 6. Encyrption is (temporarily) disabled.

The LEDs Power and Link are alternatly blinking. But there is no ping.

'iwlist ath0 scan' shows that the ap is available

ath0      Scan completed  
          Cell 01 - Address  xx xx xx D4 70 37
                    ESSID "myNet"
                    Mode Master
                    Frequency 2.437 GHz (Channel 6)
                    Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
                    Encryption key off
                    Bit Rate 1 Mb/s
                    Bit Rate 2 Mb/s
                    Bit Rate 5 Mb/s
                    Bit Rate 6 Mb/s
                    Bit Rate 9 Mb/s
                    Bit Rate 11 Mb/s
                    Bit Rate 12 Mb/s
                    Bit Rate 18 Mb/s
                    Bit Rate 24 Mb/s
                    Bit Rate 36 Mb/s
                    Bit Rate 48 Mb/s
                    Bit Rate 54 Mb/s
                    Extra bcn_int=100


Any ideas ?

If its useful, here is the output from iwpriv ath0 -a

ath0 Available read-only private ioctl  
ath0 get_turbo 0
ath0 get_mode 2
ath0 get_authmode 1
ath0 get_protmode 1
ath0 get_mcastcipher 1
ath0 get_mcastkeylen 16
ath0 get_uciphers 15
ath0 get_ucastcipher 0
ath0 get_ucastkeylen 13
ath0 get_keymgtalgs 3
ath0 get_rsncaps 0
ath0 get_roaming 1
ath0 get_privacy 0
ath0 get_countermeas 0
ath0 get_dropunencry 1
ath0 get_wpa 0
ath0 get_driver_caps 255247
ath0 get_wme 0
ath0 get_hide_ssid 0
ath0 get_ap_bridge 1
ath0 get_inact 300
ath0 get_inact_auth 180
ath0 get_inact_init 30

BTW the card works with linuxant-driverloader and Ubuntu, as with Linksys-Driver and Windows too.


Thanks for help


h0bi

---

### Post by FLeiXiuS on 2005-09-24
Do you have 2 network interfaces?

What's the command "route -n" show?

---

### Post by h0bi on 2005-10-01
:) Uhhh, I've got it.

The problem was the communication between the madwifi-driver and the router-firmware (WRT54g). It seems to be incompatible.

After I've changed the firmware from alchemy to dd-wrt everthing works fine.

---

