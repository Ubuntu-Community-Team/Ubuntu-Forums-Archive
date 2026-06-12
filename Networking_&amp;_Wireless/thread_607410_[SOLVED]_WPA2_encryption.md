---
title: "[SOLVED] WPA2 encryption"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by semperfiguy on 2007-11-08
I am running a dell inspiron 1100 laptop with a linksys54g wireless card.  It is accessed using ndiswrapper and I use the network manager to configure it.  Currently I have it running through an unsecured router without encryption using the "roaming mode" and I just select my router and it works fine.  I am trying to put WPA2 encryption on a seperate router to test it but when I manually configure the card to use WPA2 encryption and dhcp it doesn't connect.  The router I am trying to connect to is an apple airport express.  The router I am currently connected with (without encryption) is a linsys WRT54g.  Can anyone help me with this?

---

### Post by wieman01 on 2007-11-09
Does the network applet give you a WPA option at all? If that is the case, please let us know more about your network e.g. hidden ESSID or not, etc.

---

### Post by semperfiguy on 2007-11-10
the nm-applet give me the wpa2 option when I start manually configureing the card yes.  My card is running as eth1 right now in "roaming mode".  The ESSID is not hidden.  I know the name of the router and the password which I am just typing in as is into the space provided.

---

### Post by unsavory on 2007-11-10
I ran into this same issue, and found out I couldn't use a WPA2 password longer than 8 characters.  My original wireless password was 32 and it just wouldn't connect.  I then tried 16 characters and still wouldn't connect.  It wasn't until I dropped the password down to 8 characters that I could connect to my router.

I don't know if this is how it works for everyone, but it is certainly the case for me.

---

### Post by semperfiguy on 2007-11-10
I tried that but no sucess.  

Okay in roaming mode I can see the network I want to connect to but I need a passcode for it and the only options it gives me for passwords are WEP and LEAP.  I need WPA.  So in the nm-applet I click manual configuration and then select my wireless network -> properties.  In propertied I disable roaming mode, select the proper network, select WPA2 Personal encryption, and enter my 8character passcode.  I exit properties and it starts configuring my changes.  I exit the applet and try but I have no connection.

So then I go back into the applet and wireless properties and now it switched to WPA Personal encryption and has this 64character passcode instead..  Where did that come from?

Edit:  I tried it under WPA personal and it works fine.  It's just WPA2 that is the problem

---

### Post by wieman01 on 2007-11-11
What about WPA with AES? Same issue? WPA with AES is pretty much WPA2.

---

### Post by semperfiguy on 2007-11-13
OK now plain WPA is acting alittle flaky.  It doesn't connect right away upon reboot.  Forgive my ignorance but what is AES? how do I use that option?

---

