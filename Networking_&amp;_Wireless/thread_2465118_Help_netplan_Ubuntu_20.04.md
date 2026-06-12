---
title: "Help netplan Ubuntu 20.04"
date: 2021-07-22
forum: Networking &amp; Wireless
---

### Post by jackwan2 on 2021-07-22
I kept on getting this error message(warning: interface "enp1s0" has no IP addresses)
  in journalctl:


```
Jul 22 00:22:49 ubuntu20backup systemd-networkd[261624]: bond1: netdev exists, using existing without changing its parameters
Jul 22 00:22:49 ubuntu20backup systemd-networkd[261624]: bond1: IPv6 successfully enabled
Jul 22 00:22:49 ubuntu20backup sudo[261433]: pam_unix(sudo:session): session closed for user root
Jul 22 00:22:49 ubuntu20backup systemd-networkd[261624]: wlp2s0: IPv6 successfully enabled
Jul 22 00:22:49 ubuntu20backup systemd-networkd[261624]: enp1s0: IPv6 successfully enabled
Jul 22 00:22:49 ubuntu20backup kernel: wlp2s0: authenticate with 18:e8:29:a7:f6:60
Jul 22 00:22:49 ubuntu20backup wpa_supplicant[261628]: wlp2s0: SME: Trying to authenticate with 18:e8:29:a7:f6:60 (SSID='wanj' freq=2462 MHz)
Jul 22 00:22:49 ubuntu20backup kernel: wlp2s0: send auth to 18:e8:29:a7:f6:60 (try 1/3)
Jul 22 00:22:49 ubuntu20backup wpa_supplicant[261628]: wlp2s0: Trying to associate with 18:e8:29:a7:f6:60 (SSID='wanj' freq=2462 MHz)
Jul 22 00:22:49 ubuntu20backup kernel: wlp2s0: authenticated
Jul 22 00:22:49 ubuntu20backup kernel: wlp2s0: associate with 18:e8:29:a7:f6:60 (try 1/3)
Jul 22 00:22:49 ubuntu20backup kernel: wlp2s0: RX AssocResp from 18:e8:29:a7:f6:60 (capab=0x31 status=0 aid=2)
Jul 22 00:22:49 ubuntu20backup kernel: wlp2s0: associated
Jul 22 00:22:49 ubuntu20backup wpa_supplicant[261628]: wlp2s0: Associated with 18:e8:29:a7:f6:60
Jul 22 00:22:49 ubuntu20backup wpa_supplicant[261628]: wlp2s0: CTRL-EVENT-SUBNET-STATUS-UPDATE status=0
Jul 22 00:22:49 ubuntu20backup wpa_supplicant[261628]: wlp2s0: WPA: Key negotiation completed with 18:e8:29:a7:f6:60 [PTK=CCMP GTK=CCMP]
Jul 22 00:22:49 ubuntu20backup kernel: IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
Jul 22 00:22:49 ubuntu20backup wpa_supplicant[261628]: wlp2s0: CTRL-EVENT-CONNECTED - Connection to 18:e8:29:a7:f6:60 completed [id=0 id_str=]
Jul 22 00:22:49 ubuntu20backup systemd-networkd[261624]: wlp2s0: Gained carrier
Jul 22 00:22:49 ubuntu20backup systemd-networkd[261624]: wlp2s0: Connected WiFi access point: wanj (18:e8:29:a7:f6:60)
Jul 22 00:22:49 ubuntu20backup systemd-networkd[261624]: wlp2s0: DHCPv4 address 192.168.1.4/24 via 192.168.1.1
Jul 22 00:22:49 ubuntu20backup systemd-timesyncd[633]: Network configuration changed, trying to establish connection.
Jul 22 00:22:49 ubuntu20backup systemd-timesyncd[633]: Initial synchronization to time server 91.189.89.199:123 (ntp.ubuntu.com).
Jul 22 00:22:51 ubuntu20backup systemd-networkd[261624]: wlp2s0: Gained IPv6LL
Jul 22 00:23:26 ubuntu20backup nextcloud.mdns-publisher[1113]: 2021/07/22 00:23:26 WARNING: interface "enp1s0" has no IP addresses
```

and here is my netplan config

# This is the network config written by 'subiquity'
```
network:
#  bonds:
#    bond1:
#      interfaces: []
#      parameters:
#        mode: balance-rr
#  bridges: {}
  ethernets:
    enp1s0:
      dhcp4: true
  vlans: {}
  renderer: networkd
  wifis:
    wlp2s0:
      access-points:
        wxxj:
          password: "vvvvvvvv"
      dhcp4: true
```


What did I do wrong with the config yaml? I tried both with the "bond" and "bridge" in and out, but no effect, same error.
I do not have an cable connected, but the wifi is working fine.

---

### Post by TheFu on 2021-07-23
enp1s0 is an wired ethernet device.  It is setup to look for a DHCP server to get a network configuration.  If you don't connect a wire to it that connects to a DHCP server, then it won't get any network config - definitely no IP address.
[LIST]
[*]If you are happy using wifi (which I wouldn't be), then great.
[*]A server shouldn't use wifi, IMHO. It is just asking for problems.
[*]A server shouldn't use dhcp either, IMHO.  It is just asking for problems.
[*]A server SHOULD have a wired connection, with static network configuration, setup locally.  IMHO.
[/LIST]

Others can have different opinions.

The message means nothing. If it drives you crazy, remove the stanza for the wired ethernet device and regenerate and apply the netplan config.

---

### Post by Tadaen_Sylvermane on 2021-07-25
Agree with TheFu about wired vs wifi and static ip. That being said to eliminate the error just remove the interface from the netplan config file. Problem solved. It won't try to configure something if it doesn't have any directives to do so.

Eliminate this section:

```
ethernets:
    enp1s0:
         dhcp4: true
```

---

### Post by jackwan2 on 2021-07-26
Thank you all.
Actually, I did set a static ip for the server at the router using the mac address. And I agree I should use wired connections. Its an temporary arrangement for now.

---

### Post by TheFu on 2021-07-26
If this is solved, please help the community by using the "Thread tools" button at the top of the page and marking it SOLVED.  This drastically reduces wasted time for people seeking answers and for people looking to be helpful.

---

