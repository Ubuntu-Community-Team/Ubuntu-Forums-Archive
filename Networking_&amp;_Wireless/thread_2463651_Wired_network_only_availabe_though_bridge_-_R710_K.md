---
title: "Wired network only availabe though bridge - R710 KVM server on Ubuntu 18.04"
date: 2021-06-15
forum: Networking &amp; Wireless
---

### Post by gunner71 on 2021-06-15
Full disclosure, I'm fairly new to Linux, so please bear with me.

I've been trying to get a KVM home server set up on my R710 and I'm running into some trouble after experiencing some hardware crashes.

I had KVM set up with the network bridge working, until one day the R710 crashed due to an unrecoverable memory error. Re-seating the ram in the machine seems to have solved that problem, but the machine still would not connect to my home network. After messing with the netplan config I got the machine onto my network, however it seems to only connect through the bridge, and I am unable to start any of the VM's.

I would like to configure the server so that I can SSH into the R710 to manage virtual machines, and for each virtual machine to have an IP on my network.

Thank you in advance, I'm at my wits end here.

wireless-info:
[HTML]########## wireless info START ##########

Report from: 15 Jun 2021 20:19 UTC +0000

Booted last: 15 Jun 2021 00:00 UTC +0000

Script from: 25 Jan 2020 03:34 UTC +0000

##### release ###########################

Distributor ID: Ubuntu
Description:    Ubuntu 18.04.5 LTS
Release:        18.04
Codename:       bionic

##### kernel ############################

Linux 4.15.0-144-generic #148-Ubuntu SMP Sat May 8 02:33:43 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, maybe-ubiquity

##### desktop ###########################

sed: can't read /home/tgolding/.dmrc: No such file or directory

Could not be determined.

##### lspci #############################

01:00.0 Ethernet controller [0200]: Broadcom Inc. and subsidiaries NetXtreme II BCM5709 Gigabit Ethernet [14e4:1639] (rev 20)
        Subsystem: Dell PowerEdge R710 BCM5709 Gigabit Ethernet [1028:0235]
        Kernel driver in use: bnx2

01:00.1 Ethernet controller [0200]: Broadcom Inc. and subsidiaries NetXtreme II BCM5709 Gigabit Ethernet [14e4:1639] (rev 20)
        Subsystem: Dell PowerEdge R710 BCM5709 Gigabit Ethernet [1028:0235]
        Kernel driver in use: bnx2

02:00.0 Ethernet controller [0200]: Broadcom Inc. and subsidiaries NetXtreme II BCM5709 Gigabit Ethernet [14e4:1639] (rev 20)
        Subsystem: Dell PowerEdge R710 BCM5709 Gigabit Ethernet [1028:0235]
        Kernel driver in use: bnx2

02:00.1 Ethernet controller [0200]: Broadcom Inc. and subsidiaries NetXtreme II BCM5709 Gigabit Ethernet [14e4:1639] (rev 20)
        Subsystem: Dell PowerEdge R710 BCM5709 Gigabit Ethernet [1028:0235]
        Kernel driver in use: bnx2

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0624:0248 Avocent Corp. Virtual Hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 001 Device 002: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

./wireless-info: line 192: rfkill: command not found

##### secure boot #######################

'mokutil' is not installed (package "mokutil").

##### lsmod #############################

wmi                    24576  0

##### interfaces ########################

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq master br0 state UP group default qlen 1000
    link/ether <MAC 'eno1' [IF1]> brd <MAC address>
3: eno2: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether <MAC 'eno2' [IF2]> brd <MAC address>
4: eno3: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether <MAC 'eno3' [IF3]> brd <MAC address>
5: eno4: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether <MAC 'eno4' [IF4]> brd <MAC address>
6: br0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether <MAC 'br0' [IF5]> brd <MAC address>
    inet 192.168.2.55/24 brd 192.168.2.255 scope global dynamic br0
       valid_lft 84853sec preferred_lft 84853sec
    inet6 fe80::<IP6 'br0' [IF5]>/64 scope link
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