### Post by semperfiguy on 2007-11-18
Ok I started following the guide from here: [https://help.ubuntu.com/community/WifiDocs/WPAHowTo#head-0ea8cdec8956fd98e68d5c887976b6bc331d95cb](https://help.ubuntu.com/community/WifiDocs/WPAHowTo#head-0ea8cdec8956fd98e68d5c887976b6bc331d95cb)
to configure WPA. 

I also started configuring the network manually instead of using nm-applet
My /etc/network/interfaces file now looks like this```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# Maually configure wireless card without using nm-applet
auto eth1
iface eth1 inet dhcp
wpa-driver wext
wpa-ssid Myneta
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk 1d998ae3daf1b8e4805a9c8d849ca3c5a63d23c68cb4ce83ff234e9f8aad79b9

```

My /etc/wpa_supplicant.conf file looks like this:```
network={
        ssid="Myneta"
	proto=WPA
	key_mgmt=WPA-PSK
        psk=1d998ae3daf1b8e4805a9c8d849ca3c5a63d23c68cb4ce83ff234e9f8aad79b9
}

```

When I run the command ```
sudo wpa_supplicant -ieth1 -c/etc/wpa_supplicant.conf -Dndiswrapper -dd -w

```
Like this instructions in the guide I get the error:
```
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ndiswrapper' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Line: 1 - start of a new network block
ssid - hexdump_ascii(len=6):
     4d 79 6e 65 74 61                                 Myneta          
proto: 0x1
key_mgmt: 0x2
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='Myneta'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=22 WE(source)=18 enc_capa=0x0
  capabilities: key_mgmt 0x0 enc 0x3
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:0c:41:2e:73:40
Driver does not support WPA.
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
Setting scan request: 0 sec 100000 usec
Added interface eth1
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b06 len=8
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 574 bytes of scan results (3 BSSes)
Scan results: 3
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:14:51:6b:07:ff ssid='Myneta' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
1: 00:1a:70:e4:5c:57 ssid='krs10' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:12:17:e2:e9:84 ssid='mynet54g' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:14:51:6b:07:ff ssid='Myneta' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - non-WPA network not allowed
1: 00:1a:70:e4:5c:57 ssid='krs10' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:12:17:e2:e9:84 ssid='mynet54g' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 0 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
Scan results: -1
Failed to get scan results

```

Maybe all this extra information will be able to help somebody solve my problem.

---

### Post by kevdog on 2007-11-18
Have you tried connecting manually according to my guide in my signature.  It will give you some more tips how to properly configure your wpa_supplicant.conf file.

---

### Post by semperfiguy on 2007-11-18
following your guide the error was:
```
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ap_scan=1
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=6):
     4d 79 6e 65 74 61                                 Myneta          
scan_ssid=0 (0x0)
proto: 0x1
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=8): [REMOVED]
pairwise: 0x8
group: 0x8
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='Myneta'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=22 WE(source)=18 enc_capa=0x0
  capabilities: key_mgmt 0x0 enc 0x3
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:0c:41:2e:73:40
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
Setting scan request: 0 sec 100000 usec
Added interface eth1
RTM_NEWLINK: operstate=0 ifi_flags=0x1002 ()
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 574 bytes of scan results (3 BSSes)
Scan results: 3
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:14:51:6b:07:ff ssid='Myneta' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
1: 00:1a:70:e4:5c:57 ssid='krs10' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:12:17:e2:e9:84 ssid='mynet54g' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:14:51:6b:07:ff ssid='Myneta' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - non-WPA network not allowed
1: 00:1a:70:e4:5c:57 ssid='krs10' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:12:17:e2:e9:84 ssid='mynet54g' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 0 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 574 bytes of scan results (3 BSSes)
Scan results: 3
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:14:51:6b:07:ff ssid='Myneta' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
1: 00:1a:70:e4:5c:57 ssid='krs10' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:12:17:e2:e9:84 ssid='mynet54g' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
[COLOR="Red"]0: 00:14:51:6b:07:ff ssid='Myneta' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
  skip - non-WPA network not allowed[/COLOR]
1: 00:1a:70:e4:5c:57 ssid='krs10' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:12:17:e2:e9:84 ssid='mynet54g' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 5 sec 0 usec
CTRL-EVENT-TERMINATING - signal 2 received
Removing interface eth1
State: SCANNING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_wext_set_wpa
wpa_driver_wext_set_drop_unencrypted
wpa_driver_wext_set_countermeasures
No keys have been configured - skip key clearing
Cancelling scan request
Cancelling authentication timeout
WEXT: Operstate: linkmode=0, operstate=6

```

That is the network I'm trying to connect to.

---

### Post by kevdog on 2007-11-18
Can you post you wpa_supplicant.conf file??

---

### Post by semperfiguy on 2007-11-18
```
ap_scan=1
ctrl_interface=/var/run/wpa_supplicant

network={
        ssid="Myneta"
        scan_ssid=0
        proto=WPA
        key_mgmt=WPA-PSK
        psk="h0ffman1"
        pairwise=TKIP
        group=TKIP

}

```

---

### Post by kevdog on 2007-11-18
Just want you to verify a few things.  TKIP ciphers are usually for wpa1 - but can be used with wpa2 if your router is set up for this configuration.  Do you have access to the configuration screen of your wpa2 router?  If so, can you check that you are using pairwise and group TKIP ciphers (as opposed to AES which is usually the rule with wpa2).  The most important part of this discussion, is that you match the parameters.

Can you also post your command line sequence -- or how you are trying to obtain a dhcp lease?

---

### Post by semperfiguy on 2007-11-18
Well I am using an airport express router.  It was set to WPA/WPA2 encryption and wouldn't say what type of protocol it was tkip or aes so I switched it to WPA2 encryption.  So my wpa_supplicant.conf file now reads```
ap_scan=1
ctrl_interface=/var/run/wpa_supplicant

network={
        ssid="Myneta"
        scan_ssid=0
        proto=WPA
        key_mgmt=RSN
        psk="h0ffman1"
        pairwise=TKIP CCMP
        group=TKIP CCMP

}

```

My command line usually goes like this:
```

sudo ifdown th1
sudo ifconfig eth1 down
sudo dhclient -r eth1
sudo wpa_supplicant -w -Dwext -ieth1 -c/etc/wpa_supplicant.conf -dd

```

And then I get the error that I posted.
But the error is now:
```
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ap_scan=1
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=6):
     4d 79 6e 65 74 61                                 Myneta          
