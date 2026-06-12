---
title: "Intel NUC (NUC7i3BNH) w/ Intel-AC 8265 wireless Kubuntu 18.10, wireless not working"
date: 2019-03-11
forum: Networking &amp; Wireless
---

### Post by bportpat on 2019-03-11
Hey Everyone, 

I am new to the forum but decently familiar with Linux. I had wireless working on this NUC until Feb, 27, 2019 and since then I have not been able to get the Wireless adaptor to show up. I have done a lot of t-shooting already and will try to summarize here. 

First I did run the script that is asked prior to posting (I removed the name of my SSID):
```
pat@pat-NUCi3:~$ cat wireless-info.txt

########## wireless info START ##########


Report from: 11 Mar 2019 13:03 EDT -0400


Booted last: 11 Mar 2019 00:00 EDT -0400


Script from: 22 Oct 2018 03:34 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 18.10
Release:    18.10
Codename:    cosmic


##### kernel ############################


Linux 4.18.0-16-generic #17-Ubuntu SMP Fri Feb 8 00:06:57 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=1


##### desktop ###########################


sed: can't read /home/pat/.dmrc: No such file or directory


Could not be determined.


##### lspci #############################


00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (4) I219-V [8086:15d8] (rev 21)
    Subsystem: Intel Corporation Ethernet Connection (4) I219-V [8086:2068]
    Kernel driver in use: e1000e


##### lsusb #############################


Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 8087:0a2b Intel Corp.
Bus 001 Device 003: ID 046d:c051 Logitech, Inc. G3 (MX518) Optical Mouse
Bus 001 Device 002: ID 03f0:0024 Hewlett-Packard KU-0316 Keyboard
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### secure boot #######################


SecureBoot disabled
Platform is in Setup Mode


##### lsmod #############################


wmi_bmof               16384  0
intel_wmi_thunderbolt    16384  0
wmi                    24576  2 intel_wmi_thunderbolt,wmi_bmof


##### interfaces ########################


[/etc/network/interfaces]
auto lo
iface lo inet loopback


##### ifconfig ##########################


1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'eno1' [IF1]> brd <MAC address>
    inet 192.168.0.18/24 brd 192.168.0.255 scope global dynamic noprefixroute eno1
       valid_lft 6559sec preferred_lft 6559sec
    inet6 fe80::9fe6:6799:75d2:5adc/64 scope link noprefixroute
       valid_lft forever preferred_lft forever


##### iwconfig ##########################


lo        no wireless extensions.


eno1      no wireless extensions.


##### route #############################


default via 192.168.0.1 dev eno1 proto dhcp metric 100
169.254.0.0/16 dev eno1 scope link metric 1000
192.168.0.0/24 dev eno1 proto kernel scope link src 192.168.0.18 metric 100


##### resolv.conf #######################


[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']


nameserver 127.0.0.53
options edns0


##### network managers ##################


Installed:


    NetworkManager


Running:


root       767     1  0 12:52 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Ethernet Connection (4) I219-V
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.1-4
GENERAL.HWADDR:                         <MAC 'eno1' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1f.6/net/eno1
GENERAL.IP-IFACE:                       eno1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       52142d40-949e-33bc-b339-e44fff0623ce
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.0.18/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.0.1, mt = 100
IP4.ROUTE[2]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.ROUTE[3]:                           dst = 192.168.0.0/24, nh = 0.0.0.0, mt = 100
IP4.DNS[1]:                             192.168.0.110
IP4.DNS[2]:                             192.168.0.112
DHCP4.OPTION[1]:                        broadcast_address = 192.168.0.255
DHCP4.OPTION[2]:                        dhcp_lease_time = 7200
DHCP4.OPTION[3]:                        dhcp_message_type = 5
DHCP4.OPTION[4]:                        dhcp_server_identifier = 192.168.0.1
DHCP4.OPTION[5]:                        domain_name_servers = 192.168.0.110 192.168.0.112
DHCP4.OPTION[6]:                        expiry = 1552330082
DHCP4.OPTION[7]:                        ip_address = 192.168.0.18
DHCP4.OPTION[8]:                        network_number = 192.168.0.0
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       requested_broadcast_address = 1
DHCP4.OPTION[11]:                       requested_domain_name = 1
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       requested_domain_search = 1
DHCP4.OPTION[14]:                       requested_host_name = 1
DHCP4.OPTION[15]:                       requested_interface_mtu = 1
DHCP4.OPTION[16]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[17]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[18]:                       requested_netbios_scope = 1
DHCP4.OPTION[19]:                       requested_ntp_servers = 1
DHCP4.OPTION[20]:                       requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[21]:                       requested_routers = 1
DHCP4.OPTION[22]:                       requested_static_routes = 1
DHCP4.OPTION[23]:                       requested_subnet_mask = 1
DHCP4.OPTION[24]:                       requested_time_offset = 1
DHCP4.OPTION[25]:                       requested_wpad = 1
DHCP4.OPTION[26]:                       routers = 192.168.0.1
DHCP4.OPTION[27]:                       subnet_mask = 255.255.255.0
IP6.ADDRESS[1]:                         fe80::9fe6:6799:75d2:5adc/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = fe80::/64, nh = ::, mt = 100
IP6.ROUTE[2]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   52142d40-949e-33bc-b339-e44fff0623ce | Wired connection 1


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


##### NetworkManager config #############


[[/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf]]
[connection]
wifi.powersave = 3


[[/etc/NetworkManager/NetworkManager.conf]]
[main]
plugins=ifupdown,keyfile
[ifupdown]
managed=false
[device]
wifi.scan-rand-mac-address=no


[[/usr/lib/NetworkManager/conf.d/10-dns-resolved.conf]]
[main]
dns=systemd-resolved


[[/usr/lib/NetworkManager/conf.d/10-globally-managed-devices.conf]]
[keyfile]
unmanaged-devices=*,except:type:wifi,except:type:gsm,except:type:cdma


[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-mac-addr-change-wifi]
match-device=driver:rtl8723bs,driver:rtl8189es,driver:r8188eu,driver:8188eu,driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no
wifi.cloned-mac-address=preserve
ethernet.cloned-mac-address=preserve


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/The_Peasleys_2.4-80276e8b-5023-480d-9cad-830b66b7f138]] (600 root)
[connection] id=SSID_2.4 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=SSID_2.4
[ipv4] method=auto
[ipv6] method=auto


##### Netplan config ####################


[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager


##### iw reg get ########################


Region: America/New_York (based on set time zone)


global
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (6, 20), (N/A)
    (2457 - 2482 @ 20), (6, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 80), (6, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (5250 - 5330 @ 80), (6, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (6, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)


##### iwlist channels ###################


lo        no frequency information.


eno1      no frequency information.


##### iwlist scan #######################


lo        Interface doesn't support scanning.


eno1      Interface doesn't support scanning.


##### module infos ######################


##### module parameters #################


##### /etc/modules ######################


##### modprobe options ##################


[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off


[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


##### rc.local ##########################


grep: /etc/rc.local: No such file or directory


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[    5.500058] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready (repeated 2 times)
[    8.802399] e1000e: eno1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
[    8.802449] IPv6: ADDRCONF(NETDEV_CHANGE): eno1: link becomes ready


########## wireless info END ############
```

