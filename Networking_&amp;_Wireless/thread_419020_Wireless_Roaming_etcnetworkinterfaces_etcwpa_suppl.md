---
title: "Wireless Roaming /etc/network/interfaces /etc/wpa_supplicant"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by promet on 2007-04-22
Hi,

I have been able to successfully connect to my home network using WPA-PSK to a hidden SSID.

I haven't however been able to connect to any open unencrypted wireless networks, I've tried various configurations of /etc/network/interfaces and /etc/wpa_supplicant. But no luck.

I am running Ubuntu 6.10 Edgy
My wireless card is pcmcia [eHome EH101]("http://www.ehomeproducts.net/Product/View.aspx?ProdID=2")
I am using the "wext" wireless driver

My /etc/network/interfaces is:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

#The wireless interface
auto wlan0
iface wlan0 inet static
address 192.168.1.43
netmask 255.255.255.0
network 192.168.1.0
broadcast 255.255.255.255
gateway 192.168.1.1
dns-nameservers 192.168.1.1
wpa-driver wext
wpa-conf managed
wpa-ssid schliebe
wpa-ap-scan 2
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk 36de50a6623e6ee01cffb6f487578c4eb2802cc60e74d231357ec1ceb42e5367

```

My /etc/wpa_supplicant file is:


```
#ctrl_interface=/var/run/wpa_supplicant
#ctrl_interface_group=0
#eapol_version=1
#ap_scan=1
#fast_reauth=1
#


#network={
#       ssid=""
#       key_mgmt=NONE
#}


#network={
#       ssid="schliebe"
#       scan_ssid=1
#       proto=WPA
#       pairwise=CCMP TKIP
 #       key_mgmt=WPA-PSK
#       psk=36de50a6623e6ee01cffb6f487578c4eb2802cc60e74d231357ec1ceb42e5367
#}

#ctrl_interface=/var/run/wpa_supplicant
#ap_scan=1

#network={
#        ssid="schliebe"
#        scan_ssid=1
#               proto=WPA RSN
#       key_mgmt=WPA-PSK
#               pairwise=CCMP TKIP
#               group=CCMP TKIP
#        psk=36de50a6623e6ee01cffb6f487578c4eb2802cc60e74d231357ec1ceb42e5367
#
#}


```
Oddly, having my wpa_supplicant commented out, essentially blank, was the only way I could get my home wireless to work. I haven't been able to make any additions to /etc/wpa_supplicant and make any successful wireless connections whatever.

Although I've jury-rigged the home network I'd like to connect to general unencrypted wifi-spots.

Here is what iwconfig reports when I am successfully connected with the above configurations:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"schliebe"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:6C:98:C8:8A   
          Bit Rate:1 Mb/s   Sensitivity=-200 dBm  
          RTS thr:2346 B   Fragment thr:2346 B   
          Encryption key:5072-169E-474B-3C4A-3162-5A0B-D120-41FD-8B0E-0EDB-733D-EA08-0D51-6C7E-89BC-D349   Security mode:restricted
          Power Management:off
          Link Quality:100/100  Signal level:-65 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```



I've tried several standard implementations of each of these config files for open networks.
i.e.:

```
network={
              ssid=""
              key_mgmt=NONE
}


```

Here's a sample of my /etc/network/interfaces attempt at roaming:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
allow-hotplug eth0
iface eth0 inet dhcp

#The wireless interface
allow-hotplug wlan0
iface wlan0 inet manual

wpa-driver wext
wpa-roam /etc/wpa_supplicant.conf
```

Here's an example of my /etc/wpa_supplicant.conf for attempting roaming:

```
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
eapol_version=1
ap_scan=2
fast_reauth=1


#Home network
network={
        ssid="schliebe"
        scan_ssid=1
        proto=WPA RSN
        key_mgmt=WPA-PSK
        pairwise=CCMP TKIP
        group=CCMP TKIP
        psk=36de50a6623e6ee01cffb6f487578c4eb2802cc60e74d231357ec1ceb42e5367

}



#Open networks
network={
        ssid=""
        key_mgmt=NONE
        #priority=2
}
```


I've tried these and other common solutions

Here is the results of "iwlist scan" for my local wireless networks:

```
wlan0     Scan completed :
          Cell 01 - Address: 00:14:6C:98:C8:8A
                    ESSID:"schliebe"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-57 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
          Cell 02 - Address: 00:04:5A:FD:2B:A1
                    ESSID:"nycb"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.457 GHz (Channel 10)
                    Quality:0/100  Signal level:-91 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:14:6C:98:C8:8A
                    ESSID:""
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-55 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
          Cell 04 - Address: 00:13:10:86:E9:3A
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-92 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 05 - Address: 00:18:39:FA:BD:A6
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-91 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

```

I'd like to configure a setup where I could contact Cell 05 "linksys" which apprears to be open. Afterward I could craft that setup for general wireless roaming, That's the idea anyway. If anyone has any experience with the eHome EH101 and wext driver configuration I;d appreciate any insights.

Also if there is a way making iwconfig statements from the command line, etc. that might work (I've tried without much success so far), please let me know your thoughts, Thanks.

---

