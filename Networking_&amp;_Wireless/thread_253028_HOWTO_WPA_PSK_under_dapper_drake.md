---
title: "HOWTO WPA PSK under dapper drake"
date: 2006-09-07
forum: Networking &amp; Wireless
---

### Post by cccc on 2006-09-07
**[SIZE=5][COLOR="SeaGreen"]HOWTO WPA PSK dapper drake[/COLOR][/SIZE]**


I have wireless router WGU624 and wlan card WG311T from Netgear

at the wireless router:

- create SSID (essid)
- a and **g only enabled** 
- Security mode: **WPA-PSK**
- Cipher Type: **TKIP**
- create **WPA Passphrase** (WPA key) 
- **SSID Broadcast disabled**


1.) my wlan card was identified automatically as **ath0**```

# ifconfig -a
**ath0**  Link encap:Ethernet  HWaddr 00:14:6C:31:C2:B5
          inet addr:192.168.1.20  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:6cff:fe31:c2b5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5760 errors:866 dropped:0 overruns:0 frame:866
          TX packets:5327 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:5850301 (5.5 MiB)  TX bytes:840628 (820.9 KiB)
          Interrupt:11 Memory:f8a20000-f8a30000

# lsmod | grep ath
**ath_pci**                80540  0
**ath_rate_sample**        17160  1 ath_pci
**wlan **                 144924  4 wlan_tkip,ath_pci,ath_rate_sample
**ath_hal  **             148816  3 ath_pci,ath_rate_sample
```
2.) I have done all online updates:```

# **su **
# apt-get update
# apt-get upgrade
# uname -a
Linux ubuntu 2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686 GNU/Linux

```
3.) after updates I've installed linux-restricted-modules according to my kernel:```

# apt-cache search madwifi
linux-restricted-modules-2.6.15-23-386 - Non-free Linux 2.6.15 modules on 386
linux-restricted-modules-2.6.15-23-686 - Non-free Linux 2.6.15 modules on PPro/Celeron/PII/PIII/PIV
linux-restricted-modules-2.6.15-23-k7 - Non-free Linux 2.6.15 modules on AMD K7
hostapd - user space IEEE 802.11 AP and IEEE 802.1X/WPA/WPA2/EAP Authenticator
linux-restricted-modules-2.6.15-25-386 - Non-free Linux 2.6.15 modules on 386
linux-restricted-modules-2.6.15-25-686 - Non-free Linux 2.6.15 modules on PPro/Celeron/PII/PIII/PIV
linux-restricted-modules-2.6.15-25-k7 - Non-free Linux 2.6.15 modules on AMD K7
linux-restricted-modules-2.6.15-26-386 - Non-free Linux 2.6.15 modules on 386
linux-restricted-modules-2.6.15-26-686 - Non-free Linux 2.6.15 modules on PPro/Celeron/PII/PIII/PIV
linux-restricted-modules-2.6.15-26-k7 - Non-free Linux 2.6.15 modules on AMD K7

```
in my case```

# su apt-get install linux-restricted-modules-2.6.15-25-386
```
4.)```
# su apt-get install wpasupplicant
```
reboot the machine

5.) from the Konsole use the following command:```

# which wpa_passphrase
/sbin/wpa_passphrase

# su /sbin/wpa_passphrase myessid mysecretpassphrase
network={
        [COLOR="DarkGreen"] ssid="myessid"
        #psk="mysecretpassphrase"
         psk=e46827d16672b883657307d7e8e12823c63cbfa7a6d5a8364f5d8aa8bbbeacb2
[/COLOR]
}


```
mysecretpassphrase (WPA key) must have 8-63 characters.


6.) create **[COLOR="Red"]/etc/wpa_supplicant.conf[/COLOR]**, copy from /usr/share/doc/wpa_supplicant/examples 
or edit if already exists.

open /etc/wpa_supplicant.conf, delete all example entries (example blocks)
 and you should have something like this:```

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1

# Example blocks:

# WPA-PSK
network={
        scan_ssid=1 
        proto=WPA
        key_mgmt=WPA-PSK
        pairwise=CCMP TKIP
        group=CCMP TKIP WEP104 WEP40  
          [COLOR=DarkGreen]
        ssid="myessid"
        psk=e46827d16672b883657307d7e8e12823c63cbfa7a6d5a8364f5d8aa8bbbeacb2[/COLOR]           
        
        priority=2     
}
```if won't work, you could try:```
ap_scan=2
```

7.)```

# su chmod 600 /etc/wpa_supplicant.conf
# su wpa_supplicant -dd -K -t -i ath0 -D **[COLOR="Red"]madwifi[/COLOR]** -c /etc/wpa_supplicant.conf

```or try```
# which wpa_supplicant
/sbin/wpa_supplicant
# su /sbin/wpa_supplicant -i ath0 -D **[COLOR="Red"]madwifi[/COLOR]** -c /etc/wpa_supplicant.conf -w **-d **
```option **-d** is for ddebugging

if you are not using **madwifi**, you must replace:```

# su wpa_supplicant -dd -K -t -i ath0 -D **[COLOR="Red"]yourdriver[/COLOR]** -c /etc/wpa_supplicant.conf 
```
for example, if you have **ra0** (ifconfig -a), you must use the following command:```

# su wpa_supplicant -dd -K -t -i ath0 -D **[COLOR="Red"]wext[/COLOR]** -c /etc/wpa_supplicant.conf
```

if you are using debug option, you should get something like:```

WPA: Key negotiation completed with 00:0f:b5:3b:b3:d6 [PTK=TKIP GTK=TKIP]
Cancelling authentication timeout
**State: GROUP_HANDSHAKE -> COMPLETED**
CTRL-EVENT-CONNECTED - Connection to 00:0f:b5:3b:b3:d6 completed (auth)

```
[color=Green]**State: GROUP_HANDSHAKE -> COMPLETED**[/color]
is very important, otherwise check all steps carefully again.


**in the second part I'll post startup scripts**

HAVE FUN !:)

---

### Post by shooby on 2006-09-07
Something like an AP scan result could not be received

I'm getting an error like that and it keeps looping

---

### Post by UrbenLegend on 2006-09-08
Try using 
```
sudo wpa_supplicant -i ath0 -c /etc/wpa_supplicant.conf -D *insert driver here* -w
```

---

### Post by shooby on 2006-09-08
> **UrbenLegend said:**
> Try using 
```
sudo wpa_supplicant -i ath0 -c /etc/wpa_supplicant.conf -D *insert driver here* -w
```

What do you mean by "insert driver here"?  A link to the inf file inside of the exe driver? (I'm using the linksys WMP54g 4.1 RT6 chip)

---

### Post by cccc on 2006-09-08
only if [COLOR="Red"]**madwifi**[/COLOR] pls try:```

