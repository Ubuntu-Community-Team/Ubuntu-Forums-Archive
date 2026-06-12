---
title: "Ethernet connection dropped + driver update - Ubuntu 20.04 (no internet connection)"
date: 2022-01-10
forum: Networking &amp; Wireless
---

### Post by garbros on 2022-01-10
Small backstory: Upgraded from old Windows 7 OS to Ubuntu 20.04. Everything generally working well whilst trying to find feet, apart from an intermittent internet connection. It would drop out every now and then. I have a direct ethernet connection plugged into a TP link booster (router/modem is downstairs).

After reading around I decided to hopefully fix it, but unfortunately i've made things worse. I have lost the internet connection totally now (I'm doing this from another laptop). What I tried to do was download/update the Realtek driver from the official website. I followed the steps (which I will copy below) but the internet totally dropped out after running the ./autorun.sh script. The network icon disappeared from the top right, and no visible options inside of the network settings (not even to add a network/wired connection).

I've attached my wireless-info below, hopefully that will help.

```



########## wireless info START ##########


Report from: 10 Jan 2022 13:20 GMT +0000


Booted last: 10 Jan 2022 00:00 GMT +0000


Script from: 25 Jan 2020 03:34 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 20.04.3 LTS
Release:	20.04
Codename:	focal


##### kernel ############################


Linux 5.11.0-44-generic #48~20.04.2-Ubuntu SMP Tue Dec 14 15:36:44 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


sed: can't read /root/.dmrc: No such file or directory


Could not be determined.


##### lspci #############################


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
	Subsystem: Gigabyte Technology Co., Ltd Onboard Ethernet [1458:e000]


##### lsusb #############################


Bus 002 Device 003: ID 0bc2:ac20 Seagate RSS LLC BUP Slim
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 046d:c050 Logitech, Inc. RX 250 Optical Mouse
Bus 001 Device 002: ID 046d:c31c Logitech, Inc. Keyboard K120
Bus 001 Device 005: ID 046d:0a44 Logitech, Inc. Headset H390
Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### secure boot #######################


SecureBoot disabled
Platform is in Setup Mode


##### lsmod #############################


intel_wmi_thunderbolt    20480  0
wmi                    32768  1 intel_wmi_thunderbolt


##### interfaces ########################


##### ifconfig ##########################


1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: br-723dba2f9f4d: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default 
    link/ether <MAC 'br-723dba2f9f4d' [IF1]> brd <MAC address>
    inet 172.18.0.1/16 brd 172.18.255.255 scope global br-723dba2f9f4d
       valid_lft forever preferred_lft forever
3: docker0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default 
    link/ether <MAC 'docker0' [IF2]> brd <MAC address>
    inet 172.17.0.1/16 brd 172.17.255.255 scope global docker0
       valid_lft forever preferred_lft forever


##### iwconfig ##########################


lo        no wireless extensions.


br-723dba2f9f4d  no wireless extensions.


docker0   no wireless extensions.


##### route #############################


169.254.0.0/16 dev br-723dba2f9f4d scope link metric 1000 linkdown 
172.17.0.0/16 dev docker0 proto kernel scope link src 172.17.0.1 linkdown 
172.18.0.0/16 dev br-723dba2f9f4d proto kernel scope link src 172.18.0.1 linkdown 


##### resolv.conf #######################


[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']


nameserver 127.0.0.53
options edns0 trust-ad


##### network managers ##################


Installed:


	NetworkManager


Running:


root        2859       1  0 11:56 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         br-723dba2f9f4d
GENERAL.TYPE:                           bridge
GENERAL.NM-TYPE:                        NMDeviceBridge
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/2
GENERAL.VENDOR:                         --
GENERAL.PRODUCT:                        --
GENERAL.DRIVER:                         bridge
GENERAL.DRIVER-VERSION:                 2.3
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'br-723dba2f9f4d' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.IP4-CONNECTIVITY:               1 (none)
GENERAL.IP6-CONNECTIVITY:               1 (none)
GENERAL.UDI:                            /sys/devices/virtual/net/br-723dba2f9f4d
GENERAL.IP-IFACE:                       br-723dba2f9f4d
GENERAL.IS-SOFTWARE:                    yes
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     br-723dba2f9f4d
GENERAL.CON-UUID:                       c9e0e7ad-87b5-4d25-bf1f-cc83f2833c77
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               yes
CAPABILITIES.SRIOV:                     no
INTERFACE-FLAGS.UP:                     yes
INTERFACE-FLAGS.LOWER-UP:               no
INTERFACE-FLAGS.CARRIER:                no
IP4.ADDRESS[1]:                         172.18.0.1/16
IP4.GATEWAY:                            --
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.ROUTE[2]:                           dst = 172.18.0.0/16, nh = 0.0.0.0, mt = 0
IP6.GATEWAY:                            --
BRIDGE.SLAVES:                          --
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/2
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   c9e0e7ad-87b5-4d25-bf1f-cc83f2833c77 | br-723dba2f9f4d


GENERAL.DEVICE:                         docker0
GENERAL.TYPE:                           bridge
GENERAL.NM-TYPE:                        NMDeviceBridge
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/3
GENERAL.VENDOR:                         --
GENERAL.PRODUCT:                        --
GENERAL.DRIVER:                         bridge
GENERAL.DRIVER-VERSION:                 2.3
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'docker0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.IP4-CONNECTIVITY:               1 (none)
GENERAL.IP6-CONNECTIVITY:               1 (none)
GENERAL.UDI:                            /sys/devices/virtual/net/docker0
GENERAL.IP-IFACE:                       docker0
GENERAL.IS-SOFTWARE:                    yes
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     docker0
GENERAL.CON-UUID:                       05499778-0430-4298-94e8-f531ab65fbef
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               yes
CAPABILITIES.SRIOV:                     no
INTERFACE-FLAGS.UP:                     yes
INTERFACE-FLAGS.LOWER-UP:               no
INTERFACE-FLAGS.CARRIER:                no
IP4.ADDRESS[1]:                         172.17.0.1/16
IP4.GATEWAY:                            --
IP4.ROUTE[1]:                           dst = 172.17.0.0/16, nh = 0.0.0.0, mt = 0
IP6.GATEWAY:                            --
BRIDGE.SLAVES:                          --
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/3
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   05499778-0430-4298-94e8-f531ab65fbef | docker0


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


##### NetworkManager config #############


[[/etc/NetworkManager/conf.d/10-ubuntu-fan.conf]]
[keyfile]
unmanaged-devices+=interface-name:fan-*


[[/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf]]
[connection]
wifi.powersave = 3


[[/etc/NetworkManager/NetworkManager.conf]]
[main]
plugins=ifupdown,keyfile
[ifupdown]
managed=true
[device]
wifi.scan-rand-mac-address=no


[[/usr/lib/NetworkManager/conf.d/10-dns-resolved.conf]]
[main]
dns=systemd-resolved


[[/usr/lib/NetworkManager/conf.d/10-globally-managed-devices.conf]]
[keyfile]
unmanaged-devices=*,except:type:ethernet,except:type:wifi,except:type:gsm,except:type:cdma


[[/usr/lib/NetworkManager/conf.d/20-connectivity-ubuntu.conf]]
[connectivity]
uri=http://connectivity-check.ubuntu.com/


[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-mac-addr-change-wifi]
match-device=driver:rtl8723bs,driver:rtl8189es,driver:r8188eu,driver:8188eu,driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no


##### NetworkManager profiles ###########


##### Netplan config ####################


[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager


##### iw reg get ########################


Region: Europe/London (based on set time zone)


global
country 00: DFS-UNSET
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


br-723dba2f9f4d  no frequency information.


docker0   no frequency information.


##### iwlist scan #######################


lo        Interface doesn't support scanning.


br-723dba2f9f4d  Interface doesn't support scanning.


docker0   Interface doesn't support scanning.


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


##### rc.local ##########################


grep: /etc/rc.local: No such file or directory


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


########## wireless info END ############



```

