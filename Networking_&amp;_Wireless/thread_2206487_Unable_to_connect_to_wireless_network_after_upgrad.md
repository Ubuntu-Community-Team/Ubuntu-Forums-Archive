---
title: "Unable to connect to wireless network after upgrading kernel (3.5.0-46) 12.04 64bits"
date: 2014-02-19
forum: Networking &amp; Wireless
---

### Post by Murasaki_san on 2014-02-19
Hello! I've been using Ubuntu for a while, but I don't know much about IT, so please bear with me.

I have a Dell Inspiron 3521 with Ubuntu 12.04. Today I installed the recommended update which included the version 3.5.0-46 of the kernel. After rebooting, the wireless connection was lost.
Went to Terminal, typed**rfkill list all** and it did't return any "wireless network" (the bluetooth does appear though). Then I tried **lshw -C network **and this is what came up:

  ```
*-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 05
       serial: 74:86:7a:56:c5:26
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:41 ioport:2000(size=256) memory:c0404000-c0404fff memory:c0400000-c0403fff
  [COLOR=#ff0000]*-network UNCLAIMED
       description: Network controller
       product: QCA9565 / AR9565 Wireless Network Adapter
       vendor: Qualcomm Atheros[/COLOR]
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:c0500000-c057ffff memory:afb00000-afb0ffff
```



I noticed the "UNCLAIMED" on the second part of the result, so my guess is that there is an issue with drivers and that's why is not working. (I had to install some kind of special patch for the kernel when I first installed this version of Ubuntu on my laptop a couple of months ago because it had the same problem).

If I log in using the previous version of the kernel everything is fine, so now I have 2 questions:

- Should I just keep using the old version of the kernel and forget about it?
- Is it better to fix it right away, and if so, where can I find the solution? (I've been looking for answers but I couldn't find what I needed)

Thanks in advance for your help! :)

---

### Post by chili555 on 2014-02-19
> I had to install some kind of special patch for the kernel when I first installed this version of Ubuntu on my laptop a couple of months ago because it had the same problemThat's exactly what we need to do. Before we get started, please run and post:```
lspci -nn | grep 0280
```Once we have the exact details of your device, we'll propose a solution.

---

### Post by Murasaki_san on 2014-02-20
Hi chili555, here are the details:

```
 lspci -nn | grep 0280
02:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)


```

---

### Post by chili555 on 2014-02-20
I suggest you obtain a temporary wired ethernet connection and open a terminal:```
sudo apt-get install linux-backports-modules-cw-3.8-precise-generic 
sudo modprobe ath9k
```Your wireless should be working.

---

### Post by Murasaki_san on 2014-02-21
I did it but still not working. Here's what came up when I tried to install the packages:

```
 sudo apt-get install linux-backports-modules-cw-3.8-precise-generic

Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-backports-modules-cw-3.8-precise-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  gir1.2-ubuntuoneui-3.0 linux-image-3.2.0-58-generic linux-headers-3.2.0-58
  guile-1.8-libs linux-headers-3.2.0-58-generic
  linux-backports-modules-cw-3.8-3.2.0-58-generic
  linux-headers-3.5.0-23-generic linux-headers-3.5.0-23 libubuntuoneui-3.0-1
  thunderbird-globalmenu gnome-games-data
Use 'apt-get autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 3 not to upgrade.


```

Apparently they are already installed, I wonder why it doesn't recognize the chip then... (I didn't forget to run sudo modprobe ath9k)

---

### Post by chili555 on 2014-02-21
I believe it does claim your device; check:```
modinfo ath9k | grep 0036
```You should see this:> alias:          pci:v0000168Cd0000[COLOR="#FF0000"]0036[/COLOR]sv*sd*bc*sc*i*This corresponds to your device:> Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [[COLOR="#FF0000"]168c:0036[/COLOR]] Let's see if there is any clue in the log:```
sudo modprobe ath9k
dmesg | grep ath
rfkill list all
```We are close!!

---

### Post by Murasaki_san on 2014-02-21
modinfo ath9k | grep 0036 didn't return any result. Then I entered the next command and this is what came up:

```

 dmesg | grep ath
[   13.883274] usbcore: registered new interface driver ath3k


```

(I searched "ath3k" and if I'm not mistaken it refers to the Bluetooth?) 

 
rfkill list all ==> still only the Bluetooth appears listed

:P

---

### Post by chili555 on 2014-02-21
Let's see:```
modinfo ath9k | head -n5
```If it doesn't report that the filename includes 'updates' and 'cw' then reinstall the backports package:```
sudo apt-get install --reinstall linux-backports-modules-cw-3.8-precise-generic
```Unload and reload:```
sudo modprobe -r ath9k && sudo modprobe ath9k
```And check again:```
modinfo ath9k | head -n5
```Now are we on updates and cw? If so, your wireless should be working.> I searched "ath3k" and if I'm not mistaken it refers to the BluetoothCorrect.```
$ modinfo ath3k | head -n6
filename:         /lib/modules/3.11.0-17-generic/kernel/drivers/[COLOR="#FF0000"]bluetooth[/COLOR]/ath3k.ko
firmware:        ath3k-1.fw
license:           GPL
version:          1.0
description:    Atheros AR30xx firmware driver
author:           Atheros Communications
```

---

### Post by Murasaki_san on 2014-02-22
> If it doesn't report that the filename includes 'updates' and 'cw' then reinstall the backports package

It didn't, so I followed the instructios (reinstall, unload and reload), then checked, and this was the outcome:

```
 modinfo ath9k|head -n5

