---
title: "Wireless network scan fails"
date: 2017-05-16
forum: Networking &amp; Wireless
---

### Post by fakeacct843954 on 2017-05-16
Hello all,


I am having difficulty detecting wireless networks on my Linux system:


```
>> iwlist wlo1 scan
wlo1      No scan results
```


Unfortunately, this has come to the point where I am willing to throw whatever I can at the problem! Please let me know if you have any suggestions at all about how to fix it. I wish that I could reinstall the OS from CD, but the OS download is blocked by a firewall at my only wired access point. (I am also concerned that a number of important updates are similarly blocked.)


Potentially relevant information, together with my attempts to resolve the issue:


```
>> sudo apt-get update
>> sudo apt-get upgrade

```


```
>> nmcli dev
DEVICE           TYPE      STATE         CONNECTION         
enxe8802ee78a2e  ethernet  connected     Wired connection 1 
wlo1             wifi      disconnected  --                 
eno1             ethernet  unavailable   --                 
lo               loopback  unmanaged     --                 
```


(The commented lines below resulted from a failed attempt to resolve this.)
```
>> cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


# Wireless
#auto wlo1
#iface wlo1 inet dhcp
```


```
>> rfkill list all
0: hci0: Bluetooth
        Soft blocked: yes
        Hard blocked: no
2: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
```


```
>> sudo lshw -C network
  *-network                 
       description: Ethernet interface
       product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eno1
       version: 0a
       serial: 98:e7:f4:58:73:21
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8107e-2_0.0.2 02/26/15 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:128 ioport:4000(size=256) memory:b1104000-b1104fff memory:b1100000-b1103fff
  *-network
       description: Wireless interface
       product: RTL8723BE PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlo1
       version: 00
       serial: 94:e9:79:67:d8:c1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8723be driverversion=4.8.0-22-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:19 ioport:3000(size=256) memory:b1000000-b1003fff
  *-network
       description: Ethernet interface
       physical id: 3
       logical name: enxe8802ee78a2e
       serial: e8:80:2e:e7:8a:2e
       size: 100Mbit/s
       capacity: 100Mbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=asix driverversion=22-Dec-2011 duplex=full firmware=ASIX AX88772 USB 2.0 Ethernet ip=170.212.109.235 link=yes multicast=yes port=MII speed=100Mbit/s
```


```
>> ifconfig
eno1: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 98:e7:f4:58:73:21  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


enxe8802ee78a2e: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 170.212.109.235  netmask 255.255.255.0  broadcast 170.212.109.255
        inet6 fe80::f05c:3c83:cd9:4b0a  prefixlen 64  scopeid 0x20<link>
        ether e8:80:2e:e7:8a:2e  txqueuelen 1000  (Ethernet)
        RX packets 924452  bytes 1049492466 (1.0 GB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 505956  bytes 40947200 (40.9 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 6326  bytes 779852 (779.8 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 6326  bytes 779852 (779.8 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlo1: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 94:e9:79:67:d8:c1  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```


```
>> iwconfig
wlo1      IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
enxe8802ee78a2e  no wireless extensions.


eno1      no wireless extensions.


lo        no wireless extensions.
```


```
>> sudo ifconfig wlo1 down
>> sudo ifconfig wlo1 up
>> sudo modprobe  -rv rtl8723be && sudo modprobe  -v rtl8723be
rmmod rtl8723be
rmmod rtl_pci
rmmod rtlwifi
rmmod mac80211
rmmod cfg80211
rmmod rtl8723_common
rmmod btcoexist
insmod /lib/modules/4.8.0-22-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/4.8.0-22-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/4.8.0-22-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko 
insmod /lib/modules/4.8.0-22-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_pci.ko 
insmod /lib/modules/4.8.0-22-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723com/rtl8723-common.ko 
insmod /lib/modules/4.8.0-22-generic/kernel/drivers/net/wireless/realtek/rtlwifi/btcoexist/btcoexist.ko 
insmod /lib/modules/4.8.0-22-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko
```


