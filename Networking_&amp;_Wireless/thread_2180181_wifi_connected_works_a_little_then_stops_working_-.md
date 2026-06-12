---
title: "wifi connected works a little then stops working - ubuntu 12.04"
date: 2013-10-11
forum: Networking &amp; Wireless
---

### Post by doulos2 on 2013-10-11
I've followed other threads, and the system has a Realtek 8188cus driver installed.
Nothing in the system is black listed.
The system seems to connect to the wireless router at boot (static IP), but Firefox can't find any server.
If you disconnect the wireless and then connect, Firefox will work at least for a little while.
The same scenario is true for Update Manager.
Note:  At the bottom - I can ping localhost and my IP, but I can't ping the router.

_**lspci -nnk | grep -iA2 net**_
01:0d.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: ASUSTeK Computer Inc. P5P800-MX Mainboard [1043:8109]
    Kernel driver in use: 8139too

_**lsusb**_
Bus 001 Device 004: ID 0846:9041 NetGear, Inc. WNA1000M 802.11bgn [Realtek RTL8188CUS]
Bus 002 Device 002: ID 03f0:010c Hewlett-Packard Multimedia Keyboard Hub
Bus 002 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 004 Device 002: ID 0a48:3239 I/O Interconnect Multimedia Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 03f0:020c Hewlett-Packard Multimedia Keyboard

_**nm-tool**_
NetworkManager Tool

State: connected (global)

- Device: wlan0  [gracioustest] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             connected
  Default:           yes
  HW Address:        10:0D:7F:C0:7E:39

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *gracioustest:   Infra, C8:D7:19:E5:76:91, Freq 2437 MHz, Rate 54 Mb/s, Strength 79 WPA WPA2

  IPv4 Settings:
    Address:         192.168.2.20
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             unavailable
  Default:           no
  HW Address:        00:11:2F:E9:AD:1A

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

_**lshw -C network**_
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: d
       bus info: pci@0000:01:0d.0
       logical name: eth0
       version: 10
       serial: 00:11:2f:e9:ad:1a
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:17 ioport:c000(size=256) memory:ec000000-ec0000ff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:5
       logical name: wlan0
       serial: 10:0d:7f:c0:7e:39
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu driverversion=3.5.0-41-generic firmware=N/A ip=192.168.2.20 link=yes multicast=yes wireless=IEEE 802.11bgn


_**ifconfig -a**_
eth0      Link encap:Ethernet  HWaddr 00:11:2f:e9:ad:1a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1002 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1002 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:95946 (95.9 KB)  TX bytes:95946 (95.9 KB)

wlan0     Link encap:Ethernet  HWaddr 10:0d:7f:c0:7e:39  
          inet addr:192.168.2.20  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::120d:7fff:fec0:7e39/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5748 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3069 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6713602 (6.7 MB)  TX bytes:394744 (394.7 KB)

_**lsmod | egrep "rt|81"**_
snd_mpu401_uart        13866  3 snd_wavefront,snd_cs4236,snd_mpu401
rtl8192cu              67480  0 
rtl8192c_common        47696  1 rtl8192cu
rtlwifi                65304  1 rtl8192cu
snd_rawmidi            25426  3 snd_wavefront,snd_mpu401_uart,snd_seq_midi
rfcomm                 38104  0 
mac80211              475546  3 rtl8192cu,rtl8192c_common,rtlwifi
cfg80211              181041  2 rtlwifi,mac80211
snd_pcm                81124  4 snd_cs4236,snd_wss_lib,snd_intel8x0,snd_ac97_codec
snd                    62675  18 snd_wavefront,snd_cs4236,snd_wss_lib,snd_opl3_lib,snd_hwdep,snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_intel8x0,snd_ac97_codec,snd_seq_device,snd_pcm,snd_timer
gameport               15089  2 ns558
parport_pc             32115  1 
parport                40931  3 ppdev,parport_pc,lp
8139too                23312  0 
8139cp                 26719  0 

_**iwconfig**_
wlan0     IEEE 802.11bgn  ESSID:"gracioustest"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: C8:D7:19:E5:76:91   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.

