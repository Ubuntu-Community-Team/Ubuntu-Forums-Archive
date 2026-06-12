---
title: "How to bring up wireless after it sometimes goes down on reboot (wlan0 up gives error"
date: 2013-10-16
forum: Networking &amp; Wireless
---

### Post by GePBtY7 on 2013-10-16
NOTE: I've already posted this question at [http://askubuntu.com/questions/359538/how-to-bring-up-wireless-after-it-sometimes-goes-down-on-reboot-wlan0-up-gives](http://askubuntu.com/questions/359538/how-to-bring-up-wireless-after-it-sometimes-goes-down-on-reboot-wlan0-up-gives) but I am trying to increase the chances of getting help by asking it here as well.

I run (K)Ubuntu 12.10/12.04 in a triple boot with Windows 7 and  access the Intenet wirelessly. This works perfectly most of the time.  Sometimes after a normal reboot, the wireless connection dissapears. In  Ubuntu, it manifests itself in "Device not ready" being shown in Network  Manager, and in Kubuntu, the WLAN Interface is "Unavailable" in the  corresponding KDE Network Manager widget. Normally, when available, my  wireless connection's SSID is displayed and I automatically get  connected to it.

  At this point, the only thing that helps me get back the wireless is  booting in and out of Windows 7 and then back to (K)Ubuntu. However, I  would like to be able to fix the problem without having to rely on  Windows 7 being there.
  Below are some relevant command outputs I've used for debugging:
```


user@user-desktop:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
        Subsystem: Hewlett-Packard Company Device [103c:2a9c]
        Kernel driver in use: r8169
--
04:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]
        Subsystem: Lite-On Communications Inc Device [11ad:6632]
        Kernel driver in use: rt2800pci

user@user-desktop:~$ lsmod
Module                  Size  Used by
parport_pc             32689  0 
ppdev                  17074  0 
bnep                   18141  2 
binfmt_misc            17501  1 
rfcomm                 46620  0 
bluetooth             209438  10 bnep,rfcomm
nvidia               9367981  38 
arc4                   12530  2 
rt2800pci              18529  0 
rt2800lib              58731  1 rt2800pci
crc_ccitt              12708  1 rt2800lib
rt2x00pci              14519  1 rt2800pci
snd_hda_codec_realtek    78147  1 
rt2x00lib              54995  3 rt2800pci,rt2800lib,rt2x00pci
snd_hda_intel          33492  3 
mac80211              535936  3 rt2800lib,rt2x00pci,rt2x00lib
snd_hda_codec         134213  2 snd_hda_codec_realtek,snd_hda_intel
coretemp               13401  0 
snd_hwdep              17699  1 snd_hda_codec
gpio_ich               13384  0 
cfg80211              206797  2 rt2x00lib,mac80211
snd_pcm                96668  2 snd_hda_intel,snd_hda_codec
kvm_intel             132760  0 
snd_seq_midi           13325  0 
snd_rawmidi            30513  1 snd_seq_midi
kvm                   414111  1 kvm_intel
eeprom_93cx6           13345  1 rt2800pci
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
psmouse               100424  0 
joydev                 17458  0 
lpc_ich                17062  0 
i7core_edac            23572  0 
mei                    40691  0 
snd_timer              29426  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
mac_hid                13206  0 
serio_raw              13216  0 
lp                     17760  0 
snd                    78921  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
edac_core              52452  3 i7core_edac
parport                46346  3 parport_pc,ppdev,lp
wmi                    19071  0 
microcode              22804  0 
soundcore              15048  1 snd
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
hid_sony               12795  0 
hid_generic            12541  0 
usb_storage            48839  0 
usbhid                 46987  0 
hid                   100411  3 hid_sony,hid_generic,usbhid
firewire_ohci          40402  0 
firewire_core          64369  1 firewire_ohci
crc_itu_t              12708  1 firewire_core
ahci                   25721  2 
r8169                  61671  0 
libahci                31192  1 ahci

user@user-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr aa:aa:aa:aa:aa:aa  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1284 (1.2 KB)  TX bytes:1284 (1.2 KB)

wlan0     Link encap:Ethernet  HWaddr aa:aa:aa:aa:aa:aa  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

user@user-desktop:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

user@user-desktop:~$ rfkill list all
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no

user@user-desktop:~$ sudo iwlist scan
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

user@user-desktop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: aa:aa:aa:aa:aa:aa
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168d-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:45 ioport:d800(size=256) memory:fbdff000-fbdfffff memory:f6ffc000-f6ffffff memory:fbdc0000-fbddffff
  *-network DISABLED
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 00
       serial: aa:aa:aa:aa:aa:aa
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.5.0-41-generic firmware=0.34 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:fbff0000-fbffffff
```