When doing lsusb and lspci I do not see a wifi adaptor at all:
```
pat@pat-NUCi3:~$ lsusbBus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 8087:0a2b Intel Corp.
Bus 001 Device 003: ID 046d:c051 Logitech, Inc. G3 (MX518) Optical Mouse
Bus 001 Device 002: ID 03f0:0024 Hewlett-Packard KU-0316 Keyboard
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
pat@pat-NUCi3:~$ lspci
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers (rev 02)
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 620 (rev 02)
00:08.0 System peripheral: Intel Corporation Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th Gen Core Processor Gaussian Mixture Model
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI #1 (rev 21)
00:17.0 SATA controller: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] (rev 21)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #1 (rev f1)
00:1c.5 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #6 (rev f1)
00:1c.7 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #8 (rev f1)
00:1d.0 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #9 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Intel(R) 100 Series Chipset Family LPC Controller/eSPI Controller - 9D4E (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
00:1f.6 Ethernet controller: Intel Corporation Ethernet Connection (4) I219-V (rev 21)
01:00.0 PCI bridge: Intel Corporation JHL6340 Thunderbolt 3 Bridge (C step) [Alpine Ridge 2C 2016] (rev 02)
02:00.0 PCI bridge: Intel Corporation JHL6340 Thunderbolt 3 Bridge (C step) [Alpine Ridge 2C 2016] (rev 02)
02:01.0 PCI bridge: Intel Corporation JHL6340 Thunderbolt 3 Bridge (C step) [Alpine Ridge 2C 2016] (rev 02)
02:02.0 PCI bridge: Intel Corporation JHL6340 Thunderbolt 3 Bridge (C step) [Alpine Ridge 2C 2016] (rev 02)
39:00.0 USB controller: Intel Corporation Device 15db (rev 02)
3b:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)
3c:00.0 Non-Volatile memory controller: Realtek Semiconductor Co., Ltd. Device 5760 (rev 01)
```