```
>> lsmod|grep -i wifi
rtlwifi                77824  2 rtl_pci,rtl8723be
mac80211              757760  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              581632  2 mac80211,rtlwifi
```


```
>> sudo ifconfig wlo1 down
>> sudo ifconfig wlo1 up
>> sudo iwconfig wlo1 essid ${NETWORK_NAME}
>> sudo iwconfig
wlo1      IEEE 802.11  ESSID:"${NETWORK_NAME}"  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          
enxe8802ee78a2e  no wireless extensions.


eno1      no wireless extensions.


lo        no wireless extensions.
>> sudo dhcpcd wlo1
wlo1: waiting for carrier
timed out
dhcpcd exited
```


```
>> cat /var/log/syslog|grep firmware
May 16 09:13:45 kernel: [    7.674102] [drm] GuC firmware load skipped
May 16 09:13:45 kernel: [   26.507741] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
May 16 09:13:48 NetworkManager[854]: <info>  [1494940428.0167] manager[0x55814f5861a0]: monitoring kernel firmware directory '/lib/firmware'.
May 16 10:07:24 kernel: [  233.469257] [drm] GuC firmware load skipped
May 16 10:19:09 NetworkManager[854]: <info>  [1494944349.6289] manager: kernel firmware directory '/lib/firmware' changed
May 16 10:19:14 NetworkManager[854]: <info>  [1494944354.0868] manager: kernel firmware directory '/lib/firmware' changed
May 16 10:34:50 kernel: [    7.948019] [drm] GuC firmware load skipped
May 16 10:34:50 kernel: [   23.710434] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
May 16 10:34:55 NetworkManager[904]: <info>  [1494945295.5146] manager[0x55939daae200]: monitoring kernel firmware directory '/lib/firmware'.
May 16 11:25:02 kernel: [    7.565350] [drm] GuC firmware load skipped
May 16 11:25:02 kernel: [   24.761620] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
May 16 11:25:04 NetworkManager[991]: <info>  [1494948304.9225] manager[0x55ca427dd200]: monitoring kernel firmware directory '/lib/firmware'.
May 16 11:59:17 kernel: [ 2085.834382] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
```


```
>> cat /var/log/syslog|grep wireless
May 16 09:13:45  kernel: [   26.510598] rtlwifi: rtlwifi: wireless switch is on
May 16 09:15:32  NetworkManager[854]: <info>  [1494940532.8417] device (wlo1): Activation: (wifi) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network '${NETWORK_NAME}'.
May 16 10:07:24  kernel: [  233.460208] rtlwifi: rtlwifi: wireless switch is on
May 16 10:34:50  kernel: [   23.935677] rtlwifi: rtlwifi: wireless switch is on
May 16 10:35:47  ureadahead[318]: ureadahead:ibm-wireless: Ignored relative path
May 16 10:35:47  ureadahead[318]: ureadahead:asus-wireless-off: Ignored relative path
May 16 10:35:47  ureadahead[318]: ureadahead:tosh-wireless: Ignored relative path
May 16 10:35:47  ureadahead[318]: ureadahead:asus-wireless-on: Ignored relative path
May 16 11:25:02  kernel: [   24.766668] rtlwifi: rtlwifi: wireless switch is on
May 16 11:59:17  kernel: [ 2085.836162] rtlwifi: rtlwifi: wireless switch is on
```


