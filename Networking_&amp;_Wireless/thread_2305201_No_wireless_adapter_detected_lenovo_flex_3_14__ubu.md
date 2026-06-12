---
title: "No wireless adapter detected| lenovo flex 3 14 | ubuntu 14.04"
date: 2015-12-03
forum: Networking &amp; Wireless
---

### Post by Soham_Das on 2015-12-03
Hi guys,

I recently bought a Lenovo flex 3 14 and installed Ubuntu 14.04 alongside Windows 10.
The wifi works in windows, but doesn't show up in ubuntu.
I have tried different solutions, but could not solve the issue.

rfkill list all shows only bluetooth.

Any help is appreciated.

Thanks!

---

### Post by Hadaka on 2015-12-03
Hi, please go here
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
follow instructions and post the wireless-info.txt file
thanks.

---

### Post by Soham_Das on 2015-12-03
my wireless-info.txt file:


########## wireless info START ##########

Report from: 03 Dec 2015 18:17 EST -0500

Booted last: 03 Dec 2015 18:12 EST -0500

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-55-generic #74~14.04.1-Ubuntu SMP Tue Nov 17 10:15:59 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0042] (rev 30)
    Subsystem: Lenovo Device [17aa:4035]

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Lenovo Device [17aa:3835]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0cf3:e360 Atheros Communications, Inc. 
Bus 001 Device 003: ID 04f3:2083 Elan Microelectronics Corp. 
Bus 001 Device 002: ID 5986:0670 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

