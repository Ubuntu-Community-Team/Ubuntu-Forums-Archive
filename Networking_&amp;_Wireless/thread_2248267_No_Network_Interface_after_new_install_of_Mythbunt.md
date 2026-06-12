---
title: "No Network Interface after new install of Mythbuntu 14.04.1"
date: 2014-10-13
forum: Networking &amp; Wireless
---

### Post by qz9090 on 2014-10-13
I installed Mythbuntu 14.04.1 (64 bit) over a Win7 installation on a 1 TB drive and did a total replacement of the OS.
It seems that Mythbuntu is operating correctly, i.e. I get menus, etc. but I don't seem to have network connectivity.

When I run "lspci" I get Atheros Communications AR8121.

Based on my research (yes, I did that before posting this question), it seems that I may be missing a driver.
From what I could determine the driver should be either "atl1e" or "atl1c"

Unfortunately, I don't know where to get these drivers and how to install them. Although, they seem to be present in the installation.

In looking at the /sys/bus/pci/drivers/ there is a folder called "ATL1E"   in all caps but I was unable to rename it (I assumed it should be all lowercase).

I tried to edit the /etc/rc.local file but was unable to do so, since Mybuntu does not include any editors...... aaarg...
I was trying to insert:

modprobe atl1e
echo "1969 1026" > /sys/bus/pci/drivers/atl1e/new_id


Any thoughts or assistance would be appreciated.

---

### Post by qz9090 on 2014-10-15
> **qz9090 said:**
> I installed Mythbuntu 14.04.1 (64 bit) over a Win7 installation on a 1 TB drive and did a total replacement of the OS.
It seems that Mythbuntu is operating correctly, i.e. I get menus, etc. but I don't seem to have network connectivity.

When I run "lspci" I get Atheros Communications AR8121.

Based on my research (yes, I did that before posting this question), it seems that I may be missing a driver.
From what I could determine the driver should be either "atl1e" or "atl1c"

Unfortunately, I don't know where to get these drivers and how to install them. Although, they seem to be present in the installation.

In looking at the /sys/bus/pci/drivers/ there is a folder called "ATL1E"   in all caps but I was unable to rename it (I assumed it should be all lowercase).

I tried to edit the /etc/rc.local file but was unable to do so, since Mybuntu does not include any editors...... aaarg...
I was trying to insert:

modprobe atl1e
echo "1969 1026" > /sys/bus/pci/drivers/atl1e/new_id


Any thoughts or assistance would be appreciated.

Okay, so I was able to get some output from some command line commands:

lspci -nnk | grep -iA2 net

02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8121/AR8113/AR8114 Gigabit or Fast Ethernet [1969:1026] (rev b0)
    Subsystem: ASUSTeK Computer Inc. Device [1043:831c]

lsmod

Module                  Size  Used by
radeon               1522422  2 
ttm                    85115  1 radeon
drm_kms_helper         53081  1 radeon
drm                   303102  4 ttm,drm_kms_helper,radeon
snd_hda_codec_hdmi     46254  1 
snd_hda_codec_via      27860  1 
nfsd                  280330  13 
i2c_algo_bit           13413  1 radeon
snd_hda_intel          52355  5 
snd_hda_codec         192906  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
snd_seq_midi           13324  0 
auth_rpcgss            59338  1 nfsd
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_hwdep              13602  1 snd_hda_codec
nfs_acl                12837  1 nfsd
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
shpchp                 37032  0 
nfs                   236636  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
edac_core              62291  0 
serio_raw              13462  0 
edac_mce_amd           22617  0 
kvm_amd                59987  0 
sp5100_tco             13979  0 
snd                    69238  21 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_via,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
kvm                   451511  1 kvm_amd
k10temp                13126  0 
wmi                    19177  0 
soundcore              12680  1 snd
i2c_piix4              22155  0 
asus_atk0110           18657  0 
mac_hid                13205  0 
lockd                  93977  2 nfs,nfsd
sunrpc                284590  23 nfs,nfsd,auth_rpcgss,lockd,nfs_acl
fscache                63988  1 nfs
lp                     17759  0 
parport                42348  1 lp
pata_acpi              13038  0 
psmouse               106678  0 
pata_atiixp            13271  0 
ahci                   25819  2 
libahci                32560  1 ahci
atl1e                  42380  0 
floppy                 69418  0 

Does this help? Any input would be appreciated....

---

### Post by qz9090 on 2014-10-20
Since I have not gotten any input, I was wondering if I posted this question in the wrong area? If so, would someone let me know.
Thanks.

---

### Post by chili555 on 2014-10-20
As you can see, the needed driver is already loaded:> ....
pata_atiixp 13271 0 
ahci 25819 2 
libahci 32560 1 ahci
[COLOR="#FF0000"]atl1e[/COLOR] 42380 0 
floppy 69418 0 Was an interface, ideally eth0 created?```
ifconfig
```Do you see a Network Manager icon? Can you click it and try to connect? Are there any clues in the log?```
dmesg | grep -e eth0 -e atl1e
```

---

### Post by qz9090 on 2014-10-21
> **chili555 said:**
> As you can see, the needed driver is already loaded:Was an interface, ideally eth0 created?```
ifconfig
```Do you see a Network Manager icon? Can you click it and try to connect? Are there any clues in the log?```
dmesg | grep -e eth0 -e atl1e
```

In running: ifconfig

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:500 errors:0 dropped:0 overruns:0 frame:0
          TX packets:500 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:35008 (35.0 KB)  TX bytes:35008 (35.0 KB)