_**iwlist scan**_
wlan0     Scan completed :
          Cell 01 - Address: C8:D7:19:E5:76:91
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"gracioustest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000021f08a9a184
                    Extra: Last beacon: 612ms ago
                    IE: Unknown: 000C67726163696F757374657374
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 0B0501000A0000
                    IE: Unknown: 2D1AAD1817FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001300000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080100080000000040
                    IE: Unknown: DD090010180201001C0000
                    IE: WPA Version 1lsmod | egrep "rt|81"

snd_mpu401_uart        13866  3 snd_wavefront,snd_cs4236,snd_mpu401
rtl8192cu              67480  0 
rtl8192c_common        47696  1 rtl8192cu
rtlwifi                65304  1 rtl8192cu
snd_rawmidi            25426  3 snd_wavefront,snd_mpu401_uart,snd_seq_midi
rfcomm                 38104  0 
mac80211              475546  3 rtl8192cu,rtl8192c_common,rtlwifi
cfg80211              181041  2 rtlwifi,mac80211
snd_pcm                81124  4 snd_cs4236,snd_wss_lib,snd_intel8x0,snd_ac97_codec
snd                    62675  18 snd_wavefront,snd_cs4236,snd_wss_lib,snd_opl3_lib,snd_hwdep,snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_intel8x0,snd_ac97_codec,snd_seq_device,snd_pcm,snd_timer
gameport               15089  2 ns558
parport_pc             32115  1 
parport                40931  3 ppdev,parport_pc,lp
8139too                23312  0 
8139cp                 26719  0 

_**rfkill list**_
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

_**ping -c 4 127.0.0.1**_
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_req=1 ttl=64 time=0.061 ms
64 bytes from 127.0.0.1: icmp_req=2 ttl=64 time=0.048 ms
64 bytes from 127.0.0.1: icmp_req=3 ttl=64 time=0.047 ms
64 bytes from 127.0.0.1: icmp_req=4 ttl=64 time=0.055 ms

--- 127.0.0.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2999ms
rtt min/avg/max/mdev = 0.047/0.052/0.061/0.010 ms

_**ping -c 4 192.168.2.20**_
PING 192.168.2.20 (192.168.2.20) 56(84) bytes of data.
64 bytes from 192.168.2.20: icmp_req=1 ttl=64 time=0.064 ms
64 bytes from 192.168.2.20: icmp_req=2 ttl=64 time=0.048 ms
64 bytes from 192.168.2.20: icmp_req=3 ttl=64 time=0.059 ms
64 bytes from 192.168.2.20: icmp_req=4 ttl=64 time=0.051 ms

--- 192.168.2.20 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2998ms
rtt min/avg/max/mdev = 0.048/0.055/0.064/0.009 ms

_**ping -c 4 192.168.2.1**_
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.

--- 192.168.2.1 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3022ms

---

### Post by praseodym on 2013-10-12
Hi,

update the driver and add the USB-Id to it according to:

```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms  
wget https://realtek-8188cus-wireless-drivers-3444749-ubuntu-1304.googlecode.com/files/rtl8192cu-tjp-dkms_1.6_all.deb
sudo dpkg -i rtl8192cu-tjp-dkms_1.6_all.deb
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
echo 'install 8192cu modprobe --ignore-install 8192cu ; /bin/echo "0846 9041" > /sys/bus/usb/drivers/rtl8192cu/new_id' | sudo tee /etc/modprobe.d/8192cu.conf
```
Reboot.

---

### Post by doulos2 on 2013-10-12
I did as you recommended, even though I doubted it would work.
When I did it again I get no wireless:
Wireless shows disconnected on boot, and there is no wireless entry at all in the network applet.
Additionally, there is no light on the Netgear USB adapter.
BTW - everything about the site for the deb say 1304 and kernel 3.8 or 3.9.  I'm on 12.04 with kernel 3.5.

---

### Post by doulos2 on 2013-10-12
I put the realtek build driver back in place and removed the two changes to /etc/modprobe.d.
Wifi is again working, albeit with the disconnects.
Subsequently, I made the wifi tools that come with the driver, and I've been running iwevent and watching.
Every 2 minutes, it reports wlan scan completed.
It seems that my ping to the router failing may be associated with these scans.  
Sometimes the ping works, and sometimes the router is unreachable.

---

### Post by praseodym on 2013-10-13
Did you try the driver as explained? I know it also works with kernel 3.5.

---