scan_ssid=0 (0x0)
proto: 0x1
Line 8: invalid key_mgmt 'RSN'
Line 8: no key_mgmt values configured.
key_mgmt: 0x0
Line 8: failed to parse key_mgmt 'RSN'.
PSK (ASCII passphrase) - hexdump_ascii(len=8): [REMOVED]
pairwise: 0x18
group: 0x18
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Line 13: failed to parse network block.
Failed to read or parse configuration '/etc/wpa_supplicant.conf'.
Failed to add interface eth1
Cancelling scan request
Cancelling authentication timeout


```

---

### Post by kevdog on 2007-11-18
Sorry I kind of lead you astray.  If your router is using AES pairwise and group ciphers, then in your configuration files you use :

        key_mgmt=RSN
        pairwise=CCMP
        group=CCMP


Also try bringing the interface up before the wpa statement (I know my guide doesnt read like this, but Im just trying things).  You bring the interface up like:


sudo ifconfig <interface> up
sudo wpa_supplicant -w -D wext -i eth1 -c/ etc/wpa_supplicant.conf -dd

---

### Post by semperfiguy on 2007-11-18
But I still get the error

Line 8: invalid key_mgmt 'RSN'
Line 8: no key_mgmt values configured.
key_mgmt: 0x0
Line 8: failed to parse key_mgmt 'RSN'.

When I enter
sudo wpa_supplicant -w -D wext -i eth1 -c/ etc/wpa_supplicant.conf -dd

---

### Post by kevdog on 2007-11-18
Here let me start over since Im just giving you plain WRONG advice

Try this:

network={
        ssid="Myneta"
        scan_ssid=0
        proto=RSN
        key_mgmt=WPA-PSK
        psk="h0ffman1"
        pairwise=CCMP
        group=CCMP
}

---

### Post by semperfiguy on 2007-11-18
Ok running the wpa_supplicant command again and I get this error with the lines i think are odd highlighted:
```
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ap_scan=1
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=6):
     4d 79 6e 65 74 61                                 Myneta          
scan_ssid=0 (0x0)
proto: 0x2
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=8): [REMOVED]
pairwise: 0x10
group: 0x10
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='Myneta'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=22 WE(source)=18 enc_capa=0x0
  capabilities: key_mgmt 0x0 enc 0x3
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:0c:41:2e:73:40
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
Setting scan request: 0 sec 100000 usec
Added interface eth1
RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 574 bytes of scan results (3 BSSes)
Scan results: 3
Selecting BSS from priority group 0
Try to find WPA-enabled AP
[COLOR="Red"]0: 00:14:51:6b:07:ff ssid='Myneta' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE[/COLOR]
1: 00:1a:70:e4:5c:57 ssid='krs10' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:12:17:e2:e9:84 ssid='mynet54g' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
[COLOR="Red"]0: 00:14:51:6b:07:ff ssid='Myneta' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - non-WPA network not allowed[/COLOR]
1: 00:1a:70:e4:5c:57 ssid='krs10' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:12:17:e2:e9:84 ssid='mynet54g' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 0 sec 0 usec
Starting AP scan (broadcast SSID)
CTRL-EVENT-TERMINATING - signal 2 received
Removing interface eth1
State: SCANNING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_wext_set_wpa
wpa_driver_wext_set_drop_unencrypted
wpa_driver_wext_set_countermeasures
No keys have been configured - skip key clearing
Cancelling scan request
Cancelling authentication timeout
WEXT: Operstate: linkmode=0, operstate=6

```

---

### Post by kevdog on 2007-11-18
Can you connect to just wpa(1) and not wpa(2)?  I know that you will have to modify the wpa_supplicant.conf file, but I just want to check you can do 1 before 2.

---

### Post by kevdog on 2007-11-18
Can you also post 

iwlist scan

---

### Post by semperfiguy on 2007-11-18
I was trying to use WPA earlier but with the same error, so I decided to start trying WPA2.  In the mac configuration tool for the router the options are WPA/WPA2 encryption and WPA2 encryption.  So I chose the one that I was sure had no other tricks.  

iwlist scan:
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:12:17:E2:E9:84
                    ESSID:"mynet54g"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:100/100  Signal level:-29 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:1A:70:E4:5C:57
                    ESSID:"krs10"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:35/100  Signal level:-73 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:14:51:6B:07:FF
                    ESSID:"Myneta"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:82/100  Signal level:-43 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

```