# su /sbin/wpa_supplicant -dd -K -t -i ath0 -D **[COLOR="Red"]madwifi[/COLOR]** -c /etc/wpa_supplicant.conf
```
or```

# su wpa_supplicant -i ath0 -c /etc/wpa_supplicant.conf -D **[COLOR="Red"]madwifi[/COLOR]** -w **-d**
```
option -d is for debug

and post what you get.

---

### Post by oliviercaro on 2006-09-08
Hello I'm new to the forum, to Ubuntu and to this thread...

Here is what I get when doing what you suggested:

```
Initializing interface 'ra0' conf '/etc/wpa_supplicant.conf' driver 'madwifi' ctrl_interface 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Priority group 2
   id=0 ssid='OTHD'
Initializing interface (2) 'ra0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=19 WE(source)=14 enc_capa=0x0
  capabilities: key_mgmt 0x0 enc 0x3
Own MAC address: 00:12:17:91:81:8b
wpa_driver_madwifi_del_key: keyidx=0
ioctl[IEEE80211_IOCTL_DELKEY]: Operation not supported
wpa_driver_madwifi_del_key: keyidx=1
ioctl[IEEE80211_IOCTL_DELKEY]: Operation not supported
wpa_driver_madwifi_del_key: keyidx=2
ioctl[IEEE80211_IOCTL_DELKEY]: Operation not supported
wpa_driver_madwifi_del_key: keyidx=3
ioctl[IEEE80211_IOCTL_DELKEY]: Operation not supported
wpa_driver_madwifi_set_countermeasures: enabled=0
wpa_driver_madwifi_set_drop_unencrypted: enabled=1
Setting scan request: 0 sec 100000 usec
Added interface ra0
RTM_NEWLINK, IFLA_IFNAME: Interface 'ra0' added
RTM_NEWLINK, IFLA_IFNAME: Interface 'ra0' added
RTM_NEWLINK, IFLA_IFNAME: Interface 'ra0' added
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=4):
     4f 54 48 44                                       OTHD
Scan timeout - try to get results
Received 1247 bytes of scan results (12 BSSes)
Scan results: 12
Selecting BSS from priority group 2
0: 9e:f4:e8:cb:57:f4 ssid='OTHD' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
1: 9e:f4:e8:cb:57:f5 ssid='' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 9e:f4:e8:cb:57:f6 ssid='' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
3: 00:03:c9:e8:ee:bf ssid='Wanadoo_7b61' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
4: 00:0f:66:c9:39:54 ssid='linksys' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
5: 00:0f:a3:df:b4:e2 ssid='FreeNissim' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
6: 00:14:a4:49:ee:b2 ssid='WANADOO-AE30' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
7: 00:14:a4:31:28:2c ssid='WANADOO-666F' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
8: 00:16:41:0d:66:0b ssid='Wanadoo_813d' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
9: 00:07:cb:55:50:be ssid='LGnet' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
10: 00:11:95:eb:6c:dc ssid='Funbook France' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
11: 00:11:f5:d7:43:0a ssid='THOMSON' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 1144 bytes of scan results (11 BSSes)
Scan results: 11
Selecting BSS from priority group 2
0: 9e:f4:e8:cb:57:f5 ssid='' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
1: 9e:f4:e8:cb:57:f6 ssid='' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 9e:f4:e8:cb:57:f4 ssid='OTHD' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
3: 00:0f:a3:df:b4:e2 ssid='FreeNissim' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
4: 00:03:c9:e8:ee:bf ssid='Wanadoo_7b61' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
5: 00:0f:66:c9:39:54 ssid='linksys' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
6: 00:14:a4:49:ee:b2 ssid='WANADOO-AE30' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
7: 00:16:41:0d:66:0b ssid='Wanadoo_813d' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
8: 00:14:a4:31:28:2c ssid='WANADOO-666F' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
9: 00:07:cb:55:50:be ssid='LGnet' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
10: 00:11:95:eb:6c:dc ssid='Funbook France' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=4):
     4f 54 48 44                                       OTHD
Scan timeout - try to get results
Received 1355 bytes of scan results (13 BSSes)
Scan results: 13
Selecting BSS from priority group 2
0: 9e:f4:e8:cb:57:f5 ssid='' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
1: 9e:f4:e8:cb:57:f4 ssid='OTHD' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 9e:f4:e8:cb:57:f6 ssid='' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
3: 00:03:c9:e8:ee:bf ssid='Wanadoo_7b61' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
4: 00:0f:a3:df:b4:e2 ssid='FreeNissim' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
5: 00:0f:66:c9:39:54 ssid='linksys' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
6: 00:14:a4:31:28:2c ssid='WANADOO-666F' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
7: 00:14:a4:49:ee:b2 ssid='WANADOO-AE30' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
8: 00:16:41:0d:66:0b ssid='Wanadoo_813d' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
9: 00:07:cb:55:50:be ssid='LGnet' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
10: 00:11:95:eb:6c:dc ssid='Funbook France' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
11: 00:11:f5:d7:43:0a ssid='THOMSON' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
12: 00:0e:9b:6d:4d:30 ssid='N9UF_TEL9COM' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
CTRL-EVENT-TERMINATING - signal 2 received
Removing interface ra0
State: SCANNING -> DISCONNECTED
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_madwifi_set_drop_unencrypted: enabled=0
wpa_driver_madwifi_set_countermeasures: enabled=0
No keys have been configured - skip key clearing
ioctl[IEEE80211_IOCTL_SETOPTIE]: Operation not supported
wpa_driver_madwifi_deinit: failed to clear WPA IE

```
and then I stopped it...

and by the way, my card is a WMP54G V4 so it's supposed to use RT2500 driver. I installed it but when replacing "madwifi" by "rt2500" or "Rt2500" it says
```
Unsupported driver 'rt2500'.
```

---

### Post by shooby on 2006-09-08
Sorry I can't copy the exact code, but it says "Wireless event: cmd=0x8b1a len=14
Scan timeout - try to get results
Resource temporarily unavailable
Scan results: -1
Failed to get scan results
Failed to get scan results - try scanning again
Starting AP scan (broadcast SSID)

---

### Post by cccc on 2006-09-08
> **oliviercaro said:**
> Hello I'm new to the forum, to Ubuntu and to this thread...

Here is what I get when doing what you suggested:

```
Initializing interface 'ra0' conf '/etc/wpa_supplicant.conf' driver 'madwifi' ctrl_interface 'N/A'


```
and then I stopped it...

and by the way, my card is a WMP54G V4 so it's supposed to use RT2500 driver. I installed it but when replacing "madwifi" by "rt2500" or "Rt2500" it says
```
Unsupported driver 'rt2500'.
```

**ra0 is NOT using madwifi driver **

pls try:```

