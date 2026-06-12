---
title: "no wifi connection-ACER V5 591G"
date: 2016-01-30
forum: Networking &amp; Wireless
---

### Post by alex-volos on 2016-01-30
Hello everyone,

I have just finished a fresh intallation of Ubuntu 14 LTS in an ACER V5 591G laptop .

However there is not wifi oprion to connect (and thetouchpad is also not working, but that's or related to this forum section).

I have tried these steps

sudo apt-get remove --purge bcmwl-kernel-source
sudo rm -rf /var/lib/apt/lists/lock
sudo dpkg -r bcmwl-kernel-source
sudo apt-get updatesudo apt-get install bcmwl-kernel-source
sudo modprobw wl

with no success.


Also, lspci -v | grep -i wireless doesn't return any results.

Does anyone have any ideas?

Thanks
Alex

---

### Post by chili555 on 2016-01-30
How about this command?```
lspci -nn | grep 0280
```Thanks.

---

### Post by alex-volos on 2016-01-31
Hi!

Thanks for your time.

It shows me 07:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:003e] (rev 32)

I don't know if it helps but sudo lshw -C network shows:

  *-network UNCLAIMED     
       description: Network controller
       product: Qualcomm Atheros
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 32
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:94000000-941fffff




Cheers
Alex

---

### Post by chili555 on 2016-01-31
Your device is covered by the driver* ath10k_pci*. It doesn't appear in the kernel until 15.04 and later, if I remember correctly. You could install 15.10 and also the needed firmware and be all set.