./wireless-info: line 230: iwconfig: command not found

##### route #############################

default via 192.168.2.1 dev br0 proto dhcp src 192.168.2.55 metric 100
192.168.2.0/24 dev br0 proto kernel scope link src 192.168.2.55
192.168.2.1 dev br0 proto dhcp scope link src 192.168.2.55 metric 100

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
    eno1:
      addresses: []
      dhcp4: true
    eno2:
      addresses: []
      dhcp4: true
      optional: true
    eno3:
      addresses: []
      dhcp4: true
      optional: true
    eno4:
      addresses: []
      dhcp4: true
      optional: true
  version: 2
  bridges:
    br0:
      interfaces: [eno1]
      dhcp4: true
      parameters:
        stp: false
        forward-delay: 0

##### iw reg get ########################

Region: Etc/UTC (based on set time zone)

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

[/etc/modprobe.d/qemu-system-x86.conf]
options kvm_intel nested=1

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   20.817783] IPv6: ADDRCONF(NETDEV_UP): br0: link is not ready
[   20.989736] bnx2 0000:02:00.1 eno4: using MSIX
[   20.990006] IPv6: ADDRCONF(NETDEV_UP): eno4: link is not ready
[   21.069336] bnx2 0000:02:00.0 eno3: using MSIX
[   21.069572] IPv6: ADDRCONF(NETDEV_UP): eno3: link is not ready
[   21.149314] bnx2 0000:01:00.1 eno2: using MSIX
[   21.149564] IPv6: ADDRCONF(NETDEV_UP): eno2: link is not ready
[   21.149869] br0: port 1(eno1) entered blocking state
[   21.149871] br0: port 1(eno1) entered disabled state
[   21.149954] device eno1 entered promiscuous mode
[   21.601338] bnx2 0000:01:00.0 eno1: using MSIX
[   21.601584] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[   21.601591] br0: port 1(eno1) entered blocking state
[   21.601593] br0: port 1(eno1) entered forwarding state
[   21.601621] IPv6: ADDRCONF(NETDEV_CHANGE): br0: link becomes ready
[   21.788800] br0: port 1(eno1) entered disabled state
[   24.769993] bnx2 0000:01:00.0 eno1: NIC Copper Link is Up, 1000 Mbps full duplex
[   24.770086] IPv6: ADDRCONF(NETDEV_CHANGE): eno1: link becomes ready
[   24.770131] br0: port 1(eno1) entered blocking state
[   24.770134] br0: port 1(eno1) entered forwarding state

########## wireless info END ############

[/HTML]

netplan config:

[HTML]# This file is generated from information provided by
# the datasource.  Changes to it will not persist across an instance.
# To disable cloud-init's network configuration capabilities, write a file
# /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following:
# network: {config: disabled}
network:
  ethernets:
    eno1:
      addresses: []
      dhcp4: true
    eno2:
      addresses: []
      dhcp4: true
      optional: true
    eno3:
      addresses: []
      dhcp4: true
      optional: true
    eno4:
      addresses: []
      dhcp4: true
      optional: true
  version: 2

  bridges:
    br0:
      interfaces: [eno1]
      dhcp4: true
      parameters:
        stp: false
        forward-delay: 0[/HTML]

ip a:

[HTML]1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq master br0 state UP group default qlen 1000
    link/ether 78:2b:cb:44:f3:e5 brd ff:ff:ff:ff:ff:ff
3: eno2: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether 78:2b:cb:44:f3:e7 brd ff:ff:ff:ff:ff:ff
4: eno3: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether 78:2b:cb:44:f3:e9 brd ff:ff:ff:ff:ff:ff
5: eno4: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether 78:2b:cb:44:f3:eb brd ff:ff:ff:ff:ff:ff
6: br0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether 7e:fa:7e:d0:47:c7 brd ff:ff:ff:ff:ff:ff
    inet 192.168.2.55/24 brd 192.168.2.255 scope global dynamic br0
       valid_lft 85457sec preferred_lft 85457sec
    inet6 fe80::7cfa:7eff:fed0:47c7/64 scope link
       valid_lft forever preferred_lft forever