I am able to find the card with dmidecode
```
pat@pat-NUCi3:~$ sudo dmidecode -t 10# dmidecode 3.1
Getting SMBIOS data from sysfs.
SMBIOS 3.1.1 present.


Handle 0x000F, DMI type 10, 20 bytes
On Board Device 1 Information
    Type: Video
    Status: Enabled
    Description:  Intel(R) HD Graphics Device
On Board Device 2 Information
    Type: Ethernet
    Status: Enabled
    Description:  Intel(R) I219-V Gigabit Network Device
On Board Device 3 Information
    Type: Sound
    Status: Enabled
    Description:  Realtek High Definition Audio Device
On Board Device 4 Information
    Type: Other
    Status: Enabled
    Description: CIR Device
On Board Device 5 Information
    Type: Other
    Status: Enabled
    Description: SD
On Board Device 6 Information
    Type: Other
    Status: Enabled
    Description: Intel Dual Band Wireless-AC 8265
On Board Device 7 Information
    Type: Other
    Status: Enabled
    Description: Bluetooth
On Board Device 8 Information
    Type: Other
    Status: Disabled
    Description: Thunderbolt
```

I also did review the [Intel Linux]("http://www.intel.com/content/www/us/en/support/articles/000005511/network-and-i-o/wireless-networking.html") wireless site and it looks like this chip should be supported since 4.6
I also reviewed dmesg but there is nothing that starts with iw* (good or bad) in the file at all.
I looked at my BIOS settings and the wifi card is still on/enabled as well.

Any guidance or ideas would be helpful.

---

### Post by bportpat on 2019-03-12
An update

I installed 18.04 to the Sata SSD (current 18.10 is on M.2). Needed ethernet for updates at install. Then rebooted and I was able to connect to Wifi no problem. I patched
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-update

```

rebooted - wifi still worked

Then I did a shutdown and and power up. No Wifi

Here is a list of all the data I grabbed while wifi was working
```

test@test-NUC7i3BNH:~$ sudo lsmod | grep iwl
[sudo] password for test:
iwlmvm                376832  0
mac80211              802816  1 iwlmvm
iwlwifi               299008  1 iwlmvm
cfg80211              667648  3 iwlmvm,iwlwifi,mac8021