# wpa_supplicant -i ra0 -D **[COLOR="Red"]wext[/COLOR]** -c /etc/wpa_supplicant.conf -w -d
```

---

### Post by cccc on 2006-09-08
> **shooby said:**
> Sorry I can't copy the exact code, but it says "Wireless event: cmd=0x8b1a len=14
Scan timeout - try to get results
Resource temporarily unavailable
Scan results: -1
Failed to get scan results
Failed to get scan results - try scanning again
Starting AP scan (broadcast SSID)

1.) why you cannot post what you get ?
I try to be a clairvoyant, but is very difficult.
2.) what kind of the wlan card do you have ?
3.) is it PCI, PCMCIA, USB ?
4.) and pls post:```

# lsmod
# cat /etc/wpa_supplicant.conf

```
5.) which command you are using to start wpa_supplicant ?

---

### Post by oliviercaro on 2006-09-08
> **cccc said:**
> **ra0 is NOT using madwifi driver **

pls try:```

# wpa_supplicant -i ra0 -D **wext** -c /etc/wpa_supplicant.conf -w -d
```
Here is what I get:
```
Initializing interface 'ra0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Priority group 2
   id=0 ssid='OTHD'
Initializing interface (2) 'ra0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=19 WE(source)=14 enc_capa=0x0
  capabilities: key_mgmt 0x0 enc 0x3
Own MAC address: 00:12:17:91:81:8b
wpa_driver_wext_set_wpa
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 7 value 0x1 - Driver does not support WPA.
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: Operation not supported
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: Operation not supported
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: Operation not supported
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: Operation not supported
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
wpa_driver_wext_set_countermeasures
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 4 value 0x0 - wpa_driver_wext_set_drop_unencrypted
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 5 value 0x1 - Setting scan request: 0 sec 100000 usec
Added interface ra0
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=4):
     4f 54 48 44                                       OTHD
Scan timeout - try to get results
Received 935 bytes of scan results (9 BSSes)
Scan results: 9
Selecting BSS from priority group 2
0: 9e:f4:e8:cb:57:f4 ssid='OTHD' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
1: 9e:f4:e8:cb:57:f5 ssid='' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 9e:f4:e8:cb:57:f6 ssid='' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
3: 00:03:c9:e8:ee:bf ssid='Wanadoo_7b61' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
4: 00:0f:a3:df:b4:e2 ssid='FreeNissim' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
5: 00:0f:66:c9:39:54 ssid='linksys' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
6: 00:14:a4:49:ee:b2 ssid='WANADOO-AE30' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
7: 00:14:a4:31:28:2c ssid='WANADOO-666F' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
8: 00:11:95:eb:6c:dc ssid='Funbook France' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 935 bytes of scan results (9 BSSes)
Scan results: 9
Selecting BSS from priority group 2
0: 9e:f4:e8:cb:57:f4 ssid='OTHD' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
1: 9e:f4:e8:cb:57:f5 ssid='' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 9e:f4:e8:cb:57:f6 ssid='' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
3: 00:03:c9:e8:ee:bf ssid='Wanadoo_7b61' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
4: 00:0f:a3:df:b4:e2 ssid='FreeNissim' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
5: 00:0f:66:c9:39:54 ssid='linksys' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
6: 00:14:a4:49:ee:b2 ssid='WANADOO-AE30' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
7: 00:14:a4:31:28:2c ssid='WANADOO-666F' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
8: 00:11:95:eb:6c:dc ssid='Funbook France' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=4):
     4f 54 48 44                                       OTHD
Scan timeout - try to get results
Received 1043 bytes of scan results (10 BSSes)
Scan results: 10
Selecting BSS from priority group 2
0: 9e:f4:e8:cb:57:f4 ssid='OTHD' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
1: 9e:f4:e8:cb:57:f5 ssid='' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 9e:f4:e8:cb:57:f6 ssid='' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
3: 00:03:c9:e8:ee:bf ssid='Wanadoo_7b61' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
4: 00:0f:a3:df:b4:e2 ssid='FreeNissim' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
5: 00:0f:66:c9:39:54 ssid='linksys' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
6: 00:14:a4:49:ee:b2 ssid='WANADOO-AE30' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
7: 00:14:a4:31:28:2c ssid='WANADOO-666F' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
8: 00:16:41:0d:66:0b ssid='Wanadoo_813d' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
9: 00:11:95:eb:6c:dc ssid='Funbook France' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 1043 bytes of scan results (10 BSSes)
Scan results: 10
Selecting BSS from priority group 2
0: 9e:f4:e8:cb:57:f4 ssid='OTHD' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
1: 9e:f4:e8:cb:57:f5 ssid='' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 9e:f4:e8:cb:57:f6 ssid='' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
3: 00:03:c9:e8:ee:bf ssid='Wanadoo_7b61' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
4: 00:0f:a3:df:b4:e2 ssid='FreeNissim' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
5: 00:14:a4:49:ee:b2 ssid='WANADOO-AE30' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
6: 00:0f:66:c9:39:54 ssid='linksys' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
7: 00:14:a4:31:28:2c ssid='WANADOO-666F' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
8: 00:16:41:0d:66:0b ssid='Wanadoo_813d' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
9: 00:11:95:eb:6c:dc ssid='Funbook France' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=4):
     4f 54 48 44                                       OTHD
Scan timeout - try to get results
Received 1043 bytes of scan results (10 BSSes)
Scan results: 10
Selecting BSS from priority group 2
0: 9e:f4:e8:cb:57:f4 ssid='OTHD' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
1: 9e:f4:e8:cb:57:f5 ssid='' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 9e:f4:e8:cb:57:f6 ssid='' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
3: 00:03:c9:e8:ee:bf ssid='Wanadoo_7b61' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
4: 00:0f:a3:df:b4:e2 ssid='FreeNissim' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
5: 00:14:a4:49:ee:b2 ssid='WANADOO-AE30' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
6: 00:0f:66:c9:39:54 ssid='linksys' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
7: 00:14:a4:31:28:2c ssid='WANADOO-666F' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
8: 00:16:41:0d:66:0b ssid='Wanadoo_813d' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
9: 00:11:95:eb:6c:dc ssid='Funbook France' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
No suitable AP found.
Setting scan request: 5 sec 0 usec
CTRL-EVENT-TERMINATING - signal 2 received
Removing interface ra0
State: SCANNING -> DISCONNECTED
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_wext_set_wpa
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 7 value 0x0 - Failed to disable WPA in the driver.
wpa_driver_wext_set_drop_unencrypted
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 5 value 0x0 - wpa_driver_wext_set_countermeasures
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 4 value 0x0 - No keys have been configured - skip key clearing
Cancelling scan request

