---
title: "Wireless connection with &quot;WPA2-PSK [AES]&quot; security cannot be established anymore"
date: 2014-01-05
forum: Networking &amp; Wireless
---

### Post by ali98ir on 2014-01-05
After upgrading to 12.04 from 11.1, wireless connection with "WPA2-PSK [AES]" security cannot be stablished anymore. 
My power line network only supports 
"WPA2-PSK [AES]"
OR
"WPA-PSK [TKIP] + WPA2-PSK [AES]"

Ubuntu 11.1 was working perfectly fine with that but now it cannot make a connection. I am however able to connect to another wireless network with "WPA-PSK(TKIP)" security.

Is there any solution for this problem? I appreciate your comments.


ali@Jimbo:~$ lspci -nnv | grep '\[02.0\]'
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
04:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354]

ali@Jimbo:~$ lshw -C network -sanitize
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network               
       description: Wireless interface
       product: BCM4313 802.11bgn Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: [REMOVED]
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) ip=[REMOVED] latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:16 memory:d0300000-d0303fff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 00
       serial: [REMOVED]
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 firmware=N/A latency=0 multicast=yes port=twisted pair
       resources: irq:44 memory:d0400000-d0403fff ioport:b000(size=256)
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

---

### Post by varunendra on 2014-01-06
What is your kernel version? Check with -
```
uname -mr
```

If it is 3.8 or above, try using the native "brcmsmac" driver instead of the sta driver that you have currently installed. It would also work on lower kernels, but probably not as good as the versions included in kernel 3.8 or higher.

To purge the current sta driver (so that the native one can load on next boot) -
```
sudo apt-get purge bcmwl-kernel-source
```
Then reboot and check -
```
lsmod | grep brcm
```
Do you see brcmsmac in the output? If yes, can you connect now?

If not, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by ali98ir on 2014-01-06
Hello Varun,

I am using 3.2.0-58-generic x86_64
Do you still recomment to change the driver?

Thanks,
Ali

---

### Post by ali98ir on 2014-01-06
Thank you very much indeed.
Changing the driver to the native one worked just fine.

ali@Jimbo:~$ lsmod | grep brcm
brcmsmac              570930  0 
mac80211              506862  1 brcmsmac
brcmutil               15139  1 brcmsmac
cfg80211              205774  2 brcmsmac,mac80211
crc8                   12893  1 brcmsmac
cordic                 12574  1 brcmsmac

Best Regards,
Ali

---

### Post by varunendra on 2014-01-06
Glad it worked. If you upgrade the OS or just the kernel later, make sure to NOT install the sta driver again, it often causes troubles with this card and usually the native (current) one works much better than the sta.

Note that in a fresh installation, choosing to "Install Updates" during installation also installs the sta driver if the system is connected to internet while installing. So you should disable "Install Updates" and "Third Party software" options during a fresh install. You can do them selectively later once the system is installed.

Enjoy Ubuntu ! :)

---

### Post by ali98ir on 2014-01-07
Unfortunately it worked only the first time. After going to sleep mode and back, it couldn't make the connection. Restarting the machine didn't help. I had no change in any of network settings.


ali@Jimbo:~$ uname -mr
3.2.0-58-generic x86_64
ali@Jimbo:~$ lshw -C network -sanitize
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4313 802.11bgn Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: [REMOVED]
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.2.0-58-generic firmware=N/A ip=[REMOVED] latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:d0300000-d0303fff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 00
       serial: [REMOVED]
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 firmware=N/A latency=0 multicast=yes port=twisted pair
       resources: irq:44 memory:d0400000-d0403fff ioport:b000(size=256)
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
ali@Jimbo:~$ lsmod | grep brcm
brcmsmac              570930  0 
mac80211              506862  1 brcmsmac
brcmutil               15139  1 brcmsmac
cfg80211              205774  2 brcmsmac,mac80211
crc8                   12893  1 brcmsmac
cordic                 12574  1 brcmsmac

---

### Post by varunendra on 2014-01-07
Please use 'Code' tags for the outputs as mentioned in my first post (the bottom line).

Let us see what options you have available regarding the driver and kernel. Please do an update -
```
sudo apt-get update
```
..then post the outputs of -
```
apt-cache show bcmwl* | grep Version
apt-cache show linux-image-3.* | grep Package | sort -V
apt-cache show linux-generic-lts* | grep Package
```

---

### Post by ali98ir on 2014-01-07
Please find following the requested information.

```

ali@Jimbo:~$ apt-cache show bcmwl* | grep Version
Version: 6.20.155.1+bdcom-0ubuntu0.0.2
Version: 5.100.82.38+bdcom-0ubuntu6

```