Readme instructions from Realtek:

```
<Quick install with proper kernel settings>	Unpack the tarball :
		# tar vjxf r8125-9.aaa.bb.tar.bz2


	Change to the directory:
		# cd r8125-9.aaa.bb


	If you are running the target kernel, then you should be able to do :


		# ./autorun.sh	(as root or with sudo)


	You can check whether the driver is loaded by using following commands.


		# lsmod | grep r8125
		# ifconfig -a


	If there is a device name, ethX, shown on the monitor, the linux
	driver is loaded. Then, you can use the following command to activate
	the ethX.


		# ifconfig ethX up


		,where X=0,1,2,...

```

---

### Post by chili555 on 2022-01-10
Please run and post:

```
sudo modprobe r8168
sudo dpkg -s linux-modules-extra-$(uname -r) | grep Status
uname -r
```

---

### Post by garbros on 2022-01-10
> **chili555 said:**
> Please run and post:

```
sudo modprobe r8168
sudo dpkg -s linux-modules-extra-$(uname -r) | grep Status
uname -r
```

Thanks chili555,

Ran those commands - outputs below.

```

sudo modprobe r8168 
modprobe: FATAL: Module r8168 not found in directory /lib/modules/5.11.0-44-generic


sudo dpkg -s linux-modules-extra-$(uname -r) | grep Status
Status: install ok installed


uname -r
5.11.0-44-generic

```

---

### Post by chili555 on 2022-01-10
```
Module r8168 not found 
```That suggests that your failed driver install did no harm. Now let's try the in-kernel module:

```
sudo modprobe r8169
sudo dmesg | grep r816
```

---

### Post by garbros on 2022-01-10
> **chili555 said:**
> ```
Module r8168 not found 
```That suggests that your failed driver install did no harm. Now let's try the in-kernel module:

```
sudo modprobe r8169
sudo dmesg | grep r816
```