filename:       /lib/modules/3.5.0-46-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     2739A66454A502EC7DA66D6


```

Wireless still not working (feels like the package is playing hide and seek with me hehe :P)

---

### Post by chili555 on 2014-02-22
KKKKrazy!! Please see if the matching package is installed:```
sudo dpkg -s linux-backports-modules-cw-3.8-`uname -r`
```Those backticks are on the left side of my US keyboard on the same key with ~. If it is not installed, try installing it:```
sudo apt-get install linux-backports-modules-cw-3.8-`uname -r`
```Reboot and check again:```
modinfo ath9k | head -n5
```If you have Synaptic installed, you might see what linux-backports-modules-cw are available. We need one at or above 3.8, I believe.

Don't make me come over there with my hammer and saw and "fix" your computer!!

---

### Post by Murasaki_san on 2014-02-22
Good news Chili, you don't need to pack hammer and saw. :) I had to do some more research to find the solution, though...Here's what happened (in case is useful for someone else):

 - Acording to sudo dpkg -s, the package was not installed. Tried to do it:
```
 sudo apt-get install linux-backports-modules-cw-3.8-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR=#ff0000]E: Unable to locate package linux-backports-modules-cw-3.8-3.5.0-46-generic
E: Couldn't find any package by regex 'linux-backports-modules-cw-3.8-3.5.0-46-generic[/COLOR]'


```

Hm! I checked Synaptic, and the packages were there, appearing as installed and up to date. Weird! Well, I looked for the latest version of the backports available on Synaptic (3.12) and installed them. Rebooted...still no wireless.

- So I went searching for every piece of info about backports and found this thread:
[http://ubuntuforums.org/archive/index.php/t-2190930.html](http://ubuntuforums.org/archive/index.php/t-2190930.html)

The steps were:
```

sudo apt-get install --reinstall linux-headers-generic build-essential
```

Downloaded the driver package from [http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/](http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/) , extracted it to Desktop and then went back to the Terminal:

```

cd Desktop/backports-3.13.2-1
make defconfig-ath9k
make
sudo make install
```

Rebooted and finally! Wireless was back working fine. It feels as if I had to put backports and ath9k face to face and tell them "OK guys, YOU work together, get it?" (Sorry if my interpretation is not scientific at all :P) 

Anyway, thank you so much for your guidance and help! I've learned a few things :biggrin:

(I'll mark this thread as "solved")

---

### Post by agualdino on 2014-04-06
Hi, 

I have a similar problem with my Centrino Wireless-N 2230 on quantal after an updated (Network unclaimed problem).

when installing the backports-modules i get the following error:

```
/etc/init.d/udev: 117: /etc/init.d/udev: /usr/lib/hal/hal-system-smbios: not found
invoke-rc.d: initscript udev, action "restart" failed.
dpkg: error processing udev (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing: udev
```

do you have any clue what is the problem and how to fix it?
Thanks


> **chili555 said:**
> I suggest you obtain a temporary wired ethernet connection and open a terminal:```
sudo apt-get install linux-backports-modules-cw-3.8-precise-generic 
sudo modprobe ath9k
```Your wireless should be working.

---

### Post by chili555 on 2014-04-06
Do you have the Precise version?```
lsb_release -d
uname -r
```I suggest you try a reboot.

---

### Post by agualdino on 2014-04-06
Ubuntu 12.10
3.5.0-48-generic



> **chili555 said:**
> Do you have the Precise version?```
lsb_release -d
uname -r
```I suggest you try a reboot.

---

### Post by chili555 on 2014-04-06
> **agualdino said:**
> Ubuntu 12.10
3.5.0-48-genericUbuntu 12.10 is Quantal, not Precise. I suggest you follow the process described above:> The steps were:
Code:

sudo apt-get install --reinstall linux-headers-generic build-essential

Downloaded the driver package from [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.13.2/backports-3.13.2-1.tar.xz](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.13.2/backports-3.13.2-1.tar.xz) (Edited from original post by chili555) , extracted it to Desktop and then went back to the Terminal:


```
cd Desktop/backports-3.13.2-1
make defconfig-ath9k
make
sudo make install
```

Rebooted and finally! Wireless was back working fine. It feels as if I had to put backports and ath9k face to face and tell them "OK guys, YOU work together, get it?" (Sorry if my interpretation is not scientific at all )


---

