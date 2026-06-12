---
title: "WiFi not getting IP from DHCP"
date: 2021-10-21
forum: Networking &amp; Wireless
---

### Post by stevermann on 2021-10-21
I have a small-form computer running Ubuntu 20.04 Server in a headless system.
The computer (a Viewsonic VOT132) also has Ethernet and this box lives in my basement with other servers and an Ethernet switch.
Because it is wired Ethernet, I don't *need* WiFi to work.

**But, I am asking for help to better understand WiFi on Linux. How do I get WiFi connected to my network?**

I am pretty sure the WiFi hardware is working:

steve@sonic:~$[COLOR=#0000ff] rfkill list all[/COLOR]
> 0: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no

steve@sonic:~$ [COLOR=#0000ff]nmcli general[/COLOR]
> STATE      CONNECTIVITY  WIFI-HW  WIFI     WWAN-HW  WWAN
connected  full          enabled  enabled  enabled  enabled


steve@sonic:~$ [COLOR=#0000ff]nmcli dev wifi list[/COLOR]
> IN-USE  BSSID              SSID                           MODE   CHAN  RATE        SIGNAL  BARS  SECURITY
        22:C0:47:60:C0:43  Mann-Guest                     Infra  1     195 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA2
        20:C0:47:60:C0:42  Kaywinnet                      Infra  1     195 Mbit/s  55      &#9602;&#9604;__  WPA2
        42:37:86:87:92:34  --                             Infra  3     130 Mbit/s  44      &#9602;&#9604;__  WPA2
        42:37:86:B1:B8:3E  --                             Infra  3     130 Mbit/s  40      &#9602;&#9604;__  WPA2
        7E:D2:94:B4:8A:43  parammesh                      Infra  3     130 Mbit/s  40      &#9602;&#9604;__  WPA1 WPA2
        6C:CD:D6:EB:C2:77  --                             Infra  4     540 Mbit/s  39      &#9602;&#9604;__  WPA2
        72:CD:D6:EC:0C:7A  --                             Infra  4     540 Mbit/s  37      &#9602;&#9604;__  WPA2
        3C:37:86:B1:B8:3E  parammesh                      Infra  3     130 Mbit/s  35      &#9602;&#9604;__  WPA1 WPA2
        22:AD:56:2F:A6:03  HotspotA603                    Infra  1     65 Mbit/s   34      &#9602;&#9604;__  WPA1 WPA2
        6C:CD:D6:EC:0C:7A  w00t                           Infra  4     540 Mbit/s  34      &#9602;&#9604;__  WPA2
        72:CD:D6:EB:C2:77  w00t                           Infra  4     540 Mbit/s  34      &#9602;&#9604;__  WPA2
        72:F8:53:DC:BF:1E  MAY6GUEST                      Infra  11    540 Mbit/s  32      &#9602;&#9604;__  WPA2
        A0:04:60:76:5C:A6  NETGEAR30                      Infra  9     54 Mbit/s   30      &#9602;___  WPA2
        3E:94:ED:44:68:14  --                             Infra  9     130 Mbit/s  29      &#9602;___  WPA2
        38:94:ED:45:12:8D  --                             Infra  9     130 Mbit/s  27      &#9602;___  WPA2
        38:94:ED:44:68:14  Bob and Frank                  Infra  9     130 Mbit/s  27      &#9602;___  WPA2
        B8:F8:53:DC:BF:1D  PRANEEL                        Infra  11    540 Mbit/s  27      &#9602;___  WPA2
        3E:94:ED:45:12:29  Bob and Frank                  Infra  9     130 Mbit/s  24      &#9602;___  WPA2
        C8:D3:FF:FE:9B:B1  DIRECT-B0-HP ENVY 4520 series  Infra  3     65 Mbit/s   22      &#9602;___  WPA2
        38:94:ED:45:12:29  --                             Infra  9     130 Mbit/s  22      &#9602;___  WPA2
        9C:3D:CF:76:E3:68  NETGEAR79                      Infra  6     54 Mbit/s   19      &#9602;___  WPA2
        70:F2:20:43:BC:51  param                          Infra  11    130 Mbit/s  19      &#9602;___  WPA2
        10:78:5B:B5:BC:61  BRT                            Infra  1     130 Mbit/s  15      &#9602;___  WPA2


However, ifconfig doesn't show an IP address for WiFi the adapter:
steve@sonic:~$ [COLOR=#0000ff]ifconfig[/COLOR]
> enp5s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.81  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::d227:88ff:fe61:2153  prefixlen 64  scopeid 0x20<link>
        ether d0:27:88:61:21:53  txqueuelen 1000  (Ethernet)
        RX packets 1727325  bytes 2422729127 (2.4 GB)
        RX errors 0  dropped 910  overruns 0  frame 0
        TX packets 135535  bytes 12244557 (12.2 MB)
        TX errors 0  dropped 0 overruns 0  carrier 3  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 713  bytes 54248 (54.2 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 713  bytes 54248 (54.2 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


[COLOR=#ff0000]wlp6s0:[/COLOR] flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether ec:55:f9:1c:c2:b2  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

---

### Post by chili555 on 2021-10-21
Please check here: [https://askubuntu.com/questions/1164074/how-to-connect-to-wifi-using-just-the-terminal/1164095#1164095](https://askubuntu.com/questions/1164074/how-to-connect-to-wifi-using-just-the-terminal/1164095#1164095)

If requested, I can propose a permanent solution; that is, one that survives a reboot and connects automagically.

---