Ran those, I get the same error as listed above, but the second command doesn't return anything at all, tried it multiple times.

```

modprobe: FATAL: Module r8169 not found in directory /lib/modules/5.11.0-44-generic

```

---

### Post by chili555 on 2022-01-10
Please do:

```
sudo apt update
sudo apt install --reinstall linux-modules-extra-$(uname -r) linux-generic mlocate
sudo updatedb
locate r8169.ko
```

Assuming it is now present, do:

```
sudo modprobe r8169
```

Now do you have ethernet?

---

### Post by garbros on 2022-01-11
[QUOTE=chili555;14074809]Please do:

```
sudo apt update

```

Thanks for your continued help. I ran the command but got an error - temporary failure. Presumably after I killed the internet/ethernet connection yesterday. This is what the first command returns:

```

sudo apt update
Err:1 http://security.ubuntu.com/ubuntu focal-security InRelease
  Temporary failure resolving ‘security.ubuntu.com’
Err:2 https://dl.google.com/linux/chrome/deb stable InRelease
  Temporary failure resolving ‘dl.google.com’
Err:3 https://dl.yarnpkg.com/debian stable InRelease
  Temporary failure resolving ‘dl.yarnpkg.com’
Err:4 http://packages.microsoft.com/repos/code stable InRelease            
  Temporary failure resolving ‘packages.microsoft.com’
Err:5 http://ppa.launchpad.net/git-core/ppa/ubuntu focal InRelease         
  Temporary failure resolving ‘ppa.launchpad.net’
Err:6 http://gb.archive.ubuntu.com/ubuntu focal InRelease
  Temporary failure resolving ‘gb.archive.ubuntu.com’
Err:7 http://ppa.launchpad.net/shutter/ppa/ubuntu focal InRelease
  Temporary failure resolving ‘ppa.launchpad.net’
Err:8 http://gb.archive.ubuntu.com/ubuntu focal-updates InRelease
  Temporary failure resolving ‘gb.archive.ubuntu.com’
Err:9 http://gb.archive.ubuntu.com/ubuntu focal-backports InRelease
  Temporary failure resolving ‘gb.archive.ubuntu.com’
Reading package lists... Done
Building dependency tree       
Reading state information... Done
14 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/focal/InRelease  Temporary failure resolving ‘gb.archive.ubuntu.com’
W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/focal-updates/InRelease  Temporary failure resolving ‘gb.archive.ubuntu.com’
W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/focal-backports/InRelease  Temporary failure resolving ‘gb.archive.ubuntu.com’
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/focal-security/InRelease  Temporary failure resolving ‘security.ubuntu.com’
W: Failed to fetch http://ppa.launchpad.net/git-core/ppa/ubuntu/dists/focal/InRelease  Temporary failure resolving ‘ppa.launchpad.net’
W: Failed to fetch https://dl.google.com/linux/chrome/deb/dists/stable/InRelease  Temporary failure resolving ‘dl.google.com’
W: Failed to fetch http://ppa.launchpad.net/shutter/ppa/ubuntu/dists/focal/InRelease  Temporary failure resolving ‘ppa.launchpad.net’
W: Failed to fetch http://packages.microsoft.com/repos/code/dists/stable/InRelease  Temporary failure resolving ‘packages.microsoft.com’
W: Failed to fetch https://dl.yarnpkg.com/debian/dists/stable/InRelease  Temporary failure resolving ‘dl.yarnpkg.com’
W: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by chili555 on 2022-01-11
> but got an error - temporary failure. Presumably after I killed the internet/ethernet connection yesterday.I see. Let's do it with a USB key! On some other computer, download this file:

[http://security.ubuntu.com/ubuntu/pool/main/l/linux-hwe-5.11/linux-modules-extra-5.11.0-44-generic_5.11.0-44.48~20.04.2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-hwe-5.11/linux-modules-extra-5.11.0-44-generic_5.11.0-44.48~20.04.2_amd64.deb)

We'll skip the others if we can. Transfer the file to the desktop of the subject computer and, in a terminal, do:

```
cd ~/Desktop
sudo dpkg -i linux*.deb
```

Now check:

```
sudo modprobe r8169
```

Is your ethernet working?

---

### Post by garbros on 2022-01-12
> **chili555 said:**
> I see. Let's do it with a USB key! On some other computer, download this file:

[http://security.ubuntu.com/ubuntu/pool/main/l/linux-hwe-5.11/linux-modules-extra-5.11.0-44-generic_5.11.0-44.48~20.04.2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-hwe-5.11/linux-modules-extra-5.11.0-44-generic_5.11.0-44.48~20.04.2_amd64.deb)

We'll skip the others if we can. Transfer the file to the desktop of the subject computer and, in a terminal, do:

```
cd ~/Desktop
sudo dpkg -i linux*.deb
```

Now check:

```
sudo modprobe r8169
```

Is your ethernet working?

It works! Thank you very much for your detailed help on this, it's really appreciated!

---