---

### Post by kevdog on 2007-11-18
What wireless driver are you using with ndiswrapper?  bcmwl5??

---

### Post by semperfiguy on 2007-11-18
lsbcmnds - the driver that came on the windows cd with the card. its a linksys wireless-g (wpc54g)

---

### Post by kevdog on 2007-11-18
it has two parts, a sys and inf file.  What is the name of thw sys file

---

### Post by semperfiguy on 2007-11-18
I dont know. I thought it was lsbcmnds.sys. I only have and use the .inf file

---

### Post by kevdog on 2007-11-18
The inf file is a text file.  You can open it up and read it.  Inside the file is a link (somewhere) to a binary .sys file.  Inside your /etc/ndiswrapper/lsbcmds folder, what files are present??

What does

ndiswrapper -l 
state?

---

### Post by semperfiguy on 2007-11-18
Here is the relevant output from lshw -C network
```
*-network
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 02
       serial: 00:0c:41:2e:73:40
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+lsbcmnds driverversion=1.45+The Linksys Group, Inc.,12/ ip=192.168.1.129 latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11b

```

---

### Post by kevdog on 2007-11-18
Yea -- I get that, it looks like everything is installed correctly, Im just trying to make sure everything is installed correctly up to this point, and trying to make sure that your linksys driver actually supports wpa.  Do you have a link to their website with info about the driver?

---