```

ali@Jimbo:~$ apt-cache show linux-image-3.* | grep Package | sort -V
Package: linux-image-3.0.0-12-generic
Package: linux-image-3.0.0-13-generic
Package: linux-image-3.0.0-14-generic
Package: linux-image-3.0.0-15-generic
Package: linux-image-3.0.0-16-generic
Package: linux-image-3.0.0-17-generic
Package: linux-image-3.0.0-19-generic
Package: linux-image-3.0.0-20-generic
Package: linux-image-3.0.0-21-generic
Package: linux-image-3.0.0-22-generic
Package: linux-image-3.0.0-23-generic
Package: linux-image-3.0.0-24-generic
Package: linux-image-3.0.0-25-generic
Package: linux-image-3.0.0-26-generic
Package: linux-image-3.0.0-28-generic
Package: linux-image-3.0.0-29-generic
Package: linux-image-3.0.0-30-generic
Package: linux-image-3.0.0-31-generic
Package: linux-image-3.0.0-32-generic
Package: linux-image-3.2.0-23-generic
Package: linux-image-3.2.0-23-lowlatency
Package: linux-image-3.2.0-23-virtual
Package: linux-image-3.2.0-24-generic
Package: linux-image-3.2.0-24-generic
Package: linux-image-3.2.0-24-virtual
Package: linux-image-3.2.0-24-virtual
Package: linux-image-3.2.0-25-generic
Package: linux-image-3.2.0-25-virtual
Package: linux-image-3.2.0-26-generic
Package: linux-image-3.2.0-26-virtual
Package: linux-image-3.2.0-27-generic
Package: linux-image-3.2.0-27-virtual
Package: linux-image-3.2.0-29-generic
Package: linux-image-3.2.0-29-virtual
Package: linux-image-3.2.0-30-generic
Package: linux-image-3.2.0-30-virtual
Package: linux-image-3.2.0-31-generic
Package: linux-image-3.2.0-31-virtual
Package: linux-image-3.2.0-32-generic
Package: linux-image-3.2.0-32-virtual
Package: linux-image-3.2.0-33-generic
Package: linux-image-3.2.0-33-lowlatency
Package: linux-image-3.2.0-33-virtual
Package: linux-image-3.2.0-34-generic
Package: linux-image-3.2.0-34-virtual
Package: linux-image-3.2.0-35-generic
Package: linux-image-3.2.0-35-lowlatency
Package: linux-image-3.2.0-35-virtual
Package: linux-image-3.2.0-36-generic
Package: linux-image-3.2.0-36-lowlatency
Package: linux-image-3.2.0-36-virtual
Package: linux-image-3.2.0-37-generic
Package: linux-image-3.2.0-37-lowlatency
Package: linux-image-3.2.0-37-virtual
Package: linux-image-3.2.0-38-generic
Package: linux-image-3.2.0-38-lowlatency
Package: linux-image-3.2.0-38-virtual
Package: linux-image-3.2.0-39-generic
Package: linux-image-3.2.0-39-lowlatency
Package: linux-image-3.2.0-39-virtual
Package: linux-image-3.2.0-40-generic
Package: linux-image-3.2.0-40-lowlatency
Package: linux-image-3.2.0-40-virtual
Package: linux-image-3.2.0-41-generic
Package: linux-image-3.2.0-41-lowlatency
Package: linux-image-3.2.0-41-virtual
Package: linux-image-3.2.0-43-generic
Package: linux-image-3.2.0-43-virtual
Package: linux-image-3.2.0-44-generic
Package: linux-image-3.2.0-44-lowlatency
Package: linux-image-3.2.0-44-virtual
Package: linux-image-3.2.0-45-generic
Package: linux-image-3.2.0-45-virtual
Package: linux-image-3.2.0-48-generic
Package: linux-image-3.2.0-48-lowlatency
Package: linux-image-3.2.0-48-virtual
Package: linux-image-3.2.0-49-generic
Package: linux-image-3.2.0-49-lowlatency
Package: linux-image-3.2.0-49-virtual
Package: linux-image-3.2.0-51-generic
Package: linux-image-3.2.0-51-lowlatency
Package: linux-image-3.2.0-51-virtual
Package: linux-image-3.2.0-52-generic
Package: linux-image-3.2.0-52-lowlatency
Package: linux-image-3.2.0-52-virtual
Package: linux-image-3.2.0-53-generic
Package: linux-image-3.2.0-53-lowlatency
Package: linux-image-3.2.0-53-virtual
Package: linux-image-3.2.0-54-generic
Package: linux-image-3.2.0-54-lowlatency
Package: linux-image-3.2.0-54-virtual
Package: linux-image-3.2.0-55-generic
Package: linux-image-3.2.0-55-lowlatency
Package: linux-image-3.2.0-55-virtual
Package: linux-image-3.2.0-56-generic
Package: linux-image-3.2.0-56-lowlatency
Package: linux-image-3.2.0-56-virtual
Package: linux-image-3.2.0-57-generic
Package: linux-image-3.2.0-57-lowlatency
Package: linux-image-3.2.0-57-virtual
Package: linux-image-3.2.0-58-generic
Package: linux-image-3.2.0-58-lowlatency
Package: linux-image-3.2.0-58-virtual
Package: linux-image-3.5.0-18-generic
Package: linux-image-3.5.0-19-generic
Package: linux-image-3.5.0-21-generic
Package: linux-image-3.5.0-22-generic
Package: linux-image-3.5.0-23-generic
Package: linux-image-3.5.0-24-generic
Package: linux-image-3.5.0-25-generic
Package: linux-image-3.5.0-26-generic
Package: linux-image-3.5.0-27-generic
Package: linux-image-3.5.0-28-generic
Package: linux-image-3.5.0-30-generic
Package: linux-image-3.5.0-31-generic
Package: linux-image-3.5.0-32-generic
Package: linux-image-3.5.0-34-generic
Package: linux-image-3.5.0-36-generic
Package: linux-image-3.5.0-37-generic
Package: linux-image-3.5.0-39-generic
Package: linux-image-3.5.0-40-generic
Package: linux-image-3.5.0-41-generic
Package: linux-image-3.5.0-42-generic
Package: linux-image-3.5.0-43-generic
Package: linux-image-3.5.0-44-generic
Package: linux-image-3.5.0-45-generic
Package: linux-image-3.8.0-19-generic
Package: linux-image-3.8.0-21-generic
Package: linux-image-3.8.0-22-generic
Package: linux-image-3.8.0-23-generic
Package: linux-image-3.8.0-25-generic
Package: linux-image-3.8.0-26-generic
Package: linux-image-3.8.0-27-generic
Package: linux-image-3.8.0-29-generic
Package: linux-image-3.8.0-30-generic
Package: linux-image-3.8.0-31-generic
Package: linux-image-3.8.0-32-generic
Package: linux-image-3.8.0-33-generic
Package: linux-image-3.8.0-34-generic
Package: linux-image-3.8.0-35-generic
Package: linux-image-3.11.0-13-generic
Package: linux-image-3.11.0-14-generic
Package: linux-image-3.11.0-15-generic

```

