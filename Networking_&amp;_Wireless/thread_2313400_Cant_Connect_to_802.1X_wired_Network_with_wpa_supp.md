---
title: "Cant Connect to 802.1X wired Network with wpa_supplicant Xubuntu 14.04"
date: 2016-02-12
forum: Networking &amp; Wireless
---

### Post by GunnarOeh on 2016-02-12
I want to connect to my companies wired Network with my laptop

Using Toshiba Portégé Z50 (i5-4210U) RV2015 
Intel Core i5-4210U (1.70GHz, 2.7GHz)

Network Card: Intel(R) Ethernet Connection I218-V

with a freshly installed Xubuntu 14.04.

The network admin stated that the following informations about the network are correct:

        key_mgmt=IEEE8021X
        eap=PEAP
        anonymous_identity="some identity"
        ca_cert="path to ca.cer"
        phase2="auth=mschapv2"
        private_key="path to privkey2.pem"

To be able to connect I use wpa supllicant while I disconnected all wired and wireless connections in the network manager.

/etc/wpa_supplicant.conf:                                                    
```
# Where is the control interface located
ctrl_interface=/var/run/wpa_supplicant

# Who can use the WPA frontend? 0 or Group Name
ctrl_interface_group=0

# Which version of IEEE 802.1X - Set it to 2
eapol_version=2

# Scanning for wireless access-points?
ap_scan=0

#Network settings for the dbfz network

network={
                key_mgmt=IEEE8021X
        eap=PEAP
        anonymous_identity="some identity"
        ca_cert="path to ca.cer"
        phase2="auth=mschapv2"
        private_key="path to privkey2.pem"}
```

Trying to establish the connection:
```
sudo wpa_supplicant -c /etc/wpa_supplicant.conf -dd wired -i eth0

wpa_supplicant v2.1
random: Trying to read entropy from /dev/random
Successfully initialized wpa_supplicant
Initializing interface 'eth0' conf '/etc/wpa_supplicant.conf' driver 'default' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ctrl_interface_group='0'
eapol_version=2
ap_scan=0
Line: 15 - start of a new network block
key_mgmt: 0x8
eap methods - hexdump(len=16): 00 00 00 00 19 00 00 00 00 00 00 00 00 00 00 00
anonymous_identity - hexdump_ascii(len=6):
     62 69 6f 65 35 36                                 some identity          
ca_cert - hexdump_ascii(len=36):
     2f 68 6f 6d 65 2f 61 64 6d 69 6e 69 73 74 72 61    path to ca.cer
     74 6f 72 2f 44 6f 77 6e 6c 6f 61 64 73 2f 63 61   
     2e 63 65 72                                                   
phase2 - hexdump_ascii(len=13):
     61 75 74 68 3d 6d 73 63 68 61 70 76 32            auth=mschapv2   
private_key - hexdump_ascii(len=32):
     2f 68 6f 6d 65 2f 61 64 6d 69 6e 69 73 74 72 61   path to privkey.pem
     74 6f 72 2f 70 72 69 76 6b 65 79 32 2e 70 65 6d   
Priority group 0
   id=0 ssid=''
rfkill: initial event: idx=0 type=2 op=0 soft=0 hard=0
rfkill: initial event: idx=1 type=1 op=0 soft=0 hard=0
rfkill: initial event: idx=2 type=8 op=0 soft=0 hard=0
rfkill: initial event: idx=3 type=2 op=0 soft=0 hard=0
nl80211: Supported cipher 00-0f-ac:4
nl80211: Supported cipher 00-0f-ac:2
nl80211: Supported cipher 00-0f-ac:1
nl80211: Supported cipher 00-0f-ac:5
nl80211: Supported cipher 00-0f-ac:6
nl80211: Supported cipher 00-14-72:1
nl80211: Using driver-based off-channel TX
nl80211: Use separate P2P group interface (driver advertised support)
nl80211: interface eth0 in phy phy0
nl80211: Set mode ifindex 2 iftype 2 (STATION)
nl80211: Failed to set interface 2 to mode 2: -19 (No such device)
nl80211: Could not configure driver mode
nl80211: Remove monitor interface: refcount=0
netlink: Operstate: ifindex=2 linkmode=0 (kernel-control), operstate=6 (IF_OPER_UP)
nl80211: Set mode ifindex 2 iftype 2 (STATION)
nl80211: Failed to set interface 2 to mode 2: -19 (No such device)
eth0: Failed to initialize driver interface
Failed to add interface eth0
eth0: Cancelling scan request
eth0: Cancelling authentication timeout
```

Some help interpreting the log and improving the .conf and network settings would be much appreciated.

---

### Post by GunnarOeh on 2016-02-15
Network Settings (CLient Side):

```
sudo lshw -C network
  *-network               
       Beschreibung: Ethernet interface
       Produkt: Ethernet Connection I218-V
       Hersteller: Intel Corporation
       Physische ID: 19
       Bus-Informationen: pci@0000:00:19.0
       Logischer Name: eth0
       Version: 04
       Seriennummer: b8:6b:23:25:70:c2
       Größe: 1Gbit/s
       Kapazität: 1Gbit/s
       Breite: 32 bits
       Takt: 33MHz
       Fähigkeiten: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       Konfiguration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k duplex=full firmware=0.6-3 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       Ressourcen: irq:43 memory:f0600000-f061ffff memory:f063e000-f063efff ioport:3080(Größe=32)
  *-network
       Beschreibung: Kabellose Verbindung
       Produkt: Wireless 3160
       Hersteller: Intel Corporation
       Physische ID: 0
       Bus-Informationen: pci@0000:02:00.0
       Logischer Name: wlan0
       Version: 83
       Seriennummer: d0:7e:35:a7:36:9a
       Breite: 64 bits
       Takt: 33MHz
       Fähigkeiten: pm msi pciexpress bus_master cap_list ethernet physical wireless
       Konfiguration: broadcast=yes driver=iwlwifi driverversion=3.19.0-15-generic firmware=25.15.12.0 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       Ressourcen: irq:45 memory:f0400000-f0401fff
  *-network DEAKTIVIERT
       Beschreibung: Ethernet interface
       Physische ID: 1
       Logischer Name: wwan0
       Seriennummer: 4e:28:62:8d:18:5a
       Fähigkeiten: ethernet physical
       Konfiguration: broadcast=yes driver=cdc_mbim driverversion=22-Aug-2005 firmware=CDC MBIM link=no multicast=yes
```

---

### Post by GunnarOeh on 2016-02-17
Any Ideas? I got the impression, that to be able to connect to a 802.1X wired network, which is not password protected (certificates only) I need to use wpasupplicant.
I cant save a connection like that in network manager as long as the username and password is empty.

I partly tried to follow: [https://help.ubuntu.com/community/Network802.1xAuthentication](https://help.ubuntu.com/community/Network802.1xAuthentication)

---