### Post by kevdog on 2007-11-18
I just looked up info from this website:
[http://www.linksys.com/servlet/Satellite?childpagename=US%2FLayout&packedargs=c%3DL_Product_C2%26cid%3D1115416827032&pagename=Linksys%2FCommon%2FVisitorWrapper](http://www.linksys.com/servlet/Satellite?childpagename=US%2FLayout&packedargs=c%3DL_Product_C2%26cid%3D1115416827032&pagename=Linksys%2FCommon%2FVisitorWrapper)

Under the data sheet pdf link, it states security protocol WEP and TKIP, 802.1x.  Im assuming by this they  are saying that it can only handle WPA TKIP ciphers.  Again its not really clear.

Assuming you can get an unencrypted connection (which I think way back when you did), Im going to assume your driver is setup correctly.

Log back into your WPA router, and choose the WPA/WPA2 option.  I want you to change all the possible choices to WPA(1) with TKIP.  You can do WPA2 with TKIP (if your router allows you to do so), but really lets just start with WPA since it was first established with TKIP.

Could you post a screenshot of your wireless security setup page on your router?

---

### Post by semperfiguy on 2007-11-18
The sys file is actually bcmwl5.sys

---

### Post by kevdog on 2007-11-18
Ok great, nothing unexpected then about your driver (I use the same driver!! -- only a wpc54gs card -- which I think defaults to the same bcmwl5 driver in linux -- no speed enhancement for the gs card under linux.)

---

### Post by semperfiguy on 2007-11-18
The first screen when configuring the network
********

and when WPA/WPA2 encryption is clicked on it takes you to this page
[ATTACH]50659[/ATTACH]

Now my card is the first version I do believe.  It would really stink if it didn't support WPA
the back says its IC is wpc54gv1 but I don't know if that matters.

---

### Post by kevdog on 2007-11-18
I think its only going to support wpa1.

What is under the following tabs (from the second screen shot)??:

Wireless Security

Wireless Options

---

### Post by semperfiguy on 2007-11-18
Wireless Security
[ATTACH]50661[/ATTACH]


Wireless Options
[ATTACH]50660[/ATTACH]

---

### Post by kevdog on 2007-11-18
Hmm not as informative as I would have liked,  definitely use wpa/wpa2.  Thats all I can say.  Use a variation of this for your wpa_supplicant.conf file:

ap_scan=1
ctrl_interface=/var/run/wpa_supplicant 

network={
        ssid="ESSID_IN_QUOTES"
        scan_ssid=0
        proto=WPA
        key_mgmt=WPA-PSK
        psk="ASCII PSK Password in Quotes"
        pairwise=TKIP
        group=TKIP
}


Tell me what happens.

---

### Post by semperfiguy on 2007-11-18
Same error I have been having...
```
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ap_scan=1
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=6):
     4d 79 6e 65 74 61                                 Myneta          
scan_ssid=0 (0x0)
proto: 0x1
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=8): [REMOVED]
pairwise: 0x8
group: 0x8
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='Myneta'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=22 WE(source)=18 enc_capa=0x0
  capabilities: key_mgmt 0x0 enc 0x3
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:0c:41:2e:73:40
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
Setting scan request: 0 sec 100000 usec
Added interface eth1
RTM_NEWLINK: operstate=0 ifi_flags=0x1002 ()
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 384 bytes of scan results (2 BSSes)
Scan results: 2
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:14:51:6b:07:ff ssid='Myneta' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
1: 00:12:17:e2:e9:84 ssid='mynet54g' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:14:51:6b:07:ff ssid='Myneta' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - non-WPA network not allowed
1: 00:12:17:e2:e9:84 ssid='mynet54g' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 0 sec 0 usec
Starting AP scan (broadcast SSID)
CTRL-EVENT-TERMINATING - signal 2 received
Removing interface eth1
State: SCANNING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_wext_set_wpa
wpa_driver_wext_set_drop_unencrypted
wpa_driver_wext_set_countermeasures
No keys have been configured - skip key clearing
Cancelling scan request
Cancelling authentication timeout
WEXT: Operstate: linkmode=0, operstate=6
```

Is there supposed to be stuff written in my /etc/network/interfaces file?

---

### Post by kevdog on 2007-11-18
Just to double check -- you can connect to this airport extreme router with an unencrypted connection??

Its weird with your output b/c this what it states:
Try to find WPA-enabled AP
0: 00:14:51:6b:07:ff ssid='Myneta' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE

Try to find non-WPA AP
0: 00:14:51:6b:07:ff ssid='Myneta' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - non-WPA network not allowed

Aren't these two statements the exact opposite??

---

### Post by semperfiguy on 2007-11-18
Ok yes I can connect with no encryption.  It was being flukey at first but I rebooted and am connected fine right now.  And yes those statements make no sense.  The second is a double negative so It's really like "WPA network allowed" wierd.

---

### Post by kevdog on 2007-11-18
Ok retry WPA(1).  If that doesnt work really try to pair down the wpa_supplicant.conf file to the following:

ctrl_interface=/var/run/wpa_supplicant
 network={
   ssid="myssid"
   psk="mysecret"
   key_mgmt=WPA-PSK
   proto=WPA
   pairwise=TKIP
 }

If this doesnt work -- Im not really sure!

---

### Post by semperfiguy on 2007-11-19
Is there supposed to be stuff in my /etc/network/interfaces file? because there is some lines in there pertaining to WPA

Also I noticed some guides use a generated psk in the wpa_supplicant.conf file? why do you use a ancii code?

---

### Post by kevdog on 2007-11-19
Using a wpa_supplicant.conf file is only necessary if you want to establish a connection manually -- manual connection is the most basic, it removes any potential problems you would have using network manager, wicd, etc.  Usually if you get a connection you start adding layers  -- for example the GUI network manager layer.  

As far as ASCII vs generated psk -- it guess it really doesnt matter.  Again Im just trying to make the manual connection steps as idiot proof as possible.  Manual connection is for troubleshooting, not everyday use -- even though I guess it could be used in that manner.

---

### Post by semperfiguy on 2007-11-21
Okay, I think I got it.  The commands I ran were:
```

sudo ifconfig eth1 down
sudo dhclient -r eth1
sudo wpa_supplicant -w -D wext -i eth1 -c /etc/wpa_supplicant.conf -dd 
sudo ifup eth1

```

Now the command sudo wpa_supplicant -w -D wext -i eth1 -c /etc/wpa_supplicant.conf -dd 
was filling up the terminal with this and then stopping:
```

Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 3 - start of a new network block
ssid - hexdump_ascii(len=6):
     4d 79 6e 65 74 61                                 Myneta          
PSK (ASCII passphrase) - hexdump_ascii(len=8): [REMOVED]
key_mgmt: 0x2
proto: 0x1
pairwise: 0x8
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Line 9: removed CCMP from group cipher list since it was not allowed for pairwise cipher
Priority group 0
   id=0 ssid='Myneta'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=22 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:0c:41:2e:73:40
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
Setting scan request: 0 sec 100000 usec
Added interface eth1
RTM_NEWLINK: operstate=0 ifi_flags=0x1002 ()
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 516 bytes of scan results (2 BSSes)
Scan results: 2
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:14:51:6b:07:ff ssid='Myneta' wpa_ie_len=26 rsn_ie_len=26 caps=0x11
   selected based on WPA IE
   selected WPA AP 00:14:51:6b:07:ff ssid='Myneta'
Try to find non-WPA AP
Trying to associate with 00:14:51:6b:07:ff (SSID='Myneta' freq=2412 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2 proto 1
WPA: set AP WPA IE - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 00 00
WPA: set AP RSN IE - hexdump(len=26): 30 18 01 00 00 0f ac 02 02 00 00 0f ac 04 00 0f ac 02 01 00 00 0f ac 02 00 00
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK

[COLOR="Red"]Trimmed out middle for size...[/COLOR]

wpa_driver_wext_set_operstate: operstate 0->1 (UP)
WEXT: Operstate: linkmode=-1, operstate=6
EAPOL: External notification - portValid=1
EAPOL: External notification - EAP success=1
EAPOL: SUPP_PAE entering state AUTHENTICATING
EAPOL: SUPP_BE entering state SUCCESS
EAP: EAP entering state DISABLED
EAPOL: SUPP_PAE entering state AUTHENTICATED
EAPOL: SUPP_BE entering state IDLE
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
EAPOL: startWhen --> 0

```

And then was stopping.  So I canceled it with Ctrl-C and my network would not work at all so I had to reboot.  Then I tried it again and this time opened another terminal and typed ifup eth1.  Bingo.  

So now my iwconfig reads
```

semperfiguy $ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Myneta"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:14:51:6B:07:FF   
          Bit Rate=54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:65/100  Signal level:-54 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

So I assume that means I'm connected to the proper network.   

Now I have one more question.  Is there a way I can integrate this into the startup so I don't have to run the commmands everytime?

---

### Post by kevdog on 2007-11-21
question -- so mean to tell me that it was working the entire time??

Try using this statement so you dont have to open another terminal:

sudo wpa_supplicant -Bw -D wext -i eth1 -c /etc/wpa_supplicant.conf

I've removed the -dd statement which stands for output the debugging output (-dd -- double d)

And added the -B statement which means run in the background.

Just for purposes of my tutorial can you relist your wpa_supplicant.conf file.

And lastly --- is this working with WPA or WPA2???

---

### Post by semperfiguy on 2007-11-21
No! it certainly wasn't working the whole time.  I altered my wpa_supplicant.conf which I think was the problem.

My .conf file now reads:
```
ctrl_interface=/var/run/wpa_supplicant

network={
        ssid="network"
        psk="password"
        key_mgmt=WPA-PSK
        proto=WPA
        pairwise=TKIP
}

```

It's working with WPA

---

### Post by kevdog on 2007-11-21
Did you retry with WPA2 just for kicks??

It would be:
```

ctrl_interface=/var/run/wpa_supplicant

network={
        ssid="network"
        psk="password"
        key_mgmt=WPA-PSK
        proto=RSN
        pairwise=CCMP
}
```

Im not sure if you are able to list more than one value for parameter, like
pairwise=CCMP TKIP

---

### Post by semperfiguy on 2007-11-22
I used the exact config file you just posted and it worked fine.  Thank you so much for your help.  I guess it was just the ap_scan line some others that I cut out that were making it have some trouble finding the proper essid.

---

### Post by kevdog on 2007-11-22
Im going to go ahead and make changes to my guide based on your findings.

Can you tell me if you change your .conf file to the following, does it work????:
```

ctrl_interface=/var/run/wpa_supplicant

network={
        ssid="network"
        psk="password"
        key_mgmt=WPA-PSK
        proto=RSN WPA
        pairwise=CCMP TKIP
}
```

---

### Post by semperfiguy on 2007-11-22
Yup. I just tried WPA2 and it worked like a charm.  The only thing that I changed was taking some of those lines..  Also I just tried for 2 of the lines

proto=RSN
pairwise=CCMP

Leaving out the WPA and TKIP but I don't know if that makes a difference I didn't try the other way.

---

### Post by semperfiguy on 2007-11-22
Edit:  Double Post

---

### Post by maramot on 2008-05-14
I read through this whole thread, but the steps here didn't solve my problem.
I have a Broadcom 4310. It's installed properly, using ndiswrapper 1.52 It can connect wirelessly to a nearby unprotected network. When I try to connect the "Airport Home" network at home though, the indicator stays at 0% and there's no connection established. I tried connecting manually, in the way described:
```

maramot@ubuntu:~$ sudo ifconfig wlan0 down
[sudo] password for maramot: 
maramot@ubuntu:~$ sudo dhclient -r wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:16:44:a8:1e:4a
Sending on   LPF/wlan0/00:16:44:a8:1e:4a
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
maramot@ubuntu:~$ sudo wpa_supplicant -w -D wext -i wlan0 -c /etc/wpa_supplicant.conf -dd

```

The output I get from the last command (wpa_supplicant...):

```

Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 3 - start of a new network block
ssid - hexdump_ascii(len=12):
     41 69 72 70 6f 72 74 20 48 6f 6d 65               Airport Home    
scan_ssid=0 (0x0)
proto: 0x1
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=8): [REMOVED]
pairwise: 0x8
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Line 10: removed CCMP from group cipher list since it was not allowed for pairwise cipher
Priority group 0
   id=0 ssid='Airport Home'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=22 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:16:44:a8:1e:4a
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
Setting scan request: 0 sec 100000 usec
Added interface wlan0
RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
Added BSSID 00:00:00:00:00:00 into blacklist
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
State: DISCONNECTED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 1219 bytes of scan results (5 BSSes)
Scan results: 5
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1e:52:6c:94:e9 ssid='Aiport Home' wpa_ie_len=26 rsn_ie_len=26 caps=0x11
   [COLOR="Red"]skip - SSID mismatch[/COLOR]