test@test-NUC7i3BNH:~$ ll /lib/firmware/iwlwifi-8265-*
-rw-r--r-- 1 root root 2389968 Nov 17  2017 /lib/firmware/iwlwifi-8265-21.ucode
-rw-r--r-- 1 root root 1811984 Apr 24  2018 /lib/firmware/iwlwifi-8265-22.ucode
-rw-r--r-- 1 root root 2234528 Dec  5  2017 /lib/firmware/iwlwifi-8265-27.ucode
-rw-r--r-- 1 root root 2307104 Dec  6  2017 /lib/firmware/iwlwifi-8265-31.ucode
-rw-r--r-- 1 root root 2440780 Apr 25  2018 /lib/firmware/iwlwifi-8265-34.ucode
-rw-r--r-- 1 root root 2498044 Dec 14 07:54 /lib/firmware/iwlwifi-8265-36.ucode


test@test-NUC7i3BNH:~$ dmesg | grep iwl
[    4.163675] iwlwifi 0000:3a:00.0: enabling device (0000 -> 0002)
[    4.186708] iwlwifi 0000:3a:00.0: loaded firmware version 36.e91976c0.0 op_mode iwlmvm
[    4.229494] iwlwifi 0000:3a:00.0: Detected Intel(R) Dual Band Wireless AC 8265, REV=0x230
[    4.292694] iwlwifi 0000:3a:00.0: base HW address: 88:b1:11:eb:01:a4
[    4.385113] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    4.392745] iwlwifi 0000:3a:00.0 wlp58s0: renamed from wlan0




test@test-NUC7i3BNH:~$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: eno1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether 94:c6:91:16:18:0b brd ff:ff:ff:ff:ff:ff
3: wlp58s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 88:b1:11:eb:01:a4 brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.19/24 brd 192.168.0.255 scope global dynamic noprefixroute wlp58s0
       valid_lft 6818sec preferred_lft 6818sec
    inet6 fe80::cb23:db2a:8058:9d08/64 scope link noprefixroute
       valid_lft forever preferred_lft forever


test@test-NUC7i3BNH:/etc/modprobe.d$ cat iwlwifi.conf
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

```

now dmesg doesn't show anything with grep iwl. All the firmware files are the same.

Here is the list of packages that were upgraded - I plan to review this list closer shortly
```

bind9-host busybox-initramfs busybox-static dnsutils firefox ghostscript ghostscript-x gir1.2-gtk-3.0 gtk-update-icon-cache initramfs-tools initramfs-tools-bin initramfs-tools-core libbind9-160
  libdbusmenu-glib4 libdbusmenu-gtk3-4 libdns-export1100 libdns1100 libgd3 libgs9 libgs9-common libgtk-3-0 libgtk-3-bin libgtk-3-common libidn11 libirs160 libisc-export169 libisc169 libisccc160
  libisccfg160 libldb1 liblwres160 libnss-systemd libnss3 libpam-modules libpam-modules-bin libpam-runtime libpam-systemd libpam0g libpoppler-qt5-1 libpoppler73 libpulse-mainloop-glib0 libpulse0
  libpulsedsp libseccomp2 libssl1.0.0 libsystemd0 libu2f-udev libvulkan1 libx11-6 libx11-data libx11-xcb1 libxcb-composite0 libxcb-damage0 libxcb-dpms0 libxcb-dri2-0 libxcb-dri3-0 libxcb-glx0
  libxcb-present0 libxcb-randr0 libxcb-record0 libxcb-render0 libxcb-shape0 libxcb-shm0 libxcb-sync1 libxcb-xfixes0 libxcb-xinerama0 libxcb-xkb1 libxcb-xv0 libxcb1 poppler-utils pulseaudio
  pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-utils python-gi python3-gi systemd systemd-sysv unattended-upgrades

