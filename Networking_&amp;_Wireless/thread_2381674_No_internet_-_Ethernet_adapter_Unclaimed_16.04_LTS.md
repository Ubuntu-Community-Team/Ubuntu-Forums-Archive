---
title: "No internet - Ethernet adapter *Unclaimed* 16.04 LTS"
date: 2018-01-03
forum: Networking &amp; Wireless
---

### Post by unixdb on 2018-01-03
Hello everyone, it's first time I don't find a fix by searching the internet although I saw many similar issues. Hopefully some of you can help me out here since I'm relatively new to linux. 

Long story short, the laptop I used to run Ubuntu 16.04 LTS fell on the ground while plugged and the motherboard shorted out. Luckily I extracted the HDD and it's content from the case and re-used it. It's now plugged into my tower via SATA. I installed a fresh Ubuntu 16.04 LTS on it from a flash drive and formatted the hard drive to ext4 as recommended. 

Upon booting up, first thing I notice is the resolution way lower than what it should be, all pixelated and zoomed in. Second thing the loading screen is entirely black except for the orange/white dots that appear when loading. After a rather slow boot time considering my computer specs I get into the desktop environment to notice the resolution and slow speed problem persist. 

My biggest concern is that my ethernet cable is plugged in directly into the motherboard at the rear I/O panel and I can't access the internet. I tried a couple commands I saw from people with similar problems and it told me my adapter is "unclaimed". I'm pretty sure the graphical problems and other minor problems are related to drivers and updates, which I could easily find a fix for once I get an internet connection going. Feel free to give me any terminal command that cross your mind that could teach you more about my system so I can update my post with them. The more the better, it'll avoid me booting up a dozen times. I also tried turning off/on the network by right clicking the little wi-fi icon top right of the screen, didn't work this time.

My hardware : intel core i7 - 7700k
mobo : MSI z270 Gaming M3
gpu : MSI GTX 1080
ram : 2x8Gb DDR4
storage : refurbished 650Gb HDD

Thank you for your time.

msi@msi-MS-7A62:~$ **sudo lshw -C network**
  *-network UNCLAIMED     
       description: Ethernet controller
       product: Qualcomm Atheros
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list
       configuration: latency=0
       resources: memory:df100000-df13ffff ioport:d000(size=128)


msi@msi-MS-7A62:~$ **lspci**
00:00.0 Host bridge: Intel Corporation Device 591f (rev 05)
00:01.0 PCI bridge: Intel Corporation Sky Lake PCIe Controller (x16) (rev 05)
00:08.0 System peripheral: Intel Corporation Sky Lake Gaussian Mixture Model
00:14.0 USB controller: Intel Corporation Device a2af
00:14.2 Signal processing controller: Intel Corporation Device a2b1
00:16.0 Communication controller: Intel Corporation Device a2ba
00:17.0 SATA controller: Intel Corporation Device a282
00:1b.0 PCI bridge: Intel Corporation Device a2e7 (rev f0)
00:1b.2 PCI bridge: Intel Corporation Device a2e9 (rev f0)
00:1c.0 PCI bridge: Intel Corporation Device a290 (rev f0)
00:1c.7 PCI bridge: Intel Corporation Device a297 (rev f0)
00:1f.0 ISA bridge: Intel Corporation Device a2c5
00:1f.2 Memory controller: Intel Corporation Device a2a1
00:1f.3 Audio device: Intel Corporation Device a2f0
00:1f.4 SMBus: Intel Corporation Device a2a3
01:00.0 VGA compatible controller: NVIDIA Corporation Device 1b80 (rev a1)
01:00.1 Audio device: NVIDIA Corporation Device 10f0 (rev a1)
03:00.0 USB controller: ASMedia Technology Inc. Device 2142
05:00.0 Ethernet controller: Qualcomm Atheros Device e0b1 (rev 10)

msi@msi-MS-7A62:~$ **arch**
x86_64

msi@msi-MS-7A62:~$ **uname -r**
4.4.0-31-generic

msi@msi-MS-7A62:~$ **ifconfig**
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:964 errors:0 dropped:0 overruns:0 frame:0
          TX packets:964 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:71280 (71.2 KB)  TX bytes:71280 (71.2 KB)