```

ali@Jimbo:~$ apt-cache show linux-generic-lts* | grep Package
Package: linux-generic-lts-quantal
Package: linux-generic-lts-quantal-eol-upgrade
Package: linux-generic-lts-raring
Package: linux-generic-lts-raring-eol-upgrade
Package: linux-generic-lts-saucy
Package: linux-generic-lts-saucy-eol-upgrade

```

---

### Post by varunendra on 2014-01-07
Okay, just one more report please, before we proceed to either compiling a backported driver, or installing a whole new kernel. Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

This report is to make sure there is no configuration issue that will persist even with the new driver.

---

### Post by praseodym on 2014-01-07
Here I recommend installing the backport modules 3.6 and linux-firmware-nonfree

---

### Post by ali98ir on 2014-01-07
The result of running your script is attached.

I don't know how to make backport modules.

Regards,

---

### Post by ali98ir on 2014-01-08
Another try, looks working again. It is stable enough after a few power down and up. Not sure what caused that failure.  
I appreciate your efforts. Please consider it as solved.

Thanks again,
Ali

---

### Post by varunendra on 2014-01-08
As per the report you attached, the access-point to which you seem connected was using WPA-TKIP encryption, not WPA2-AES. It may fail to connect again if the router/ap is using TKIP and has N-channel enabled. Even if the AP is b/g mode only (no n-channel support), the TKIP is an inefficient encryption algorithm and may cause speed/performance issues.

It is highly recommended to use pure WPA2-AES, not WPA or WPA/WPA2 mixed mode, or TKIP with any combination. Also, you may wish to try setting the channel in the router to 1 or 11, which usually work best with Linux drivers.

Apart from this, there seems to be a blacklist file (/etc/modprobe.d/blacklist-local.conf) in your system which is unnecessary now that you don't have the "wl" driver installed. It also indicates that you must have tried some other manual tweaks that you didn't mention in this thread. Not a problem though as long as there are no more remnants possibly causing trouble later.

Lastly, your udev rules file for network connections could use some cleaning up. I recommend deleting the current one. It will be automatically regenerated on next boot -
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```
Reboot and check it again (cat /etc/udev/rules.d/70-persistent-net.rules). It should contain only two interface entries now, not the one regarding the "wl" driver.

Deletion of the above mentioned blacklist file or the udev rules file won't harm in any way. On the contrary, the fresh udev rules file will avoid confusion to the system. And I'm sure the recommended changes in the router, if you choose to do them, will be helpful too. But if not, they can be reverted anytime if required. As such, I'd recommend to apply all the changes suggested above if you experience any lag, slowness, or disconnection problem again.

---