1: 00:1e:2a:65:2d:b2 ssid='NETGEAR' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:19:5b:0a:9b:ac ssid='gsm' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
3: 00:15:eb:e1:a8:0b ssid='DGruev' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
4: 00:0e:2e:6b:36:8c ssid='default' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:1e:52:6c:94:e9 ssid='Aiport Home' wpa_ie_len=26 rsn_ie_len=26 caps=0x11
   skip - SSID mismatch
1: 00:1e:2a:65:2d:b2 ssid='NETGEAR' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:19:5b:0a:9b:ac ssid='gsm' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
3: 00:15:eb:e1:a8:0b ssid='DGruev' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
4: 00:0e:2e:6b:36:8c ssid='default' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
No APs found - clear blacklist and try again
Removed BSSID 00:00:00:00:00:00 from blacklist (clear)
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1e:52:6c:94:e9 ssid='Aiport Home' wpa_ie_len=26 rsn_ie_len=26 caps=0x11
   skip - SSID mismatch
1: 00:1e:2a:65:2d:b2 ssid='NETGEAR' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:19:5b:0a:9b:ac ssid='gsm' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
3: 00:15:eb:e1:a8:0b ssid='DGruev' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
4: 00:0e:2e:6b:36:8c ssid='default' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:1e:52:6c:94:e9 ssid='Aiport Home' wpa_ie_len=26 rsn_ie_len=26 caps=0x11
   skip - SSID mismatch
