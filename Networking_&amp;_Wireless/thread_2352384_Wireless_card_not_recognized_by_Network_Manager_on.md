---
title: "Wireless card not recognized by Network Manager on Lenovo"
date: 2017-02-12
forum: Networking &amp; Wireless
---

### Post by stavrosian on 2017-02-12
I have a nice Lenovo Yoga Pro 13 that has always given me trouble with the wireless card and I replaced it twice and then it was working mostly all of 2016 on 16.04 and just recently I started using a wired connection and when I looked today at my network manager list there is no longer a WiFi option.

```

########## wireless info START ##########


Report from: 11 Feb 2017 20:49 PST -0800


Booted last: 11 Feb 2017 00:00 PST -0800


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial


##### kernel ############################


Linux 4.4.0-62-generic #83-Ubuntu SMP Wed Jan 18 14:10:15 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, noprompt, quiet, splash, elevator=deadline, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


##### lsusb #############################


Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 007: ID 5986:0535 Acer, Inc 
Bus 002 Device 006: ID 04f3:016f Elan Microelectronics Corp. 
Bus 002 Device 005: ID 2047:0855 Texas Instruments Invensense Embedded MotionApp HID Sensor
Bus 002 Device 004: ID 8087:07dc Intel Corp. 
Bus 002 Device 003: ID 2001:1a02 D-Link Corp. DUB-E100 Fast Ethernet Adapter(rev.C1) [ASIX AX88772]
Bus 002 Device 002: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no


##### lsmod #############################


cfg80211              565248  0
ideapad_laptop         24576  0
sparse_keymap          16384  1 ideapad_laptop
wmi                    20480  1 ideapad_laptop
video                  40960  2 i915,ideapad_laptop


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enx<IF from MAC [IF1]> Link encap:Ethernet  HWaddr <MAC 'enx<IF from MAC [IF1]>' [IF1]>  
          inet addr:192.168.1.72  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::dbca:4571:e915:26c3/64 Scope:Link
          inet6 addr: 2602:304:686d:5cb0:cdac:5195:487b:701a/64 Scope:Global
          inet6 addr: 2602:304:686d:5cb0:af6e:113c:5269:6835/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4265 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3459 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1538212 (1.5 MB)  TX bytes:1614636 (1.6 MB)


##### iwconfig ##########################


lo        no wireless extensions.


enx<IF from MAC [IF1]>  no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    100    0        0 enx<IF from MAC [IF1]>
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enx<IF from MAC [IF1]>
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enx<IF from MAC [IF1]>


##### resolv.conf #######################


nameserver 127.0.1.1
search attlocal.net


##### network managers ##################


Installed:


    NetworkManager


Running:


root      1187     1  0 20:23 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enx<IF from MAC [IF1]>
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         D-Link          
GENERAL.PRODUCT:                        DUB-E100
GENERAL.DRIVER:                         asix
GENERAL.DRIVER-VERSION:                 22-Dec-2011
GENERAL.FIRMWARE-VERSION:               ASIX AX88772 USB 2.0 Ethernet
GENERAL.HWADDR:                         <MAC 'enx<IF from MAC [IF1]>' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb2/2-2/2-2:1.0/net/enx<IF from MAC [IF1]>
GENERAL.IP-IFACE:                       enx<IF from MAC [IF1]>
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       02d04e6b-77fe-3a8e-9116-f299f3937967
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{38}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   02d04e6b-77fe-3a8e-9116-f299f3937967 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.72/24
IP4.GATEWAY:                            192.168.1.254
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.254
IP4.DOMAIN[1]:                          attlocal.net
DHCP4.OPTION[1]:                        requested_ms_classless_static_routes = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 192.168.1.254
DHCP4.OPTION[11]:                       expiry = 1486959835
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 192.168.1.254
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 192.168.1.72
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       domain_name = attlocal.net
DHCP4.OPTION[19]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.1.254
DHCP4.OPTION[23]:                       requested_ntp_servers = 1
DHCP4.OPTION[24]:                       dhcp_lease_time = 86400
DHCP4.OPTION[25]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[26]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[27]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[28]:                       network_number = 192.168.1.0
DHCP4.OPTION[29]:                       requested_routers = 1
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.1.254
IP6.ADDRESS[1]:                         2602:304:686d:5cb0:cdac:5195:487b:701a/64
IP6.ADDRESS[2]:                         2602:304:686d:5cb0:af6e:113c:5269:6835/64
IP6.ADDRESS[3]:                         fe80::dbca:4571:e915:26c3/64
IP6.GATEWAY:                            fe80::16ed:bbff:fe64:68e5
IP6.DNS[1]:                             2602:304:686d:5cb0::1


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/SD_CO_LIBRARY]] (600 root)
[connection] id=SD_CO_LIBRARY | type=wifi | permissions=user:stav:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=SD_CO_LIBRARY
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ATT5B5r4s2]] (600 root)
[connection] id=ATT5B5r4s2 | type=wifi | permissions=user:stav:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=ATT5B5r4s2
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Los_Angeles (based on set time zone)


country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)


##### iwlist channels ###################


lo        no frequency information.


enx<IF from MAC [IF1]>  no frequency information.


##### iwlist scan #######################


lo        Interface doesn't support scanning.


enx<IF from MAC [IF1]>  Interface doesn't support scanning.


##### module infos ######################


[cfg80211]
filename:       /lib/modules/4.4.0-62-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     902BDA34A9B6BB2AE64F135
depends:        
intree:         Y
vermagic:       4.4.0-62-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


##### modprobe options ##################


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


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


for user in stav; do
  DIR=/tmp/$user/cache/chromium
  sudo -u $user -- sh -c "mkdir -p $DIR && chmod -R 700 /tmp/$user"
done


exit 0


##### pm-utils ##########################


[/etc/pm/sleep.d/00_check_touchpad_status] (755 root)
LOGFILE="/var/log/sleep.log"
case "$1" in
        resume|thaw)
                echo "Resumed normal from suspend at `date`" >> "$LOGFILE"
                /usr/bin/python3 /opt/extras.ubuntu.com/touchpad-indicator/share/touchpad-indicator/check_touchpad_status.py resume
                echo "Touchpad enabled"
                ;;
esac


##### udev rules ########################


##### dmesg #############################


[    5.020136] asix 2-2:1.0 eth0: register 'asix' at usb-0000:00:14.0-2, ASIX AX88772 USB 2.0 Ethernet, <MAC 'enx<IF from MAC [IF1]>' [IF1]>
[    5.022007] asix 2-2:1.0 enx<IF from MAC [IF1]>: renamed from eth0
[    5.040112] IPv6: ADDRCONF(NETDEV_UP): enx<IF from MAC [IF1]>: link is not ready
[    5.040484] asix 2-2:1.0 enx<IF from MAC [IF1]>: link down
[    5.041041] IPv6: ADDRCONF(NETDEV_UP): enx<IF from MAC [IF1]>: link is not ready
[    6.774125] IPv6: ADDRCONF(NETDEV_CHANGE): enx<IF from MAC [IF1]>: link becomes ready
[    6.774503] asix 2-2:1.0 enx<IF from MAC [IF1]>: link up, 100Mbps, full-duplex, lpa 0xCDE1
[   84.809284] [UFW BLOCK] IN=enx<IF from MAC [IF1]> OUT= MAC=01:00:5e:00:00:01:14:ed:bb:64:68:e5:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2  (repeated 12 times)


########## wireless info END ############

```

