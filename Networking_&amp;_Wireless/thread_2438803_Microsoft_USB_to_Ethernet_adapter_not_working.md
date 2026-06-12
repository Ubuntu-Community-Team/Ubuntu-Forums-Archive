---
title: "Microsoft USB to Ethernet adapter not working"
date: 2020-03-18
forum: Networking &amp; Wireless
---

### Post by widert on 2020-03-18
[COLOR=#242729][FONT=Arial]Unfortunately, I am not able to configure the Microsoft USB to ethernet adapter. [/FONT][/COLOR][COLOR=#242729][FONT=Arial]Output from ifconfig -a:
[/FONT][/COLOR]
```
wide@wideServer:~$ ifconfig -a
enp3s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.50.41  netmask 255.255.255.0  broadcast 192.168.50.255
        inet6 fe80::7285:c2ff:fea9:b1bc  prefixlen 64  scopeid 0x20<link>
        ether 70:85:c2:a9:b1:bc  txqueuelen 1000  (Ethernet)
        RX packets 12446  bytes 6416808 (6.4 MB)
        RX errors 0  dropped 711  overruns 0  frame 0
        TX packets 3650  bytes 339732 (339.7 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

enxc0335eee724f: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether c0:33:5e:ee:72:4f  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 35713  bytes 15210508 (15.2 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 35713  bytes 15210508 (15.2 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

[COLOR=#242729][FONT=Arial]Output from lsusb:[/FONT][/COLOR]
```
wide@wideServer:~$ lsusb
Bus 002 Device 002: ID 045e:07c6 Microsoft Corp.
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```[COLOR=#242729][FONT=Arial]What can I do to get the adapter up and running?[/FONT][/COLOR]

---

### Post by TheFu on 2020-03-18
Looks like enxc0335eee724f is the interface.  Disable the wired interface, enp3s0, first?  Try again.

BTW, that wired interface is dropping packets. That isn't good.  I'd fix that first, but I avoid using any wifi stuff whenever possible.
There is a sticky thread at the top of this sub-forum with a data gathering script.  Think it is called wifi-info or something similar.  Get that, run it, post the results.  Thanks very much for using code tags!

---

### Post by widert on 2020-03-19
> **TheFu said:**
> Looks like enxc0335eee724f is the interface.  Disable the wired interface, enp3s0, first?  Try again.

BTW, that wired interface is dropping packets. That isn't good.  I'd fix that first, but I avoid using any wifi stuff whenever possible.
There is a sticky thread at the top of this sub-forum with a data gathering script.  Think it is called wifi-info or something similar.  Get that, run it, post the results.  Thanks very much for using code tags!

Thanks for the reply. You are right about the interface, tried to disable enp3s0 but no changes.
Packets: I'll try another network cable, maybe that will help.
Output from script:
```
[COLOR=#000000]########## wireless info START ##########[/COLOR]
Report from: 18 Mar 2020 15:21 CET +0100

Booted last: 18 Mar 2020 00:00 CET +0100

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.4 LTS
Release:    18.04
Codename:    bionic

##### kernel ############################

Linux 4.15.0-91-generic #92-Ubuntu SMP Fri Feb 28 11:09:48 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro

##### desktop ###########################

sed: can't read /home/wide/.dmrc: No such file or directory

Could not be determined.

##### lspci #############################

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: ASRock Incorporation Motherboard (one of many) [1849:8168]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 002: ID 045e:07c6 Microsoft Corp. 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

./wireless-info: line 192: rfkill: command not found

##### secure boot #######################

SecureBoot disabled
Platform is in Setup Mode

##### lsmod #############################

##### interfaces ########################

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'enp3s0' [IF1]> brd <MAC address>
    inet 192.168.50.41/24 brd 192.168.50.255 scope global dynamic enp3s0
       valid_lft 76710sec preferred_lft 76710sec
    inet6 fe80::<IP6 'enp3s0' [IF1]>/64 scope link 
       valid_lft forever preferred_lft forever
3: enx<IF from MAC [IF2]>: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'enx<IF from MAC [IF2]>' [IF2]> brd <MAC address>
    inet6 fe80::<IP6 'enx<IF from MAC [IF2]>' [IF2]>/64 scope link 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

./wireless-info: line 230: iwconfig: command not found

##### route #############################

default via 192.168.50.1 dev enp3s0 proto dhcp src 192.168.50.41 metric 100 
192.168.50.0/24 dev enp3s0 proto kernel scope link src 192.168.50.41 
192.168.50.1 dev enp3s0 proto dhcp scope link src 192.168.50.41 metric 100 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0

##### network managers ##################

Installed:

    None found.

Running:

    None found.

##### NetworkManager info ###############

NetworkManager is not installed (package "network-manager").

##### NetworkManager.state ##############

cat: /var/lib/NetworkManager/NetworkManager.state: No such file or directory

##### NetworkManager config #############

##### NetworkManager profiles ###########

No NetworkManager profiles found.

##### Netplan config ####################

[/etc/netplan/50-cloud-init.yaml]
network:
    ethernets:
        enp3s0:
            dhcp4: true
    version: 2

##### iw reg get ########################

Region: Europe/Oslo (based on set time zone)

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

'iwlist' is not installed (package "wireless-tools").

##### iwlist scan #######################

'iwlist' is not installed (package "wireless-tools").

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

[/etc/modprobe.d/mdadm.conf]
options md_mod start_ro=1

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[    7.912410] systemd[1]: Listening on Network Service Netlink Socket.
[    9.764618] r8152 2-4:1.0 eth0: v1.09.9
[    9.860934] r8152 2-4:1.0 enx<IF from MAC [IF2]>: renamed from eth0
[   12.838681] r8169 0000:03:00.0 enp3s0: link down (repeated 2 times)
[   12.838823] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[   16.794200] r8169 0000:03:00.0 enp3s0: link up
[   16.794211] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready
[ 6181.726212] IPv6: ADDRCONF(NETDEV_UP): enx<IF from MAC [IF2]>: link is not ready
[ 6181.749219] r8152 2-4:1.0 enx<IF from MAC [IF2]>: carrier on
[ 6181.749368] IPv6: ADDRCONF(NETDEV_CHANGE): enx<IF from MAC [IF2]>: link becomes ready

########## wireless info END ############



```

---

### Post by TheFu on 2020-03-19
Did you install "server", not "desktop"?

None of the normal desktop wifi tools are available, appears they aren't installed.  Hard to do wifi stuff without those.

---

### Post by chili555 on 2020-03-19
Please detach the ethernet cable from the internal ethernet port and attach it to the USB device.

Next, do:

```
sudo nano /etc/netplan/50-cloud-init.yaml
```Change it to read:
```

network:
  version: 2
  renderer: networkd
  ethernets:
    enxc0335eee724f:
      dhcp4: true
```Indentation and spacing are very important; please proofread twice. Save (Ctrl+o) and exit (Ctrl+x) the text editor. Follow with:
```
sudo netplan generate
sudo netplan apply
```You should be all set. It may, however, take a reboot.

---

### Post by TheFu on 2020-03-19
> **TheFu said:**
> Did you install "server", not "desktop"?

None of the normal desktop wifi tools are available, appears they aren't installed.  Hard to do wifi stuff without those.

**UPDATE: - wow, just goes to show how much sleep I needed!  Sorry. Don't know where the wifi came from.**
What's really bad is that I use a usb-2-GigE adapter here too!  So sorry.

---

