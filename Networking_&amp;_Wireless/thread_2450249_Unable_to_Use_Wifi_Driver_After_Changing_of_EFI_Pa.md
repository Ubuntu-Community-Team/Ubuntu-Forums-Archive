---
title: "Unable to Use Wifi Driver After Changing of EFI Path on Acer One 10 S1003(d16h1)"
date: 2020-09-10
forum: Networking &amp; Wireless
---

### Post by czerwone on 2020-09-10
I have Acer One 10 machine that comes with Windows 10 x86 OS preinstalled (UEFI x86, Processor x64 based Intel Atom x64), and I installed Lubuntu 20.04 following the instructions on [this page]("https://www.reddit.com/r/linuxhardware/comments/8azizs/running_ubuntu_on_the_terrible_acer_one_10_s1003/"). Wifi driver was working on Windows and knowing absolutely nothing about SDIO drivers, after lot of struggles I managed to install Lubuntu 20.04 on this machine with erasing all the partitions. Wifi driver had worked without a problem after I run the shell script (which copies **brcmfmac43430a0-sdio.txt **and binaries from armbian to /lib/firmware/brcm) shared in Reddit post on Lubuntu.

The thing is, when I tried to install Lubuntu 20.04 from the ISO file (from Lubuntu official page) contents on USB  (I formatted usb with FAT32 filesystem with copying ISO contents in it because I needed to put BOOTIA32.efi on USB to be able to run x64 installer, iso9960 standart is read-only) the installer had returned errors related with grub (Python bootloader error: Cannot set EFI variable). So I had manually grub-installed on this machine ignorantly because it was my first time to implement grub-install command . I have two partitions, (/dev/mmcblk0p1/ fat32 fs for /boot/efi and /dev/mmcblk0p2 ext4 fs for / root partition), I firstly copied boot folder of p2 partition in p1 with EFI files. Grub was booting with errors and were unable to boot with updated kernel versions( I had to manually copy vmlinuz and initrd images in p1 partitions to be able to run with updated kernels). I was booting with BOOTIA32.EFI which were in /EFI/BOOT folder in p1 partition. I just tried to change the BOOTIA32.EFI path in p1 partition to see if it solves anything and then, interesting enough even thought I reverted my changes I had lost the Wifi functionality. This is the start point of the Wifi issue.

Aftermath, I reinstalled the Lubuntu 20.04 with manual partitioning but this time, doing the grub-install for EFI with [more proper way]("https://askubuntu.com/questions/831216/how-can-i-reinstall-grub-to-the-efi-partition"). I ran the script again but this time, it didn't solve anything related with Network like it did. I searched about this issue almost everywhere on every page and tried to solve this issue with given instructions but none of them worked. brcmfmac module exists but interesting enough, it doesn't list in lsmod and ```
modprobe brcmfmac
``` loads the module without errors but that doesn't solve anything either.

Another difference about my situation is, nothing related with sdio and brcm is run even during kernel boot.
```
sudo dmesg | grep sdio
sudo dmesg | grep brcm
```
Returns nothing. Nothing related with network driver is listed in lspci lsusb and even dmidecode either. It can be caused from a missing driver or it may be a firmware bug issue. I am not sure about the source of the problem. I am able to connect internet via USB Tethering and all of my packages are up to date. Already tried to run and reinstall several drivers like such as linux-firmware, brcm80211, bcmlw-kernel (deleted aftermath since it blacklists the main Broadcom drivers). This issue had already stolen my three days and I think I'm going to lose my mind.