1: 00:1e:2a:65:2d:b2 ssid='NETGEAR' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:19:5b:0a:9b:ac ssid='gsm' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
3: 00:15:eb:e1:a8:0b ssid='DGruev' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
4: 00:0e:2e:6b:36:8c ssid='default' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 0 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 775 bytes of scan results (3 BSSes)
Scan results: 3
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1e:52:6c:94:e9 ssid='Aiport Home' wpa_ie_len=26 rsn_ie_len=26 caps=0x11
   skip - SSID mismatch
1: 00:1e:2a:65:2d:b2 ssid='NETGEAR' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:15:eb:e1:a8:0b ssid='DGruev' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:1e:52:6c:94:e9 ssid='Aiport Home' wpa_ie_len=26 rsn_ie_len=26 caps=0x11
   skip - SSID mismatch
1: 00:1e:2a:65:2d:b2 ssid='NETGEAR' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:15:eb:e1:a8:0b ssid='DGruev' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 5 sec 0 usec
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b1a len=14
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c07 len=59
AssocReq IE wireless event - hexdump(len=51): 00 06 44 47 72 75 65 76 01 08 82 84 8b 96 24 30 48 6c 21 02 08 12 24 02 01 0e 32 04 0c 12 18 60 dd 09 00 10 18 02 00 10 00 00 00 dd 06 00 40 96 01 01 00
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c08 len=32
AssocResp IE wireless event - hexdump(len=24): 01 08 82 84 8b 96 24 30 48 6c 32 04 0c 12 18 60 dd 06 00 10 18 02 00 00
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:15:eb:e1:a8:0b
Association info event
req_ies - hexdump(len=51): 00 06 44 47 72 75 65 76 01 08 82 84 8b 96 24 30 48 6c 21 02 08 12 24 02 01 0e 32 04 0c 12 18 60 dd 09 00 10 18 02 00 10 00 00 00 dd 06 00 40 96 01 01 00
resp_ies - hexdump(len=24): 01 08 82 84 8b 96 24 30 48 6c 32 04 0c 12 18 60 dd 06 00 10 18 02 00 00
WPA: clearing own WPA/RSN IE
State: SCANNING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:15:eb:e1:a8:0b
No keys have been configured - skip key clearing
No network configuration found for the current AP
wpa_driver_wext_disassociate
No keys have been configured - skip key clearing
State: ASSOCIATED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
Added BSSID 00:00:00:00:00:00 into blacklist
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
State: DISCONNECTED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
RTM_NEWLINK: operstate=0 ifi_flags=0x1043 ([UP][RUNNING])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x1043 ([UP][RUNNING])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b1a len=14
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c07 len=59
AssocReq IE wireless event - hexdump(len=51): 00 06 44 47 72 75 65 76 01 08 82 84 8b 96 24 30 48 6c 21 02 08 12 24 02 01 0e 32 04 0c 12 18 60 dd 09 00 10 18 02 00 10 00 00 00 dd 06 00 40 96 01 01 00
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c08 len=32
AssocResp IE wireless event - hexdump(len=24): 01 08 82 84 8b 96 24 30 48 6c 32 04 0c 12 18 60 dd 06 00 10 18 02 00 00
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:15:eb:e1:a8:0b
Association info event
req_ies - hexdump(len=51): 00 06 44 47 72 75 65 76 01 08 82 84 8b 96 24 30 48 6c 21 02 08 12 24 02 01 0e 32 04 0c 12 18 60 dd 09 00 10 18 02 00 10 00 00 00 dd 06 00 40 96 01 01 00
resp_ies - hexdump(len=24): 01 08 82 84 8b 96 24 30 48 6c 32 04 0c 12 18 60 dd 06 00 10 18 02 00 00
WPA: clearing own WPA/RSN IE
State: DISCONNECTED -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:15:eb:e1:a8:0b
No keys have been configured - skip key clearing
No network configuration found for the current AP
wpa_driver_wext_disassociate
No keys have been configured - skip key clearing
State: ASSOCIATED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x1043 ([UP][RUNNING])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
BSSID 00:00:00:00:00:00 blacklist count incremented to 2
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
State: DISCONNECTED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Scan timeout - try to get results
Received 999 bytes of scan results (4 BSSes)
Scan results: 4
Selecting BSS from priority group 0