```
>> cat /var/log/syslog|grep wifi
May 16 09:13:45  kernel: [   26.507741] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
May 16 09:13:45  kernel: [   26.510598] rtlwifi: rtlwifi: wireless switch is on
May 16 09:13:47  NetworkManager[854]: <info>  [1494940427.9566] Read config: /etc/NetworkManager/NetworkManager.conf (etc: default-wifi-powersave-on.conf)
May 16 09:13:48  NetworkManager[854]: <info>  [1494940428.6032] Loaded device plugin: NMWifiFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-wifi.so)
May 16 09:15:18  NetworkManager[854]: <info>  [1494940518.4402] device (wlo1): Activation: (wifi) access point '${NETWORK_NAME}' has security, but secrets are required.
May 16 09:15:18  NetworkManager[854]: <info>  [1494940518.4698] device (wlo1): Activation: (wifi) connection '${NETWORK_NAME}' has security, and secrets exist.  No new secrets needed.
May 16 09:15:32  NetworkManager[854]: <info>  [1494940532.8417] device (wlo1): Activation: (wifi) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network '${NETWORK_NAME}'.
May 16 09:16:25  NetworkManager[854]: <info>  [1494940585.2225] device (wlo1): Activation: (wifi) access point '${NETWORK_NAME}' has security, but secrets are required.
May 16 09:16:25  NetworkManager[854]: <info>  [1494940585.2725] device (wlo1): Activation: (wifi) connection '${NETWORK_NAME}' has security, and secrets exist.  No new secrets needed.
May 16 09:16:50  NetworkManager[854]: <warn>  [1494940610.3018] device (wlo1): Activation: (wifi) association took too long, failing activation
May 16 10:07:24  kernel: [  233.460208] rtlwifi: rtlwifi: wireless switch is on
May 16 10:34:50  kernel: [   23.710434] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
May 16 10:34:50  kernel: [   23.935677] rtlwifi: rtlwifi: wireless switch is on
May 16 10:34:55  NetworkManager[904]: <info>  [1494945295.4793] Read config: /etc/NetworkManager/NetworkManager.conf (etc: default-wifi-powersave-on.conf)
May 16 10:34:57  NetworkManager[904]: <info>  [1494945297.3658] Loaded device plugin: NMWifiFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-wifi.so)
May 16 11:24:16  NetworkManager[904]: <warn>  [1494948256.4090] error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: Authorization check failed: Message recipient disconnected from message bus without replying
May 16 11:24:16  NetworkManager[904]: <warn>  [1494948256.4092] error requesting auth for org.freedesktop.NetworkManager.wifi.share.protected: Authorization check failed: Message recipient disconnected from message bus without replying
May 16 11:25:02  kernel: [   24.761620] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
May 16 11:25:02  kernel: [   24.766668] rtlwifi: rtlwifi: wireless switch is on
May 16 11:25:04  NetworkManager[991]: <info>  [1494948304.9085] Read config: /etc/NetworkManager/NetworkManager.conf (etc: default-wifi-powersave-on.conf)
May 16 11:25:05  NetworkManager[991]: <info>  [1494948305.5545] Loaded device plugin: NMWifiFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-wifi.so)
May 16 11:59:17  kernel: [ 2085.834382] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
May 16 11:59:17  kernel: [ 2085.836162] rtlwifi: rtlwifi: wireless switch is on
```


```
SYSTEM SPECIFICATIONS
------------------------------------------
Kubuntu 16.10
KDE Plasma Version 5.7.5
KDE Frameworks Version: 5.26.0
Qt Version: 5.6.1
Kernel Version: 4.8.0-22-generic
OS Type: 64-bit
```

---

### Post by fakeacct843954 on 2017-05-16
A lot of this information will be duplicated, but the output from the Ubuntu forums diagnostic can be found [here]("https://paste.ubuntu.com/24588870/").

---

### Post by jeremy31 on 2017-05-16
Since it is a HP with the rtl8723be chipset do
```
sudo modprobe -r rtl8723be
```
```
sudo modprobe rtl8723be ant_sel=1
```
```
iwlist scan | egrep -i 'ssid|quality'
```
```
sudo modprobe -r rtl8723be
```
```
sudo modprobe rtl8723be ant_sel=2
```
```
iwlist scan | egrep -i 'ssid|quality'
```

Then compare the results from the iwlist scan commands to see if one is better than the other, if one setting is better
```
echo "options rtl8723be ant_sel=X" | sudo tee /etc/modprobe.d/rtl8723be-ant.conf
```
Replace the X with the ant_sel parameter that worked the best and reboot

---

### Post by fakeacct843954 on 2017-05-17
Thanks -- that resolved the issue!

---

### Post by jeremy31 on 2017-05-17
Please use the thread tools menu near the top right of the page to mark as solved

---

