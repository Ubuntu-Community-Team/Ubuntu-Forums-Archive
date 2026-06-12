---
title: "Lenovo Yoga 3 Pro BCM4352 not working in Ubuntu 14.10"
date: 2015-01-13
forum: Networking &amp; Wireless
---

### Post by Lividium on 2015-01-13
Good evening all,

I have been trying to get the wireless working on my Lenovo Yoga 3 Pro. As soon as I got the laptop I stripped the factory operating system off of it and installed Ubuntu 14.04 LTS and the wireless controller worked after a installing the bcmwl-kernel-source and blacklisting ideapad_laptop. The problem was that the touchpad and the touchscreen didn't work. I submitted a bug report to see if I could get the touchpad working. The guys at the bug reporting center had me upgrade the kernel to the mainline kernel. After updating the kernel my touchpad and touchscreen now work, but the Wireless Controller is not working. I have been searching and troubleshooting for quite a while now. I have tried a lot of things, with not much luck.

I have tried the workaround here [HTML]http://ubuntuforums.org/showthread.php?t=2214110[/HTML] with no luck, and the solution that got the wifi working in 14.04 didn't work in 14.10.

Here is the wireless info from the script found on the sticky here: [HTML]http://ubuntuforums.org/showthread.php?t=370108[/HTML]

```

########## wireless info START ##########

Report from: 13 Jan 2015 21:33 CST -0600

Booted last: 13 Jan 2015 21:24 CST -0600

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 14.10
Release:	14.10
Codename:	utopic

##### kernel ############################

Linux 3.19.0-031900rc4-generic #201501112135 SMP Sun Jan 11 21:36:48 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Network controller [0280]: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)
	Subsystem: Lenovo Device [17aa:0623]

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 048d:8386 Integrated Technology Express, Inc. 
Bus 001 Device 003: ID 5986:0535 Acer, Inc 
Bus 001 Device 002: ID 0489:e07a Foxconn / Hon Hai 
Bus 001 Device 006: ID 18d1:4ee3 Google Inc. Nexus 4 (tether)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

wmi                    19379  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

usb0      Link encap:Ethernet  HWaddr <MAC 'usb0' [IF]>  
          inet addr:192.168.42.133  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::6097:1fff:fe3a:1fba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2270 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2329 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1067465 (1.0 MB)  TX bytes:608577 (608.5 KB)

##### iwconfig ##########################

usb0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.42.129  0.0.0.0         UG    0      0        0 usb0
192.168.42.0    0.0.0.0         255.255.255.0   U     1      0        0 usb0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: usb0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            rndis_host
  State:             connected
  Default:           yes
  HW Address:        <MAC 'usb0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.42.133
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.42.129

    DNS:             192.168.42.129

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/UCO_SECURE]] (600 root)
[ipv6] method=auto
[connection] id=UCO_SECURE | type=802-11-wireless
[802-11-wireless] ssid=UCO_SECURE | mac-address=<MAC address>
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/FilthyNet]] (600 root)
[connection] id=FilthyNet | type=802-11-wireless
[802-11-wireless] ssid=FilthyNet | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Chicago (based on set time zone)

country 00: DFS-UNSET
	(2402 - 2472 @ 40), (6, 20)
	(2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN
	(2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN
	(5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN
	(5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN
	(5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN

##### iwlist channels ###################

usb0      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

usb0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

##### /etc/modules ######################

lp

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

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
blacklist ideapad_laptop

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x14e4:0x43b1 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[    3.954757] bluetooth hci0: Direct firmware load for brcm/BCM20702A0-0489-e07a.hcd failed with error -2
[    3.954759] Bluetooth: hci0: BCM: patch brcm/BCM20702A0-0489-e07a.hcd not found

########## wireless info END ############

```

Any help that anyone could offer would be fantastic.

---

### Post by chili555 on 2015-01-14
Please try:```
sudo -i
apt-get install --reinstall bcmwl-kernel-source
echo wl  >>  /etc/modules
exit
```Reboot and let us hear your report. If it is not working, please give us another wireless_script.

---

### Post by Lividium on 2015-01-14
Chili,

I have re-installed the bcmwl-kernel-source and rebooted with no luck on the wifi.

The new script is as follows:

```

########## wireless info START ##########

Report from: 14 Jan 2015 11:37 CST -0600

Booted last: 14 Jan 2015 11:20 CST -0600

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 14.10
Release:	14.10
Codename:	utopic

##### kernel ############################

Linux 3.19.0-031900rc4-generic #201501112135 SMP Sun Jan 11 21:36:48 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Network controller [0280]: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)
	Subsystem: Lenovo Device [17aa:0623]

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 048d:8386 Integrated Technology Express, Inc. 
Bus 001 Device 003: ID 5986:0535 Acer, Inc 
Bus 001 Device 002: ID 0489:e07a Foxconn / Hon Hai 
Bus 001 Device 006: ID 18d1:4ee3 Google Inc. Nexus 4 (tether)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

wmi                    19379  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

usb0      Link encap:Ethernet  HWaddr <MAC 'usb0' [IF]>  
          inet addr:192.168.42.232  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::b09d:28ff:febd:c76f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4152 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3516 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3117570 (3.1 MB)  TX bytes:1013289 (1.0 MB)

##### iwconfig ##########################

usb0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.42.129  0.0.0.0         UG    0      0        0 usb0
192.168.42.0    0.0.0.0         255.255.255.0   U     1      0        0 usb0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: usb0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            rndis_host
  State:             connected
  Default:           yes
  HW Address:        <MAC 'usb0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.42.232
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.42.129

    DNS:             192.168.42.129

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/UCO_SECURE]] (600 root)
[ipv6] method=auto
[connection] id=UCO_SECURE | type=802-11-wireless
[802-11-wireless] ssid=UCO_SECURE | mac-address=<MAC address>
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/FilthyNet]] (600 root)
[connection] id=FilthyNet | type=802-11-wireless
[802-11-wireless] ssid=FilthyNet | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Chicago (based on set time zone)

country 00: DFS-UNSET
	(2402 - 2472 @ 40), (6, 20)
	(2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN
	(2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN
	(5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN
	(5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN
	(5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN

##### iwlist channels ###################

usb0      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

usb0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

##### /etc/modules ######################

lp
wl

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

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
blacklist ideapad_laptop

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x14e4:0x43b1 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[    3.874153] bluetooth hci0: Direct firmware load for brcm/BCM20702A0-0489-e07a.hcd failed with error -2
[    3.874156] Bluetooth: hci0: BCM: patch brcm/BCM20702A0-0489-e07a.hcd not found

########## wireless info END ############

```

---

### Post by chili555 on 2015-01-14
Although we reinstalled the driver and asked that it load automatically on boot, it is not present in your script. That suggests that something else may be wrong. Let's load the driver from the terminal and see if any interesting errors appear.```
sudo modprobe wl
dmesg | grep wl
iwconfig
```

---

### Post by Lividium on 2015-01-14
Ok, I got 

```
$ sudo modprobe wl
modprobe: FATAL: Module wl not found.

```

```
$ dmesg | grep wl
$ iwconfig
usb0      no wireless extensions.

lo        no wireless extensions.


```

---

### Post by jeremy31 on 2015-01-14
Redo chili555's first idea and post the output from the command ```
[COLOR=#000000][FONT=Ubuntu Mono]apt-get install --reinstall bcmwl-kernel-source
```
As I doubt it will it will work with your kernel without another patch

It will likely work with installing from here [/FONT][/COLOR]http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14.28-utopic/ but you will have to press the SHIFT key during boot to get the grub menu if you aren't using a dual boot and then select Advanced options of previous versions to select the new kernel to boot to

---

### Post by Lividium on 2015-01-14
Here is the output of the reinstall:

```

# sudo apt-get install --reinstall bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/1,511 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 207554 files and directories currently installed.)
Preparing to unpack .../bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu1_amd64.deb ...
Removing all DKMS Modules
Done.
Unpacking bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu1) over (6.30.223.248+bdcom-0ubuntu1) ...
Setting up bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu1) ...
Loading new bcmwl-6.30.223.248+bdcom DKMS files...
Building only for 3.19.0-031900rc4-generic
Building for architecture x86_64
Building initial module for 3.19.0-031900rc4-generic
ERROR (dkms apport): kernel package linux-headers-3.19.0-031900rc4-generic is not supported
Error! Bad return status for module build on kernel: 3.19.0-031900rc4-generic (x86_64)
Consult /var/lib/dkms/bcmwl/6.30.223.248+bdcom/build/make.log for more information.
modprobe: FATAL: Module wl not found.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.103ubuntu8) ...
update-initramfs: Generating /boot/initrd.img-3.19.0-031900rc4-generic