```
Looks like wext doesn't like WPA... (see lines at the beginning)

---

### Post by cccc on 2006-09-08
> **oliviercaro said:**
> 
Looks like wext doesn't like WPA... (see lines at the beginning)

what kind of the wlan card do you have ?
is it PCI, PCMCIA, USB ?

how did you install the driver ? 

have you dhcp or fix ip addresses ?

and pls post:```

# uname -a
# ifconfig -a
# route -n
# iwconfig
# lsmod 
# cat /etc/wpa_supplicant.conf

```

---

### Post by oliviercaro on 2006-09-08
> **cccc said:**
> what kind of the wlan card do you have ?
is it PCI, PCMCIA, USB ?

how did you install the driver ? 

have you dhcp or fix ip addresses ?

- PCI
- ndiswrapper
- DHCP
```
uname -a
Linux olivier-desktop 2.6.15-26-amd64-generic #1 SMP PREEMPT Thu Aug 3 02:52:35 UTC 2006 x86_64 GNU/Linux
ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:14:85:34:2D:4F  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:85ff:fe34:2d4f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7066 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5250 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4573025 (4.3 MiB)  TX bytes:882151 (861.4 KiB)
          Interrupt:177 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:23 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1172 (1.1 KiB)  TX bytes:1172 (1.1 KiB)

ra0       Link encap:Ethernet  HWaddr 00:12:17:91:81:8B  
          inet6 addr: fe80::212:17ff:fe91:818b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17094 errors:0 dropped:0 overruns:0 frame:0
          TX packets:283165 errors:8 dropped:8 overruns:0 carrier:0
          collisions:3044 txqueuelen:1000 
          RX bytes:2509432 (2.3 MiB)  TX bytes:13512186 (12.8 MiB)
          Interrupt:225 Base address:0xc000 

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.254   0.0.0.0         UG    0      0        0 eth0
iwconfig
ra0       RT2500 Wireless  ESSID:"OTHD"  
          Mode:Managed  Frequency=2.462 GHz  Bit Rate=24 Mb/s   Tx-Power:0 dBm   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=55/100  Signal level=-49 dBm  Noise level:-206 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lsmod
Module                  Size  Used by
sg                     43696  0 
rfcomm                 45600  0 
l2cap                  30464  5 rfcomm
bluetooth              59268  4 rfcomm,l2cap
ppdev                  11400  0 
powernow_k8            12992  0 
cpufreq_userspace       9184  1 
cpufreq_stats           8264  0 
freq_table              6464  2 powernow_k8,cpufreq_stats
cpufreq_powersave       3328  0 
cpufreq_ondemand        9768  0 
cpufreq_conservative    10984  0 
video                  18824  0 
tc1100_wmi              9096  0 
sony_acpi               7188  0 
pcc_acpi               16128  0 
hotkey                 13768  0 
dev_acpi               15364  0 
container               6272  0 
button                  8864  0 
acpi_sbs               24600  0 
battery                12296  1 acpi_sbs
i2c_acpi_ec             7040  1 acpi_sbs
ac                      7176  1 acpi_sbs
nls_utf8                3584  2 
ntfs                  101376  2 
dm_mod                 63176  1 
md_mod                 76792  0 
sr_mod                 19748  0 
sbp2                   27908  0 
lp                     15040  0 
tsdev                  10240  0 
parport_pc             40816  1 
snd_hda_intel          21664  1 
snd_hda_codec         190920  1 snd_hda_intel
floppy                 74120  0 
snd_pcm_oss            59424  0 
snd_mixer_oss          20608  1 snd_pcm_oss
snd_pcm               104584  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
parport                44172  3 ppdev,lp,parport_pc
snd_timer              29064  1 snd_pcm
snd                    68576  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              13216  1 snd
snd_page_alloc         13968  2 snd_hda_intel,snd_pcm
pcspkr                  3592  0 
psmouse                40324  0 
serio_raw               9732  0 
rt2500                205800  1 
ipv6                  300416  8 
nvidia               5433176  0 
i2c_core               26624  2 i2c_acpi_ec,nvidia
af_packet              28172  8 
evdev                  14464  1 
ext2                   74640  1 
ide_generic             2816  0 
ohci_hcd               23684  0 
ohci1394               37324  0 
ieee1394              369048  2 sbp2,ohci1394
forcedeth              34444  0 
ehci_hcd               36232  0 
usbcore               147004  3 ohci_hcd,ehci_hcd
ide_cd                 35744  0 
cdrom                  41144  2 sr_mod,ide_cd
ide_disk               19456  5 
generic                 7300  0 
amd74xx                17072  0 [permanent]
sata_nv                12548  0 
libata                 85536  1 sata_nv
scsi_mod              160504  4 sg,sr_mod,sbp2,libata
thermal                16524  0 
processor              29736  2 powernow_k8,thermal
fan                     6408  0 
capability              7176  0 
commoncap               9728  1 capability
vga16fb                15120  1 
cfbcopyarea             5120  1 vga16fb
vgastate               10368  1 vga16fb
cfbimgblt               4224  1 vga16fb
cfbfillrect             5760  1 vga16fb
fbcon                  43136  72 
tileblit                4096  1 fbcon
font                    9984  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit
cat /etc/wpa_supplicant.conf
# WPA-PSK
network={
        scan_ssid=1 
        proto=WPA
        key_mgmt=WPA-PSK
        pairwise=CCMP TKIP
        group=CCMP TKIP WEP104 WEP40  
          
        ssid="OTHD"
        psk=30ad9dce8ec9548c7d3ba8508d834e3eb1c39fe0e9e80fd20cb0e1746c7a3f34           
        
        priority=2     
}

```

---

### Post by arosboro on 2006-09-08
shooby, the driver would be something like madwifi (for atheros), wext (for wireless extensions), ipw2200 (intel)  check out the Supported wireless cards/drivers at [http://hostap.epitest.fi/wpa_supplicant/](http://hostap.epitest.fi/wpa_supplicant/)

some people may have to use proto=WPA2 if your router is set that way. It wouldn't work without it on my configuration.

By the way, hidden ssids are tricky.  I've given up on getting it to work for my madwifi cisco card.  Instead, I turn on the ssid broadcast and turn it back off once the laptop associates.  This works fine for me.

Can't wait for the startup scripts, these were part of gentoo's default install of wpa_supplicant and I miss them not being there already.

---

### Post by cccc on 2006-09-08
> **oliviercaro said:**
> - PCI
- ndiswrapper

cat /etc/wpa_supplicant.conf
# WPA-PSK
network={
        scan_ssid=1 
        proto=WPA
        key_mgmt=WPA-PSK
        pairwise=CCMP TKIP
        group=CCMP TKIP WEP104 WEP40  
          
        ssid="OTHD"
        psk=30ad9dce8ec9548c7d3ba8508d834e3eb1c39fe0e9e80fd20cb0e1746c7a3f34           
        
        priority=2     
}
[/CODE]

what's the exact name of your wlan card ?  
did you install the driver or the wlan card was identified automatically ?

and put the following lines in /etc/wpa_supplicant.conf:```


