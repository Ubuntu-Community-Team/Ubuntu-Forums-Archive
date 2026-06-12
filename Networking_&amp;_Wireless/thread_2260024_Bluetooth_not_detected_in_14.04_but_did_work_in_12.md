---
title: "Bluetooth not detected in 14.04 but did work in 12.04"
date: 2015-01-08
forum: Networking &amp; Wireless
---

### Post by coldraven on 2015-01-08
After a couple of hours googling I have given up and come here.
I just did a fresh install of 14.04 (64bit) on to this HP 6715b laptop. As the title says the Bluetooth that worked with 12.04 is no longer detected.
The Wifi is working OK out of the box. Any help would be much appreciated, thanks.

```
rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


```

```
dmesg | grep -i blue
[   19.109723] Bluetooth: Core ver 2.17
[   19.109761] Bluetooth: HCI device and connection manager initialized
[   19.109831] Bluetooth: HCI socket layer initialized
[   19.109836] Bluetooth: L2CAP socket layer initialized
[   19.109842] Bluetooth: SCO socket layer initialized
[   19.115687] Bluetooth: RFCOMM TTY layer initialized
[   19.115704] Bluetooth: RFCOMM socket layer initialized
[   19.115717] Bluetooth: RFCOMM ver 1.11
[   19.212185] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.212191] Bluetooth: BNEP filters: protocol multicast
[   19.212204] Bluetooth: BNEP socket layer initialized
[ 8485.815932] Modules linked in: michael_mic arc4 bnep rfcomm bluetooth hid_a4tech usbhid hid hp_wmi sparse_keymap pcmcia radeon snd_hda_codec_analog kvm_amd kvm snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq snd_seq_device snd_timer lib80211_crypt_tkip joydev serio_raw snd edac_core ttm k8temp yenta_socket edac_mce_amd pcmcia_rsrc pcmcia_core drm_kms_helper wl(POX) sp5100_tco i2c_piix4 soundcore lib80211 drm i2c_algo_bit cfg80211 shpchp wmi tpm_infineon video hp_accel lis3lv02d input_polldev mac_hid parport_pc ppdev lp parport pata_acpi firewire_ohci firewire_core psmouse crc_itu_t pata_atiixp tg3 ptp pps_core ahci libahci


```

```
sudo lshw -C network
[sudo] password for cr: 
  *-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:29:a8:71:96
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.134 firmware=sb v2.09 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:d0000000-d000ffff
  *-network
       description: Wireless interface
       product: BCM4311 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:30:00.0
       logical name: wlan0
       version: 02
       serial: 00:21:00:4f:c3:0c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.141 (r415941) ip=192.168.2.100 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:18 memory:c8000000-c8003fff


```

---

### Post by jeremy31 on 2015-01-08
Please post the results of ```
lsusb
```

---

### Post by coldraven on 2015-01-09
We just just got the power back on here after an outage :)

```
lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 09da:000a A4 Tech Co., Ltd Optical Mouse Opto 510D
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


```

---

### Post by jeremy31 on 2015-01-09
Do you have a 12.04 ISO burned to a disk that you could get the lsusb info from?  I would recommend filing a bug report at [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug) as this might be very difficult to diagnose

---

### Post by coldraven on 2015-01-10
> **jeremy31 said:**
> Do you have a 12.04 ISO burned to a disk that you could get the lsusb info from?  I would recommend filing a bug report at [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug) as this might be very difficult to diagnose

Good idea. I will make a bootable 12.04 USB stick and get back with the results.

---