[COLOR="Red"](You can already see here that it has started looping. From here downwards you have seen this output already)[/COLOR]

Try to find WPA-enabled AP
0: 00:1e:52:6c:94:e9 ssid='Aiport Home' wpa_ie_len=26 rsn_ie_len=26 caps=0x11
   skip - SSID mismatch
1: 00:1e:2a:65:2d:b2 ssid='NETGEAR' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:15:eb:e1:a8:0b ssid='DGruev' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
3: 00:0e:2e:6b:36:8c ssid='default' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:1e:52:6c:94:e9 ssid='Aiport Home' wpa_ie_len=26 rsn_ie_len=26 caps=0x11
   skip - SSID mismatch
1: 00:1e:2a:65:2d:b2 ssid='NETGEAR' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:15:eb:e1:a8:0b ssid='DGruev' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
3: 00:0e:2e:6b:36:8c ssid='default' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
No APs found - clear blacklist and try again
Removed BSSID 00:00:00:00:00:00 from blacklist (clear)
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1e:52:6c:94:e9 ssid='Aiport Home' wpa_ie_len=26 rsn_ie_len=26 caps=0x11
   skip - SSID mismatch
1: 00:1e:2a:65:2d:b2 ssid='NETGEAR' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:15:eb:e1:a8:0b ssid='DGruev' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
3: 00:0e:2e:6b:36:8c ssid='default' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:1e:52:6c:94:e9 ssid='Aiport Home' wpa_ie_len=26 rsn_ie_len=26 caps=0x11
   skip - SSID mismatch
1: 00:1e:2a:65:2d:b2 ssid='NETGEAR' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:15:eb:e1:a8:0b ssid='DGruev' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
3: 00:0e:2e:6b:36:8c ssid='default' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
No suitable AP found.

[COLOR="Red"]...And it keeps repeating over and over. I'm stopping it here.[/COLOR] 

```
I don't understand why does it say "SSID mismatch" when this is exactly the SSID I've specified in my wpa_supplicant.conf. You can see it here:

```

ctrl_interface=/var/run/wpa_supplicant 

network={
        ssid="Airport Home"
        scan_ssid=0
        proto=WPA
        key_mgmt=WPA-PSK
        psk="12345678"
        pairwise=TKIP
}

```

Any help will be greatly appreciated. I don't want to go back to gutsy just because of some router incompatibility.

---

### Post by kevdog on 2008-05-15
Dont put spaces in your essid name -- that really tends to confuse things.  Change the name on your router.

---