[B]ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1[/B]

# WPA-PSK
network={
        scan_ssid=1 
        proto=WPA
        key_mgmt=WPA-PSK
        pairwise=CCMP TKIP
        group=CCMP TKIP WEP104 WEP40  
          
        ssid="OTHD"
        psk=30ad9dce8ec9548c7d3ba8508d834e3eb1c39fe0e9e80fd20cb0e1746c7a3f34           
        
        priority=2     
}
```

---

### Post by shooby on 2006-09-09
I am getting the same errors as oliviercaro

I cannot post the exact code because the machine I'm trying to configure this on is not connected to the Internet!

I've switched to a USB card (Linksys WUSB54g v4)
I've installed the driver using ndiswrapper and have tried doing the command to enable the wpa_supplicant using the ndiswrapper driver

Still getting the same errors about "no suitable AP found"

---

### Post by cccc on 2006-09-09
> **shooby said:**
> 
I've switched to a USB card (Linksys WUSB54g v4)
I've installed the driver using ndiswrapper and have tried doing the command to enable the wpa_supplicant using the ndiswrapper driver

Still getting the same errors about "no suitable AP found"

which wlan card have you tried before ?

your wlan interface is called **wlan0** now ?
have you tried:```
# wpa_supplicant -i **wlan0** -D **ndiswrapper** -c /etc/wpa_supplicant.conf -d
```

you could try in /etc/wpa_supplicant.conf:```
**ap_scan=2**
```
is it working without any encryption ?
could you post all steps, how did you install the driver and wpa_supplicant.conf ?

---

### Post by cccc on 2006-09-09
> **shooby said:**
> I am getting the same errors as oliviercaro

I cannot post the exact code because the machine I'm trying to configure this on is not connected to the Internet!



if still doesn't work, pls try:

1.)```
apt-get remove --purge wpasupplicant
```
2.) download the newest wpa_supplicant from: 
[http://hostap.epitest.fi/wpa_supplicant/](http://hostap.epitest.fi/wpa_supplicant/)```

# tar xvfz  wpa_supplicant-0.4.9.tar.gz
# cd /wpa_supplicant-0.4.9
```
create **.config** and put into:```

CONFIG_DRIVER_WEXT=y
CONFIG_CTRL_IFACE=y
``````

# make clean
# make
# make install
```

p.s
this is only for **ndiswrapper**, don't do it for madwifi, etc.

---

### Post by shooby on 2006-09-10
I got it working by switching back to my Linksys WMP54g (v4.1 RT6 chipset) PCI card.  Basically, all I had to do was put in the WPA info in the /etc/network/Wireless/RT61STA/rt61sta.dat file, reboot, and voila it worked!

Sorry of all the confusion and thanks

---

### Post by dgrafix on 2006-09-13
Followed this and doesnt work for me. Got a Belkin 7010 job that ive got working under normal network setting with WEP with ndiswrapper. Problem is, my windows laptop seems to not work with wep so its gotta be wpa-psk.

am i using mad wifi? dunno, (i dont even know what that is)

Heres what i get and the contents of my conf file:


```
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
eapol_version=1
ap_scan=2
fast_reauth=1

# Example blocks:

# WPA-PSK
network={
        scan_ssid=1 
        proto=WPA
        key_mgmt=WPA-PSK
        pairwise=CCMP TKIP
        group=CCMP TKIP WEP104 WEP40  
          
        ssid="DanAirNet"
        psk=1d553b91e7761bc6fb80e05fe065abbb56161fa05a489f311b6ca877b2f75008          
        
        priority=2     
}

