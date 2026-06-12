---
title: "Atheros with WPA - trouble!"
date: 2005-05-02
forum: Networking &amp; Wireless
---

### Post by p0rnflake on 2005-05-02
I'm having serious issues getting my T42 with an Atheros based 802.11a/b/g card working with WPA. I've had it working before with Fedora Core 3 but just switched to Ubuntu. If I disable WPA on my AP I can connect just fine without encryption.

I've installed the wpa_supplicant deb and can lauch the program:

sudo wpa_supplicant -w -iath0 -c /etc/wpa_supplicant.conf -D  madwifi -dd

(Output at the bottom)

I can check the connection status on my AP - and the laptop is actually listed as connected - but always ends up disconnecting and trying again..

```

Initializing interface 'ath0' conf '/etc/wpa_supplicant.conf' driver 'madwifi'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Line: 1 - start of a new network block
ssid - hexdump_ascii(len=5):
     62 6c 61 68 68                                    blahh
scan_ssid=1 (0x1)
proto: 0x1
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=11): [REMOVED]
pairwise: 0x18
group: 0x18
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='blahh'
Initializing interface (2) 'ath0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Own MAC address: 00:0e:9b:7c:19:c0
wpa_driver_madwifi_set_wpa: enabled=1
wpa_driver_madwifi_del_key: keyidx=0
wpa_driver_madwifi_del_key: keyidx=1
wpa_driver_madwifi_del_key: keyidx=2
wpa_driver_madwifi_del_key: keyidx=3
wpa_driver_madwifi_set_countermeasures: enabled=0
wpa_driver_madwifi_set_drop_unencrypted: enabled=1
Setting scan request: 0 sec 100000 usec
Wireless event: cmd=0x8b06 len=8
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=5):
     62 6c 61 68 68                                    blahh
Wireless event: cmd=0x8b1a len=18
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
Wireless event: cmd=0x8b19 len=12
Received 267 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
0: 00:0c:76:71:f6:4a ssid='blahh' wpa_ie_len=24 rsn_ie_len=0
   selected
Trying to associate with 00:0c:76:71:f6:4a (SSID='blahh' freq=2437 MHz)
Cancelling scan request
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Own WPA IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_madwifi_set_drop_unencrypted: enabled=1
wpa_driver_madwifi_associate
Setting authentication timeout: 5 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
Wireless event: cmd=0x8b1a len=18
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:0c:76:71:f6:4a
Association event - clear replay counter
Associated to a new BSS: BSSID=00:0c:76:71:f6:4a
No keys have been configured - skip key clearing
Associated with 00:0c:76:71:f6:4a
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: txStart
WPA: drop TX EAPOL in non-IEEE 802.1X mode (type=1 len=0)
EAPOL: SUPP_BE entering state IDLE
EAP: EAP entering state INITIALIZE
EAP: EAP entering state IDLE
Setting authentication timeout: 10 sec 0 usec
RTM_NEWLINK, IFLA_IFNAME: Interface 'ath0' added
RX EAPOL from 00:0c:76:71:f6:4a
RX EAPOL - hexdump(len=107): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 01 c5 7c 50 27 c9 99 07 83 33 75 13 14 31 97 2e e4 ae ee ba 8c 88 db d2 9d 73 d5 ce dc 12 3f 45 69 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 01 fe 2e 50 d3 d4 6d 90
Setting authentication timeout: 10 sec 0 usec
EAPOL: Ignoring WPA EAPOL-Key frame in EAPOL state machines
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
WPA: RX EAPOL-Key - hexdump(len=107): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 01 c5 7c 50 27 c9 99 07 83 33 75 13 14 31 97 2e e4 ae ee ba 8c 88 db d2 9d 73 d5 ce dc 12 3f 45 69 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 01 fe 2e 50 d3 d4 6d 90
WPA: ignoring 8 bytes after the IEEE 802.1X data
WPA: RX message 1 of 4-Way Handshake from 00:0c:76:71:f6:4a (ver=1)
WPA: WPA IE for msg 2/4 - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Renewed SNonce - hexdump(len=32): 2e ca b6 05 c1 0f d2 be 53 ad cd d0 4e 06 15 a5 07 39 80 80 48 01 22 82 b0 c5 4a 55 5d b4 3a ad
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: EAPOL-Key MIC - hexdump(len=16): 2a 4d b9 a6 6f 36 2f 6e 21 e2 69 f3 63 4c 3c 22
WPA: Sending EAPOL-Key 2/4
WPA: TX EAPOL-Key 2/4 - hexdump(len=137): 00 0c 76 71 f6 4a 00 0e 9b 7c 19 c0 88 8e 01 03 00 77 fe 01 09 00 20 00 00 00 00 00 00 00 01 2e ca b6 05 c1 0f d2 be 53 ad cd d0 4e 06 15 a5 07 39 80 80 48 01 22 82 b0 c5 4a 55 5d b4 3a ad 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 2a 4d b9 a6 6f 36 2f 6e 21 e2 69 f3 63 4c 3c 22 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
RX EAPOL from 00:0c:76:71:f6:4a
RX EAPOL - hexdump(len=131): 01 03 00 77 fe 01 c9 00 20 00 00 00 00 00 00 00 02 c5 7c 50 27 c9 99 07 83 33 75 13 14 31 97 2e e4 ae ee ba 8c 88 db d2 9d 73 d5 ce dc 12 3f 45 69 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 10 97 0a f3 a3 2f f0 4e 56 09 e2 18 81 98 9f a9 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 b6 05 de 83 05 21 e7 14
EAPOL: Ignoring WPA EAPOL-Key frame in EAPOL state machines
IEEE 802.1X RX: version=1 type=3 length=119
  EAPOL-Key type=254
WPA: RX EAPOL-Key - hexdump(len=131): 01 03 00 77 fe 01 c9 00 20 00 00 00 00 00 00 00 02 c5 7c 50 27 c9 99 07 83 33 75 13 14 31 97 2e e4 ae ee ba 8c 88 db d2 9d 73 d5 ce dc 12 3f 45 69 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 10 97 0a f3 a3 2f f0 4e 56 09 e2 18 81 98 9f a9 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 b6 05 de 83 05 21 e7 14
WPA: ignoring 8 bytes after the IEEE 802.1X data
WPA: RX message 3 of 4-Way Handshake from 00:0c:76:71:f6:4a (ver=1)
WPA: IE KeyData - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Sending EAPOL-Key 4/4
WPA: TX EAPOL-Key 4/4 - hexdump(len=113): 00 0c 76 71 f6 4a 00 0e 9b 7c 19 c0 88 8e 01 03 00 5f fe 01 09 00 20 00 00 00 00 00 00 00 02 2e ca b6 05 c1 0f d2 be 53 ad cd d0 4e 06 15 a5 07 39 80 80 48 01 22 82 b0 c5 4a 55 5d b4 3a ad 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 22 eb 66 d2 0d a3 7d 1a 0e 89 88 39 5c 92 f6 ed 00 00
WPA: Installing PTK to the driver.
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
wpa_driver_madwifi_set_key: alg=TKIP key_idx=0 set_tx=1 seq_len=6 key_len=32
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=29 idleWhile=59
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=28 idleWhile=58
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=27 idleWhile=57
Signal 2 received - terminating
wpa_driver_madwifi_deauthenticate
wpa_driver_madwifi_del_key: keyidx=0
wpa_driver_madwifi_del_key: keyidx=1
wpa_driver_madwifi_del_key: keyidx=2
wpa_driver_madwifi_del_key: keyidx=3
wpa_driver_madwifi_del_key: keyidx=0
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portValid=0
wpa_driver_madwifi_set_wpa: enabled=0
wpa_driver_madwifi_set_drop_unencrypted: enabled=0
wpa_driver_madwifi_set_countermeasures: enabled=0

``` 