```

---

### Post by chili555 on 2019-03-12
Is there any clue when you manually load the module and then check the log?```
sudo modprobe iwlwifi && dmesg | grep iwl
```Are there any clues if we check to see what's happening, or not, on the PCI bus?```
dmesg | grep 3a:00
```

---

### Post by bportpat on 2019-03-12
Ok another update..

I think I have made some interesting headway here. The following information is true for both 18.04 (SSD) and 18.10 (NVMe)

When the NUC is shutdown (powered off) and turned on. Wifi does not come up at all. Once the system is up, if I reboot, the wifi comes up without an issue. This leads me to think I need to look closer at the boot process. I am thinking on power up the system is coming up quicker than the wifi chipset has time to say "Hey I'm here" so to speak. When doing a reboot the power is not fully lost so that the wifi is "warm" and it's "Hey I'm here" is heard.

---

### Post by bportpat on 2019-03-12
Hey chili555 thanks for the response - the following is from the 18.10 install 

When I do this coming up from a "cold boot"/off state I don't get anything in dmesg for iwlwifi or 3a:00 - I do get a single line about "Intel Networking driver" when I modprobe iwlwifi, but it doesn't do anything other than start cfg80211 when doing a lsmod. I didn't capture it recently though.

When I reboot after a power up I get it to work and get the following
```

pat@pat-NUCi3:~$ dmesg | grep wl
[    4.081364] iwlwifi 0000:3a:00.0: enabling device (0000 -> 0002)
[    4.100194] iwlwifi 0000:3a:00.0: loaded firmware version 36.e91976c0.0 op_mode iwlmvm
[    4.139355] iwlwifi 0000:3a:00.0: Detected Intel(R) Dual Band Wireless AC 8265, REV=0x230
[    4.201299] iwlwifi 0000:3a:00.0: base HW address: 88:b1:11:eb:01:a4
[    4.307483] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    4.405051] iwlwifi 0000:3a:00.0 wlp58s0: renamed from wlan0
[   94.328276] IPv6: ADDRCONF(NETDEV_UP): wlp58s0: link is not ready
[   94.562288] IPv6: ADDRCONF(NETDEV_UP): wlp58s0: link is not ready
[   94.656139] IPv6: ADDRCONF(NETDEV_UP): wlp58s0: link is not ready
[   98.120237] wlp58s0: authenticate with f8:c2:88:5b:7f:40
[   98.133064] wlp58s0: send auth to f8:c2:88:5b:7f:40 (try 1/3)
[   98.139501] wlp58s0: authenticated
[   98.140027] wlp58s0: associate with f8:c2:88:5b:7f:40 (try 1/3)
[   98.144247] wlp58s0: RX AssocResp from f8:c2:88:5b:7f:40 (capab=0x431 status=0 aid=4)
[   98.148238] wlp58s0: associated
[   98.169796] IPv6: ADDRCONF(NETDEV_CHANGE): wlp58s0: link becomes ready
pat@pat-NUCi3:~$ dmesg | grep 3a:00
[    0.230576] pci 0000:3a:00.0: [8086:24fd] type 00 class 0x028000
[    0.230676] pci 0000:3a:00.0: reg 0x10: [mem 0xdc200000-0xdc201fff 64bit]
[    0.230945] pci 0000:3a:00.0: PME# supported from D0 D3hot D3cold
[    4.081364] iwlwifi 0000:3a:00.0: enabling device (0000 -> 0002)
[    4.100194] iwlwifi 0000:3a:00.0: loaded firmware version 36.e91976c0.0 op_mode iwlmvm
[    4.139355] iwlwifi 0000:3a:00.0: Detected Intel(R) Dual Band Wireless AC 8265, REV=0x230
[    4.201299] iwlwifi 0000:3a:00.0: base HW address: 88:b1:11:eb:01:a4
[    4.405051] iwlwifi 0000:3a:00.0 wlp58s0: renamed from wlan0
```

This makes me think I need to "slow down" the boot process to allow the wifi chipset to come up or move the wifi check to later in the boot process.

---

### Post by bportpat on 2019-03-12
I sent dmesg to a file for both wifi and no wifi under 18.04. The 1st line that is different between the two files is at line 314 in the having wifi file. I get something like this
```