```


```
dan@dan-laptop:~$ ifconfig -a 
eth0      Link encap:Ethernet  HWaddr 00:20:E0:6D:4B:E7
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::220:e0ff:fe6d:4be7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:762 errors:0 dropped:0 overruns:0 frame:0
          TX packets:711 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:702970 (686.4 KiB)  TX bytes:98173 (95.8 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:472 (472.0 b)  TX bytes:472 (472.0 b)

ra1       Link encap:Ethernet  HWaddr 00:11:50:66:16:E4
          inet6 addr: fe80::211:50ff:fe66:16e4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52890 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:2115600 (2.0 MiB)
          Interrupt:5

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

```

dan@dan-laptop:~$ sudo wpa_supplicant -i ra1 -D ndiswrapper -c /etc/wpa_supplicant.conf -d
Initializing interface 'ra1' conf '/etc/wpa_supplicant.conf' driver 'ndiswrapper' ctrl_interface 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ctrl_interface_group=0
eapol_version=1
ap_scan=2
fast_reauth=1
Priority group 2
   id=0 ssid='DanAirNet'
Initializing interface (2) 'ra1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=19 WE(source)=14 enc_capa=0x0
  capabilities: key_mgmt 0x0 enc 0x3
Own MAC address: 00:11:50:66:16:e4
Driver does not support WPA.
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: Operation not supported
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: Operation not supported
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: Operation not supported
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: Operation not supported
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
Setting scan request: 0 sec 100000 usec
Added interface ra1
State: DISCONNECTED -> SCANNING
Trying to associate with SSID 'DanAirNet'
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: No WPA/RSN IE available from association info
WPA: Set cipher suites based on configuration
WPA: Selected cipher suites: group 30 pairwise 24 key_mgmt 2
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: using GTK CCMP
WPA: using PTK CCMP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 04 01 00 00 50 f2 04 01 00 00 50 f2 02
No keys have been configured - skip key clearing
State: SCANNING -> ASSOCIATING
Setting authentication timeout: 60 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto



```

---

### Post by cccc on 2006-09-13
> **dgrafix said:**
> 
am i using mad wifi? dunno, (i dont even know what that is)
[/CODE]

**MadWifi - a Linux kernel device driver for Wireless LAN chipsets from Atheros. **

madwifi supports only wland card with Atheros chipset.

but your wlan card doesn't have an Atheros chipset.

you get:
```

**Driver does not support WPA.**

```

can you explain pls how did you installed ndiswrapper ?

pls try:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/WPA](http://ndiswrapper.sourceforge.net/mediawiki/index.php/WPA)

ot if that dosn't work pls try following:

[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500)

---

### Post by dgrafix on 2006-09-14
Think i got it fixed now. Afer all that im not even sure it was the ndiswrapped driver i was using. As someone pointed out the device should become wlan0.

As my device is ra1 im thinking one of the generic ones must have worked (wext) although the ndis one is still installed.

Anyway heres how we did it in the end using WPA-PSK without network-manager (NM just seemed to cause me loads of probs!):

[http://ubuntuforums.org/showthread.php?p=1495610#post1495610](http://ubuntuforums.org/showthread.php?p=1495610#post1495610) (page3)

IF ANYONE SAYS WPA-PSK TKIP/AES IS NOT POSSIBLE WITHOUT N.M. ITS NOT TRUE! (I spent 1 week of unsuccessful uneccasary tinkering with network manager because i got told this)

---

### Post by withayanda on 2006-09-20
I hope that ccc is still watching this.  I'm having problem with authentication to my Linksys WRT54GX4 via my Intel 3945 card.  My configs are below.

#uname -a
```
Linux orangecat 2.6.15-27-686 #1 SMP PREEMPT Sat Sep 16 02:13:27 UTC 2006 i686 GNU/Linux
```

#ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 00:16:36:36:44:45
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe36:4445/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2862 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2478 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1852649 (1.7 MiB)  TX bytes:360490 (352.0 KiB)
          Interrupt:185

eth1      Link encap:Ethernet  HWaddr 00:13:02:21:A7:FF
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:24627 errors:59 dropped:48120 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8240055 (7.8 MiB)  TX bytes:1409683 (1.3 MiB)
          Interrupt:177 Base address:0x4000 Memory:8a000000-8a000fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1072 (1.0 KiB)  TX bytes:1072 (1.0 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

#route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.2     0.0.0.0         UG    0      0        0 eth0
```

#iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"mynetwork"
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:16 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:1  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:48620   Missed beacon:0

sit0      no wireless extensions.
```

#lsmod
```
Module                  Size  Used by
michael_mic             2784  0
arc4                    2048  0
ieee80211_crypt_tkip    11456  0
smbfs                  71576  0
binfmt_misc            13064  1
rfcomm                 43604  0
l2cap                  28192  5 rfcomm
bluetooth              54212  4 rfcomm,l2cap
ipv6                  286976  22
ppdev                   9668  0
fglrx                 391756  9
speedstep_centrino      8752  1
cpufreq_userspace       6496  2
cpufreq_stats           6688  0
freq_table              4928  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        7752  0
cpufreq_conservative     9000  0
video                  16324  0
tc1100_wmi              6884  0
sony_acpi               5580  0
pcc_acpi               12416  0
hotkey                 11492  0
dev_acpi               11236  0
container               4608  0
button                  6704  0
acpi_sbs               20172  0
battery                 9988  1 acpi_sbs
ac                      5220  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               22848  1 i2c_acpi_ec
dm_mod                 63256  1
md_mod                 76052  0
af_packet              24520  2
sbp2                   25060  0
parport_pc             37988  0
lp                     12356  0
parport                39400  3 ppdev,parport_pc,lp
pcmcia                 41948  0
joydev                 10432  0
tsdev                   8032  0
psmouse                40004  0
ipw3945               132348  1
serio_raw               7748  0
ieee80211              38952  1 ipw3945
ieee80211_crypt         6528  2 ieee80211_crypt_tkip,ieee80211
yenta_socket           30124  1
rsrc_nonstatic         14624  1 yenta_socket
ieee80211_1_1_13       39880  0
ieee80211_1_1_13_crypt     7040  1 ieee80211_1_1_13
tg3                   113060  0
snd_hda_intel          20468  2
snd_hda_codec         166096  1 snd_hda_intel
pcmcia_core            45272  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_pcm_oss            56448  0
snd_mixer_oss          20544  1 snd_pcm_oss
snd_pcm                96708  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              26884  1 snd_pcm
hw_random               5716  0
snd                    60004  10 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
shpchp                 49504  0
pci_hotplug            30788  1 shpchp
soundcore              10784  1 snd
snd_page_alloc         11304  2 snd_hda_intel,snd_pcm
intel_agp              24700  1
agpgart                36784  2 fglrx,intel_agp
sr_mod                 17988  0
sg                     40160  0
evdev                  10176  1
cdrom                  41408  1 sr_mod
ext3                  148296  1
jbd                    65876  1 ext3
ide_generic             1504  0
ohci1394               37524  0
ieee1394              306520  2 sbp2,ohci1394
ehci_hcd               36104  0
uhci_hcd               35536  0
usbcore               139172  3 ehci_hcd,uhci_hcd
sd_mod                 20448  3
generic                 5124  0
ata_piix               11364  4
libata                 83440  1 ata_piix
scsi_mod              145960  5 sbp2,sr_mod,sg,sd_mod,libata
thermal                13768  0
processor              26888  2 speedstep_centrino,thermal
fan                     4836  0
capability              4968  0
commoncap               7328  1 capability
vga16fb                13992  1
vgastate               10208  1 vga16fb
fbcon                  43904  72
tileblit                2784  1 fbcon
font                    8320  1 fbcon
bitblit                 6464  1 fbcon
softcursor              2304  1 bitblit
```

#cat /etc/wpa_suuplicant.conf
```
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1

network={
        ssid="mynetwork"
	psk=0123456789abcdef0123456789abcdef0123456789abcdef0123456789abcdef
        scan_ssid=1
        proto=WPA2
        key_mgmt=WPA-PSK
        pairwise=CCMP TKIP
        group=CCMP TKIP WEP104 WEP40
        priority=2
}
```

#wpa_supplicant -dd -K -t -i eth1 -D ipw -c /etc/wpa_supplicant.conf
```
Sep 20 02:12:54.613315: Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ipw' ctrl_interface 'N/A'
Sep 20 02:12:54.613621: Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Sep 20 02:12:54.613702: Reading configuration file '/etc/wpa_supplicant.conf'
Sep 20 02:12:54.613823: ctrl_interface='/var/run/wpa_supplicant'
Sep 20 02:12:54.614698: ctrl_interface_group=0
Sep 20 02:12:54.614783: eapol_version=1
Sep 20 02:12:54.614856: ap_scan=1
Sep 20 02:12:54.614928: fast_reauth=1
Sep 20 02:12:54.614998: Line: 7 - start of a new network block
Sep 20 02:12:54.615077: ssid - hexdump_ascii(len=8):
     62 72 61 6e 63 61 64 61                           mynetwork
Sep 20 02:12:54.615220: PSK - hexdump(len=32): 01 23 45 67 89 ab cd ef 01 23 45 67 89 ab cd ef 01 23 45 67 89 ab cd ef 01 23 45 67 89 ab cd ef
Sep 20 02:12:54.616512: scan_ssid=1 (0x1)
Sep 20 02:12:54.616558: proto: 0x2
Sep 20 02:12:54.616582: key_mgmt: 0x2
Sep 20 02:12:54.616605: pairwise: 0x18
Sep 20 02:12:54.616631: group: 0x1e
Sep 20 02:12:54.616660: priority=2 (0x2)
Sep 20 02:12:54.616709: Priority group 2
Sep 20 02:12:54.616740:    id=0 ssid='mynetwork'
Sep 20 02:12:54.616766: Initializing interface (2) 'eth1'
Sep 20 02:12:54.620892: EAPOL: SUPP_PAE entering state DISCONNECTED
Sep 20 02:12:54.620923: EAPOL: KEY_RX entering state NO_KEY_RECEIVE
Sep 20 02:12:54.620943: EAPOL: SUPP_BE entering state INITIALIZE
Sep 20 02:12:54.620961: EAP: EAP entering state DISABLED
Sep 20 02:12:54.621016: EAPOL: External notification - portEnabled=0
Sep 20 02:12:54.621052: EAPOL: External notification - portValid=0
Sep 20 02:12:54.621091: wpa_driver_ipw_init is called
Sep 20 02:12:54.621184: SIOCGIWRANGE: WE(compiled)=19 WE(source)=16 enc_capa=0xfSep 20 02:12:54.621208:   capabilities: key_mgmt 0xf enc 0xf
Sep 20 02:12:54.647422: Own MAC address: 00:13:02:21:a7:ff
Sep 20 02:12:54.647549: wpa_driver_ipw_set_wpa: enabled=1
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Sep 20 02:12:54.647753: wpa_driver_ipw_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Sep 20 02:12:54.647912: Failed to set encryption.
Sep 20 02:12:54.647986: wpa_driver_ipw_set_key: alg=none key_idx=1 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Sep 20 02:12:54.648143: Failed to set encryption.
Sep 20 02:12:54.648217: wpa_driver_ipw_set_key: alg=none key_idx=2 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Sep 20 02:12:54.648373: Failed to set encryption.
Sep 20 02:12:54.648448: wpa_driver_ipw_set_key: alg=none key_idx=3 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Sep 20 02:12:54.648603: Failed to set encryption.
Sep 20 02:12:54.648678: wpa_driver_ipw_set_countermeasures: enabled=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Sep 20 02:12:54.648831: wpa_driver_ipw_set_drop_unencrypted: enabled=1
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Sep 20 02:12:54.649000: Setting scan request: 0 sec 100000 usec
Sep 20 02:12:54.649225: Added interface eth1
Sep 20 02:12:54.649347: Wireless event: cmd=0x8b06 len=8
Sep 20 02:12:54.751488: State: DISCONNECTED -> SCANNING
Sep 20 02:12:54.751550: Starting AP scan (specific SSID)
Sep 20 02:12:54.751570: Scan SSID - hexdump_ascii(len=8):
     62 72 61 6e 63 61 64 61                           mynetwork
Sep 20 02:12:57.755500: Scan timeout - try to get results
Sep 20 02:12:57.755916: Received 1799 bytes of scan results (9 BSSes)
Sep 20 02:12:57.755944: Scan results: 9
Sep 20 02:12:57.755964: Selecting BSS from priority group 2
Sep 20 02:12:57.755983: 0: 00:16:b6:f5:19:9e ssid='mynetwork' wpa_ie_len=24 rsn_ie_len=22 caps=0x11
Sep 20 02:12:57.756016:    selected based on RSN IE
Sep 20 02:12:57.756043: Trying to associate with 00:16:b6:f5:19:9e (SSID='mynetwork' freq=0 MHz)
Sep 20 02:12:57.756064: Cancelling scan request
Sep 20 02:12:57.756082: WPA: clearing own WPA/RSN IE
Sep 20 02:12:57.756100: Automatic auth_alg selection: 0x1
Sep 20 02:12:57.756118: wpa_driver_ipw_set_auth_alg: auth_alg=0x1
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Sep 20 02:12:57.756187: RSN: using IEEE 802.11i/D9.0
Sep 20 02:12:57.756209: WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2
Sep 20 02:12:57.756229: WPA: set AP WPA IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
Sep 20 02:12:57.756261: WPA: set AP RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 02 01 00 00 0f ac 02 01 00 00 0f ac 02 00 00
Sep 20 02:12:57.756293: WPA: using GTK TKIP
Sep 20 02:12:57.756312: WPA: using PTK TKIP
Sep 20 02:12:57.756330: WPA: using KEY_MGMT WPA-PSK
Sep 20 02:12:57.756349: WPA: Set own WPA IE default - hexdump(len=22): 30 14 01 00 00 0f ac 02 01 00 00 0f ac 02 01 00 00 0f ac 02 00 00
Sep 20 02:12:57.756381: No keys have been configured - skip key clearing
Sep 20 02:12:57.756399: wpa_driver_ipw_set_drop_unencrypted: enabled=1
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Sep 20 02:12:57.756448: State: SCANNING -> ASSOCIATING
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Sep 20 02:12:57.756548: Setting authentication timeout: 10 sec 0 usec
Sep 20 02:12:57.756573: EAPOL: External notification - EAP success=0
Sep 20 02:12:57.756612: EAPOL: External notification - EAP fail=0
Sep 20 02:12:57.756652: EAPOL: External notification - portControl=Auto
Sep 20 02:12:57.756697: RSN: Ignored PMKID candidate without preauth flag
Sep 20 02:12:57.756735: Wireless event: cmd=0x8b1a len=17
Sep 20 02:13:07.760132: Authentication with 00:00:00:00:00:00 timed out.
Sep 20 02:13:07.760216: Added BSSID 00:00:00:00:00:00 into blacklist
Sep 20 02:13:07.760243: State: ASSOCIATING -> DISCONNECTED
Sep 20 02:13:07.760262: No keys have been configured - skip key clearing
Sep 20 02:13:07.760282: EAPOL: External notification - portEnabled=0
Sep 20 02:13:07.760320: EAPOL: External notification - portValid=0
Sep 20 02:13:07.760359: Setting scan request: 0 sec 0 usec
Sep 20 02:13:07.760391: State: DISCONNECTED -> SCANNING
Sep 20 02:13:07.760411: Starting AP scan (broadcast SSID)
Sep 20 02:13:10.764309: Scan timeout - try to get results
Sep 20 02:13:10.764482: Received 1764 bytes of scan results (9 BSSes)
Sep 20 02:13:10.764509: Scan results: 9
Sep 20 02:13:10.764530: Selecting BSS from priority group 2
Sep 20 02:13:10.764549: 0: 00:16:b6:f5:19:9e ssid='mynetwork' wpa_ie_len=24 rsn_ie_len=22 caps=0x11
Sep 20 02:13:10.764578:    selected based on RSN IE
Sep 20 02:13:10.764613: Trying to associate with 00:16:b6:f5:19:9e (SSID='mynetwork' freq=0 MHz)
Sep 20 02:13:10.764637: Cancelling scan request
Sep 20 02:13:10.764656: WPA: clearing own WPA/RSN IE
Sep 20 02:13:10.764687: Automatic auth_alg selection: 0x1
Sep 20 02:13:10.764709: wpa_driver_ipw_set_auth_alg: auth_alg=0x1
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Sep 20 02:13:10.764794: RSN: using IEEE 802.11i/D9.0
Sep 20 02:13:10.764817: WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2
Sep 20 02:13:10.764840: WPA: set AP WPA IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
Sep 20 02:13:10.764873: WPA: set AP RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 02 01 00 00 0f ac 02 01 00 00 0f ac 02 00 00
Sep 20 02:13:10.764905: WPA: using GTK TKIP
Sep 20 02:13:10.764925: WPA: using PTK TKIP
Sep 20 02:13:10.764949: WPA: using KEY_MGMT WPA-PSK
Sep 20 02:13:10.764967: WPA: Set own WPA IE default - hexdump(len=22): 30 14 01 00 00 0f ac 02 01 00 00 0f ac 02 01 00 00 0f ac 02 00 00
Sep 20 02:13:10.764998: No keys have been configured - skip key clearing
Sep 20 02:13:10.765017: wpa_driver_ipw_set_drop_unencrypted: enabled=1
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Sep 20 02:13:10.765067: State: SCANNING -> ASSOCIATING
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Sep 20 02:13:10.765172: Setting authentication timeout: 10 sec 0 usec
Sep 20 02:13:10.765197: EAPOL: External notification - EAP success=0
Sep 20 02:13:10.765244: EAPOL: External notification - EAP fail=0
Sep 20 02:13:10.765283: EAPOL: External notification - portControl=Auto
Sep 20 02:13:10.765328: RSN: Ignored PMKID candidate without preauth flag
Sep 20 02:13:10.765366: Wireless event: cmd=0x8b1a len=17
Sep 20 02:13:13.564904: CTRL-EVENT-TERMINATING - signal 2 received
Sep 20 02:13:13.564984: Removing interface eth1
Sep 20 02:13:13.565005: State: ASSOCIATING -> DISCONNECTED
Sep 20 02:13:13.565025: No keys have been configured - skip key clearing
Sep 20 02:13:13.565044: EAPOL: External notification - portEnabled=0
Sep 20 02:13:13.565083: EAPOL: External notification - portValid=0
Sep 20 02:13:13.565120: wpa_driver_ipw_set_wpa: enabled=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Sep 20 02:13:13.565236: wpa_driver_ipw_set_drop_unencrypted: enabled=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Sep 20 02:13:13.565287: wpa_driver_ipw_set_countermeasures: enabled=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Sep 20 02:13:13.565340: No keys have been configured - skip key clearing
Sep 20 02:13:13.585020: Removed BSSID 00:00:00:00:00:00 from blacklist (clear)
Sep 20 02:13:13.585155: Cancelling scan request
```

Sorry, I didn't know how much of that debug you needed.  Any help would be greatly appreciated.

---

### Post by cccc on 2006-09-20
> **withayanda said:**
> I hope that ccc is still watching this.  

#uname -a
```
Linux orangecat 2.6.15-**27**-686 #1 SMP PREEMPT Sat Sep 16 02:13:27 UTC 2006 i686 GNU/Linux
```



did you upgrade your kernel ?
the new 2.6.15-**27**-686 kernel has a lot driver problems.
could you still boot your maschine into the 2.6.15-**26**-686 kernel ?
if you already deleted the 26 kernel, download the old one via synaptic. 
just search for "linux-kernel" and pick #26, install it and you can reboot into the old kernel.

greetings
cc

---

### Post by withayanda on 2006-09-20
> **cccc said:**
> could you still boot your maschine into the 2.6.15-**26**-686 kernel?

I was having this problem before I got the newer 2.6.15-27 kernel.  But just to make sure, I downloaded & booted into the -26 kernel and still get the same errors.

---

### Post by cccc on 2006-09-20
could you explain pls, how did you install the driver and the wpa_supplicant ?

---

### Post by withayanda on 2006-09-20
> **cccc said:**
> could you explain pls, how did you install the driver and the wpa_supplicant ?

I didn't have to.  They were installed for me.  The ipw3945 driver was included in the -26 kernel, and the wpasupplicant package is a dependency of ubuntu-minimal.

---

### Post by cccc on 2006-09-20
pls try to download:

[http://ipw3945.sourceforge.net/#downloads](http://ipw3945.sourceforge.net/#downloads)

& install the driver under the -26 kernel.


if still doesn't work, you can try to install wpa_supplicant as well:

[http://www.bughost.org/ipw/wpa_howto.txt](http://www.bughost.org/ipw/wpa_howto.txt)

---

### Post by withayanda on 2006-09-20
> **cccc said:**
> if still doesn't work, you can try to install wpa_supplicant as well:
[http://www.bughost.org/ipw/wpa_howto.txt](http://www.bughost.org/ipw/wpa_howto.txt)

I happened to see on that page only one thing that was different.  I should have specified this driver:
```
wpa_supplicant -d -K -t -ieth1 -D**wext** -c/etc/wpa_supplicant.conf
```
rather than this driver:
```
wpa_supplicant -K -t -ieth1 -D**ipw** -c/etc/wpa_supplicant.conf
```

To confirm, I googled for ipw3945 and wext.  What do you know...I finally get a few hits of better information.  This link Kanotix's FAQ (another Debian derivative for those that don't know and happen to see this) was especially helpful: [http://kanotix.com/FAQ-id_cat-140.html#q441](http://kanotix.com/FAQ-id_cat-140.html#q441).

I really wish the man page had said something about this.  I've spent a week and a half off-and-on trying to get this to work without using the gnome network-manager applet and it was as simple as that to solve.  Maybe this should go into the Wiki & Help pages regarding wpa_supplicant (after it's been confirmed on more than one type of card, of course.)

---

### Post by withayanda on 2006-09-20
Oh, and thanks so much for your help, ccc.  I sincerely appreciate it.

---

### Post by stokedfish on 2007-02-20
> **cccc said:**
> **in the second part I'll post startup scripts**
Uhm, where are the scripts? Can't find 'em anywhere...

---

### Post by stokedfish on 2007-03-04
I'm afraid this doesn't work.

I have got the very same network card and followed all this, it could handshake, but then when I try to use apt-get it's telling me my network is down...why could that be? any help?

---

### Post by Elviswind on 2007-09-29
deleted

---

