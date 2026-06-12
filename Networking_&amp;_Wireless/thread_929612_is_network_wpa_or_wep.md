---
title: "is network wpa or wep?"
date: 2008-09-25
forum: Networking &amp; Wireless
---

### Post by jamaas on 2008-09-25
I'm at a friends and have been given a key for a wireless network ... which I can get to connect via XP but no luck with hardy.  Is there a way to determine if the network is wep or wpa protected?

The key I've been given is apparently 63 characters long ...unless there is a blank space at the end?  and begins and ends as such.  When I try using some command line commands like iwconfig to put in they key, bash seems to interpret the $ as a new line and won't read it properly

(>vU2  ...  J-$9w


Any advice on what type of network it is will be big help, know what type to try and configure.

TIA

Jim

---

### Post by lisati on 2008-09-25
When network manager detects the signal, it should automatically detect what kind of key is required, whether it is WEP or WPA

---

### Post by jamaas on 2008-09-25
Kia Ora,

Doesn't seem to, am I doing something wrong?  I just dug around in windows and it seems it is a wpa personal, tkip connection.   Does the 63 characters make senses?  Would need to be 64 wouldn't it?

Thanks

Jim

> **lisati said:**
> When network manager detects the signal, it should automatically detect what kind of key is required, whether it is WEP or WPA

---

### Post by lisati on 2008-09-25
> **jamaas said:**
> Kia Ora,

Doesn't seem to, am I doing something wrong?  I just dug around in windows and it seems it is a wpa personal, tkip connection.   Does the 63 characters make senses?  Would need to be 64 wouldn't it?

Thanks

Jim

64 makes better sense to me than 63. I'm sure there's a command somewhere that can be used to show what the network expects, but it eludes me for the moment..... Another possibility is that it's one of the arguments for the wpa_passphrase  command mentioned at the tutorial at [http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

Anyone else got any thoughts?

---

### Post by HangMan101 on 2008-09-25
Does your friend has an hidden network?

if so,
you need to tel the network manager to manually connect to a network.
supply the name and try wep / wpa

if not,
post the result of:
```

iwlist wlan0 scanning 

```

and check that you do not have a kill switch on. (in some systems this can be toggled in windows by software like some acer's do)
you can check by looking through the result of
```

dmesg

```
(most drivers report if wireless is disabled by switch)

---

### Post by jamaas on 2008-09-25
Thanks,

Network is visible, have the name

also says it is wpa version 1, group cipher tkip, pairwise cipher tkip and authentication suites psk.

does this make sense?

Where can I look for the presence of kill switch in dmesg output?

Thanks

Jim

> **HangMan101 said:**
> Does your friend has an hidden network?

if so,
you need to tel the network manager to manually connect to a network.
supply the name and try wep / wpa

if not,
post the result of:
```

iwlist wlan0 scanning 

```

and check that you do not have a kill switch on. (in some systems this can be toggled in windows by software like some acer's do)
you can check by looking through the result of
```

dmesg

```
(most drivers report if wireless is disabled by switch)

---

### Post by HangMan101 on 2008-09-25
well you can see the network there it means you have no kill switch problem but an GUI problem. try to manually connect with the gui and use the information from the "iwlist wlan0 scanning"

but to check look for a message that says that a kill switch is on depends on the driver how the message look like

for more key detail: [http://darkvoice.dyndns.org/wlankeygen/](http://darkvoice.dyndns.org/wlankeygen/) 
it give some insight on how a key looks just generate a few(not usable in your ap unless you configure it with one you generated)

---

### Post by jamaas on 2008-09-25
Does this help diagnose the problem at all ??

sudo wpa_supplicant -w -D wext -i wlan0 -c/etc/wpa_supplicant.conf -dd
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ap_scan=1
ctrl_interface='/var/run/wpa_supplicant'
Line: 5 - start of a new network block
ssid - hexdump_ascii(len=17):
     4d 41 50 72 65 6d 6f 74 65 77 69 72 65 6c 65 73   MAPremotewireles
     73                                                s               
scan_ssid=0 (0x0)
proto: 0x1
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=63): [REMOVED]
pairwise: 0x8
group: 0x8
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='MAPremotewireless'
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
Waiting for interface..
ioctl[SIOCGIFINDEX]: No such device
Waiting for interface..
ioctl[SIOCGIFINDEX]: No such device
Waiting for interface..
ioctl[SIOCGIFINDEX]: No such device
Waiting for interface..



or perhaps this ????



eth1      IEEE 802.11g  ESSID:"MAPremotewireless"  Nickname:"MAPremotewireless"
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:02:CF:57:74:A2   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=68/100  Signal level=-59 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:79  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:56   Missed beacon:2



Thanks

Jim

---

