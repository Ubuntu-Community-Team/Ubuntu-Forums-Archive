---
title: "WPA + EAP TLS (help with radius server)???"
date: 2007-08-23
forum: Networking &amp; Wireless
---

### Post by ryanfx on 2007-08-23
hey guys - I'm trying to get my wireless working with a radius server using TLS and this is what I get after trying to connect with wpa_supplicant - any ideas??

I believe I have everything configured correctly (radius server, AP, certs, etc.) but obviously not.

```

bt etc # cat /etc/wpa_supplicant.conf
network={
    ssid="dlink"
    proto=RSN
    key_mgmt=WPA-EAP
    eap=TLS
    identity="loader"
    ca_cert="/etc/certs/cacert.pem"
    client_cert="/etc/certs/client_cert.pem"
    private_key="/etc/certs/client_key.pem"
    private_key_passwd="mypass"
}


```


```

bt etc # wpa_supplicant -d -Dwext -iath0 -c./wpa_supplicant.conf
Initializing interface 'ath0' conf './wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file './wpa_supplicant.conf' -> '/etc/./wpa_supplicant.conf'
Reading configuration file '/etc/./wpa_supplicant.conf'
Priority group 0
   id=0 ssid='dlink'
Initializing interface (2) 'ath0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=21 WE(source)=13 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:11:22:33:44:55:66
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
Setting scan request: 0 sec 100000 usec
Added interface ath0
RTM_NEWLINK: operstate=0 ifi_flags=0x1002 ()
Wireless event: cmd=0x8b06 len=8
Ignore event for foreign ifindex 3
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ath0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ath0' added
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
No suitable AP found.
Setting scan request: 0 sec 0 usec
Starting AP scan (broadcast SSID)
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b19 len=8
Received 220 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
0: 00:17:9a:xx:xx:xx ssid='dlink' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN proto match
No suitable AP found.

```

---

### Post by wirelessmonkey on 2007-08-28
your neglected to specify your pairwise and group values.  Some APs are smart enough to send this data back for you, but usually they're just dump. Specify CCMP and TKIP for both sets, unless you're trying something else entirely.

Just to be sure, what authentication types are you wanting to use?  Are your APs WPA enterprise capable? Maybe they only do 802.1x Dynamic Wep? *shrug* let me know more, and I'll help the best I can.

---