You could also compile the driver from source code like this on your current installation: [http://askubuntu.com/questions/707746/qualcom-atheros-wirelless-adapter-not-recognized-in-my-acer-v-nitro-laptop/707805#707805](http://askubuntu.com/questions/707746/qualcom-atheros-wirelless-adapter-not-recognized-in-my-acer-v-nitro-laptop/707805#707805)

Then you will need the firmware: [http://askubuntu.com/questions/726271/wifi-ol-lenovo-ideapad-300-15isk-atheros-qca9377/726324#726324](http://askubuntu.com/questions/726271/wifi-ol-lenovo-ideapad-300-15isk-atheros-qca9377/726324#726324)

Post back if you get stuck or need additional guidance.

---

### Post by alex-volos on 2016-01-31
> **chili555 said:**
> 

You could also compile the driver from source code like this on your current installation: [http://askubuntu.com/questions/707746/qualcom-atheros-wirelless-adapter-not-recognized-in-my-acer-v-nitro-laptop/707805#707805](http://askubuntu.com/questions/707746/qualcom-atheros-wirelless-adapter-not-recognized-in-my-acer-v-nitro-laptop/707805#707805)

Then you will need the firmware: [http://askubuntu.com/questions/726271/wifi-ol-lenovo-ideapad-300-15isk-atheros-qca9377/726324#726324](http://askubuntu.com/questions/726271/wifi-ol-lenovo-ideapad-300-15isk-atheros-qca9377/726324#726324)

Post back if you get stuck or need additional guidance.


I tried compiling the source code etc.

However now I don't even have ethernet conenction.

---

### Post by chili555 on 2016-01-31
> **alex-volos said:**
> I tried compiling the source code etc.

However now I don't even have ethernet conenction.Let's have a look at the ethernet card and try to fix that:```
lspci -nnk | grep 0200 -A2
```Did the compile process go without error? What is the result of:```
sudo modprobe ath10k_pci && dmesg | grep ath
```

---

### Post by alex-volos on 2016-02-01
Hello!

> **chili555 said:**
> Let's have a look at the ethernet card and try to fix that:```
lspci -nnk | grep 0200 -A2
```Did the compile process go without error? 


08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Acer Incorporated [ALI] Device [1025:1033]
    Kernel driver in use: r8169



> **chili555 said:**
> 
What is the result of:```
sudo modprobe ath10k_pci && dmesg | grep ath
```


[    0.645127] Loaded X.509 cert 'Magrathea: Glacier signing key: a932dc237895a44d3959bf91a3566a20ee211f37'


Thanks
Alex

---

### Post by chili555 on 2016-02-01
Ahhh! The twitchy ethernet driver r8169. Fun.

Please be sure the ethernet is connected with a known good cable. Then try:```
sudo ethtool -s eth0 speed 100 autoneg off
```Does it connect now? If so, please proceed with the compile and firmware installation.

---

### Post by alex-volos on 2016-02-02
Hello,

no still it doesn't connect. Also there is no button for network connection, on the upper right of the screen.


EDIT:

I added these lines : 

[B]auto eth0
iface eth0 inet dhcp

to [/B][COLOR=#000000]/etc/network/interfaces

but still no wifi and no network button on the upper right.

The installation of the firmware returns this:

(Reading database ... 248566 files and directories currently installed.)
Preparing to unpack linux-firmware_1.149.3_all.deb ...
Unpacking linux-firmware (1.149.3) over (1.149.3) ...
Setting up linux-firmware (1.149.3) ...



[/COLOR]

---

### Post by chili555 on 2016-02-02
> I added these lines :

auto eth0
iface eth0 inet dhcp

to /etc/network/interfacesWould you please change it to:```
auto lo
iface lo inet loopback

auto eth0
pre-up /usr/sbin/ethtool -s eth0 autoneg off
iface eth0 inet dhcp
```Now, please run:```
sudo ifdown eth0 && sudo ifup -v eth0
```The -v for verbose should produce some output telling us what is or isn't happening.

Of course, you could simply install Ubuntu 15.10 where the driver exists already. Install the latest firmware and you should be all set.

---

### Post by alex-volos on 2016-02-02
> **chili555 said:**
> 

Of course, you could simply install Ubuntu 15.10 where the driver exists already. Install the latest firmware and you should be all set.

I will try to change the code tomorrow, because I don't have it with me right now.

I am a bit sceptic about installing 15.10, because during one of my earlier tries I upgraded the kernel in 14 LTS and then I had the error " The system is running in low-graphics mode".

Anyway I could also try again with a clean installation. How can I install the latest firmware? With apt-get update & apt-get upgrade?


Thank you very much for taking the time to help me.
Alex

---

### Post by chili555 on 2016-02-02
You could certainly try the live session from the DVD or USB to see that everything is working. 'Low graphics mode' often means that the graphics card hasn't yet found a proper driver. You might check Software and Updates > Additional Drivers to see if a graphics driver is available.> How can I install the latest firmware? With apt-get update & apt-get upgrade?
I suggest:```
sudo apt-get update
sudo apt-get install linux-firmware
```Then check:```
sudo dpkg -s linux-firmware
```We hope you see:```
Package: linux-firmware
Status: install ok installed
Priority: optional
Section: misc
Installed-Size: 104722
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: all
Multi-Arch: foreign
[COLOR="#FF0000"]Version: 1.149.3[/COLOR]
Replaces: atmel-firmware, linux-restricted-common
Provides: atmel-firmware
Conflicts: atmel-firmware
Description: Firmware for Linux kernel drivers
 This package provides firmware used by Linux kernel drivers.

```You could also download the package on a USB stick or similar and, after dropping it on your desktop:```
cd ~/Desktop
sudo dpkg -i linux*.deb
```Load the driver:```
sudo modprobe ath10k_pci

```Check the log for errors, warnings, etc.:```
dmesg | grep ath10k
```

---

### Post by alex-volos on 2016-02-03
> **chili555 said:**
>  Now, please run:```
sudo ifdown eth0 && sudo ifup -v eth0
```The -v for verbose should produce some output telling us what is or isn't happening.

Of course, you could simply install Ubuntu 15.10 where the driver exists already. Install the latest firmware and you should be all set.

Hello!

The above command shows me this:

ifdown: couldn't read interfaces file "/etc/network/interfaces"

---

### Post by alex-volos on 2016-02-03
OK I did a clean installation of 15.10.

The ethernet is a  bit slow,

I followed your instructions and everything seems to be OK, but then i get a lot of errors from 


```
 dmesg | grep ath10k
```




```
[   10.596127] ath10k_pci 0000:07:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[   11.422463] ath10k_pci 0000:07:00.0: Direct firmware load for ath10k/cal-pci-0000:07:00.0.bin failed with error -2
[   11.475847] ath10k_pci 0000:07:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/board-pci-168c:003e:11ad:0807.bin failed with error -2
[   11.475850] ath10k_pci 0000:07:00.0: failed to load spec board file, falling back to generic: -2
[   11.558622] ath10k_pci 0000:07:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/firmware-5.bin failed with error -2
[   11.558626] ath10k_pci 0000:07:00.0: could not fetch firmware file 'ath10k/QCA6174/hw3.0/firmware-5.bin': -2
[   13.760433] ath10k_pci 0000:07:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff, 168c:003e:11ad:0807 fallback) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 api 4 htt 3.26 wmi 4 cal otp max_sta 32
[   13.760436] ath10k_pci 0000:07:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[   14.757396] ath10k_pci 0000:07:00.0: suspend timed out - target pause event never came
[   18.436628] ath10k_pci 0000:07:00.0 wlp7s0: renamed from wlan0
[   26.303575] ath10k_pci 0000:07:00.0: failed to enable dynamic BW: -11
[   29.303110] ath10k_pci 0000:07:00.0: could not suspend target (-11)
[   37.865867] ath10k_pci 0000:07:00.0: failed to enable dynamic BW: -11
[   40.865325] ath10k_pci 0000:07:00.0: could not suspend target (-11)
[   49.152016] ath10k_pci 0000:07:00.0: failed to enable dynamic BW: -11
[   52.151634] ath10k_pci 0000:07:00.0: could not suspend target (-11)
[   60.618236] ath10k_pci 0000:07:00.0: failed to enable dynamic BW: -11
[   63.621799] ath10k_pci 0000:07:00.0: could not suspend target (-11)
[   71.908548] ath10k_pci 0000:07:00.0: failed to enable dynamic BW: -11
[   74.908079] ath10k_pci 0000:07:00.0: could not suspend target (-11)
[   83.198694] ath10k_pci 0000:07:00.0: failed to enable dynamic BW: -11
[   86.198308] ath10k_pci 0000:07:00.0: could not suspend target (-11)
[   94.485014] ath10k_pci 0000:07:00.0: failed to enable dynamic BW: -11
[   97.484544] ath10k_pci 0000:07:00.0: could not suspend target (-11)
[  105.775185] ath10k_pci 0000:07:00.0: failed to enable dynamic BW: -11
[  108.774788] ath10k_pci 0000:07:00.0: could not suspend target (-11)
[  117.057501] ath10k_pci 0000:07:00.0: failed to enable dynamic BW: -11
[  120.057019] ath10k_pci 0000:07:00.0: could not suspend target (-11)
[  129.971473] ath10k_pci 0000:07:00.0: failed to enable dynamic BW: -11
[  132.971060] ath10k_pci 0000:07:00.0: could not suspend target (-11)
[  141.253715] ath10k_pci 0000:07:00.0: failed to enable dynamic BW: -11
[  144.253223] ath10k_pci 0000:07:00.0: could not suspend target (-11)
[  152.535822] ath10k_pci 0000:07:00.0: failed to enable dynamic BW: -11
[  155.535370] ath10k_pci 0000:07:00.0: could not suspend target (-11)


```

---