ACPI: Power Resource [WRST] (on)
```

at lines 418-421 or so I see that the wireless card is seen on the pci bus on 0000:3a:00.0. The issue continues to be why this is not seen at a normal startup and then is on a reboot. I am not sure if this is networking/wireless related at this point. Should this thread be moved to a different place?

---

### Post by chili555 on 2019-03-12
> I didn't capture it recently though.Would you please? What you've posted here looks just perfect; i.e. nothing is wrong and therefore fixable.

Is WoWLAN available in your BIOS/EFI? Is it on or off? Can you please reverse it?

[http://revolutionwifi.blogspot.com/2010/11/wake-on-wireless-lan.html](http://revolutionwifi.blogspot.com/2010/11/wake-on-wireless-lan.html) 

[https://www.intel.com/content/www/us/en/support/articles/000027615/mini-pcs.html](https://www.intel.com/content/www/us/en/support/articles/000027615/mini-pcs.html)

I would love to see the entire dmesg when it is not working; please paste it here and give us the link. [http://paste.ubuntu.com](http://paste.ubuntu.com)

Is this a dual-boot with that other dark meat, Windows? Does it have a WoWLAN setting that can be reversed?

---

### Post by chili555 on 2019-03-12
I also suggest that you check the BIOS/EFI for S1 through S4 settings: [https://docs.microsoft.com/en-us/windows-hardware/drivers/kernel/system-sleeping-states](https://docs.microsoft.com/en-us/windows-hardware/drivers/kernel/system-sleeping-states)

---

### Post by bportpat on 2019-03-13
These are from dmesg from 18.04

[https://paste.ubuntu.com/p/Jyr5pbYpyh/](https://paste.ubuntu.com/p/Jyr5pbYpyh/) -- no wireless
[https://paste.ubuntu.com/p/cRM6Y5YmvN/](https://paste.ubuntu.com/p/cRM6Y5YmvN/) -- wireless working

Checked BIOS for Wake on LAN and Wake on WLAN only. This system only has LAN as an option and I have it as "Power on - Normal Boot" as this is the 1Gb connection I left it this way. I have checked that I am running the newest BIOS for my NUC version as well. 

This is a dual boot in that the NVMe is running Kubuntu 18.10 and the SSD is running 18.04. This NUC has never had Windows installed on it. 

I have no special settings for any sleep states. I usually don't use any sleep or hibernate type setting anyway, but I made sure to review them.

My working theory
- system is off -> power on -> not enough time for wifi to come up > no wifi > reboot > the wifi chip has power and is not lost during a reboot > wifi comes up fine.

also the wifi does show up in lspci when it is working correctly. When it isn't the card is never seen at all. I don't see any errors in dmesg. It just doesn't exist.
```
test@test-NUC7i3BNH:~$ lspci00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers (rev 02)
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 620 (rev 02)
00:08.0 System peripheral: Intel Corporation Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th Gen Core Processor Gaussian Mixture Model
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI #1 (rev 21)
00:17.0 SATA controller: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] (rev 21)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #1 (rev f1)
00:1c.5 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #6 (rev f1)
00:1c.7 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #8 (rev f1)
00:1d.0 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #9 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Intel(R) 100 Series Chipset Family LPC Controller/eSPI Controller - 9D4E (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
00:1f.6 Ethernet controller: Intel Corporation Ethernet Connection (4) I219-V (rev 21)
01:00.0 PCI bridge: Intel Corporation JHL6340 Thunderbolt 3 Bridge (C step) [Alpine Ridge 2C 2016] (rev 02)
02:00.0 PCI bridge: Intel Corporation JHL6340 Thunderbolt 3 Bridge (C step) [Alpine Ridge 2C 2016] (rev 02)
02:01.0 PCI bridge: Intel Corporation JHL6340 Thunderbolt 3 Bridge (C step) [Alpine Ridge 2C 2016] (rev 02)
02:02.0 PCI bridge: Intel Corporation JHL6340 Thunderbolt 3 Bridge (C step) [Alpine Ridge 2C 2016] (rev 02)
39:00.0 USB controller: Intel Corporation Device 15db (rev 02)
3a:00.0 Network controller: Intel Corporation Wireless 8265 / 8275 (rev 78)
3b:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)
3c:00.0 Non-Volatile memory controller: Realtek Semiconductor Co., Ltd. Device 5760 (rev 01)
```

Thanks for continuing to look into this! At this point the system could be "useable". I could turn it on and know I need to reboot then all is fine, but that just isn't a great solution. I want to solve this for real :)

---

### Post by chili555 on 2019-03-14
In your 'not working' dmesg, we see this sequence; I've included the timestamps for comparisons:

```
[    0.229150] pci 0000:02:02.0: PCI bridge to [bus 39]
[    0.229159] pci 0000:02:02.0:   bridge window [mem 0xd9f00000-0xd9ffffff]
[    0.229294] pci 0000:00:1c.5: PCI bridge to [bus 3a]
[    0.229432] pci 0000:3b:00.0: [10ec:5229] type 00 class 0xff0000
[    0.229470] pci 0000:3b:00.0: reg 0x10: [mem 0xdc100000-0xdc100fff]
[    0.229617] pci 0000:3b:00.0: supports D1 D2
[    0.229618] pci 0000:3b:00.0: PME# supported from D1 D2 D3hot