wireless - info
```


########## wireless info START ##########


Report from: 10 Sep 2020 01:05 +03 +0300


Booted last: 10 Sep 2020 00:00 +03 +0300


Script from: 22 Oct 2018 03:34 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.1 LTS
Release:    20.04
Codename:    focal


##### kernel ############################


Linux 5.4.0-47-generic #51-Ubuntu SMP Fri Sep 4 19:50:52 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash


##### desktop ###########################


sed: can't read /root/.dmrc: No such file or directory


Could not be determined.


##### lspci #############################


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0489:c001 Foxconn / Hon Hai Android
Bus 001 Device 002: ID 06cb:73f5 Synaptics, Inc. ITE Device(8910)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### secure boot #######################


This system doesn't support Secure Boot


##### lsmod #############################


snd_soc_sst_cht_bsw_rt5645    28672  2
snd_soc_rt5645        172032  2 snd_soc_sst_cht_bsw_rt5645
snd_soc_acpi           16384  4 snd_sof_acpi,snd_soc_acpi_intel_match,snd_intel_sst_acpi,snd_soc_sst_cht_bsw_rt5645
snd_soc_rl6231         20480  1 snd_soc_rt5645
snd_soc_core          245760  4 snd_sof,snd_soc_sst_atom_hifi2_platform,snd_soc_rt5645,snd_soc_sst_cht_bsw_rt5645
snd_pcm               106496  6 snd_sof,snd_soc_sst_atom_hifi2_platform,snd_soc_core,snd_soc_rt5645,snd_soc_sst_cht_bsw_rt5645,snd_pcm_dmaengine
wmi_bmof               16384  0
wmi                    32768  1 wmi_bmof


##### interfaces ########################


##### ifconfig ##########################


1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever


##### iwconfig ##########################


lo        no wireless extensions.


##### route #############################


##### resolv.conf #######################


[644 root '/etc/resolv.conf']
nameserver 127.0.0.53


##### network managers ##################


Installed:


    NetworkManager


Running:


root         628       1  0 00:59 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


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


Region: Europe/Istanbul (based on set time zone)


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


##### iwlist scan #######################


lo        Interface doesn't support scanning.


##### module infos ######################


##### module parameters #################


##### /etc/modules ######################


##### modprobe options ##################


[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode


[/etc/modprobe.d/blacklist-acer-hdmi.conf]
blacklist snd-hdmi-lpe-audio


[/etc/modprobe.d/blacklist-acer-i915.conf]
blacklist i915


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


[   10.060479] rt5645 i2c-10EC5645:00: i2c-10EC5645:00 supply avdd not found, using dummy regulator
[   10.060518] rt5645 i2c-10EC5645:00: i2c-10EC5645:00 supply cpvdd not found, using dummy regulator
[   10.894087] cht-bsw-rt5645 cht-bsw-rt5645: snd-soc-dummy-dai <-> media-cpu-dai mapping ok
[   10.894627] cht-bsw-rt5645 cht-bsw-rt5645: snd-soc-dummy-dai <-> deepbuffer-cpu-dai mapping ok
[   10.896103] cht-bsw-rt5645 cht-bsw-rt5645: rt5645-aif1 <-> ssp2-port mapping ok
[   10.957902] input: chtrt5645 Headset as /devices/pci0000:00/808622A8:00/cht-bsw-rt5645/sound/card0/input16


########## wireless info END ############



```

Things I Tried
[LIST=1]
[*] Learned SDIO drivers work with nvram files thats stored in efivars file (EFI firmware settings) and understood why EFI configuration breaks the Wifi. Like Jeremy31 suggested in several [posts]("https://ubuntuforums.org/showthread.php?t=2438250&page=3&highlight=d16h1"), I had checked /sys/firmware/efi/efivars and it was empty, no nvram file were found. But it can be done without nvram file since there are people who managed to run Wifi driver without nvram file.
[*] Tried to copy and rename **brcmfmac43430a0-sdio.txt ****to** **nvram-74b00bd9-805a-4d61-b51f-43268123d113 **and copy it to /sys/firmware/efi/efivars with both efibootmgr and efivar packages but it was not permanent, the nvram file deleted after the reboot. Nvram files actually differs from systems to systems, it was kind of dirty hack.
[*]Tried to modprobe several modules especially Broadcom modules (b43, brcmfmac), nothing changed.
[*]Tried to blacklist acer_wmi module that loads during the kernel and produces No WMID Detection Found error. It is listed in dmesg but not in lsmod. Removed the error in kernel boot but didn't solve anything. Reverted back.
[*] Tried to install [Acer S1003 network drivers]("https://www.acer.com/ac/en/US/content/support-product/6822?b=1") on machine via ndiswrapper-utils. As expected, nothing useful happened. (I did this one before I reinstalled the Lubuntu again, so possibly this couldn't hurt the system)
[*]Found the UEFI a little bit buggy and notice the BIOS is upgradable in dmidecode and updates are available in vendors website, I decided to install and run the BIOS updates (.exe files). First, I tried to do it via FreeDOS but since the machine works only with UEFI (no CSM available since this machine is a low-budget market production) and FreeDOS only works with BIOS, I couldn't boot FreeDOS. The other solution was, reinstalling the Windows 10 x32 and installing both the drivers and BIOS updates hoping it would regenerate nvram files. UEFI couldn't even boot Windows 10 x86 ISO (system restarts within a loop). (This should be another issue of different topic)
[*]Examined several [/sys/bus files]("https://askubuntu.com/questions/566130/ubuntu-does-not-detect-wifi-bt-combo-card-bcm4330-ap6383") from different sources for my SDIO drive, also mentioned by Jeremy31. It depends on the drive of course, probably it should be Broadcom 802.11 abgn SDIO drive if I'm not remembering wrong from Windows incorrectly but also this information is available in Acer forums. All of the outputs product auto commands and turning it on (echo on>/sys/...) didn't change anything.
[/LIST]

Thank you very much for the contributions.

---

