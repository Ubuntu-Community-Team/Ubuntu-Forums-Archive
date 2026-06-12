---
title: "Ubuntu 12.04 - WiFi connected but no internet"
date: 2014-02-20
forum: Networking &amp; Wireless
---

### Post by sam32 on 2014-02-20
I recently install Ubuntu 12.04 and am having some trouble with the wireless. It shows that I'm connected, but I can only access the internet intermittantly. I've looked at 

[http://www.linuxquestions.org/questions/linux-newbie-8/ubuntu-12-04-upgrade-can-connect-to-wifi-but-no-internet-connection-4175416315/](http://www.linuxquestions.org/questions/linux-newbie-8/ubuntu-12-04-upgrade-can-connect-to-wifi-but-no-internet-connection-4175416315/)
[http://ubuntuforums.org/showthread.php?t=1985079](http://ubuntuforums.org/showthread.php?t=1985079)
[http://askubuntu.com/questions/318555/wifi-is-connected-but-no-internet-access-ubuntu-12-04-lts](http://askubuntu.com/questions/318555/wifi-is-connected-but-no-internet-access-ubuntu-12-04-lts)

but none of those solutions have worked for me. The wireless card is an Intel Centrino Advanced-N 6235.

ifconfig
```

eth0      Link encap:Ethernet  HWaddr f0:bf:97:dc:84:f7  
          inet addr:192.168.0.9  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::f2bf:97ff:fedc:84f7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2667223 errors:0 dropped:0 overruns:0 frame:0
          TX packets:639438 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3970576127 (3.9 GB)  TX bytes:50238357 (50.2 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:18294 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18294 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1889879 (1.8 MB)  TX bytes:1889879 (1.8 MB)

wlan0     Link encap:Ethernet  HWaddr b4:b6:76:18:c1:08  
          inet addr:192.168.0.28  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::b6b6:76ff:fe18:c108/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21026 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2775 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4578414 (4.5 MB)  TX bytes:517131 (517.1 KB)

```

iwconfig
```

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"SBG658062"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 1C:C6:3C:44:6B:B7   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=52/70  Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:52   Missed beacon:0

```

lshw -C network
```
  
*-network               
       description: Wireless interface
       product: Centrino Advanced-N 6235
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 24
       serial: b4:b6:76:18:c1:08
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.11.0-17-generic firmware=18.168.6.1 ip=192.168.0.28 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:46 memory:b7000000-b7001fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 07
       serial: f0:bf:97:dc:84:f7
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.0.9 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:43 ioport:3000(size=256) memory:b5004000-b5004fff memory:b5000000-b5003fff

```

iwlist scan
```

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 1C:C6:3C:44:6B:B7
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"SBG658062"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000e50fe480
                    Extra: Last beacon: 29744ms ago
                    IE: Unknown: 0009534247363538303632
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: DD830050F204104A0001101044000102103B00010310470010E443B645067CAA9E9871C250C2396A0D102100084D6F746F726F6C61102300084D6F746F726F6C611024000631323334353610420007303030303030311054000800060050F20400011011000A4D6F746F726F6C614150100800022008103C0001011049000600372A000120
                    IE: Unknown: DD090010180207F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

```


Sorry if this is too much/the wrong info, I figured more is better than less.

---

### Post by varunendra on 2014-02-21
Welcome to Ubuntu Forums sam32 !

Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates. The information you have posted covers quite some useful information, but the wireless_script report covers a lot more and it is easier to get all that info in one go if we needed the same after trying a few things.

Apart from the above report, please also post back the output of -
```
grep [[:alnum:]] /sys/module/iwl*/parameters/*
```

---

### Post by sam32 on 2014-02-21
Attached is a copy of the report generated by running the script.

grep [[:alnum:]] /sys/module/iwl*/parameters/*
```

/sys/module/iwlwifi/parameters/11n_disable:0
/sys/module/iwlwifi/parameters/amsdu_size_8K:0
/sys/module/iwlwifi/parameters/antenna_coupling:0
/sys/module/iwlwifi/parameters/bt_coex_active:Y
/sys/module/iwlwifi/parameters/fw_restart:Y
/sys/module/iwlwifi/parameters/led_mode:0
/sys/module/iwlwifi/parameters/nvm_file:(null)
/sys/module/iwlwifi/parameters/power_level:0
/sys/module/iwlwifi/parameters/power_save:N
/sys/module/iwlwifi/parameters/swcrypto:0
/sys/module/iwlwifi/parameters/wd_disable:1

```


Thank you very much for your reply, I hope we're able to get this problem sorted out!

---

### Post by varunendra on 2014-02-21
Please try this in a terminal, with the cable connection unplugged -
```
echo "options iwlwifi 11n_disable=1" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rv iwldvm
sudo modprobe -v iwldvm
```
Does it connect now? After a reboot without the cable connection?

If not, please run the script again, with the Ethernet cable unplugged this time, and post back the same report + the command output as in your above post.

---

### Post by sam32 on 2014-02-22
That did not fix the problem, so here is the requested information, this time run with the ethernet cable unplugged.

grep [[:alnum:]] /sys/module/iwl*/parameters/*
```

/sys/module/iwlwifi/parameters/11n_disable:1
/sys/module/iwlwifi/parameters/amsdu_size_8K:0
/sys/module/iwlwifi/parameters/antenna_coupling:0
/sys/module/iwlwifi/parameters/bt_coex_active:Y
/sys/module/iwlwifi/parameters/fw_restart:Y
/sys/module/iwlwifi/parameters/led_mode:0
/sys/module/iwlwifi/parameters/nvm_file:(null)
/sys/module/iwlwifi/parameters/power_level:0
/sys/module/iwlwifi/parameters/power_save:N
/sys/module/iwlwifi/parameters/swcrypto:0
/sys/module/iwlwifi/parameters/wd_disable:1
```
[ATTACH]250580[/ATTACH]

---

### Post by varunendra on 2014-02-24
> **sam32 said:**
> That did not fix the problem, so here is the requested information, this time run with the ethernet cable unplugged.

The attached report is the same one that you posted earlier. Please delete that file and run the script again (with the cable unplugged), then post back the new report. :)

---

### Post by sam32 on 2014-02-24
Sorry about that. Here is a new report

---

### Post by varunendra on 2014-02-24
Everything looks great, however, you don't seem to have the DNS defined. Assuming you are using DHCP, not a manually configured IP, please try this -

In the "IPv4 Settings" tab for your wifi connection in Network Manager, choose the 'Method' to be "Automatic (DHCP) address only". Then in the 'DNS servers' field, enter these addresses (Google's DNS servers) :

**8.8.8.8, 8.8.4.4**

Save and close the settings. Now try to browse and if needed, Disconnect > Reconnect to the network.

Hope that is the only thing we need now.

By the way, if you are using DHCP, either DNS is not configured properly in it or DHCP is not working properly.

---

### Post by sam32 on 2014-02-25
It looks like that solved it. Thank you very much for your help!

---

### Post by varunendra on 2014-02-25
You're welcome! :)

---