```

---

### Post by chili555 on 2015-01-14
> ERROR (dkms apport): kernel package linux-headers-3.19.0-031900rc4-generic is not supported
Error! Bad return status for module build on kernel: 3.19.0-031900rc4-generic (x86_64)
Consult /var/lib/dkms/bcmwl/6.30.223.248+bdcom/build/make.log for more information.I'd try again booted into the default 14.10 kernel; 3.16.0-something.

---

### Post by Lividium on 2015-01-14
I'll give that a try, the last time I booted up into a different kernel it was the one for 14.04 and when I did that I didn't have use of my touchpad and touch screen. I may end up having to choose which is more important at the time, mouse or wifi. I appreciate everyone's help.

---

### Post by Lividium on 2015-01-14
ok, I guess when I installed the mainline kernel, somehow I deleted the other kernel. How do I re-install the standard kernel and keep it on the grub menu?

---

### Post by chili555 on 2015-01-15
I would try:```
sudo apt-get install --reinstall linux-image-generic
sudo apt-get install linux-image-3.16.0-29-generic
```After it finishes, reboot, select 3.16.0-29 at the GRUB menu and then:```
sudo apt-get install --reinstall bcmwl-kernel-source
```And finally...```
sudo modprobe wl
```

---

### Post by Lividium on 2015-01-15
Ok, I have re-installed the 3.16.0-29 kernel, rebooted and tried the re-install of the bcmw-kernel-source. It appears that it didn't find the kernel source for the bcmw for 3.16 kernel and it just tried to re-install the bcmw for 3.19. 

```
sudo apt-get install --reinstall bcmwl-kernel-source 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/1,511 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 212612 files and directories currently installed.)
Preparing to unpack .../bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu1_amd64.deb ...
Removing all DKMS Modules
Done.
Unpacking bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu1) over (6.30.223.248+bdcom-0ubuntu1) ...
Setting up bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu1) ...
Loading new bcmwl-6.30.223.248+bdcom DKMS files...                                                                                                                                        
Building for 3.16.0-29-generic and 3.19.0-031900rc4-generic                                                                                                                               
Building for architecture x86_64                                                                                                                                                          
Module build for the currently running kernel was skipped since the                                                                                                                       
kernel source for this kernel does not seem to be installed.                                                                                                                              
Building initial module for 3.19.0-031900rc4-generic                                                                                                                                      
ERROR (dkms apport): kernel package linux-headers-3.19.0-031900rc4-generic is not supported                                                                                               
Error! Bad return status for module build on kernel: 3.19.0-031900rc4-generic (x86_64)                                                                                                    
Consult /var/lib/dkms/bcmwl/6.30.223.248+bdcom/build/make.log for more information.                                                                                                       
modprobe: FATAL: Module wl not found.                                                                                                                                                     
update-initramfs: deferring update (trigger activated)                                                                                                                                    
Processing triggers for initramfs-tools (0.103ubuntu8) ...                                                                                                                                
update-initramfs: Generating /boot/initrd.img-3.19.0-031900rc4-generic  
```

---

### Post by chili555 on 2015-01-15
> Building initial module for 3.[COLOR="#FF0000"]19.[/COLOR]0-031900rc4-generic   Were or are you actualy booted into 3.16.0-xx?```
uname -r
```

---

### Post by Lividium on 2015-01-15
When I did that last install I was booted into the 3.16 and for some reason it just decided to stop the build for the 3.16 and started the build for 3.19 which failed miserably.

```

Building for 3.16.0-29-generic and 3.19.0-031900rc4-generic                                                                                                                               
Building for architecture x86_64                                                                                                                                                          
Module build for the currently running kernel was skipped since the                                                                                                                       
kernel source for this kernel does not seem to be installed.                                                                                                                              
Building initial module for 3.19.0-031900rc4-generic        

```

After that happened, I got frustrated, and thought that because I have installed the kernel for 14.04, 14.10, and the mainline kernel, maybe it would be better to just wipe it and start over from a fresh install. So, I downloaded a new Ubuntu 14.10 iso and installed fresh, and I was pleased to find that after the install the wireless card was recognized but marked as hardware locked. I then crossed my fingers and added ideapad_laptop to my blacklist, rebooted and it popped up. I now have a fully functional [s]deathstar[/s] laptop. Thank you for all of your help Chili!

---

### Post by chili555 on 2015-01-15
>  I now have a fully functional deathstar laptop. LOL!

I am glad it's working by whatever means. Have fun!

---