wmi                    19193  0 
ideapad_laptop         18278  0 
sparse_keymap          13948  1 ideapad_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5947 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3637 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7656698 (7.6 MB)  TX bytes:362511 (362.5 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       976     1  0 18:12 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.10
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

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

##### iw reg get ########################

Region: America/New_York (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN
    (5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

##### /etc/modules ######################

lp
rtc

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
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[   19.874094] r8169 0000:03:00.0 eth0: link down (repeated 2 times)
[   19.874169] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.446612] r8169 0000:03:00.0 eth0: link up
[   21.446621] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

########## wireless info END ############

---

### Post by Hadaka on 2015-12-03
Hi, per the good Dr. Chili555
from a working wired connection please COPY and paste
one command at a time...
```
sudo apt-get update
sudo apt-get install linux-headers-generic build-essential
wget https://www.kernel.org/pub/linux/kernel/projects/backports/2015/11/20/backports-20151120.tar.gz
tar -zxvf backports-20151120.tar.gz
cd backports-20151120
make defconfig-ath10k
make
sudo make install
```
boot ...remove wired connection
and test wireless

Let's clean up your missing country code while we are here.
```
sudo iw reg set US
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda
```

*Then each time there is a kernel update do this.to keep the wireless alive.
```
cd backports-20151120
make clean
make defconfig-ath10k
make
sudo make install
```
*BE SURE TO SAVE THIS

---

### Post by chili555 on 2015-12-03
Thanks for your kind comments. Soham_Das will probably need some firmware which he can determine after the installation with:```
dmesg | grep ath
```

---

### Post by Soham_Das on 2015-12-03
Hi guys, I tried the steps, but still it does not work. :(

---

### Post by Soham_Das on 2015-12-03
I get this on running   dmesg | grep ath


[    0.866022] Loaded X.509 cert 'Magrathea: Glacier signing key: c0e79120a193454330069fccfa63e661c83064f8'
[   12.031858] ath10k_pci 0000:02:00.0: enabling device (0000 -> 0002)
[   12.033709] ath10k_pci 0000:02:00.0: irq 143 for MSI/MSI-X
[   12.033821] ath10k_pci 0000:02:00.0: pci irq msi interrupts 1 irq_mode 0 reset_mode 0
[   12.525136] ath10k_pci 0000:02:00.0: Direct firmware load failed with error -2
[   12.525139] ath10k_pci 0000:02:00.0: Falling back to user helper
[   12.525722] ath10k_pci 0000:02:00.0: Direct firmware load failed with error -2
[   12.525726] ath10k_pci 0000:02:00.0: Falling back to user helper
[   12.526253] ath10k_pci 0000:02:00.0: could not fetch firmware file 'ath10k/QCA9377/hw1.0/firmware-5.bin': -12
[   12.526265] ath10k_pci 0000:02:00.0: Direct firmware load failed with error -2
[   12.526267] ath10k_pci 0000:02:00.0: Falling back to user helper
[   12.526548] ath10k_pci 0000:02:00.0: could not fetch firmware file 'ath10k/QCA9377/hw1.0/firmware-4.bin': -12
[   12.526557] ath10k_pci 0000:02:00.0: Direct firmware load failed with error -2
[   12.526559] ath10k_pci 0000:02:00.0: Falling back to user helper
[   12.527055] ath10k_pci 0000:02:00.0: could not fetch firmware file 'ath10k/QCA9377/hw1.0/firmware-3.bin': -12
[   12.527065] ath10k_pci 0000:02:00.0: Direct firmware load failed with error -2
[   12.527066] ath10k_pci 0000:02:00.0: Falling back to user helper
[   12.527464] ath10k_pci 0000:02:00.0: could not fetch firmware file 'ath10k/QCA9377/hw1.0/firmware-2.bin': -12
[   12.527473] ath10k_pci 0000:02:00.0: Direct firmware load failed with error -2
[   12.527475] ath10k_pci 0000:02:00.0: Falling back to user helper
[   12.527869] ath10k_pci 0000:02:00.0: could not fetch firmware (-12)
[   12.527873] ath10k_pci 0000:02:00.0: could not fetch firmware files (-12)
[   12.527875] ath10k_pci 0000:02:00.0: could not probe fw (-12)

---

### Post by Hadaka on 2015-12-03
you need to post,,
```
dmesg | grep ath
```

---

### Post by Soham_Das on 2015-12-03
Here it is

[    0.866022] Loaded X.509 cert 'Magrathea: Glacier signing key: c0e79120a193454330069fccfa63e661c83064f8'
[   12.031858] ath10k_pci 0000:02:00.0: enabling device (0000 -> 0002)
[   12.033709] ath10k_pci 0000:02:00.0: irq 143 for MSI/MSI-X
[   12.033821] ath10k_pci 0000:02:00.0: pci irq msi interrupts 1 irq_mode 0 reset_mode 0
[   12.525136] ath10k_pci 0000:02:00.0: Direct firmware load failed with error -2
[   12.525139] ath10k_pci 0000:02:00.0: Falling back to user helper
[   12.525722] ath10k_pci 0000:02:00.0: Direct firmware load failed with error -2
[   12.525726] ath10k_pci 0000:02:00.0: Falling back to user helper
[   12.526253] ath10k_pci 0000:02:00.0: could not fetch firmware file 'ath10k/QCA9377/hw1.0/firmware-5.bin': -12
[   12.526265] ath10k_pci 0000:02:00.0: Direct firmware load failed with error -2
[   12.526267] ath10k_pci 0000:02:00.0: Falling back to user helper
[   12.526548] ath10k_pci 0000:02:00.0: could not fetch firmware file 'ath10k/QCA9377/hw1.0/firmware-4.bin': -12
[   12.526557] ath10k_pci 0000:02:00.0: Direct firmware load failed with error -2
[   12.526559] ath10k_pci 0000:02:00.0: Falling back to user helper
[   12.527055] ath10k_pci 0000:02:00.0: could not fetch firmware file 'ath10k/QCA9377/hw1.0/firmware-3.bin': -12
[   12.527065] ath10k_pci 0000:02:00.0: Direct firmware load failed with error -2
[   12.527066] ath10k_pci 0000:02:00.0: Falling back to user helper
[   12.527464] ath10k_pci 0000:02:00.0: could not fetch firmware file 'ath10k/QCA9377/hw1.0/firmware-2.bin': -12
[   12.527473] ath10k_pci 0000:02:00.0: Direct firmware load failed with error -2
[   12.527475] ath10k_pci 0000:02:00.0: Falling back to user helper
[   12.527869] ath10k_pci 0000:02:00.0: could not fetch firmware (-12)
[   12.527873] ath10k_pci 0000:02:00.0: could not fetch firmware files (-12)
[   12.527875] ath10k_pci 0000:02:00.0: could not probe fw (-12)

---

### Post by Hadaka on 2015-12-03
Hi, again COPY and paste...one line at a time..
```
echo "options ath10k_core skip_otp=Y" | sudo tee /etc/modprobe.d/ath10k_core.conf
git clone https://github.com/kvalo/ath10k-firmware.git
sudo cp -r ath10k-firmware/ /lib/firmware/ath10k/
sudo mv /lib/firmware/ath10k/QCA6174/hw3.0/firmware-4.bin_WLAN.RM.2.0-00180-QCARMSWPZ-1 /lib/firmware/ath10k/QCA6174/hw3.0/firmware-4.bin 
```
boot
test

---

### Post by chili555 on 2015-12-03
Hadaka suggests you read my post #101 here: [http://ubuntuforums.org/showthread.php?t=2300861&page=11](http://ubuntuforums.org/showthread.php?t=2300861&page=11)

---

### Post by chili555 on 2015-12-03
> **Hadaka said:**
> Hi, again COPY and paste...one line at a time..
```
echo "options ath10k_core skip_otp=Y" | sudo tee /etc/modprobe.d/ath10k_core.conf
git clone https://github.com/kvalo/ath10k-firmware.git
sudo cp -r ath10k-firmware/ /lib/firmware/ath10k/
sudo mv /lib/firmware/ath10k/QCA6174/hw3.0/firmware-4.bin_WLAN.RM.2.0-00180-QCARMSWPZ-1 /lib/firmware/ath10k/QCA6174/hw3.0/firmware-4.bin 
```
boot
testHis is not a 6174.

---

### Post by jeremy31 on 2015-12-03
> **chili555 said:**
> His is not a 6174.

My fault, it would be nice if the github site used the correct file name with the other info in the comment

---

### Post by Soham_Das on 2015-12-03
This file seems to be missing:

soham@soham-Flex-3-1480:~$ git clone [https://github.com/kvalo/ath10k-firmware.git](https://github.com/kvalo/ath10k-firmware.git)
Cloning into 'ath10k-firmware'...
remote: Counting objects: 349, done.
remote: Compressing objects: 100% (10/10), done.
remote: Total 349 (delta 1), reused 0 (delta 0), pack-reused 339
Receiving objects: 100% (349/349), 6.37 MiB | 5.15 MiB/s, done.
Resolving deltas: 100% (126/126), done.
Checking connectivity... done.
soham@soham-Flex-3-1480:~$ sudo cp -r ath10k-firmware/ /lib/firmware/ath10k/
soham@soham-Flex-3-1480:~$ sudo mv /lib/firmware/ath10k/QCA6174/hw3.0/firmware-4.bin_WLAN.RM.2.0-00180-QCARMSWPZ-1 /lib/firmware/ath10k/QCA6174/hw3.0/firmware-4.bin
mv: cannot stat ‘/lib/firmware/ath10k/QCA6174/hw3.0/firmware-4.bin_WLAN.RM.2.0-00180-QCARMSWPZ-1’: No such file or directory

---

### Post by Hadaka on 2015-12-03
yeah, our pal jeremy31 sent me the fix,,
try this
```
sudo mv /lib/firmware/ath10k/QCA9377/hw1.0/firmware-5.bin* /lib/firmware/ath10k/QCA9377/hw1.0/firmware-5.bin
```

---

### Post by Soham_Das on 2015-12-03
I get  the same thing:
sudo mv /lib/firmware/ath10k/QCA9377/hw1.0/firmware-5.bin* /lib/firmware/ath10k/QCA9377/hw1.0/firmware-5.bin
mv: cannot stat &#8216;/lib/firmware/ath10k/QCA9377/hw1.0/firmware-5.bin*&#8217;: No such file or directory

---

### Post by Hadaka on 2015-12-03
it needed to be QCA6174
```
sudo mv /lib/firmware/ath10k/QCA6174/hw1.0/firmware-5.bin* /lib/firmware/ath10k/QCA9377/hw1.0/firmware-5.bin
```

---

### Post by Soham_Das on 2015-12-03
Thanks a lot guys, I followed the instructions and its finally working :)

---

### Post by Hadaka on 2015-12-03
THANK YOU for putting up with my stumbbeling...
I am gratefull chilli555 and jermey31 jumped in and
saved the day,
and most of all im pleased that you got it going,.
dont forget to do the reload on the next kernel update.
thanks again.

and please mark this solved

---