### Post by coldraven on 2015-01-11
Firstly I must apologise for the delay in replying. All my Linux dists are kept on an external drive along with all my backups. We have had so many thunderstorms lately that I feared to plug it in :(

I made a bootable 12.04.3 USB stick but there is a problem. It boots to the desktop but cannot install the Broadcom drivers because the media is read only.
So looking at the output of lsusb just shows the same as before plus the USB stick that it is booting from.
I have attached the tail of /var/log/jockey.log which shows the errors that occurred when I tried to install "Additional Drivers".

Other than reverting back to 12.04 I have run out of ideas :(

---

### Post by coldraven on 2015-01-12
I trawled through some old backups and found a file called hwinfo.txt. I have snipped out the parts that mention Bluetooth.
Maybe someone can make sense of it.

```
Snipped from hwinfo.txt

-------------------------------------------------------------------------------------------------------------------
44: udi = '/org/freedesktop/Hal/devices/usb_device_3f0_171d_noserial_if0_bluetooth_hci_0_rfkill_hci0_bluetooth'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'rfkill'
  info.capabilities = { 'killswitch' }
  info.category = 'killswitch'
  info.addons.singleton = { 'hald-addon-rfkill-killswitch' }
  killswitch.type = 'bluetooth'
  killswitch.state = 1 (0x1)
  killswitch.access_method = 'rfkill'
  killswitch.name = 'hci0'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.0/usb2/2-2/2-2:1.0/bluetooth/hci0/rfkill0'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_3f0_171d_noserial_if0_bluetooth_hci_0'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_3f0_171d_noserial_if0_bluetooth_hci_0_rfkill_hci0_bluetooth'
  info.subsystem = 'rfkill'
  info.product = 'hci0 bluetooth Killswitch'
  info.interfaces = { 'org.freedesktop.Hal.Device.KillSwitch' }

  45: udi = '/org/freedesktop/Hal/devices/usb_device_3f0_171d_noserial_if0_bluetooth_hci_0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'bluetooth'
  info.capabilities = { 'bluetooth_hci' }
  info.category = 'bluetooth_hci'
  bluetooth_hci.originating_device = '/org/freedesktop/Hal/devices/usb_device_3f0_171d_noserial_if0'
  bluetooth_hci.address = 0ull (0x0ull)
  info.subsystem = 'bluetooth'
  info.product = 'Bluetooth Host Controller Interface'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.0/usb2/2-2/2-2:1.0/bluetooth/hci0'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_3f0_171d_noserial_if0'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_3f0_171d_noserial_if0_bluetooth_hci_0'
----------------------------------------------------------------------------------------------------------------


linux.subsystem = 'usb'
  info.product = 'Wireless (Bluetooth + WLAN) Interface [Integrated Module]'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_3f0_171d_noserial'
  info.subsystem = 'usb_device'
  usb_device.configuration_value = 1 (0x1)
  usb_device.num_configurations = 1 (0x1)
  usb_device.num_interfaces = 4 (0x4)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_13_0'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.0/usb2/2-2'
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.0/usb2/2-2'
  usb_device.device_class = 224 (0xe0)
  usb_device.device_subclass = 1 (0x1)
  usb_device.device_protocol = 1 (0x1)
  usb_device.vendor_id = 1008 (0x3f0)
  usb_device.product_id = 5917 (0x171d)
  usb_device.vendor = 'Hewlett-Packard'
  info.vendor = 'Hewlett-Packard'
  usb_device.device_revision_bcd = 256 (0x100)
  usb_device.max_power = 0 (0x0)
  usb_device.product = 'Wireless (Bluetooth + WLAN) Interface [Integrated Module]'

---------------------------------------------------------------------------------------------------------------------
```

---

### Post by praseodym on 2015-01-12
Try the Broadcom-STA driver from 14.10:
```

sudo apt-get remove --purge bcmwl-kernel-source
wget http://de.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu1_amd64.deb
sudo dpkg -i *.deb
```
Reboot and check:
```

lspci -nnk | grep -iA2 net
dmesg | egrep '[F]irm|[B]lue'
lsmod
lsusb
```

---

### Post by coldraven on 2015-01-13
> **praseodym said:**
> Try the Broadcom-STA driver from 14.10:
```

sudo apt-get remove --purge bcmwl-kernel-source
wget http://de.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu1_amd64.deb
sudo dpkg -i *.deb
```
Reboot and check:
```

lspci -nnk | grep -iA2 net
dmesg | egrep '[F]irm|[B]lue'
lsmod
lsusb
```

I will try that later, I'm working on something else ATM.
Yesterday when searching for usb_device.product_id = 5917 (0x171d) I kept finding links that mention "Dumping 150 device(s) from the Global Device List:"
I'm not sure what that means but maybe it's the problem.
[http://www.codon.org.uk/~mjg59/tmp/lshal.txt](http://www.codon.org.uk/~mjg59/tmp/lshal.txt)

---

### Post by coldraven on 2015-01-22
Sorry that I have not replied sooner, I've been a bit out of sorts lately :(
I feel better now :)

```
sudo apt-get remove --purge bcmwl-kernel-source
[sudo] password for coldraven: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  bcmwl-kernel-source*
0 to upgrade, 0 to newly install, 1 to remove and 20 not to upgrade.
After this operation, 5,800 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 232848 files and directories currently installed.)
Removing bcmwl-kernel-source (6.30.223.141+bdcom-0ubuntu2) ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Purging configuration files for bcmwl-kernel-source (6.30.223.141+bdcom-0ubuntu2) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-44-generic


```

```
 sudo dpkg -i bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu1_amd64.deb 
Selecting previously unselected package bcmwl-kernel-source.
(Reading database ... 232782 files and directories currently installed.)
Preparing to unpack bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu1_amd64.deb ...
Unpacking bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu1) ...
Setting up bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu1) ...
Loading new bcmwl-6.30.223.248+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 3.13.0-44-generic
Building for architecture x86_64
Building initial module for 3.13.0-44-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-44-generic/updates/dkms/

depmod....

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-44-generic


```

I will reboot and see if it worked.

---

### Post by coldraven on 2015-01-22
After a reboot: In Settings>Bluetooth "Bluetooth adapter not found".

```
 lspci -nnk | grep -iA2 net
10:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:30c2]
    Kernel driver in use: tg3
30:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 02)
    Subsystem: Hewlett-Packard Company Broadcom 802.11a/b/g WLAN [103c:1371]
    Kernel driver in use: wl


```

```
dmesg | egrep '[F]irm|[B]lue'
[   18.653289] Bluetooth: Core ver 2.17
[   18.653404] Bluetooth: HCI device and connection manager initialized
[   18.654735] Bluetooth: HCI socket layer initialized
[   18.654744] Bluetooth: L2CAP socket layer initialized
[   18.654756] Bluetooth: SCO socket layer initialized
[   18.665074] Bluetooth: RFCOMM TTY layer initialized
[   18.665090] Bluetooth: RFCOMM socket layer initialized
[   18.665106] Bluetooth: RFCOMM ver 1.11
[   18.684359] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.684365] Bluetooth: BNEP filters: protocol multicast
[   18.684379] Bluetooth: BNEP socket layer initialized


```

```
lsmod
Module                  Size  Used by
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             27613  0 
vboxdrv               409815  3 vboxnetadp,vboxnetflt,vboxpci
bnep                   19624  2 
rfcomm                 69160  0 
bluetooth             391136  10 bnep,rfcomm
binfmt_misc            17468  1 
hid_a4tech             12651  0 
usbhid                 52659  0 
hid                   106148  2 hid_a4tech,usbhid
hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
wl                   6367819  0 
snd_hda_codec_analog    15049  1 
snd_hda_intel          56451  3 
snd_hda_codec         192906  2 snd_hda_intel,snd_hda_codec_analog
pcmcia                 62299  0 
snd_hwdep              13602  1 snd_hda_codec
kvm_amd                60026  0 
snd_pcm               102099  2 snd_hda_codec,snd_hda_intel
kvm                   455835  1 kvm_amd
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
joydev                 17381  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
k8temp                 12978  0 
serio_raw              13462  0 
edac_core              62291  0 
edac_mce_amd           22617  0 
snd                    69322  16 snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_hda_codec_analog,snd_seq_midi
yenta_socket           41027  0 
pcmcia_rsrc            18407  1 yenta_socket
pcmcia_core            23592  3 pcmcia,pcmcia_rsrc,yenta_socket
soundcore              12680  1 snd
sp5100_tco             13979  0 
i2c_piix4              22155  0 
cfg80211              484040  1 wl
radeon               1522640  3 
tpm_infineon           17372  0 
video                  19476  0 
hp_accel               26012  0 
ttm                    85150  1 radeon
lis3lv02d              20156  1 hp_accel
input_polldev          13896  1 lis3lv02d
wmi                    19177  1 hp_wmi
mac_hid                13205  0 
drm_kms_helper         55071  1 radeon
parport_pc             32701  1 
drm                   303102  5 ttm,drm_kms_helper,radeon
i2c_algo_bit           13413  1 radeon
ppdev                  17671  0 
shpchp                 37032  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
pata_acpi              13038  0 
firewire_ohci          40409  0 
psmouse               106714  0 
firewire_core          68769  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
pata_atiixp            13271  0 
tg3                   166478  0 
ptp                    18933  1 tg3
pps_core               19382  1 ptp
ahci                   25819  2 
libahci                32716  1 ahci


```

```
lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 09da:000a A4 Tech Co., Ltd Optical Mouse Opto 510D
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


```

Attached is result of search in "Additional Drivers".

---

### Post by coldraven on 2015-01-30
Bump!
While fixing a different problem I discovered this message. My wifi is still working OK but this must be a Broadcom related bug.
There does not seem to be any progress over on Launchpad :(
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1352821](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1352821)
```
dmesg | grep taint
[   16.274103] wl: module license 'MIXED/Proprietary' taints kernel.
[   16.274112] Disabling lock debugging due to kernel taint
[   16.285394] wl: module verification failed: signature and/or  required key missing - tainting kernel
```

---

### Post by coldraven on 2015-08-15
I just bought a duplicate of my laptop from eBay, it was £67 including postage. It came with Vista which enabled me to update the BIOS using the HPQflash utility from here:
[http://h20564.www2.hp.com/hpsc/swd/public/readIndex?sp4ts.oid=3356631&swLangOid=8&swEnvOid=1093](http://h20564.www2.hp.com/hpsc/swd/public/readIndex?sp4ts.oid=3356631&swLangOid=8&swEnvOid=1093)

Now it has BIOS version F.20. Then I swapped over the HDDs and Ubuntu 14.04 immediately found the Bluetooth adapter. So the original problem may have been due to the old BIOS or perhaps the module had failed.

From the same link I then made a FreeDos bootable USB stick to try and update my old laptop. 
The reason I used that method was because I figured that Vista would not run in a machine that it was not originally installed on. It booted and got about 10% through flashing the BIOS and then crashed. It has bricked it! So on the day my "new" laptop arrived my old one is now dead :( I'm not to unhappy because the backlight was getting very dim and the keyboard would randomly stop working. 

I hope that this helps anyone who has the HP 6715b, it's been a very reliable machine up until recently and now I have a clone!
So I will mark this thread as solved, many thanks to everyone who tried to help.

---