Would appriciate any and all help...

my current wpa_supplicant.conf file (tried many variants)

```

network={
       ssid="blahh"
       scan_ssid=1
       proto=WPA
       key_mgmt=WPA-PSK
       psk="secretkey"
       pairwise=CCMP TKIP
       group=CCMP TKIP
}

```

---

### Post by p0rnflake on 2005-05-03
I refuse to believe I'm the only one with an Atheros based wifi card running Ubuntu ???

---

### Post by kwakerz on 2005-05-17
No your not but I'm completely new to Linux never mind Ubuntu, so you have troubles? Good hunting. ;-)

---

### Post by zencoder on 2005-05-17
p0rnflake, I don't think it's necessarily anything to do with the atheros.  I've seen a few threads, readmes, etc. regarding WPA (on Ubuntu, perhaps) ...I think that's where the problem lies.  Unfortunately, I don't have any help to offer at this time, as I am working through similar problems.  I'll post what I find if it's related.

---

### Post by benplaut on 2005-05-18
actually, i beg to differ with ^^^... the IBM atheros A/B/G is horrible under ubuntu... none of the applets, except the gnome supplied network applet, seem to work with it, and i have to manually enter all the info when i want to connect!

back to your question, i have no idea  :roll: 

BTW- have you gotten GTKwifi, or something like it, to work with your card? just seeing if the problem is mine, or everyone's  :-|

---

### Post by tread on 2005-05-18
For what it's worth .. I had no trouble using my Atheros card with WEP .. never tried it with WPA (actually, don't have access to any WLAN with WPA)

---

### Post by benplaut on 2005-05-18
[QUOTE=tread]For what it's worth .. I had no trouble using my Atheros card with WEP .. never tried it with WPA (actually, don't have access to any WLAN with WPA)[/QUOTE]

...but does it work with GTKwifi, and other programs like it?

more specifically, does 

iwlist ath0 scan

return any results, when you *aren't* connected to a network?  ](*,)

---

### Post by tread on 2005-05-18
I use the gnome net applet, that seems to give me the best results. It does work with gtkwifi, but I have some problems with gtkwifi, so I dont use it anymore. I havent tested WEP on that, but it does work with the default gnome applet.

---

### Post by benplaut on 2005-05-18
[QUOTE=tread]I use the gnome net applet, that seems to give me the best results. It does work with gtkwifi, but I have some problems with gtkwifi, so I dont use it anymore. I havent tested WEP on that, but it does work with the default gnome applet.[/QUOTE]

OK, so it isn't just my system  :-x 

thanks, i'm releived  ](*,)

---

### Post by tread on 2005-05-18
Is that the only problem you had with GTKWifi? For some reason it always reported really low signal strength for any network .. when the gnome applet shows 80% this would show 35-40. 

I haven't tried iwlist -scan when I am not connected to a network .. will try that when I get home.

---

### Post by bdp on 2006-12-13
I have an IBM T42 with the Atheros a/b/g card.  Wireless with WPA has worked fine for me through Dapper.  I use nm-applet to control things.

Since upgrading to Edgy however my signal strength at home shows as being far lower and it drops out periodically.  I have not had time to figure out why this is happening, but I would love to hear if anyone figures out how to fix this.  I've been thinking about reinstalling the intel wireless to see if it works better.

---