Can anyone help get my wireless working again?

---

### Post by wildmanne39 on 2017-02-12
This is an internal card correct? if so it is not showing at all which means it has gone out, came loose, or you might need to reset the bios if it is not UEFI. If it is a broadcom card that uses the wl driver go into the bios and turn security boot off then it should work.

---

### Post by stavrosian on 2017-02-12
Thanks for the info. Yes, this is an internal PCI card and I just checked to make sure it is well seated and that I have secure boot off.  The BIOS is indeed UEFI and wireless is enabled.

So I guess what that means is that I need to buy a new card.

---

### Post by wildmanne39 on 2017-02-12
Unless the contacts are dirty, but there is not anything we can do but make suggestions when the card does not even show up, I have had one wireless card go out before, I bought a little usb adapter that was so small it did not get in the way since it was on a laptop.

---

### Post by jeremy31 on 2017-02-12
Shut down the computer and use the Novo button to go into BIOS settings, see if wifi, WLAN or whatever is disabled there.  Use reset to defaults if necessary

---

### Post by stavrosian on 2017-02-18
I opened up the laptop and made sure the two wires were tight and rebooted, still the card was not recognized. Then today (five days later) the card is now recognized but Network Manager says "device not ready."  I have a new card I will install and see if that helps.

Jeremy, thanks yeah, Wireless is enabled in BIOS.

// attaching new wireless-info
// note: I'm using a D-Link DUB-E100 USB wired dongle for network access at the moment.

---

### Post by jeremy31 on 2017-02-18
Unplug the ethernet cable and see if ```
sudo ifconfig wlp1s0 up
```
Makes the wireless work and check ```
ifconfig
```
See if the interface wlp1s0 says something about UP like your enx device did in the script results

```
enx<IF from MAC [IF1]> Link encap:Ethernet  HWaddr <MAC 'enx<IF from MAC [IF1]>' [IF1]>  
          inet addr:192.168.1.72  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::dbca:4571:e915:26c3/64 Scope:Link
          inet6 addr: 2602:304:686d:5cb0:b4d4:95a0:c030:15c3/64 Scope:Global
          inet6 addr: 2602:304:686d:5cb0:af6e:113c:5269:6835/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8622 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6915109 (6.9 MB)  TX bytes:1765585 (1.7 MB)

wlp1s0    Link encap:Ethernet  HWaddr <MAC 'wlp1s0' [IF2]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

---

### Post by stavrosian on 2017-02-18
I'm logged in now using the WiFi card, so it's working now.

I think the solution was physically re-seating the card.

Thanks for your help guys.

```
stav@venix:~$ sudo ifconfig wlp1s0 up[sudo] password for stav: 
stav@venix:~$ ifconfig
enx78542ee5c627 Link encap:Ethernet  HWaddr 78:54:2e:e5:c6:27  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:772 errors:0 dropped:0 overruns:0 frame:0
          TX packets:772 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:58180 (58.1 KB)  TX bytes:58180 (58.1 KB)


wlp1s0    Link encap:Ethernet  HWaddr 7c:7a:91:95:db:66  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by wildmanne39 on 2017-02-19
Glad you got it working!
Enjoy!

---

