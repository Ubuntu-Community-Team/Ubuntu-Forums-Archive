---
title: "broken wifi on Dell Precision 3520 running 16.04"
date: 2019-03-20
forum: Networking &amp; Wireless
---

### Post by mchatzikos on 2019-03-20
Hello,

A routine package upgrade I did this morning broke my WiFi. It appeared that the package **compat-iwlwifi-core19-intel8265** failed to install properly.  The WiFi stopped working after the update.  Trying to fix it following various threads I found online probably made things worse.

I found these threads, but they haven't helped much:
    [https://ubuntuforums.org/showthread.php?t=1314693](https://ubuntuforums.org/showthread.php?t=1314693)
[https://ubuntuforums.org/showthread.php?t=2370912](https://ubuntuforums.org/showthread.php?t=2370912)

Here's where things stand at the moment:

Network Manager no longer gives the "Enable Wireless Networking" option.

The device is there, but there's no driver for it.
```

$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: Wireless 8265 / 8275
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 78
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:ef200000-ef201fff
  *-network
       description: Ethernet interface
       product: Ethernet Connection (5) I219-LM
       vendor: Intel Corporation
       physical id: 1f.6
       bus info: pci@0000:00:1f.6
       logical name: enp0s31f6
       version: 31
       serial: d4:81:d7:be:51:2d
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=full firmware=0.1-4 ip=192.168.1.147 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:129 memory:ef300000-ef31ffff

```

The firmware is there:
```

$ ls /lib/firmware/ | grep 8265
iwlwifi-8265-21.ucode
iwlwifi-8265-21.ucode.wifi-intel8265
iwlwifi-8265-22.ucode
iwlwifi-8265-27.ucode
iwlwifi-8265-31.ucode
iwlwifi-8265-34.ucode
iwlwifi-8265-36.ucode

```

I have even downloaded the firmware from
    [https://git.kernel.org/cgit/linux/kernel/git/iwlwifi/linux-firmware.git/plain/iwlwifi-8265-31.ucode](https://git.kernel.org/cgit/linux/kernel/git/iwlwifi/linux-firmware.git/plain/iwlwifi-8265-31.ucode)
and used it instead of the original firmware, but that didn't help either.  I also downloaded v22 of the firmware from
[https://wireless.wiki.kernel.org/en/users/Drivers/iwlwifi?language=en_US](https://wireless.wiki.kernel.org/en/users/Drivers/iwlwifi?language=en_US)
but that didn't help.

I have tried to load the kernel module with ```
sudo modprobe iwlwifi
``` but to no avail.  The kernel provides firmware loader support
```

$ grep CONFIG_FW_LOADER=y /boot/config-4.4.0-143-generic 
CONFIG_FW_LOADER=y

```
so these should have worked.  I tried loading the **wl** module instead of **iwlwifi**, but no luck.

I'm not sure what to do next.  I've probably screwed something up.  Please advise.

Thanks!

---

### Post by mchatzikos on 2019-03-20
On further research, the  **compat-iwlwifi-core19-intel8265** was never installed.  Here's the log from today:
```

Start-Date: 2019-03-20  07:05:12
Commandline: /usr/bin/unattended-upgrade
Upgrade: chromium-browser:amd64 (72.0.3626.121-0ubuntu0.16.04.1, 73.0.3683.75-0ubuntu0.16.04.1), chromium-codecs-ffmpeg-extra:amd64 (72.0.3626.121-0ubuntu0.16.04.1, 73.0.3683.75-0ubuntu0.16.04.1), chromium-browser-l10n:amd64 (72.0.3626.121-0ubuntu0.16.04.1, 73.0.3683.75-0ubuntu0.16.04.1)
End-Date: 2019-03-20  07:05:25


Start-Date: 2019-03-20  07:09:14
Commandline: aptdaemon role='role-commit-packages' sender=':1.249'
Install: linux-modules-4.4.0-143-generic:amd64 (4.4.0-143.169, automatic), linux-headers-4.4.0-143:amd64 (4.4.0-143.169, automatic), linux-image-4.4.0-143-generic:amd64 (4.4.0-143.169, automatic), linux-headers-4.4.0-143-generic:amd64 (4.4.0-143.169, automatic), linux-modules-extra-4.4.0-143-generic:amd64 (4.4.0-143.169, automatic)
Upgrade: linux-headers-generic:amd64 (4.4.0.142.148, 4.4.0.143.151), libsystemd0:amd64 (229-4ubuntu21.16, 229-4ubuntu21.17), adobe-flash-properties-gtk:amd64 (1:20190212.1-0ubuntu0.16.04.1, 1:20190312.1-0ubuntu0.16.04.1), linux-image-generic:amd64 (4.4.0.142.148, 4.4.0.143.151), libcuda1-384:amd64 (384.130-0ubuntu0.16.04.1, 384.130-0ubuntu0.16.04.2), snapd:amd64 (2.34.2ubuntu0.1, 2.37.4), google-chrome-stable:amd64 (72.0.3626.121-1, 73.0.3683.75-1), udev:amd64 (229-4ubuntu21.16, 229-4ubuntu21.17), libudev1:amd64 (229-4ubuntu21.16, 229-4ubuntu21.17), adobe-flashplugin:amd64 (1:20190212.1-0ubuntu0.16.04.1, 1:20190312.1-0ubuntu0.16.04.1), systemd-sysv:amd64 (229-4ubuntu21.16, 229-4ubuntu21.17), ubuntu-core-launcher:amd64 (2.34.2ubuntu0.1, 2.37.4), libpam-systemd:amd64 (229-4ubuntu21.16, 229-4ubuntu21.17), distro-info-data:amd64 (0.28ubuntu0.9, 0.28ubuntu0.10), systemd:amd64 (229-4ubuntu21.16, 229-4ubuntu21.17), nvidia-libopencl1-384:amd64 (384.130-0ubuntu0.16.04.1, 384.130-0ubuntu0.16.04.2), linux-generic:amd64 (4.4.0.142.148, 4.4.0.143.151), nvidia-opencl-icd-384:amd64 (384.130-0ubuntu0.16.04.1, 384.130-0ubuntu0.16.04.2), nvidia-384:amd64 (384.130-0ubuntu0.16.04.1, 384.130-0ubuntu0.16.04.2)
End-Date: 2019-03-20  07:14:37


Start-Date: 2019-03-20  07:49:23
Commandline: apt autoremove
Requested-By: marios (1001)
Remove: linux-headers-4.4.0-141:amd64 (4.4.0-141.167), linux-image-4.4.0-141-generic:amd64 (4.4.0-141.167), linux-signed-image-4.4.0-141-generic:amd64 (4.4.0-141.167), linux-tools-4.4.0-141:amd64 (4.4.0-141.167), linux-image-extra-4.4.0-141-generic:amd64 (4.4.0-141.167), linux-tools-4.4.0-141-generic:amd64 (4.4.0-141.167), linux-headers-4.4.0-141-generic:amd64 (4.4.0-141.167)
End-Date: 2019-03-20  07:50:31


Start-Date: 2019-03-20  08:13:08
Commandline: apt-get install synaptic
Requested-By: marios (1001)
Install: rarian-compat:amd64 (0.8.1-6, automatic), librarian0:amd64 (0.8.1-6, automatic), libept1.5.0:amd64 (1.1+nmu3, automatic), synaptic:amd64 (0.83)
End-Date: 2019-03-20  08:13:20

```

The upgrade was to linux 4.4.0.  So, the WiFi problems seem to be an innocent bystander to the kernel upgrade.  If there are any suggestions for getting functional WiFi service, please let me know.

---

### Post by jeremy31 on 2019-03-20
See the wireless script link in my signature and post results

---

### Post by mchatzikos on 2019-03-20
Here they are:
[http://paste.ubuntu.com/p/mHPM4K3Z2p/](http://paste.ubuntu.com/p/mHPM4K3Z2p/)

---

### Post by jeremy31 on 2019-03-20
Try ```
sudo apt remove bcmwl-kernel-source
```
Reboot, go into BIOS, turn off Secure Boot, just disable it, leave any Secure Boot keys alone
See if it works

---

### Post by mchatzikos on 2019-03-20
Thanks for the suggestion.  I tried it, but it didn't work.  I reenabled Secure Boot.

---

### Post by jeremy31 on 2019-03-20
If you want to keep Secure Boot enabled you might want to install kernel 4.15
See how to enable the HWE kernel at [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

