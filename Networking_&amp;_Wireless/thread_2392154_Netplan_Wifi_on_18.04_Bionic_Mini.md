---
title: "Netplan Wifi on 18.04 Bionic Mini"
date: 2018-05-17
forum: Networking &amp; Wireless
---

### Post by Notsgnik on 2018-05-17
Hello  :),
Can somebody Nice help me out ?
 I no longer have wifi since I freshly reinstalled Ubuntu.
I followed the same steps as last time, using the following netplan configuration and it dosen't work 

```

network:
version: 2
  renderer: networkd
  ethernets:
    enp3s0:
      dhcp4: yes
      dhcp6: no
      gateway4: 192.168.0.1
      nameservers:
          addresses: [ [COLOR=#B8860B]1.1.1.1[/COLOR], [COLOR=#B8860B]8.8.8.8[/COLOR]]
  wifis:
    wlp3s0:
     dhcp4: yes
     dhcp6: no
     gateway4: 192.168.0.1
     nameservers:
          addresses: [ [COLOR=#B8860B]1.1.1.1[/COLOR], [COLOR=#B8860B]8.8.8.8[/COLOR]]
     access-points:
        [COLOR=#BB4444]"MY_HOME_ROOTER"[/COLOR]:
          password: [COLOR=#BB4444]"azerty1234"
[/COLOR]
```
( More detail here [https://paste.ubuntu.com/p/r4kt5w4QPV/](https://paste.ubuntu.com/p/r4kt5w4QPV/) )

Did i made a mistake somewhere?

---

### Post by chili555 on 2018-05-17
Spacing, indentation, etc. are crucial and must be exact. I believe your file should be: [https://paste.ubuntu.com/p/PBB7GkqPxb/](https://paste.ubuntu.com/p/PBB7GkqPxb/)

I should think that, if you get an address from the router by DHCP, the gateway address is included and needn't be explicitly declared here.

You can get some guidance from the example here:```
cat /usr/share/doc/netplan.io/examples/wireless.yaml 
```

---

### Post by Notsgnik on 2018-05-19
hello chili555,
i copied the wireless.yaml example and edited it accordingly, yet i still don't have wifi :/
maybe some package is missing?

---

### Post by chili555 on 2018-05-19
Did you follow with:```
sudo netplan apply
```What is the response to:```
sudo ip link set wlp3s0 down
sudo ip link set wlp3s0 up
ping -c3 192.168.0.1
```

---

### Post by Notsgnik on 2018-05-19
Yep chili555,
i dit : ```
netplan apply
``` and even the ```
ip link set iface up/down
``` yet, still:
```

$ ping -c3 192.168.0.1
connect: Network is unreachable

```
I even created a hotspot on my phone to try to connect to it and still nothing :/
i installed it using this tutorial: [https://gist.github.com/richardjuan/33db032a0dc4ae66f216436dd4ec3e5f](https://gist.github.com/richardjuan/33db032a0dc4ae66f216436dd4ec3e5f)

---

### Post by chili555 on 2018-05-19
Any clues in the logs?```
dmesg | grep -e wlp -e net
cat /var/log/syslog | grep -i net
```

---

### Post by Notsgnik on 2018-05-19
ah ah ! 
```

May 19 15:56:50 zePc systemd[21296]: netplan-wpa@wlp3s0.service: Failed to execute command: No such file or directory
May 19 15:56:50 zePc systemd[21296]: netplan-wpa@wlp3s0.service: Failed at step EXEC spawning /sbin/wpa_supplicant: No such file or directory

```
but i have to install wpagui?
```

$apt search wpa_supplicant
Sorting... Done
Full Text Search... Done
dhcpcd-gtk/bionic 0.7.5-0ubuntu2 amd64
  GTK+ frontend for dhcpcd and wpa_supplicant


dhcpcd-qt/bionic 0.7.5-0ubuntu2 amd64
  Qt frontend for dhcpcd and wpa_supplicant


wpagui/bionic 2:2.6-15ubuntu2 amd64
  graphical user interface for wpa_supplicant



```

---

### Post by chili555 on 2018-05-19
Perhaps your wireless interface is not wlp3s0. Check:```
iwconfig
```Is wpa_supplicant installed?```
sudo dpkg -s wpasupplicant
```As my brother often says, the thick plottens!

---

### Post by Notsgnik on 2018-05-19
It is thickening in deed chili555 :)
i did:
```

sudo apt install wpasupplicant

```
and now it still don't connect but i get this
```

ay 19 16:40:29 pc systemd-networkd[22911]: lo: Link is not managed by us
May 19 16:40:29 pc systemd-networkd[22911]: wlp3s0: IPv6 successfully enabled
May 19 16:40:29 pc systemd[1]: Started WPA supplicant for netplan wlp3s0.
May 19 16:40:29 pc networkd-dispatcher[19833]: WARNING:Unknown index 41 seen, reloading interface list
May 19 16:40:29 pc kernel: [18127.536530] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
May 19 16:40:34 pc wpa_supplicant[22922]: wlp3s0: CTRL-EVENT-SUBNET-STATUS-UPDATE status=0
May 19 16:40:54 pc wpa_supplicant[22922]: wlp3s0: CTRL-EVENT-SUBNET-STATUS-UPDATE status=0
May 19 16:41:28 pc wpa_supplicant[22922]: wlp3s0: CTRL-EVENT-SUBNET-STATUS-UPDATE status=0

```
and this:
```

[18331.342539] wlp3s0: authenticate with 00:fe:9e:fe:fe:fe
[18331.376728] wlp3s0: send auth to 00:fe:9e:fe:fe:fe (try 1/3)
[18331.378471] wlp3s0: authenticated
[18331.381417] wlp3s0: associate with 00:fe:9e:fe:fe:fe (try 1/3)
[18331.385183] wlp3s0: RX AssocResp from 00:fe:9e:fe:fe:fe (capab=0xc11 status=0 aid=1)
[18331.388589] wlp3s0: associated
[18336.982043] wlp3s0: deauthenticated from 00:fe:9e:fe:fe:fe (Reason: 2=PREV_AUTH_NOT_VALID)

```

---

### Post by chili555 on 2018-05-19
> wlp3s0: associate with 00:fe:9e:fe:fe:fe (try 1/3)
wlp3s0: RX AssocResp from 00:fe:9e:fe:fe:fe (capab=0xc11 status=0 aid=1)
wlp3s0: associated
wlp3s0: deauthenticated from 00:fe:9e:fe:fe:fe (Reason: 2=PREV_AUTH_NOT_VALID)So, it did connect for a moment or two but then dropped. There can be a few reasons for this and some of them are found in the router. May we see:```
sudo iwlist wlp3s0 scan
```We only need to see your own access point and please redact the MAC address loke this example:> Cell 01 - Address: [COLOR="#FF0000"]XXXX[/COLOR]
                    Channel:149
                    Frequency:5.745 GHz (Channel 149)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"GBR5"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000115e56b4dff
                    Extra: Last beacon: 648ms ago
                    IE: Unknown: 000447425235
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030195
                    IE: Unknown: 074255532024011E28011E2C011E30011E3401173801173C01174001176401176801176C01177001177401178401178801178C011795011E99011E9D011EA1011EA5011E
                    IE: Unknown: 200103
                    IE: Unknown: 2D1AEF091BFFFFFF0000000000000000000100000000000000000000
                    IE: Unknown: 3D16950D0400000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: Unknown: BF0CB2018033EAFF0000EAFF0000
                    IE: Unknown: C005019B00FCFF
                    IE: Unknown: C30402C4C4C4
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD8B0050F204104A0001101044000102103B00010310470010123456789ABCDEF01234A42BB0DC45861021000754502D4C494E4B1023000941726368657220433710240003322E3010420003312E301054000800060050F204000110110019576972656C65737320526F7574657220417263686572204337100800022008103C0001031049000600372A000120
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
If we see TKIP, I'm gonna scream.

---

### Post by Notsgnik on 2018-05-19
Here what i get
```

          Cell 02 - Address: 00:FE:9E:FE:FE:FE
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"HOME_BOX"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=XXX
                    Extra: Last beacon: 4596ms ago
                    IE: Unknown: XXX
                    IE: Unknown: XXX
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: XXX

```
I tried to change to WPA1/2 TKIP/AES. I also removed the "802.11n" capabilitie and still nothing.
maybe it's the driver?

---

### Post by chili555 on 2018-05-19
Please check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

If there is little or no improvement, we'll start looking at the driver.

For the benefit of the searchers, here is a great thread about auto channel select and why it is a terrible idea: [https://superuser.com/questions/1311149/why-do-wifi-routers-do-such-a-bad-job-of-channel-selection](https://superuser.com/questions/1311149/why-do-wifi-routers-do-such-a-bad-job-of-channel-selection)

---

### Post by Notsgnik on 2018-05-20
i've tried it all :/
maybe with an other distro or ubuntu 16.04 :/

---

### Post by chili555 on 2018-05-20
Remember I said:> If there is little or no improvement, we'll start looking at the driver.Let's have a look, then. Please run and post the result of:```
lspci -nnk | grep 0280 -A3
```

---

### Post by Notsgnik on 2018-05-21
thanks for your help chili555, your a nice guy :)
here the output you asked :p
```

03:00.0 Network controller [0280]: Qualcomm Atheros QCA9377 802.11ac Wireless Network Adapter [168c:0042] (rev 31)
        Subsystem: Lite-On Communications Inc QCA9377 802.11ac Wireless Network Adapter [11ad:08a6]
        Kernel driver in use: ath10k_pci
        Kernel modules: ath10k_pci

```

btw: i've tried with 2 other wifi cards. it still dosn't work but they are alfa wifi card plus i get wierd names.
```

ls /sys/class/net/
enp4s0f1  lo  lxcbr0  wlp3s0  wlx0087252a15d8  wlx00c0ca96238d

```

---

### Post by chili555 on 2018-05-21
May I assume you are running Ubuntu 18.04 and therefore have the latest firmware?```
sudo dpkg -s linux-firmware | grep Version
```We hope we see Version: 1.173.

Are there any clues in the log?```
dmesg | grep -e wlp -e ath
```

---

### Post by Notsgnik on 2018-05-22
hello chili555 :)
yep it's 1.173 in deed. the logs output this:
```

[115304.189980] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/cal-pci-0000:03:00.0.bin failed with error -2
[115304.189990] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/firmware-6.bin failed with error -2
[115304.190342] ath10k_pci 0000:03:00.0: qca9377 hw1.1 target 0x05020001 chip_id 0x003821ff sub 11ad:08a6
[115304.190345] ath10k_pci 0000:03:00.0: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[115304.191221] ath10k_pci 0000:03:00.0: firmware ver WLAN.TF.1.0-00002-QCATFSWPZ-5 api 5 features ignore-otp crc32 c3e0d04f
[115304.253167] ath10k_pci 0000:03:00.0: board_file api 2 bmi_id N/A crc32 8aedfa4a
[115304.874251] ath10k_pci 0000:03:00.0: htt-ver 3.44 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1
[115304.880854] ath: EEPROM regdomain: 0x69
[115304.880855] ath: EEPROM indicates we should expect a direct regpair map
[115304.880856] ath: Country alpha2 being used: 00
[115304.880856] ath: Regpair used: 0x69
[115304.883314] ath10k_pci 0000:03:00.0 wlp3s0: renamed from wlan0

```

i installed a regular ubuntu 18.04 and i get a working wifi. i guess it's yet an other missing package :/

---

### Post by chili555 on 2018-05-22
> i installed a regular ubuntu 18.04 and i get a working wifi. i guess it's yet an other missing package :/
No doubt it is Network Manager which won't run in a server, usually headless. Does it get the same IP address family, gateway, etc.?

Can you please paste your yaml file again so we can proofread it?

Is there any error, warning or otherwise if you do:```
sudo netplan apply
sudo ip link set wlp3s0 down
sudo ip link set wlp3s0 up
```Your firmware load looks entirely normal.

---

### Post by Notsgnik on 2018-05-23
hello chili555,
i just reinstalled my ubuntu following this tutorial: [https://gist.github.com/richardjuan/33db032a0dc4ae66f216436dd4ec3e5f](https://gist.github.com/richardjuan/33db032a0dc4ae66f216436dd4ec3e5f)
I had no internet until i installed the Nvidia drivers. now i have a working wifi.
it must be one of the installed package who fixed the issue.
```

2018-05-23 14:39:28 install gcc-8-base:i386 <none> 8-20180414-1ubuntu2
2018-05-23 14:39:29 install libgcc1:i386 <none> 1:8-20180414-1ubuntu2
2018-05-23 14:39:31 install libc6:i386 <none> 2.27-3ubuntu1
2018-05-23 14:39:32 install libxau6:i386 <none> 1:1.0.8-1
2018-05-23 14:39:33 install libbsd0:i386 <none> 0.8.7-1
2018-05-23 14:39:34 install libxdmcp6:i386 <none> 1:1.1.2-3
2018-05-23 14:39:34 install libxcb1:i386 <none> 1.13-1
2018-05-23 14:39:35 install libx11-6:i386 <none> 2:1.6.4-3
2018-05-23 14:39:37 install libxext6:i386 <none> 2:1.3.3-1
2018-05-23 14:39:37 install binutils-common:amd64 <none> 2.30-15ubuntu1
2018-05-23 14:39:38 install libbinutils:amd64 <none> 2.30-15ubuntu1
2018-05-23 14:39:39 install binutils-x86-64-linux-gnu:amd64 <none> 2.30-15ubuntu1
2018-05-23 14:39:40 install binutils:amd64 <none> 2.30-15ubuntu1
2018-05-23 14:39:41 install libc-dev-bin:amd64 <none> 2.27-3ubuntu1
2018-05-23 14:39:41 install linux-libc-dev:amd64 <none> 4.15.0-22.24
2018-05-23 14:39:43 install libc6-dev:amd64 <none> 2.27-3ubuntu1
2018-05-23 14:39:48 install libcc1-0:amd64 <none> 8-20180414-1ubuntu2
2018-05-23 14:39:48 install libitm1:amd64 <none> 8-20180414-1ubuntu2
2018-05-23 14:39:49 install libatomic1:amd64 <none> 8-20180414-1ubuntu2
2018-05-23 14:39:50 install libasan4:amd64 <none> 7.3.0-16ubuntu3
2018-05-23 14:39:51 install liblsan0:amd64 <none> 8-20180414-1ubuntu2
2018-05-23 14:39:51 install libtsan0:amd64 <none> 8-20180414-1ubuntu2
2018-05-23 14:39:52 install libubsan0:amd64 <none> 7.3.0-16ubuntu3
2018-05-23 14:39:53 install libcilkrts5:amd64 <none> 7.3.0-16ubuntu3
2018-05-23 14:39:54 install libmpx2:amd64 <none> 8-20180414-1ubuntu2
2018-05-23 14:39:54 install libquadmath0:amd64 <none> 8-20180414-1ubuntu2
2018-05-23 14:39:55 install libgcc-7-dev:amd64 <none> 7.3.0-16ubuntu3
2018-05-23 14:39:58 install gcc-7:amd64 <none> 7.3.0-16ubuntu3
2018-05-23 14:40:04 install gcc:amd64 <none> 4:7.3.0-3ubuntu2
2018-05-23 14:40:04 install libstdc++-7-dev:amd64 <none> 7.3.0-16ubuntu3
2018-05-23 14:40:06 install g++-7:amd64 <none> 7.3.0-16ubuntu3
2018-05-23 14:40:16 install g++:amd64 <none> 4:7.3.0-3ubuntu2
2018-05-23 14:40:17 install make:amd64 <none> 4.1-9.1ubuntu1
2018-05-23 14:40:17 install libdpkg-perl:all <none> 1.19.0.5ubuntu2
2018-05-23 14:40:18 install patch:amd64 <none> 2.7.6-2ubuntu1
2018-05-23 14:40:18 install dpkg-dev:all <none> 1.19.0.5ubuntu2
2018-05-23 14:40:19 install build-essential:amd64 <none> 12.4ubuntu1
2018-05-23 14:40:20 install dkms:all <none> 2.3-3ubuntu9
2018-05-23 14:40:21 install libfakeroot:amd64 <none> 1.22-2ubuntu1
2018-05-23 14:40:21 install fakeroot:amd64 <none> 1.22-2ubuntu1
2018-05-23 14:40:22 install libalgorithm-diff-perl:all <none> 1.19.03-1
2018-05-23 14:40:22 install libalgorithm-diff-xs-perl:amd64 <none> 0.04-5
2018-05-23 14:40:23 install libalgorithm-merge-perl:all <none> 0.08-3
2018-05-23 14:40:23 install libfile-fcntllock-perl:amd64 <none> 0.22-3build2
2018-05-23 14:40:24 install libjansson4:amd64 <none> 2.11-1
2018-05-23 14:40:24 install libnvidia-cfg1-396:amd64 <none> 396.24-0ubuntu0~gpu18.04.1
2018-05-23 14:40:25 install libnvidia-common-396:all <none> 396.24-0ubuntu0~gpu18.04.1
2018-05-23 14:40:26 install libnvidia-compute-396:i386 <none> 396.24-0ubuntu0~gpu18.04.1
2018-05-23 14:40:34 install libnvidia-compute-396:amd64 <none> 396.24-0ubuntu0~gpu18.04.1
2018-05-23 14:40:37 install libnvidia-decode-396:i386 <none> 396.24-0ubuntu0~gpu18.04.1
2018-05-23 14:40:39 install libnvidia-decode-396:amd64 <none> 396.24-0ubuntu0~gpu18.04.1
2018-05-23 14:40:40 install libnvidia-encode-396:amd64 <none> 396.24-0ubuntu0~gpu18.04.1
2018-05-23 14:40:40 install libnvidia-encode-396:i386 <none> 396.24-0ubuntu0~gpu18.04.1
2018-05-23 14:40:41 install libglvnd0:i386 <none> 1.0.0-2ubuntu2
2018-05-23 14:40:42 install libnvidia-gl-396:i386 <none> 396.24-0ubuntu0~gpu18.04.1
2018-05-23 14:40:46 install libglx0:i386 <none> 1.0.0-2ubuntu2
2018-05-23 14:40:46 install libgl1:i386 <none> 1.0.0-2ubuntu2
2018-05-23 14:40:47 install libnvidia-fbc1-396:i386 <none> 396.24-0ubuntu0~gpu18.04.1
2018-05-23 14:40:48 install libnvidia-fbc1-396:amd64 <none> 396.24-0ubuntu0~gpu18.04.1
2018-05-23 14:40:48 install libnvidia-gl-396:amd64 <none> 396.24-0ubuntu0~gpu18.04.1
2018-05-23 14:41:12 install libnvidia-ifr1-396:amd64 <none> 396.24-0ubuntu0~gpu18.04.1
2018-05-23 14:41:12 install libnvidia-ifr1-396:i386 <none> 396.24-0ubuntu0~gpu18.04.1
2018-05-23 14:41:13 install libvdpau1:amd64 <none> 1.1.1-3ubuntu1
2018-05-23 14:41:14 install libxnvctrl0:amd64 <none> 396.24-0ubuntu0~gpu18.04.1
2018-05-23 14:41:14 install manpages-dev:all <none> 4.15-1
2018-05-23 14:41:17 install mesa-vdpau-drivers:amd64 <none> 18.0.0~rc5-1ubuntu1
2018-05-23 14:41:18 install nvidia-compute-utils-396:amd64 <none> 396.24-0ubuntu0~gpu18.04.1
2018-05-23 14:41:19 install nvidia-kernel-source-396:amd64 <none> 396.24-0ubuntu0~gpu18.04.1
2018-05-23 14:41:24 install nvidia-kernel-common-396:amd64 <none> 396.24-0ubuntu0~gpu18.04.1
2018-05-23 14:41:24 install nvidia-dkms-396:amd64 <none> 396.24-0ubuntu0~gpu18.04.1
2018-05-23 14:41:25 install nvidia-utils-396:amd64 <none> 396.24-0ubuntu0~gpu18.04.1
2018-05-23 14:41:25 install xserver-xorg-video-nvidia-396:amd64 <none> 396.24-0ubuntu0~gpu18.04.1
2018-05-23 14:41:26 install nvidia-driver-396:amd64 <none> 396.24-0ubuntu0~gpu18.04.1
2018-05-23 14:41:27 install nvidia-prime:all <none> 0.8.8
2018-05-23 14:41:27 install pkg-config:amd64 <none> 0.29.1-0ubuntu2
2018-05-23 14:41:28 install policykit-1-gnome:amd64 <none> 0.105-6ubuntu2
2018-05-23 14:41:28 install screen-resolution-extra:all <none> 0.17.3
2018-05-23 14:41:29 install nvidia-settings:amd64 <none> 396.24-0ubuntu0~gpu18.04.1
2018-05-23 14:41:30 install vdpau-driver-all:amd64 <none> 1.1.1-3ubuntu1

```

---

### Post by chili555 on 2018-05-23
Glad it's working by whatever means! Please use thread tools at the top to mark Solved.

---

### Post by Notsgnik on 2018-05-23
Is it solved if we say to the future Ubuntu userser the following? 

> "in order to fix the wifi, just install the nvidia drivers ;)"

plus, for now i don't have the 3D rendering and it is yet an other issue to solve :/

---

### Post by chili555 on 2018-05-23
It is solved, in my opinion, because, assuming that the remainder of your system is in order, the yaml file I recommended above works as expected.

---

### Post by Notsgnik on 2018-05-23
hey, I didn't edit the yaml file since day one, i'm still following the tutorial.

Plus... I don't think that you are the kind of guy who just want points on a forum...
If all I wanted was to solve my problem i'll have went to IRC instead.
Forums are databases of solutions and contributors matters for everyone.

We both want to help the Ubuntu community, chili555.
Come on, we narrowed it to "wpasuplicant" and a butch of packets from nvidia-driver dependencies 
We are almost there, plus it's meant to last since it's an LTS :)

---

### Post by chili555 on 2018-05-23
> hey, I didn't edit the yaml file since day one,I see. You came on this forum to ask for help. I pointed out what I believed to be a spacing error and suggested that you correct it. You didn't change it at all and then come back to complain that it still doesn't work. Is that it? > If all I wanted was to solve my problem i'll have went to IRC instead.I see. You posted a question on this forum expecting to *NOT* solve your problem?? 

Lovely.

---

### Post by Notsgnik on 2018-05-23
Wow, there is a big misunderstanding!!!

It's probably because of my English. i'm sorry...

I wanned to say that i just installed a fresh Ubuntu following yet again my tutorial ( eg:  [https://gist.github.com/richardjuan/33db032a0dc4ae66f216436dd4ec3e5f ]("https://gist.github.com/richardjuan/33db032a0dc4ae66f216436dd4ec3e5f") )

So it's the exact _same yaml_ since day one, the _only thing that changed_ in the installation was _**the addition of wpasuppliant packet, thanks to you**_...

Now: I had no wifi. I installed the Nvidia driver, rebooted and miracle wifi is working. 
We also know that it's not about the Nvidia drivers, since a fresh install of Ubuntu Desktop have wifi too.

Also, you are way better than me at looking where the problem can come from and i'm doing this tutorial .
I thought that we where both helping the community with this thread.

I'm sorry yet again for my English :/

---

### Post by wildmanne39 on 2018-05-23
Hello Notsgnik, we have a one issue per thread rule here so when people are looking for a solution to a certain issue the title of the thread is actually what the thread is about, so if you want help with an issue other then wifi you need to create a thread in the proper sub-forum with a descriptive title please and I am not so sure that this is the best approach to creating a tutorial, take it from someone who knows just because what works for you in setting up a minimal install does not mean it will work for the next person because there are so many different configurations of computers in the real world.

I do not believe that github is designed to be used for tutorials, it would be best to put a tutorial on a blog of your own.

No, installing the nividia drivers is not what made your wifi work.

---

### Post by Notsgnik on 2018-05-23
```
On a minimal Ubuntu the wifi configuration using netplan dosen't work out of the box.

```
The only thread talking about it on internet looks to be this one, if the _solution to that problem_ is to _install the wpasuppliant and nvidia-drivers packets._ 

**So be it **i don't care... **it's a community** you are better suited than me to decide.

```

sudo apt install wpasupplicant 
sudo ubuntu-drivers autoinstall

```
(cause one of the dependencies fix the issue but we let you the pleasure to figure it out if you don't want the nvidia drivers, we have a forum and a free operating system, don't ask us for too much :p )
should I put solved then?

---

### Post by wildmanne39 on 2018-05-23
Yes please mark the thread solved.

---

### Post by dony71 on 2019-02-25
anybody can help me how to configure wifi with wpa enterprise?
I follow this example below but get error message
Error in network definition /etc/netplan/50-cloud-init.yaml: unknown key auth
[https://netplan.io/examples](https://netplan.io/examples)

---

### Post by shpyduck7 on 2019-02-25
Hello: I tried this and many others but nothing works!  I have an HP 9000dv pavilion laptop and the wireless is Broadcom BCM431180 2.11b/g/m WLAN [14e4:4311] rev 01 
I sure would appreciate it if you could help me fix my wireless. I am new to Ubuntu/Linux but so far like it and learning a lot., Thanks for any help.  Jerryb

---

### Post by wildmanne39 on 2019-02-25
Hello dony71, please start your own thread instead of posting in an old solved thread that way you can get the help you need.

Thanks

Old thread closed!

---

