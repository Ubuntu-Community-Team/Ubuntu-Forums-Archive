---
title: "How to fix dependencies Ubuntu 14.10"
date: 2015-10-31
forum: Networking &amp; Wireless
---

### Post by leonardo-a027 on 2015-10-31
I had a problem with my network-manager so I reinstalled it but now I can't install anything else. I tried cleaning the apt-get cache: 


     ```
sudo apt-get autoremove
```


But I got the message: 


    ```
Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    You might want to run 'apt-get -f install' to correct these.
    The following packages have unmet dependencies:
     network-manager-gnome : Depends: libnm-gtk0 (= 0.9.8.8-0ubuntu4.4) but 0.9.8.8-0ubuntu7 is installed
     network-manager-iodine : Depends: iodine but it is not installed
     network-manager-openconnect : Depends: openconnect (>= 3) but it is not installed
     network-manager-openconnect-gnome : Depends: libopenconnect2 (>= 4.99) but it is not installable
     network-manager-openvpn : Depends: openvpn (>= 2.1~rc9) but it is not installed
     network-manager-strongswan : Depends: libgnomeui-0 (>= 2.22.0) but it is not installed
                                  Depends: strongswan-nm but it is not installed
     network-manager-vpnc : Depends: vpnc but it is not installed
    E: Unmet dependencies. Try using -f.
```


So the I tried with: 
    
        ```
sudo apt-get -f install
```
    
