---
title: "Will not install: Asus Usb-ax56 Dual Band Ax1800"
date: 2023-05-25
forum: Networking &amp; Wireless
---

### Post by littlehome2 on 2023-05-25
Pretty sure I have exhausted all the posts. Still not working:
Ubuntu 22.04 LTS (no GNOME)

lsusb: Bus 001 Device 002: ID 0b05:1997 ASUSTek Computer, Inc. 802.11ac WLAN Adapter



sudo apt update
sudo apt install build-essential git dkms
git clone [https://github.com/aircrack-ng/rtl8812au.git](https://github.com/aircrack-ng/rtl8812au.git)
cd rtl8812au
sudo make dkms_install
sudo modprobe 88XXau

<no errors reported>

iwconfig:
lo        no wireless extensions.
[COLOR=var(--black-800)][FONT=var(--ff-mono)]eno1      no wireless extensions.[/FONT][/COLOR]
[COLOR=var(--black-800)][FONT=var(--ff-mono)]br0       no wireless extensions.[/FONT][/COLOR]
[COLOR=var(--black-800)][FONT=var(--ff-mono)]virbr0    no wireless extensions.[/FONT][/COLOR]

Totally new to linux, but all else has been good so far and love it as a server. Need the wifi for speed as 10Gbe is not an option for some clients.

Surely we can solve this? If not, tell me if a TPLink "[COLOR=var(--black-800)][FONT=var(--ff-mono)]Wireless Pcie Adapter (Wifi Card) Tp-link Archer Tx3000e Ax3000" will install out of the box?

Tired... cheers, and hope I can return the favor some day. Spend a day on this already.

[/FONT][/COLOR]

---

### Post by chili555 on 2023-05-25
The correct driver for this device is here: [https://github.com/lwfinger/rtl8852au](https://github.com/lwfinger/rtl8852au)

```
$ modinfo 8852au.ko | grep 1997
alias:          usb:v[COLOR="#FF0000"]0B05[/COLOR]p[COLOR="#FF0000"]1997[/COLOR]d*dc*dsc*dp*icFFiscFFipFFin*
```Post back if you need step-by-step instructions.

---

### Post by littlehome2 on 2023-05-26
Ur awesome, chili. I saw you in many posts.

modinfo: ERROR: Module 8852au.ko not found.

This is an AMD Ryzen 9 if that helps.

---

### Post by chili555 on 2023-05-26
Did you actually build and install the correct driver?

```
git clone https://github.com/lwfinger/rtl8852au.git
cd rtl8852au/
make
sudo make install 
sudo modprobe 8852au
```Also, please note from the README:

> When you get a new kernel, you will need to rebuild the driver. Do the following:
  cd rtl8852au
  git pull
  make
  sudo make install
You will know you've gotten a new kernel when Udate Manager requests a reboot and then the wifi no longer works.

Please retain the rtl8852au directory and these instructions for that time.

---

### Post by sgt-mike on 2024-03-19
found this thread because I had obtained one of these expecting it to work when I was setting up a headless server it didn't. with finding this thread my hopes soared.
so I attempted to install the driver

```
[mike@bastion:~$ git clone https://github.com/lwfinger/rtl8852au.git
Cloning into 'rtl8852au'...
remote: Enumerating objects: 1418, done.
remote: Counting objects: 100% (99/99), done.
remote: Compressing objects: 100% (44/44), done.
remote: Total 1418 (delta 59), reused 58 (delta 55), pack-reused 1319
Receiving objects: 100% (1418/1418), 10.99 MiB | 1.04 MiB/s, done.
Resolving deltas: 100% (590/590), done.
mike@bastion:~$ cd rtl8852au/
mike@bastion:~/rtl8852au$ ls
clean       core       document       include  Makefile  phl    README.md      runwpa         wlan0dhcp
common.mk  dkms.conf  ifcfg-wlan0  Kconfig  os_dep    platform    ReleaseNotes.pdf  suspend_rtw8852au
mike@bastion:~/rtl8852au$ make
/bin/sh: 1: cc: not found
(standard_in) 1: syntax error
#rm -f .symvers.8852au
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/5.15.0-101-generic/build M=/home/mike/rtl8852au  modules
make[1]: Entering directory '/usr/src/linux-headers-5.15.0-101-generic'
arch/x86/Makefile:142: CONFIG_X86_X32 enabled but no binutils support
make[1]: gcc: No such file or directory
warning: the compiler differs from the one used to build the kernel
  The kernel was built by: gcc (Ubuntu 11.4.0-1ubuntu1~22.04) 11.4.0
  You are using:           
/bin/sh: 1: gcc: not found
(standard_in) 1: syntax error
  CC [M]  /home/mike/rtl8852au/os_dep/osdep_service.o
/bin/sh: 1: gcc: not found
make[2]: *** [scripts/Makefile.build:297: /home/mike/rtl8852au/os_dep/osdep_service.o] Error 127
make[1]: *** [Makefile:1911: /home/mike/rtl8852au] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-5.15.0-101-generic'
make: *** [Makefile:639: modules] Error 2
mike@bastion:~/rtl8852au$ sudo make install 
/bin/sh: 1: cc: not found
(standard_in) 1: syntax error
install -p -m 644 8852au.ko  /lib/modules/5.15.0-101-generic/kernel/drivers/net/wireless/realtek/rtw89/
install: cannot stat '8852au.ko': No such file or directory
make: *** [Makefile:649: install] Error 1
mike@bastion:~/rtl8852au$ sudo modprobe 8852au
modprobe: FATAL: Module 8852au not found in directory /lib/modules/5.15.0-101-generic
mike@bastion:~/rtl8852au$ 

```

thoughts? suggestions?  other than buying a different usb wireless adapter

I did find one Asus usb wifi that stated it would work with Linux  [https://www.asus.com/us/networking-iot-servers/adapters/all-series/usb-n13-c1/](https://www.asus.com/us/networking-iot-servers/adapters/all-series/usb-n13-c1/)     
Which if we cant get this one working I'll locate one of those

---

### Post by sgt-mike on 2024-03-19
Wireless Info txt
```

########## wireless info START ##########

Report from: 19 Mar 2024 06:51 CDT -0500

Booted last: 19 Mar 2024 00:00 CDT -0500

Script from: 25 Jan 2020 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 22.04.4 LTS
Release:    22.04
Codename:    jammy

##### kernel ############################

Linux 5.15.0-101-generic #111-Ubuntu SMP Tue Mar 5 20:16:58 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro

##### desktop ###########################

sed: can't read /home/mike/.dmrc: No such file or directory

Could not be determined.

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection (Lewisville) [8086:1502] (rev 04)
    DeviceName:  Onboard LAN
    Subsystem: Dell 82579LM Gigabit Network Connection (Lewisville) [1028:047e]

##### lsusb #############################

Bus 002 Device 003: ID 0b05:1a62 ASUSTek Computer, Inc. 802.11ax WLAN Adapter
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

./wireless-info: line 192: rfkill: command not found

##### secure boot #######################

This system doesn't support Secure Boot

##### lsmod #############################

##### interfaces ########################

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'eno1' [IF1]> brd <MAC address>
    altname enp0s25
    inet 192.168.1.130/24 metric 100 brd 192.168.1.255 scope global dynamic eno1
       valid_lft 81176sec preferred_lft 81176sec
    inet6 fe80::<IP6 'eno1' [IF1]>/64 scope link 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

./wireless-info: line 230: iwconfig: command not found

##### route #############################

default via 192.168.1.1 dev eno1 proto dhcp src 192.168.1.130 metric 100 
192.168.1.0/24 dev eno1 proto kernel scope link src 192.168.1.130 metric 100 
192.168.1.1 dev eno1 proto dhcp scope link src 192.168.1.130 metric 100 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0 trust-ad
search .

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

grep: /etc/netplan/00-installer-config.yaml: Permission denied

##### iw reg get ########################

'iw' is not installed (package "iw").

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

[ 2754.868407] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:38:1a:52:4f:da:1e:08:00 SRC=192.168.1.25 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 2800.743779] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=31811 PROTO=2 
[ 2875.700801] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 2875.702118] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[ 2877.214882] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:20:0c:c8:45:93:d1:08:00 SRC=192.168.1.250 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 2879.387519] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 2933.047568] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=31816 PROTO=2 
[ 3001.039392] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 3001.040485] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[ 3001.652724] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:20:0c:c8:45:93:d1:08:00 SRC=192.168.1.250 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 3003.908100] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 3126.377606] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 3126.378857] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[ 3128.015961] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:80:5b:65:bf:e1:74:08:00 SRC=192.168.1.6 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 3134.979199] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 3180.854771] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=31828 PROTO=2 
[ 3251.718953] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 3251.720098] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[ 3255.403280] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:70:8b:cd:2e:2d:b2:08:00 SRC=192.168.1.14 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=23748 PROTO=2 
[ 3303.735634] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=31834 PROTO=2 
[ 3377.469792] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 3377.470803] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[ 3379.413923] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:20:0c:c8:45:93:d1:08:00 SRC=192.168.1.250 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 3386.066403] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 3429.893410] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=31839 PROTO=2 
[ 3502.809938] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 3502.811128] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[ 3504.440750] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:70:8b:cd:2e:2d:b2:08:00 SRC=192.168.1.14 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=23765 PROTO=2 
[ 3505.670063] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 3558.115366] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=31844 PROTO=2 
[ 3628.140677] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 3628.141990] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[ 3628.325274] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:20:0c:c8:45:93:d1:08:00 SRC=192.168.1.250 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 3628.960581] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 3678.521834] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=31849 PROTO=2 
[ 3753.479014] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 3753.480332] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[ 3753.515175] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:20:0c:c8:45:93:d1:08:00 SRC=192.168.1.250 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 3754.298190] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 3804.680984] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=31854 PROTO=2 
[ 3879.227086] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 3879.228241] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[ 3883.323475] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:38:1a:52:4f:da:1e:08:00 SRC=192.168.1.25 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 3883.324316] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:80:5b:65:bf:e1:74:08:00 SRC=192.168.1.6 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 3887.828723] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 3933.297752] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=31859 PROTO=2 
[ 4004.567612] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 4004.568630] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[ 4004.569502] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:70:8b:cd:2e:2d:b2:08:00 SRC=192.168.1.14 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=23798 PROTO=2 
[ 4009.891370] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 4056.585736] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=31864 PROTO=2 
[ 4129.903865] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 4129.904953] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[ 4131.547275] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 4183.562390] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=31872 PROTO=2 
[ 4255.242158] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 4255.243289] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[ 4256.064045] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 4262.206348] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:38:1a:52:4f:da:1e:08:00 SRC=192.168.1.25 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 4310.567308] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=31877 PROTO=2 
[ 4380.990212] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 4380.991249] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[ 4380.992137] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:70:8b:cd:2e:2d:b2:08:00 SRC=192.168.1.14 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=23823 PROTO=2 
[ 4388.772685] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 4429.734420] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=31882 PROTO=2 
[ 4506.328486] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 4506.329658] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[ 4511.243905] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:70:8b:cd:2e:2d:b2:08:00 SRC=192.168.1.14 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=23832 PROTO=2 
[ 4512.062900] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 4563.672976] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=31891 PROTO=2 
[ 4631.666915] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 4631.668015] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[ 4632.076577] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:80:5b:65:bf:e1:74:08:00 SRC=192.168.1.6 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 4639.864164] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 4684.915675] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=31896 PROTO=2 
[ 4757.010409] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 4757.011458] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[ 4760.282764] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:80:5b:65:bf:e1:74:08:00 SRC=192.168.1.6 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 4765.197270] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 4807.386964] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=31901 PROTO=2 
[ 4882.756403] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 4882.757597] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[ 4883.626621] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:20:0c:c8:45:93:d1:08:00 SRC=192.168.1.250 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 4884.392680] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:38:1a:52:4f:da:1e:08:00 SRC=192.168.1.25 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 4884.802604] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 4939.278431] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=31906 PROTO=2 
[ 5008.091625] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 5008.092650] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[ 5009.320329] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 5013.417390] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:38:1a:52:4f:da:1e:08:00 SRC=192.168.1.25 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 5060.111202] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=31911 PROTO=2 
[ 5133.430102] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 5133.431318] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[ 5133.839404] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:38:1a:52:4f:da:1e:08:00 SRC=192.168.1.25 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 5142.445366] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 5186.269872] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=31919 PROTO=2 
[ 5258.768255] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 5258.769378] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[ 5259.177761] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:70:8b:cd:2e:2d:b2:08:00 SRC=192.168.1.14 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=23881 PROTO=2 
[ 5260.817111] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 

########## wireless info END ############


```

---

### Post by sgt-mike on 2024-03-19
I noticed some packages was not installed so I installed them re-ran the wireless info txt
```
######### wireless info START ##########

Report from: 19 Mar 2024 07:06 CDT -0500

Booted last: 19 Mar 2024 00:00 CDT -0500

Script from: 25 Jan 2020 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 22.04.4 LTS
Release:    22.04
Codename:    jammy

##### kernel ############################

Linux 5.15.0-101-generic #111-Ubuntu SMP Tue Mar 5 20:16:58 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro

##### desktop ###########################

sed: can't read /home/mike/.dmrc: No such file or directory

Could not be determined.

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection (Lewisville) [8086:1502] (rev 04)
    DeviceName:  Onboard LAN
    Subsystem: Dell 82579LM Gigabit Network Connection (Lewisville) [1028:047e]

##### lsusb #############################

Bus 002 Device 003: ID 0b05:1a62 ASUSTek Computer, Inc. 802.11ax WLAN Adapter
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

./wireless-info: line 192: rfkill: command not found

##### secure boot #######################

This system doesn't support Secure Boot

##### lsmod #############################

##### interfaces ########################

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'eno1' [IF1]> brd <MAC address>
    altname enp0s25
    inet 192.168.1.130/24 metric 100 brd 192.168.1.255 scope global dynamic eno1
       valid_lft 80278sec preferred_lft 80278sec
    inet6 fe80::<IP6 'eno1' [IF1]>/64 scope link 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

lo        no wireless extensions.

eno1      no wireless extensions.

##### route #############################

default via 192.168.1.1 dev eno1 proto dhcp src 192.168.1.130 metric 100 
192.168.1.0/24 dev eno1 proto kernel scope link src 192.168.1.130 metric 100 
192.168.1.1 dev eno1 proto dhcp scope link src 192.168.1.130 metric 100 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0 trust-ad
search .

##### network managers ##################

Installed:

    NetworkManager

Running:

root       12078       1  0 07:01 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/2
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        82579LM Gigabit Network Connection (Lewisville)
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 5.15.0-101-generic
GENERAL.FIRMWARE-VERSION:               0.13-4
GENERAL.HWADDR:                         <MAC 'eno1' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          10 (unmanaged)
GENERAL.REASON:                         0 (No reason given)
GENERAL.IP4-CONNECTIVITY:               0 (unknown)
GENERAL.IP6-CONNECTIVITY:               0 (unknown)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:19.0/net/eno1
GENERAL.PATH:                           pci-0000:00:19.0
GENERAL.IP-IFACE:                       eno1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     no
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
INTERFACE-FLAGS.UP:                     yes
INTERFACE-FLAGS.LOWER-UP:               yes
INTERFACE-FLAGS.CARRIER:                yes
INTERFACE-FLAGS.PROMISC:                no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.1.130/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.1.1, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.1.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 192.168.1.1/32, nh = 0.0.0.0, mt = 100
IP6.ADDRESS[1]:                         fe80::<IP6 'eno1' [IF1]>/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = fe80::/64, nh = ::, mt = 256
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --

##### NetworkManager.state ##############

cat: /var/lib/NetworkManager/NetworkManager.state: No such file or directory

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
[device-31-mac-addr-change]
match-device=driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no

##### NetworkManager profiles ###########

##### Netplan config ####################

grep: /etc/netplan/00-installer-config.yaml: Permission denied

##### iw reg get ########################

Region: America/Indiana/Tell_City (based on set time zone)

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

[ 3879.227086] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 3879.228241] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[ 3883.323475] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:38:1a:52:4f:da:1e:08:00 SRC=192.168.1.25 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 3883.324316] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:80:5b:65:bf:e1:74:08:00 SRC=192.168.1.6 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 3887.828723] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 3933.297752] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=31859 PROTO=2 
[ 4004.567612] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 4004.568630] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[ 4004.569502] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:70:8b:cd:2e:2d:b2:08:00 SRC=192.168.1.14 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=23798 PROTO=2 
[ 4009.891370] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 4056.585736] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=31864 PROTO=2 
[ 4129.903865] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 4129.904953] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[ 4131.547275] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 4183.562390] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=31872 PROTO=2 
[ 4255.242158] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 4255.243289] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[ 4256.064045] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 4262.206348] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:38:1a:52:4f:da:1e:08:00 SRC=192.168.1.25 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 4310.567308] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=31877 PROTO=2 
[ 4380.990212] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 4380.991249] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[ 4380.992137] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:70:8b:cd:2e:2d:b2:08:00 SRC=192.168.1.14 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=23823 PROTO=2 
[ 4388.772685] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 4429.734420] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=31882 PROTO=2 
[ 4506.328486] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 4506.329658] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[ 4511.243905] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:70:8b:cd:2e:2d:b2:08:00 SRC=192.168.1.14 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=23832 PROTO=2 
[ 4512.062900] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 4563.672976] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=31891 PROTO=2 
[ 4631.666915] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 4631.668015] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[ 4632.076577] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:80:5b:65:bf:e1:74:08:00 SRC=192.168.1.6 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 4639.864164] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 4684.915675] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=31896 PROTO=2 
[ 4757.010409] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 4757.011458] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[ 4760.282764] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:80:5b:65:bf:e1:74:08:00 SRC=192.168.1.6 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 4765.197270] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 4807.386964] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=31901 PROTO=2 
[ 4882.756403] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 4882.757597] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[ 4883.626621] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:20:0c:c8:45:93:d1:08:00 SRC=192.168.1.250 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 4884.392680] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:38:1a:52:4f:da:1e:08:00 SRC=192.168.1.25 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 4884.802604] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 4939.278431] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=31906 PROTO=2 
[ 5008.091625] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 5008.092650] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[ 5009.320329] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 5013.417390] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:38:1a:52:4f:da:1e:08:00 SRC=192.168.1.25 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 5060.111202] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=31911 PROTO=2 
[ 5133.430102] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 5133.431318] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[ 5133.839404] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:38:1a:52:4f:da:1e:08:00 SRC=192.168.1.25 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 5142.445366] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 5186.269872] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=31919 PROTO=2 
[ 5258.768255] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 5258.769378] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[ 5259.177761] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:70:8b:cd:2e:2d:b2:08:00 SRC=192.168.1.14 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=23881 PROTO=2 
[ 5260.817111] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 5315.748997] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=31924 PROTO=2 
[ 5384.516121] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 5384.517342] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[ 5386.973679] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:38:1a:52:4f:da:1e:08:00 SRC=192.168.1.25 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 5387.793049] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 5438.587148] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=31929 PROTO=2 
[ 5509.854756] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 5509.855945] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[ 5510.264190] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:70:8b:cd:2e:2d:b2:08:00 SRC=192.168.1.14 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=23902 PROTO=2 
[ 5519.277625] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 5559.416467] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=31934 PROTO=2 
[ 5635.195144] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 5635.196212] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[ 5640.107981] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:70:8b:cd:2e:2d:b2:08:00 SRC=192.168.1.14 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=23915 PROTO=2 
[ 5640.108944] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 5691.719014] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=31939 PROTO=2 
[ 5760.531451] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 5760.532498] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[ 5764.628984] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:80:5b:65:bf:e1:74:08:00 SRC=192.168.1.6 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 5767.904841] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 5817.876625] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=31944 PROTO=2 
[ 5886.279269] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 5886.280444] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[ 5886.688919] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:70:8b:cd:2e:2d:b2:08:00 SRC=192.168.1.14 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=23932 PROTO=2 
[ 5886.689714] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:38:1a:52:4f:da:1e:08:00 SRC=192.168.1.25 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 5887.508402] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 5940.354203] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=31949 PROTO=2 
[ 6011.617650] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 6011.618362] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[ 6014.484723] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:70:8b:cd:2e:2d:b2:08:00 SRC=192.168.1.14 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=23941 PROTO=2 
[ 6016.123127] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 6063.227701] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=31954 PROTO=2 
[ 6136.956067] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 6136.957109] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[ 6138.185805] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:70:8b:cd:2e:2d:b2:08:00 SRC=192.168.1.14 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=23950 PROTO=2 
[ 6143.921225] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 

########## wireless info END ############


```     
will attempt to try a install as listed above again

---

### Post by sgt-mike on 2024-03-19
still no success
even though I thought I found the answer being my gcc version being set at 11 vs 12.
Updated the gcc to 12 and it did get closer to installing. 
I some how deleted my earlier post when I went to edit the post with this message.

---

### Post by chili555 on 2024-03-19
> /bin/sh: 1: gcc: not found
make[2]: *** [scripts/Makefile.build:297: /home/mike/rtl8852au/os_dep/osdep_service.o] Error 127
make[1]: *** [Makefile:1911: /home/mike/rtl8852au] Error 2I think you missed the step in the very first post:

```
sudo apt update
sudo apt install build-essential git dkms
```Then try to compile the driver again.

---

### Post by sgt-mike on 2024-03-19
OK got the driver to compile 
ran lsusb  and seen the adapter on the usb port I also noticed that the wifi powersave was set at 3 I changed it to 2 (sudo nano /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf)
here is wireless-info txt
```

########## wireless info START ##########

Report from: 19 Mar 2024 09:15 CDT -0500

Booted last: 19 Mar 2024 00:00 CDT -0500

Script from: 25 Jan 2020 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 22.04.4 LTS
Release:    22.04
Codename:    jammy

##### kernel ############################

Linux 5.15.0-101-generic #111-Ubuntu SMP Tue Mar 5 20:16:58 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro

##### desktop ###########################

sed: can't read /home/mike/.dmrc: No such file or directory

Could not be determined.

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection (Lewisville) [8086:1502] (rev 04)
    DeviceName:  Onboard LAN
    Subsystem: Dell 82579LM Gigabit Network Connection (Lewisville) [1028:047e]

##### lsusb #############################

Bus 002 Device 003: ID 0b05:1a62 ASUSTek Computer, Inc. 802.11ax WLAN Adapter
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

./wireless-info: line 192: rfkill: command not found

##### secure boot #######################

This system doesn't support Secure Boot

##### lsmod #############################

cfg80211              974848  1 8852au

##### interfaces ########################

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'eno1' [IF1]> brd <MAC address>
    altname enp0s25
    inet 192.168.1.130/24 metric 100 brd 192.168.1.255 scope global dynamic eno1
       valid_lft 72527sec preferred_lft 72527sec
    inet6 fe80::<IP6 'eno1' [IF1]>/64 scope link 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

lo        no wireless extensions.

eno1      no wireless extensions.

##### route #############################

default via 192.168.1.1 dev eno1 proto dhcp src 192.168.1.130 metric 100 
192.168.1.0/24 dev eno1 proto kernel scope link src 192.168.1.130 metric 100 
192.168.1.1 dev eno1 proto dhcp scope link src 192.168.1.130 metric 100 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0 trust-ad
search .

##### network managers ##################

Installed:

    NetworkManager

Running:

root       12078       1  0 07:01 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/2
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        82579LM Gigabit Network Connection (Lewisville)
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 5.15.0-101-generic
GENERAL.FIRMWARE-VERSION:               0.13-4
GENERAL.HWADDR:                         <MAC 'eno1' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          10 (unmanaged)
GENERAL.REASON:                         0 (No reason given)
GENERAL.IP4-CONNECTIVITY:               0 (unknown)
GENERAL.IP6-CONNECTIVITY:               0 (unknown)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:19.0/net/eno1
GENERAL.PATH:                           pci-0000:00:19.0
GENERAL.IP-IFACE:                       eno1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     no
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
INTERFACE-FLAGS.UP:                     yes
INTERFACE-FLAGS.LOWER-UP:               yes
INTERFACE-FLAGS.CARRIER:                yes
INTERFACE-FLAGS.PROMISC:                no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.1.130/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.1.1, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.1.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 192.168.1.1/32, nh = 0.0.0.0, mt = 100
IP6.ADDRESS[1]:                         fe80::<IP6 'eno1' [IF1]>/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = fe80::/64, nh = ::, mt = 256
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --

##### NetworkManager.state ##############

cat: /var/lib/NetworkManager/NetworkManager.state: No such file or directory

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
[device-31-mac-addr-change]
match-device=driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no

##### NetworkManager profiles ###########

##### Netplan config ####################

grep: /etc/netplan/00-installer-config.yaml: Permission denied

##### iw reg get ########################

Region: America/Indiana/Tell_City (based on set time zone)

global
country 00: DFS-UNSET
    (755 - 928 @ 2), (N/A, 20), (N/A), PASSIVE-SCAN
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (N/A, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

eno1      no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eno1      Interface doesn't support scanning.

##### module infos ######################

[cfg80211]
filename:       /lib/modules/5.15.0-101-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       5.15.0-101-generic SMP mod_unload modversions 
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

[11209.062936] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=32220 PROTO=2 
[11279.926059] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[11279.927131] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[11280.743111] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:70:8b:cd:2e:2d:b2:08:00 SRC=192.168.1.14 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=24305 PROTO=2 
[11284.840122] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[11331.533859] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=32225 PROTO=2 
[11405.673464] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[11405.674567] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[11406.664631] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:20:0c:c8:45:93:d1:08:00 SRC=192.168.1.250 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[11409.358357] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[11461.377890] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=32230 PROTO=2 
[11531.011250] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[11531.012231] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[11531.419854] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[11584.258534] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=32242 PROTO=2 
[11656.348378] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[11656.349610] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[11659.625255] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[11666.178883] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:38:1a:52:4f:da:1e:08:00 SRC=192.168.1.25 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[11706.730481] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=32251 PROTO=2 
[11781.686701] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[11781.687924] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[11782.506724] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:80:5b:65:bf:e1:74:08:00 SRC=192.168.1.6 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[11790.697877] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[11831.248547] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=32264 PROTO=2 
[11907.844105] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[11907.845273] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[11911.530689] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[11917.264971] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:38:1a:52:4f:da:1e:08:00 SRC=192.168.1.25 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[11960.273354] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=32273 PROTO=2 
[12032.780492] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[12032.781702] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[12034.411148] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[12037.278461] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:38:1a:52:4f:da:1e:08:00 SRC=192.168.1.25 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[12088.479818] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=32285 PROTO=2 
[12158.112224] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[12158.113385] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[12161.530844] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:20:0c:c8:45:93:d1:08:00 SRC=192.168.1.250 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[12165.483891] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[12214.230261] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=32294 PROTO=2 
[12283.449367] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[12285.087744] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:80:5b:65:bf:e1:74:08:00 SRC=192.168.1.6 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[12286.316097] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[12340.806977] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=32303 PROTO=2 
[12409.197186] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[12409.198315] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[12409.199277] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:70:8b:cd:2e:2d:b2:08:00 SRC=192.168.1.14 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=24378 PROTO=2 
[12410.858937] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[12460.810140] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=32312 PROTO=2 
[12534.535421] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[12534.536590] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[12536.173770] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:70:8b:cd:2e:2d:b2:08:00 SRC=192.168.1.14 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=24387 PROTO=2 
[12538.221807] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[12659.873730] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[12659.874763] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[12660.283093] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[12664.379358] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:38:1a:52:4f:da:1e:08:00 SRC=192.168.1.25 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[12710.255894] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=32330 PROTO=2 
[12786.443302] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:38:1a:52:4f:da:1e:08:00 SRC=192.168.1.25 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[12790.536680] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[12837.231270] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=32342 PROTO=2 
[12910.959811] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[12914.237348] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:38:1a:52:4f:da:1e:08:00 SRC=192.168.1.25 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[12920.380484] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[12962.569505] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=32352 PROTO=2 
[13036.299101] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[13036.300389] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[13038.345842] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[13040.803459] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:38:1a:52:4f:da:1e:08:00 SRC=192.168.1.25 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[13094.051896] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=32364 PROTO=2 
[13161.636031] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[13161.637241] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[13163.684950] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:38:1a:52:4f:da:1e:08:00 SRC=192.168.1.25 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[13167.780069] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[13218.570737] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=32373 PROTO=2 
[13286.974451] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[13286.975451] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[13289.431844] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:70:8b:cd:2e:2d:b2:08:00 SRC=192.168.1.14 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=24436 PROTO=2 
[13294.347147] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[13338.584314] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=32382 PROTO=2 
[13412.722092] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[13412.723281] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[13415.590220] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:38:1a:52:4f:da:1e:08:00 SRC=192.168.1.25 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[13418.456694] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[13463.103339] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=32391 PROTO=2 
[13538.061149] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[13538.062425] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[13539.698797] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:70:8b:cd:2e:2d:b2:08:00 SRC=192.168.1.14 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=24453 PROTO=2 
[13542.975450] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[13594.995216] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=32400 PROTO=2 
[13663.398493] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[13663.399771] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[13664.175607] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:20:0c:c8:45:93:d1:08:00 SRC=192.168.1.250 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[13672.819522] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[13717.881236] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=32412 PROTO=2 
[13788.738041] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:a0:63:91:37:47:42:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[13788.739214] [UFW BLOCK] IN=eno1 OUT= MAC=33:33:00:00:00:00:a0:63:91:37:47:42:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[13789.965703] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:38:1a:52:4f:da:1e:08:00 SRC=192.168.1.25 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[13794.473546] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:a0:63:91:37:47:42:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[13846.493847] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:7f:ff:fa:2c:f0:5d:6d:b3:d1:08:00 SRC=192.168.1.4 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=32421 PROTO=2 

########## wireless info END ############


``` 

I know what ever it is , is simple but right I'm not seeing what to do to enable the USB Asus nano for some reason (getting old is not easy on the brain cells)

---

### Post by chili555 on 2024-03-19
Did you try a reboot?

After the reboot, did the module load as expected?```
lsmod | grep 8852au
```Was a wireless interface created? ```
iwconfig
```Does it see networks? ```
nmcli device wifi list
```

PS - The 'getting old' card is hard to play here. I am confident that I have at least a decade on you!

---

### Post by sgt-mike on 2024-03-19
No I didn't reboot did not even think about doing that.


```

  mike@bastion:~$ lsmod | grep 8852au
8852au              13557760  0
cfg80211              974848  1 8852au

mike@bastion:~$ iwconfig
lo        no wireless extensions.

eno1      no wireless extensions.

mike@bastion:~$ nmcli device wifi list
mike@bastion:~$ 

```

IDK if it makes an difference it is a USB wireless adapter which I'm positive most already know that

---

### Post by chili555 on 2024-03-19
Let's see if there are any clues in the message log:

```
sudo dmesg | grep 8852
```

---

### Post by sgt-mike on 2024-03-19
that returns 
```

mike@bastion:~$ sudo dmesg | grep 8852
[sudo] password for mike: 
[    0.208852] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[   28.996885] 8852au: loading out-of-tree module taints kernel.
[   29.001902] 8852au: module verification failed: signature and/or required key missing - tainting kernel
[   29.024589] usbcore: registered new interface driver rtl8852au
```

---

### Post by chili555 on 2024-03-20
My very favorite kind of problem: everything looks great except it just doesn't work.

Please shut down the computer. Remove the USB wireless. Start the computer. Open a terminal and run: ```
tail -f /var/log/syslog
``` Insert the USB wireless. Capture the output in the terminal and post it here.

Get out of 'tail' with Ctrl+c.

Is it possible that the USB wireless needs a USB 3.0 (or greater) port but it is currently plugged in to a USB 2.0 port?

---

### Post by praseodym on 2024-03-22
```
[   29.001902] 8852au: module verification failed: signature and/or required key missing - tainting kernel
```

Driver not signed. Deactivate SecureBoot

---

### Post by sgt-mike on 2024-03-23
> **chili555 said:**
> My very favorite kind of problem: everything looks great except it just doesn't work.

Please shut down the computer. Remove the USB wireless. Start the computer. Open a terminal and run: ```
tail -f /var/log/syslog
``` Insert the USB wireless. Capture the output in the terminal and post it here.

Get out of 'tail' with Ctrl+c.

Is it possible that the USB wireless needs a USB 3.0 (or greater) port but it is currently plugged in to a USB 2.0 port?

Sorry for my delay in posting 

I obtained the usb wireless device to use when the media server (or my NFS) was disconnected from a wired connection. 
It was/is a nice to have item not required. With that in mind I removed the device driver to get out of the kernal tainted status. 

But your last question is a true statement it is a USB 3.0 device plugged into a USB 2.0 port. That could very well be a major part of the problem, even though it's supposed to be backwardly compatible it may not be.

And to praseodym post: 

secure boot --- I don't recall setting it up unless it was a default setting from Ubuntu 22.04 server install, and I don't doubt that it is, I'll research that to disable that --- it very well maybe the whole underlying fault
This may take a week or two before I can revisit this small issue (I need to flush a tractor's fuel system, joy oh joy, which means almost complete deck and rear end assembly removal to get to the fuel tank). maybe less.

After reading both post's I'll re-install the driver and do as Chilli stated and capture the output. 
Then I'll disable the secure boot if it's enabled after running down the output that Chilli advised.

---

### Post by declanshanaghy2 on 2024-11-09
> **chili555 said:**
> The correct driver for this device is here: [https://github.com/lwfinger/rtl8852au](https://github.com/lwfinger/rtl8852au)

```
$ modinfo 8852au.ko | grep 1997
alias:          usb:v[COLOR=#FF0000]0B05[/COLOR]p[COLOR=#FF0000]1997[/COLOR]d*dc*dsc*dp*icFFiscFFipFFin*
```Post back if you need step-by-step instructions.

I just got [this WiFi dongle]("https://www.bestbuy.com/site/asus-dual-band-wi-fi-6-ax1800-usb-network-adapter-black/6540490.p?skuId=6540490"), which as far as I can figure out is the same one being referred to here.

Because the USB Id's match up:
From the repo: ASUS USB-AX56 with USB ID 0b05:1a62
Fom lsusb: Bus 001 Device 006: ID 0b05:1a62 ASUSTek Computer, Inc.

In this case, im just lucky that the repo README has the USB IDs in the list, a lot of devs don't go to that level of detail.

My question is how did you find this repo?
In the general case...what's the secret sauce for finding a driver?

---

### Post by jeremy31 on 2024-11-09
> **declanshanaghy2 said:**
> I just got [this WiFi dongle]("https://www.bestbuy.com/site/asus-dual-band-wi-fi-6-ax1800-usb-network-adapter-black/6540490.p?skuId=6540490"), which as far as I can figure out is the same one being referred to here.

Because the USB Id's match up:
From the repo: ASUS USB-AX56 with USB ID 0b05:1a62
Fom lsusb: Bus 001 Device 006: ID 0b05:1a62 ASUSTek Computer, Inc.

In this case, im just lucky that the repo README has the USB IDs in the list, a lot of devs don't go to that level of detail.

My question is how did you find this repo?
In the general case...what's the secret sauce for finding a driver?

We normally do a net search for the USB ID and see where it leads, hopefully we find something that is patched for newer kernels
Sometimes for Realtek wifi you can search the /os_dep/linux/usb_intf.c for part of the USB ID

---

### Post by declanshanaghy2 on 2024-11-09
Ahhh ****, I ran into issues compiling the module.
I'm on a Raspberry Pi, which has a + in the kernel release version (5.4.79-v7+). apt treats that as a special symbol.
Here's how to install kernel headers for RasPi - **apt install raspberrypi-kernel-headers**

Next issue I ran into is that my kernel was too old.
The ole **apt-get dist-upgrade** sledgehammer solved that for me

She's compiling now! :-D

---

