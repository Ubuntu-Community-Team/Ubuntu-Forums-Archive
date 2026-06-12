---
title: "WiFi not working on Ubuntu 18 fresh installation | Intel Dual Band Wireless-AC 3165"
date: 2019-03-14
forum: Networking &amp; Wireless
---

### Post by algod25 on 2019-03-14
[COLOR=#000000][INDENT]Hi,
I've just updated Ubuntu 18 on my Lenovo ideapad 520 alongside Windows 10. Before the update WiFi has worked perfectly fine, but after reboot there were no avaiable wifi connections. In settings there is a sign, that wifi's adapters were not found, so i cannot even turn it on/off. I tried to use this solution [https://ubuntuforums.org/showthread.php?t=2382682](https://ubuntuforums.org/showthread.php?t=2382682) and this one: [https://codeyarns.com/2017/02/04/how-to-make-intel-wireless-ac-3165-work-in-ubuntu/](https://codeyarns.com/2017/02/04/how-to-make-intel-wireless-ac-3165-work-in-ubuntu/) but it had no sense at all. Here is some commands:
```

dmesg | grep iwl
[   21.718957] iwlwifi 0000:03:00.0: loaded firmware version 29.1044073957.0 op_mode iwlmvm
[   21.959292] iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 3165, REV=0x210
[   22.062829] iwlwifi 0000:03:00.0: base HW address: ac:ed:5c:74:fd:f1
[   22.149361] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   22.155051] iwlwifi 0000:03:00.0 wlp3s0: renamed from wlan0
[  190.123879] iwlwifi 0000:03:00.0: RF_KILL bit toggled to enable radio.

rfkill list all
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no



uname -a
Linux computer 4.18.0-16-generic #17~18.04.1-Ubuntu SMP Tue Feb 12 13:35:51 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

lspci | grep Network
03:00.0 Network controller: Intel Corporation Dual Band Wireless-AC 3165 Plus Bluetooth (rev 99)

ifconfig
enp0s20f0u3c4i2: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 172.20.10.2  netmask 255.255.255.240  broadcast 172.20.10.15
        inet6 fe80::d5e5:c7fa:3310:9835  prefixlen 64  scopeid 0x20<link>
        ether 2e:f0:a2:28:d7:91  txqueuelen 1000  (Ethernet)
        RX packets 71114  bytes 82797976 (82.7 MB)
        RX errors 0  dropped 1  overruns 0  frame 0
        TX packets 44041  bytes 6120621 (6.1 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


enp2s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 54:e1:ad:49:97:37  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (&#1051;&#1086;&#1082;&#1072;&#1083;&#1100;&#1085;&#1072;&#1103; &#1087;&#1077;&#1090;&#1083;&#1103; (Loopback))
        RX packets 2669  bytes 269061 (269.0 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2669  bytes 269061 (269.0 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

I don't know what can I do to make wifi work. Could you help me?





[/INDENT]
[/COLOR]

---