When I ran: dmesg | grep -e eth0 -e atl1e

I got nothing....

Cursor moves down and gives me another line but no results.

Thanks.

---

### Post by chili555 on 2014-10-21
Let's try to provoke a response that will, hopefully, give us some clues as to what's wrong; please reboot and then:```
sudo modprobe atl1e
dmesg | grep atl1e
```

---

### Post by qz9090 on 2014-10-21
Rebooted and used the command line to execute;

sudo modprobe atl1e

and 

dmesg | grep atl1e

...got nothing for results.

Hmmmm.....  
Thanks.

---

### Post by chili555 on 2014-10-21
Hmmmm, indeed! Let's dig a bit deeper:```
dmesg | grep 02:00
```Thanks.

---

### Post by qz9090 on 2014-10-21
Ok, results from 'dmesg | grep 0:200'

[    0.430168] pci 0000:02:00.0: [1969:1026] type 00 class 0x020000
[    0.430188] pci 0000:02:00.0: reg 0x10: [mem 0xfbfc0000-0xfbffffff 64bit]
[    0.430198] pci 0000:02:00.0: reg 0x18: [io  0xec00-0xec7f]
[    0.430280] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.430320] pci 0000:02:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    2.019926] ATL1E 0000:02:00.0 (unregistered net_device): get mac address failed
[    2.019988] ATL1E: probe of 0000:02:00.0 failed with error -5

Hmmm.... error -5... 
Does this help?

Thanks.

---

### Post by chili555 on 2014-10-22
> [ 2.019926] ATL1E 0000:02:00.0 (unregistered net_device):** get mac address failed**
[ 2.019988] ATL1E: probe of 0000:02:00.0 failed with error -5Very interesting. I have seen a very few of these and the solution is not very clear. First, let's see:```
cat /etc/udev/rules.d/70-persistent-net.rules
sudo lshw -C network
```Let's see if the system otherwise sees the MAC address.

Is the computer's BIOS updated?

Is it possible that the card is not quite fully seated in its PCI slot? Have you tried another slot? If you decide to open up the computer and check the hardware, please use all precautions.

---

### Post by qz9090 on 2014-10-22
The "cat" command resulted in a file not found error. In looking in the rules.d directory, there is only one text file.

In running "sudo lshw -C network"

  *-network UNCLAIMED
       description: Ethernet controller
       product: AR8121/AR8113/AR8114 Gigabit or Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       version: b0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:fbfc0000-fbffffff ioport:ec00(size=128)

The BIOS is the latest for this motherboard.
With respect to the NIC card, it's integrated into the motherboard so alternate slots or checking hardware are not feasible.

On another note, I am running an ASUS M4A78 Pro motherboard and I checked their website for drivers and they have a ZIP file of linux drivers.

See:

[http://www.asus.com/Motherboards/M4A78_PRO/HelpDesk_Download/](http://www.asus.com/Motherboards/M4A78_PRO/HelpDesk_Download/)


I don't know what is in the ZIP (still downloading it) or how to determine if the drivers are compatible with 64 bit Ubuntu/Mybuntu.
If you could help me identify where I should load those drivers and how to point the OS to look there, I would be willing to give that a shot too.

Thanks.

---

### Post by chili555 on 2014-10-22
> I don't know what is in the ZIP (still downloading it) or how to determine if the drivers are compatible with 64 bit Ubuntu/Mybuntu.
If you could help me identify where I should load those drivers and how to point the OS to look there, I would be willing to give that a shot too.
Except that you already have a driver, atl1e, that refuses to cooperate because it can't find the MAC address. I doubt it will do any good to install a different, probably older driver.

Your lshw doesn't see it either:> *-network UNCLAIMED
description: Ethernet controller
product: AR8121/AR8113/AR8114 Gigabit or Fast Ethernet
vendor: Qualcomm Atheros
physical id: 0
bus info: pci@0000:02:00.0
version: b0
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress cap_list
configuration: latency=0
resources: memory:fbfc0000-fbffffff ioport:ec00(size=128)
Ideally, the MAC address should be recorded. Here is a redacted sample from my machine:```
*-network               
       description: Ethernet interface
       product: 82577LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 06
       [COLOR="#FF0000"]serial: 99:de:f1:3e:b2:99[/COLOR]
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k firmware=0.12-1 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:f2600000-f261ffff memory:f2625000-f2625fff ioport:1820(size=32)

```Aside from setting the BIOS to defaults or buying a different ethernet card, I have no other suggestions.

---

### Post by qz9090 on 2014-10-23
I set the BIOS to the defaults and even cleared the CMOS on the motherboard but the results are still the same.
Maybe purchasing another NIC card maybe my only option.

Just thinking out loud, would it be futile to connect a USB wireless dongle to the PC, hoping to connect to the network?
I might give that a try too....

Thanks for all your help...!

---

### Post by chili555 on 2014-10-23
> would it be futile to connect a USB wireless dongle to the PC, hoping to connect to the network?Not at all. Check the many threads here about reliably working devices and choose carefully.

---

### Post by qz9090 on 2014-10-25
chili555,
I elected to go the internal NIC card route (didn't want a dongle hanging off of a USB port).

I got a generic NIC for about $15 at my local computer store, installed it, and I was up and running (got a network connection).

I have been using the machine for 3-4 hours with no problems.

Thanks for helping me out, I really appreciated it.

---

