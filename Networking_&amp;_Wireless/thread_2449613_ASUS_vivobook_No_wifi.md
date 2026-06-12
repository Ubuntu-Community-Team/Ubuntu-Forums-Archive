---
title: "ASUS vivobook No wifi"
date: 2020-08-30
forum: Networking &amp; Wireless
---

### Post by gleble on 2020-08-30
I have just installed Ubuntu 18.04 on my new Asus E203M. It refuses to connect to my EE router. Any ideas why.
```

########## wireless info START ##########

Report from: 30 Aug 2020 14:13 BST +0100

Booted last: 30 Aug 2020 00:00 BST +0100

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 18.04.5 LTS
Release:	18.04
Codename:	bionic

##### kernel ############################

Linux 5.4.0-42-generic #46~18.04.1-Ubuntu SMP Fri Jul 10 07:21:24 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

Ubuntu

##### lspci #############################

00:0c.0 Network controller [0280]: Intel Corporation Device [8086:31dc] (rev 03)
	Subsystem: Intel Corporation Device [8086:0264]
	Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 8087:0aaa Intel Corp. 
Bus 001 Device 002: ID 0408:3040 Quanta Computer, Inc. 
Bus 001 Device 004: ID abcd:1234 Unknown 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### secure boot #######################

SecureBoot disabled

##### lsmod #############################

asus_nb_wmi            28672  0
asus_wmi               32768  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
wmi_bmof               16384  0
iwlmvm                380928  0
mac80211              851968  1 iwlmvm
libarc4                16384  1 mac80211
iwlwifi               339968  1 iwlmvm
cfg80211              712704  3 iwlmvm,iwlwifi,mac80211
wmi                    32768  2 asus_wmi,wmi_bmof
video                  49152  2 asus_wmi,i915

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
2: wlo1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether <MAC 'wlo1' [IF1]> brd <MAC address>

##### iwconfig ##########################

lo        no wireless extensions.

wlo1      IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #############################

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0

##### network managers ##################

Installed:

	NetworkManager

Running:

root       769     1  0 14:11 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon
```

---

### Post by praseodym on 2020-08-30
```
wlo1      IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=[COLOR="#FF0000"]0 dBm[/COLOR]   
          Retry short limit:7   RTS thr:off   Fragment thr:off
```

The card is turned off, however, "rfkill" shows no block. Any "real" button, switch, key or key combo? You can also try

```
echo "options asus_nb_wmi wapf=1" | sudo tee /etc/modprobe.d/asus.conf 
```
and reboot

---

