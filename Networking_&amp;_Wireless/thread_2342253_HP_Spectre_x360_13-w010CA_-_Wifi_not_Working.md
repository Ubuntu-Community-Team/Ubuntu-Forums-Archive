---
title: "HP Spectre x360 13-w010CA - Wifi not Working"
date: 2016-11-05
forum: Networking &amp; Wireless
---

### Post by alex973 on 2016-11-05
Hi everyone,

I just installed Ubuntu on a brand new HP Spectre X360 but I'm unable to make the Wifi adapter working. I don't even see it in the configuration status.

It seems to be a bluetooth/wifi combo adapter on this model and the Bluetooth adapter is correctly recognized but no luck with the WiFi.

I tried the trick that was working with previous models (blacklist the acer-wmi but there is no acer-wmi running).

Thanks in advance if you have any idea.

Alex

---

### Post by howefield on 2016-11-05
Thread moved to the "*Networking & Wireless*" forum, probably a better fit.

Can you supply the wireless script information as detailed in this [sticky thread]("https://ubuntuforums.org/showthread.php?t=370108") ?

---

### Post by alex973 on 2016-11-05
> **howefield said:**
> Thread moved to the "*Networking & Wireless*" forum, probably a better fit.

Can you supply the wireless script information as detailed in this [sticky thread]("https://ubuntuforums.org/showthread.php?t=370108") ?

Thanks for moving the post at the right place!

I managed to get the Wireless infos, it's like I don't even have a Wifi card on the computer...

Thanks in advance if you have any clue.

Alex

```


########## wireless info START ##########


Report from: 04 Nov 2016 21:19 EDT -0400


Booted last: 04 Nov 2016 00:00 EDT -0400


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial


##### kernel ############################


Linux 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


01:00.0 Network controller [0280]: Intel Corporation Device [8086:24fd] (rev 78)
    Subsystem: Intel Corporation Device [8086:1010]


6d:00.0 Non-Volatile memory controller [0108]: Samsung Electronics Co Ltd NVMe SSD Controller [144d:a802] (rev 01)


##### lsusb #############################


Bus 002 Device 002: ID 0bc2:a014 Seagate RSS LLC 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 8087:0a2b Intel Corp. 
Bus 001 Device 003: ID 05c8:0431 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 001 Device 002: ID 05c8:0430 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
wmi                    20480  1 hp_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


##### iwconfig ##########################


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #######################


##### network managers ##################


Installed:


    NetworkManager


Running:


root      2516     1  0 21:17 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


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


##### iw reg get ########################


Region: America/New_York (based on set time zone)


country 00: DFS-UNSET
    (2402 - 2472 @ 40), (6, 20), (N/A)
    (2457 - 2482 @ 40), (6, 20), (N/A), PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 160), (6, 20), (N/A), PASSIVE-SCAN
    (5250 - 5330 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (6, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)


##### iwlist channels ###################


lo        no frequency information.


##### iwlist scan #######################


lo        Interface doesn't support scanning.


##### module infos ######################


##### module parameters #################


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


exit 0


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


########## wireless info END ############



```

---

### Post by chili555 on 2016-11-05
>  it's like I don't even have a Wifi card on the computer...Sure you do; it's right here:> 01:00.0 Network controller [0280]: Intel Corporation Device [8086:24fd] (rev 78)
    Subsystem: Intel Corporation Device [8086:1010]
It is usually covered by the driver iwlwifi. We wonder why the driver didn't load and start working as expected. Let's load it from the terminal and look for any informative messages, errors, warnings, etc.```
sudo modprobe iwlwifi
dmesg | grep iwl
```

---

### Post by jeremy31 on 2016-11-05
Alex973 should file a bug report against package linux, a guide to bug reports- [https://ubuntuforums.org/showthread.php?t=1011078](https://ubuntuforums.org/showthread.php?t=1011078)

The correct alias is not yet in the Ubuntu 4.4 kernels and the upstream commit is [http://git.kernel.org/cgit/linux/kernel/git/next/linux-next.git/commit/drivers/net/wireless/intel/iwlwifi?id=d34475b964b01067ed25187c4f52d8bdf2c0e113](http://git.kernel.org/cgit/linux/kernel/git/next/linux-next.git/commit/drivers/net/wireless/intel/iwlwifi?id=d34475b964b01067ed25187c4f52d8bdf2c0e113)

---

### Post by chili555 on 2016-11-05
> **jeremy31 said:**
> Alex973 should file a bug report against package linux, a guide to bug reports- [https://ubuntuforums.org/showthread.php?t=1011078](https://ubuntuforums.org/showthread.php?t=1011078)

The correct alias is not yet in the Ubuntu 4.4 kernels and the upstream commit is [http://git.kernel.org/cgit/linux/kernel/git/next/linux-next.git/commit/drivers/net/wireless/intel/iwlwifi?id=d34475b964b01067ed25187c4f52d8bdf2c0e113](http://git.kernel.org/cgit/linux/kernel/git/next/linux-next.git/commit/drivers/net/wireless/intel/iwlwifi?id=d34475b964b01067ed25187c4f52d8bdf2c0e113)The correct alias is, in fact, in the 4.8 kernel included in Ubuntu 16.10.```
chili@T440p:~$ modinfo iwlwifi | grep 24FD | grep 1010
alias:          pci:v00008086d000024FDsv*sd00001010bc*sc*i*

```Perhaps alex973 will upgrade.

---

### Post by alex973 on 2016-11-05
> **chili555 said:**
> Sure you do; it's right here:It is usually covered by the driver iwlwifi. We wonder why the driver didn't load and start working as expected. Let's load it from the terminal and look for any informative messages, errors, warnings, etc.```
sudo modprobe iwlwifi
dmesg | grep iwl
```

Thanks,

When I launch those 2 commands nothing happens, it just wait for the next command.

I also found a file /etc/modprobe.d/iwlwifi.conf and tried to comment the instructions (below) but no luck as well...

I don't know how to upgrade the distro without WiFi or an Ethernet port :(

Thanks

Alex.

File /iwlwifi.conf (after I commented everything) :

```
#remove iwlwifi \
#(/sbin/lsmod | grep -o -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod)$
#&& /sbin modprobe -r mac80211
```

---

### Post by alex973 on 2016-11-05
> **chili555 said:**
> The correct alias is, in fact, in the 4.8 kernel included in Ubuntu 16.10.```
chili@T440p:~$ modinfo iwlwifi | grep 24FD | grep 1010
alias:          pci:v00008086d000024FDsv*sd00001010bc*sc*i*

```Perhaps alex973 will upgrade.

Thanks!!

I'll download the 16.10 and try it right away, that can be a quick fix :)

Alex

---

### Post by alex973 on 2016-11-06
Hi Guys,

Just wanted to thank you for your help, after installing Ubuntu 16.10 everything is working including WiFi, sound etc...

Now I have to understand why the battery doesnt last very long and how to disable the keyboard in tablet mode but it's looking good :)

Thanks again.

Alex

---

