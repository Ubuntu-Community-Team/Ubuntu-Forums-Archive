---
title: "Netplan Wifi WPA enterprise on 18.04 Bionic Mini"
date: 2019-02-25
forum: Networking &amp; Wireless
---

### Post by dony71 on 2019-02-25
I have Ubuntu 18.04.2 LTS server for raspberry pi 3 and try to enable wifi wpa enterprise

[http://cdimage.ubuntu.com/ubuntu/releases/bionic/release/ubuntu-18.04.2-preinstalled-server-arm64+raspi3.img.xz](http://cdimage.ubuntu.com/ubuntu/releases/bionic/release/ubuntu-18.04.2-preinstalled-server-arm64+raspi3.img.xz)[COLOR=#000000]

[/COLOR][COLOR=#000000]I follow this example [/COLOR][https://netplan.io/examples](https://netplan.io/examples)[COLOR=#000000] but get error message[/COLOR]
[COLOR=#000000]Error in network definition /etc/netplan/50-cloud-init.yaml: unknown key auth[/COLOR]
[COLOR=#000000]
anybody can help me how to configure wifi with wpa enterprise?[/COLOR]

---

### Post by dony71 on 2019-02-26
[COLOR=#000000]Content yaml below
I check also no tab being used for spacing

/etc/netplan/50-cloud-init.yaml

[/COLOR]```

network:
    version: 2
    ethernets:
        eth0:
            dhcp4: true
            match:
                macaddress: 88:77:66:55:44:33
            set-name: eth0
    wifis:
        wlan0:
            dhcp4: true
            addresses: [10.168.1.41/24]
            gateway4: 10.168.1.1
            nameservers:
                addresses: [10.168.1.1, 8.8.8.8]
            access-points:
                MY_OFFICE:
                   auth:
                     key-management: eap
                     method: peap
                     identity: "xxx@xxx.com"
                     password: "xxx"

```

---