[/HTML]

virt-manager error:

[HTML]Error starting domain: error creating macvtap interface macvtap0@eno1 (52:54:00:6b:a1:28): Device or resource busy

Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/asyncjob.py", line 89, in cb_wrapper
    callback(asyncjob, *args, **kwargs)
  File "/usr/share/virt-manager/virtManager/asyncjob.py", line 125, in tmpcb
    callback(*args, **kwargs)
  File "/usr/share/virt-manager/virtManager/libvirtobject.py", line 82, in newfn
    ret = fn(self, *args, **kwargs)
  File "/usr/share/virt-manager/virtManager/domain.py", line 1508, in startup
    self._backend.create()
  File "/usr/lib/python2.7/dist-packages/libvirt.py", line 1062, in create
    if ret == -1: raise libvirtError ('virDomainCreate() failed', dom=self)
libvirtError: error creating macvtap interface macvtap0@eno1 (52:54:00:6b:a1:28): Device or resource busy

[/HTML]

---

### Post by TheFu on 2021-06-15
I didn't look through all the stuff above, but have this advice.

[LIST]
[*]Don't use wifi.
[*]Don't use DHCP.
[*]Use static IPs for everything, configured on the host and inside each VM.
[*]Never use root or sudo to manage VMs via libvirt (virt-manager or virsh).
[*]Setup ssh into each Linux system.  virt-manager can be run on any other Linux workstation and used to manage the VM host system.  Use the ssh+qemu:// URL ... which sorta "just works".  The only trick is to ensure your userid is part of the libvirtd group. There are multiple ways to force this, but logout and login from a GUI will do it. No reboot needed.
[/LIST]

As for example netplan.yaml files for setting up bridges - all my VM hosts were upgraded from 16.04. They are on 18.04 and still using the *interfaces* file, so I don't have any proven file to post, but I can post some of my notes, which is what I intend to use when 20.04 becomes stable enough for VM host use.
```
# #################################
#   [ for bridge + static - KVM ]
network:
 version: 2
  renderer: [COLOR="#FF0000"]networkd[/COLOR]
  ethernets:
     [COLOR="#FF0000"]eth0[/COLOR]:
       dhcp4: [COLOR="#FF0000"]false[/COLOR]
       dhcp6: [COLOR="#FF0000"]false[/COLOR]
  bridges:
      br0:
        interfaces: [[COLOR="#FF0000"]eth0[/COLOR]]
        dhcp4: [COLOR="#FF0000"]false[/COLOR]
        dhcp6: [COLOR="#FF0000"]false[/COLOR]
        addresses: [[COLOR="#FF0000"]192.168.1.15/24[/COLOR]]
        gateway4: [COLOR="#FF0000"]192.168.1.1[/COLOR]
        nameservers:
           addresses: [[COLOR="#FF0000"]192.168.1.1[/COLOR]]
```
Change the red stuff for your system then run:
```
sudo netplan generate
sudo netplan apply --debug

```

[https://fabianlee.org/2019/04/01/kvm-creating-a-bridged-network-with-netplan-on-ubuntu-bionic/](https://fabianlee.org/2019/04/01/kvm-creating-a-bridged-network-with-netplan-on-ubuntu-bionic/)

As for ssh, that's about the easiest network daemon to get running. It sorta "just works", if you leave the defaults and stay away from non-Unix clients.

---

### Post by gunner71 on 2021-06-16
I'm not using wifi, this is all through a wired connection. 
Why not use DHCP, I read somewhere that its more desirable to use DHCP on the client machines and then set up static IP's on the DHCP server. Is this not true when working with VM's?

That worked! though I am curious as to why it worked, and why my old configuration worked for so long before causing problems. I didn't run netplan generate the first time around. Where can I go to learn more about working with KVM and netplan?


I'm guessing its because I didn't run netplan generate

---