I've tried to bring the wireless up manually with:
  ```
sudo ifconfig wlan0 up

```  and got the following output:
  ```
SIOCSIFFLAGS: Input/output error

```  I've found the following entries in syslog interesting (logged when a boot results in a non-functional wireless):


```
Oct 15 19:29:57 user-desktop NetworkManager[1083]: <info> NetworkManager (version 0.9.6.0) is starting...
Oct 15 19:29:57 user-desktop NetworkManager[1083]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Oct 15 19:29:57 user-desktop NetworkManager[1083]: <info> WEXT support is enabled
...
Oct 15 19:29:57 user-desktop NetworkManager[1083]:    SCPlugin-Ifupdown: init!
Oct 15 19:29:57 user-desktop NetworkManager[1083]:    SCPlugin-Ifupdown: update_system_hostname
Oct 15 19:29:57 user-desktop NetworkManager[1083]:    SCPluginIfupdown: management mode: managed
Oct 15 19:29:57 user-desktop NetworkManager[1083]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/eth0, iface: eth0)
Oct 15 19:29:57 user-desktop NetworkManager[1083]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Oct 15 19:29:57 user-desktop NetworkManager[1083]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:04:00.0/net/wlan0, iface: wlan0)
Oct 15 19:29:57 user-desktop NetworkManager[1083]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:04:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Oct 15 19:29:57 user-desktop NetworkManager[1083]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Oct 15 19:29:57 user-desktop NetworkManager[1083]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Oct 15 19:29:57 user-desktop NetworkManager[1083]:    SCPlugin-Ifupdown: end _init.
Oct 15 19:29:57 user-desktop NetworkManager[1083]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Oct 15 19:29:57 user-desktop NetworkManager[1083]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Oct 15 19:29:57 user-desktop NetworkManager[1083]:    SCPlugin-Ifupdown: (18924336) ... get_connections.
Oct 15 19:29:57 user-desktop NetworkManager[1083]:    SCPlugin-Ifupdown: (18924336) connections count: 0
Oct 15 19:29:57 user-desktop NetworkManager[1083]:    keyfile: parsing xxx ... 
Oct 15 19:29:57 user-desktop NetworkManager[1083]:    keyfile:     read connection 'xxx'
Oct 15 19:29:57 user-desktop NetworkManager[1083]:    keyfile: parsing yyy ... 
Oct 15 19:29:57 user-desktop NetworkManager[1083]:    keyfile:     read connection 'yyy'
Oct 15 19:29:57 user-desktop NetworkManager[1083]:    keyfile: parsing zzz ... 
Oct 15 19:29:57 user-desktop NetworkManager[1083]:    keyfile:     read connection 'zzz'
Oct 15 19:29:57 user-desktop NetworkManager[1083]: <info> modem-manager is now available
Oct 15 19:29:57 user-desktop NetworkManager[1083]: <info> monitoring kernel firmware directory '/lib/firmware'.
...
Oct 15 19:29:57 user-desktop NetworkManager[1083]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:1c.5/0000:04:00.0/ieee80211/phy0/rfkill0) (driver (unknown))
Oct 15 19:29:57 user-desktop NetworkManager[1083]: <info> WiFi enabled by radio killswitch; enabled by state file
Oct 15 19:29:57 user-desktop NetworkManager[1083]: <info> WWAN enabled by radio killswitch; enabled by state file
Oct 15 19:29:57 user-desktop NetworkManager[1083]: <info> WiMAX enabled by radio killswitch; enabled by state file
Oct 15 19:29:57 user-desktop NetworkManager[1083]: <info> Networking is enabled by state file
Oct 15 19:29:57 user-desktop NetworkManager[1083]: <warn> failed to allocate link cache: (-10) Operation not supported
Oct 15 19:29:57 user-desktop NetworkManager[1083]: <info> (eth0): carrier is OFF
Oct 15 19:29:57 user-desktop NetworkManager[1083]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Oct 15 19:29:57 user-desktop NetworkManager[1083]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Oct 15 19:29:57 user-desktop NetworkManager[1083]: <info> (eth0): now managed
Oct 15 19:29:57 user-desktop NetworkManager[1083]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Oct 15 19:29:57 user-desktop NetworkManager[1083]: <info> (eth0): bringing up device.
Oct 15 19:29:57 user-desktop cron[1172]: (CRON) STARTUP (fork ok)
Oct 15 19:29:57 user-desktop cron[1172]: (CRON) INFO (Running @reboot jobs)
Oct 15 19:29:57 user-desktop NetworkManager[1083]: <info> (eth0): preparing device.
Oct 15 19:29:57 user-desktop NetworkManager[1083]: <info> (eth0): deactivating device (reason 'managed') [2]
Oct 15 19:29:57 user-desktop NetworkManager[1083]: <info> (wlan0): using nl80211 for WiFi device control
Oct 15 19:29:57 user-desktop NetworkManager[1083]: <warn> (wlan0): driver supports Access Point (AP) mode
Oct 15 19:29:57 user-desktop NetworkManager[1083]: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2800pci' ifindex: 3)
Oct 15 19:29:57 user-desktop NetworkManager[1083]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Oct 15 19:29:57 user-desktop NetworkManager[1083]: <info> (wlan0): now managed
Oct 15 19:29:57 user-desktop NetworkManager[1083]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Oct 15 19:29:57 user-desktop NetworkManager[1083]: <info> (wlan0): bringing up device.
...
Oct 15 19:29:59 user-desktop kernel: [   31.050638] phy0 -> rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068].
...
Oct 15 19:30:00 user-desktop NetworkManager[1083]: <info> (wlan0): deactivating device (reason 'managed') [2]
...
Oct 15 19:30:00 user-desktop NetworkManager[1083]: <info> wpa_supplicant started
Oct 15 19:30:00 user-desktop kernel: [   32.647940] phy0 -> rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068].
Oct 15 19:30:00 user-desktop kernel: [   32.647949] phy0 -> rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5).
Oct 15 19:30:00 user-desktop kernel: [   32.648045] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

Also, the following is logged each time I try to bring wlan0 up:

```
Oct 15 19:40:09 user-desktop kernel: [  519.848361] phy0 -> rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068].
Oct 15 19:40:11 user-desktop kernel: [  521.445718] phy0 -> rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068].
Oct 15 19:40:11 user-desktop kernel: [  521.445724] phy0 -> rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5).

```

OBSERVATIONS:
1. Wireless appears to be lost randomly sometimes on a reboot (both  after installing some updates and also when none were installed before  the reboot)
2. When it is lost in one of the (K)Ubuntu's, it is also unavailable in the other one after booting into it
3. The only thing that brings back the wireless is rebooting into Windows 7 and back
  How can I re-enable my wireless in this case?

---

### Post by GePBtY7 on 2013-10-17
Bump

---

### Post by unclestevieray on 2013-12-30
I have a different problem.  My WLAN works but if I go to MikDees and want to log in, there is no network controls to bring up the control center.  There is no control center in the launcher that has any netword controls to make changes with.  This all happened when I upgraded from KUBU 12.4 to 13.1 in a 2 step up upgrade...I tho't who FUBAR'd my fav O/S NOW I HAVE TO FIND ANOTHER!!!

---

