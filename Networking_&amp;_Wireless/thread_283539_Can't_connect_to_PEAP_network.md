---
title: "Can't connect to PEAP network"
date: 2006-10-24
forum: Networking &amp; Wireless
---

### Post by hatchek on 2006-10-24
Hi, I'm having difficulty connecting to the wireless network at my University.

The computer I have is an HP dv8000 laptop. The drivers I use in windows are the same I use in ndiswrapper for linux. (and I can connect to my home WPA-PSK network with no problems). The steps I took to associate at school under windows are here: [http://www.rhysman.com/wireless.html](http://www.rhysman.com/wireless.html)

The school uses Cisco APs as far as I know. 

My current WPA supplicant config file is: ```

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

network={
        ssid="Wilkes.edu"
        key_mgmt=WPA-EAP
        eap=PEAP
        auth_alg=OPEN
        phase1="peaplabel=1"
        phase2="auth=MSCHAPV2"
        identity="un"
        password="password"
}

network={
        ssid="linksys"
        key_mgmt=WPA-PSK
        psk="password"
}

```

An iwlist of the are results in: ```

eth1      Scan completed :
          Cell 01 - Address: 00:0D:ED:4D:05:2A
                    ESSID:"Wilkes.edu"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-92 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 32:7E:6C:18:31:79
                    ESSID:"hpsetup"
                    Protocol:IEEE 802.11b
                    Mode:Ad-Hoc
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-90 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:14:6A:49:BF:C0
                    ESSID:"Wilkes.edu"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-90 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 04 - Address: 00:13:19:64:73:20
                    ESSID:"Wilkes.edu"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.447 GHz (Channel 8)
                    Quality:0/100  Signal level:-83 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0


```

Running [COLOR="NAVY"]wpa_supplicant -ieth1 -c /etc/wpa_supplicant/wpa_supplicant.conf -Dwext -dd [/color] gives me
the usual parse stuff and then the scan of the networks in range: ```

State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 777 bytes of scan results (4 BSSes)
Scan results: 4
Selecting BSS from priority group 0
0: 00:13:19:64:73:20 ssid='Wilkes.edu' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
1: 00:0d:ed:4d:05:2a ssid='Wilkes.edu' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:14:6a:49:bf:c0 ssid='Wilkes.edu' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
3: 32:7e:6c:18:31:79 ssid='hpsetup' wpa_ie_len=0 rsn_ie_len=0 caps=0x2
   skip - no WPA/RSN IE
No suitable AP found.
Setting scan request: 5 sec 0 usec

```
and then it'll just loop here.

Whats wrong?

---

### Post by hatchek on 2006-10-26
bumpity bump

---