msi@msi-MS-7A62:~$ **lspci -nnk | grep -iA3 net**
05:00.0 Ethernet controller [0200]: Qualcomm Atheros Device [1969:e0b1] (rev 10)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7a62]

---

### Post by TheFu on 2018-01-04
You need the driver for the ethernet card.  None is being loaded.  Search for that solution first.

Short answer:
[https://www.killernetworking.com/driver-downloads/kb/faq/5-killer-e2500-in-linux-ubuntu-debian](https://www.killernetworking.com/driver-downloads/kb/faq/5-killer-e2500-in-linux-ubuntu-debian)

Longer answer ... the way I found that ... 
[https://www.msi.com/Motherboard/support/Z270-GAMING-M3#down-driver](https://www.msi.com/Motherboard/support/Z270-GAMING-M3#down-driver) shows ZERO linux support. Not good.  Please complain to MSI.  It won't do any good, but we need to be vocal about this if we want it to get better.

Linux doesn't understand enough about the NIC to provide many hints. Usually there should be a specific model number in the lspci and lshw output. It isn't shown above, so .... I would just buy a $25 Intel PRO/1000 NIC (any in the family is fine that fit the slot) and install that.  Then all will be good and you won't have to fight with NIC issues for the next 10 yrs on this machine.  Poorly supported network cards often don't get good support. Sometimes they do.

OTOH, this board seems to be very new, so not many people/Linux developers are using it and haven't arranged for the driver to be part of the kernel deployment.  You need to figure out the exact network chips being used and then search for a driver to be compiled, and loaded.  In theory, this really shouldn't be too hard.     	Killer_network_ke2500_inf.zip  is the Windows NIC driver file.  Network Killer ke2500 is where I'd start looking.

---

### Post by chili555 on 2018-01-04
I might have to respectfully disagree with my very fine colleague TheFu.

It seems that you’ve done some homework already and have not quite found the answer. In the hope that this may be helpful to you and a few searchers, let me outline the process that I and the usual crew of driver dawgs here on the forum usually follow.

The key to everything is the pci.id or usb.id. Yours is here:

```
05:00.0 Ethernet controller [0200]: Qualcomm Atheros Device [[COLOR="#FF0000"]1969:e0b1[/COLOR]] (rev 10)
Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7a62]

```
Next, we Google for 1969:e0b1 and we find, among other things, this:[https://cateee.net/lkddb/web-lkddb/ALX.html](https://cateee.net/lkddb/web-lkddb/ALX.html) and, interestingly (!!), this: [https://ubuntuforums.org/showthread.php?t=2350778](https://ubuntuforums.org/showthread.php?t=2350778)

So we conclude that the driver is alx. Next, check to see if the driver exists on your system:
```
modinfo alx

```
Success? Awesome!

Wait! What?? The driver is there and the device is there but the device is still unclaimed and dormant? Why?

It is because the driver will only grab devices that are listed in its list of aliases. From my machine:
```
filename:       /lib/modules/4.13.0-21-generic/kernel/drivers/net/ethernet/atheros/alx/alx.ko
license:        GPL
description:    Qualcomm Atheros(R) AR816x/AR817x PCI-E Ethernet Network Driver
author:         Qualcomm Corporation, <nic-devel@qualcomm.com>
author:         Johannes Berg <johannes@sipsolutions.net>
srcversion:     15DC599B88652387E1F807D
alias:          pci:v00001969d000010A0sv*sd*bc*sc*i*
alias:          pci:v00001969d000010A1sv*sd*bc*sc*i*
alias:          pci:v00001969d00001090sv*sd*bc*sc*i*
alias:          pci:v0000[COLOR="#FF0000"]1969[/COLOR]d0000[COLOR="#FF0000"]E0B1[/COLOR]sv*sd*bc*sc*i*
alias:          pci:v00001969d0000E0A1sv*sd*bc*sc*i*
alias:          pci:v00001969d0000E091sv*sd*bc*sc*i*
alias:          pci:v00001969d00001091sv*sd*bc*sc*i*
depends:        mdio
intree:         Y
name:           alx
vermagic:       4.13.0-21-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
```

So the exact device, 1969:e0b1, must be listed in order for the driver to “claim” and run the device. Is the alias listed in your much earlier version of alx? Check:

   ```
 modinfo alx | grep E0B1
```

No? Nothing?

We conclude, then, that the earlier version of alx included in kernel version 4.4 doesn’t include your device. As you see above, the version in 4.13 does include it.

So, what can we do? First, you could certainly try the live USB or DVD session for a later Ubuntu version to be sure the ethernet works. If so, install it and you are done.

Second, you could, as TheFu suggests, just buy a $25 Intel PRO/1000 NIC and install it.

Third, we could try the technique in the solved post. From the terminal:

```
sudo modprobe alx
echo 1969 e0b1 | sudo tee /sys/bus/pci/drivers/alx/new_id
```

Does the ethernet spring to life? If so, we can add these commands to /etc/rc.local and be done.

---

### Post by TheFu on 2018-01-04
**chili555 is probably correct**  and is very kind. For all the help he provides here, I need to buy him a beer/drink.  Perhaps at SELF in 2018?

Always something new to learn.

When I saw the lshw output, it looked like a USB identifier, but I assumed (perhaps incorrectly) that it was an onboard network port.  That lead me to look for the MB specs, get the model as it says, then look for that driver.

I ran the modinfo on my 16.04.3 laptop running 4.10.x kernels.  The news looks good.
```
$ modinfo alx | grep E0B1
alias:          pci:v00001969d0000E0B1sv*sd*bc*sc*i*
```

Good luck.

---

### Post by unixdb on 2018-01-04
Thank you so much for your input chili555 and TheFu. After following chili's instructions I decided to re-downlad the image from ubuntu since the one I had on a backup was a bit old. I went into the partition editor from the live usb and selected the HDD I want to install to. Once everything was set up and installed I entered **modinfo alx | grep E0B1** in terminal and the alias is there :  **alias:          pci:v00001969d0000E0B1sv*sd*bc*sc*i*** 
I really appreciate your help and today I've learned something new.I thought I might aswell get the newer kernel while I'm at it and it solved my issue, I am now replying from my freshly installed ubuntu machine... ahhh freedom.

Cheers!

---

### Post by chili555 on 2018-01-04
Awesome! Glad it&#8217;s working.

---

### Post by fernando550 on 2018-06-27
Question... hopefully you'll pick this up after months of inactivity... I am dealing with the following problem:


(UBUNTU 18.04)

1. installed ubuntu on my 1st disk
3. installed ubuntu on my 2nd disk
4. 2nd disk wouldnt boot up ubuntu, only 1st disk
5. formatted 1st disk to use as network storage, reinstalled ubuntu on 2nd disk
4. ethernet connection worked on 1st disk running ubuntu, but now it doesnt work with ubuntu on 2nd disk (ubuntu worked)
5. reinstall ubuntu on 2nd disk again
6. no ethernet option in 'settings' panel. It only says to set up VPN or a proxy. I also do not have the internet icon on the top bar...
7. I cannot run any apt get, apt install, ifconfig doesn't exist, ip route show doesnt return anything (acts as if I had just hit return line), no internet... no freedom... slowly dying here to solve my issue... please assist.

---

### Post by chili555 on 2018-06-28
> **fernando550 said:**
> Question... hopefully you'll pick this up after months of inactivity... I am dealing with the following problem:


(UBUNTU 18.04)

1. installed ubuntu on my 1st disk
3. installed ubuntu on my 2nd disk
4. 2nd disk wouldnt boot up ubuntu, only 1st disk
5. formatted 1st disk to use as network storage, reinstalled ubuntu on 2nd disk
4. ethernet connection worked on 1st disk running ubuntu, but now it doesnt work with ubuntu on 2nd disk (ubuntu worked)
5. reinstall ubuntu on 2nd disk again
6. no ethernet option in 'settings' panel. It only says to set up VPN or a proxy. I also do not have the internet icon on the top bar...
7. I cannot run any apt get, apt install, ifconfig doesn't exist, ip route show doesnt return anything (acts as if I had just hit return line), no internet... no freedom... slowly dying here to solve my issue... please assist.We suggest that you start your own new question. We haven't any idea which, if any at all, of the details above in unixdb's readings apply to you.

---