```
Notice that bus 0000:3a:00.0 is simply missing.

Here is the similar sequence from the 'working' dmesg:

```
[    0.230139] pci 0000:02:02.0: PCI bridge to [bus 39]
[    0.230147] pci 0000:02:02.0:   bridge window [mem 0xd9f00000-0xd9ffffff]
[    0.230692] [COLOR="#FF0000"]pci 0000:3a:00.0: [8086:24fd] type 00 class 0x028000[/COLOR]
[    0.230792] [COLOR="#FF0000"]pci 0000:3a:00.0: reg 0x10: [mem 0xdc200000-0xdc201fff 64bit][/COLOR]
[    0.231061] [COLOR="#FF0000"]pci 0000:3a:00.0: PME# supported from D0 D3hot D3cold[/COLOR]
[    0.231751] pci 0000:00:1c.5: PCI bridge to [bus 3a]
[    0.231755] pci 0000:00:1c.5:   bridge window [mem 0xdc200000-0xdc2fffff]
[    0.231892] pci 0000:3b:00.0: [10ec:5229] type 00 class 0xff0000
[    0.231929] pci 0000:3b:00.0: reg 0x10: [mem 0xdc100000-0xdc100fff]
[    0.232090] pci 0000:3b:00.0: supports D1 D2
[    0.232092] pci 0000:3b:00.0: PME# supported from D1 D2 D3hot

```
Notice that 3a is recognized and your Intel wireless 8086:24fd is seen on the bus. (Everybody on the bus!!!)

I have, so far, been unable to see any reason why this occurs; only the result.

Have you made any changes to the BIOS/EFI? Can you please revert the changes, if you remember them? I believe there is an option to reset the BIOS/EFI to factory defaults. Please try that.

I am running out of talent/ideas/mojo.

---

### Post by bportpat on 2019-03-14
Yea I saw the same thing in the different dmesg logs, but same as you, I can't explain why. I have reset my BIOS once. I will do that again tomorrow at some point (EST). I think my next test will be to use Centos or Fedora as a Linux flavor that isn't debain based. If I have similar results I think that would point to a BIOS type issue. At that point I will go to the Intel NUC forums and see if I can get something from that side. Thanks for all the help. :D

---