and the next message popped out: 
    
        ```
WARNING: The following packages cannot be authenticated!
      network-manager-gnome network-manager-iodine-gnome iodine
      network-manager-iodine liboath0 libtommath0 libtomcrypt0 libstoken1
      libopenconnect3 network-manager-openconnect-gnome vpnc-scripts
      network-manager-openconnect openconnect network-manager-openvpn-gnome
      libpkcs11-helper1 openvpn network-manager-openvpn network-manager-vpnc-gnome
      vpnc network-manager-vpnc libbonobo2-common liborbit-2-0 libbonobo2-0
      libgnome2-common libgnome2-bin libgnome2-0 libgnomecanvas2-common
      libgnomecanvas2-0 libbonoboui2-common libbonoboui2-0 libgnomeui-common
      libgnomeui-0 libstrongswan strongswan-plugin-openssl strongswan-ike
      strongswan-nm libmodemmanagerqt1 libnetworkmanagerqt1 kwalletmanager
      plasma-nm
    Install these packages without verification? [y/N] y
    Err http://archive.ubuntu.com/ubuntu/ utopic/main network-manager-gnome amd64 0.9.8.8-0ubuntu7
      404  Not Found
    Err http://archive.ubuntu.com/ubuntu/ utopic/universe network-manager-iodine-gnome amd64 0.0.5~0.gita09ce6-1
      404  Not Found
    Err http://archive.ubuntu.com/ubuntu/ utopic/universe iodine amd64 0.6.0~rc1-20
      404  Not Found
    Err http://archive.ubuntu.com/ubuntu/ utopic/universe network-manager-iodine amd64 0.0.5~0.gita09ce6-1
      404  Not Found
    Err http://archive.ubuntu.com/ubuntu/ utopic/universe libstoken1 amd64 0.6-1
      404  Not Found
    Err http://archive.ubuntu.com/ubuntu/ utopic/universe network-manager-openconnect-gnome amd64 0.9.8.6-1ubuntu2
      404  Not Found
    Err http://archive.ubuntu.com/ubuntu/ utopic/universe network-manager-openconnect amd64 0.9.8.6-1ubuntu2
      404  Not Found
    Err http://archive.ubuntu.com/ubuntu/ utopic/universe network-manager-openvpn-gnome amd64 0.9.8.4-2ubuntu1
      404  Not Found
    Err http://archive.ubuntu.com/ubuntu/ utopic/universe network-manager-openvpn amd64 0.9.8.4-2ubuntu1
      404  Not Found
    Err http://archive.ubuntu.com/ubuntu/ utopic/universe network-manager-vpnc-gnome amd64 0.9.8.6-2ubuntu1
      404  Not Found
    Err http://archive.ubuntu.com/ubuntu/ utopic/universe network-manager-vpnc amd64 0.9.8.6-2ubuntu1
      404  Not Found
    Err http://archive.ubuntu.com/ubuntu/ utopic/universe libnetworkmanagerqt1 amd64 0.9.8.2-1ubuntu1
      404  Not Found
    Err http://archive.ubuntu.com/ubuntu/ utopic/universe kwalletmanager amd64 4:4.14.1-0ubuntu1
      404  Not Found
    Err http://archive.ubuntu.com/ubuntu/ utopic/universe plasma-nm amd64 0.9.3.4-1
      404  Not Found
    Err http://archive.ubuntu.com/ubuntu/ utopic-security/main openvpn amd64 2.3.2-9ubuntu1.1
      404  Not Found
    Err http://archive.ubuntu.com/ubuntu/ utopic-security/main libstrongswan amd64 5.1.2-0ubuntu3.3
      404  Not Found
    Err http://archive.ubuntu.com/ubuntu/ utopic-security/main strongswan-plugin-openssl amd64 5.1.2-0ubuntu3.3
      404  Not Found
    Err http://archive.ubuntu.com/ubuntu/ utopic-security/main strongswan-ike amd64 5.1.2-0ubuntu3.3
      404  Not Found
    Err http://archive.ubuntu.com/ubuntu/ utopic-security/universe strongswan-nm amd64 5.1.2-0ubuntu3.3
      404  Not Found
    E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.9.8.8-0ubuntu7_amd64.deb  404  Not Found
    
    E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/universe/n/network-manager-iodine/network-manager-iodine-gnome_0.0.5~0.gita09ce6-1_amd64.deb  404  Not Found
    
    E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/universe/i/iodine/iodine_0.6.0~rc1-20_amd64.deb  404  Not Found
    
    E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/universe/n/network-manager-iodine/network-manager-iodine_0.0.5~0.gita09ce6-1_amd64.deb  404  Not Found
    
    E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/universe/s/stoken/libstoken1_0.6-1_amd64.deb  404  Not Found
    
    E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/universe/n/network-manager-openconnect/network-manager-openconnect-gnome_0.9.8.6-1ubuntu2_amd64.deb  404  Not Found
    
    E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/universe/n/network-manager-openconnect/network-manager-openconnect_0.9.8.6-1ubuntu2_amd64.deb  404  Not Found
    
    E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/universe/n/network-manager-openvpn/network-manager-openvpn-gnome_0.9.8.4-2ubuntu1_amd64.deb  404  Not Found
    
    E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/o/openvpn/openvpn_2.3.2-9ubuntu1.1_amd64.deb  404  Not Found
    
    E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/universe/n/network-manager-openvpn/network-manager-openvpn_0.9.8.4-2ubuntu1_amd64.deb  404  Not Found
    
    E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/universe/n/network-manager-vpnc/network-manager-vpnc-gnome_0.9.8.6-2ubuntu1_amd64.deb  404  Not Found
    
    E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/universe/n/network-manager-vpnc/network-manager-vpnc_0.9.8.6-2ubuntu1_amd64.deb  404  Not Found
    
    E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/s/strongswan/libstrongswan_5.1.2-0ubuntu3.3_amd64.deb  404  Not Found
    
    E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/s/strongswan/strongswan-plugin-openssl_5.1.2-0ubuntu3.3_amd64.deb  404  Not Found
    
    E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/s/strongswan/strongswan-ike_5.1.2-0ubuntu3.3_amd64.deb  404  Not Found
    
    E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/universe/s/strongswan/strongswan-nm_5.1.2-0ubuntu3.3_amd64.deb  404  Not Found
    
    E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/universe/libn/libnm-qt/libnetworkmanagerqt1_0.9.8.2-1ubuntu1_amd64.deb  404  Not Found
    
    E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/universe/k/kwalletmanager/kwalletmanager_4.14.1-0ubuntu1_amd64.deb  404  Not Found
    
    E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/universe/p/plasma-nm/plasma-nm_0.9.3.4-1_amd64.deb  404  Not Found
    
    E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

---

### Post by Bashing-om on 2015-10-31
leonardo-a027; Short answer ->

You do not ... release 14.10 is End_of_Life and no longer has support . The software repository no longer exists as you may have once known it .

Upgrade to a current release is the best bestest advise.
[https://help.ubuntu.com/community/EOLUpgradeshttps](https://help.ubuntu.com/community/EOLUpgradeshttps)
If ya choose to go this route . A clean fresh install is often the better course.

[INDENT][INDENT]beating a dead horse
[INDENT][INDENT][INDENT]does no one good
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

