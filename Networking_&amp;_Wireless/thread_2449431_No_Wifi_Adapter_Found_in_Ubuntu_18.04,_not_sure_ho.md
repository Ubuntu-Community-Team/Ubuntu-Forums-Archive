---
title: "No Wifi Adapter Found in Ubuntu 18.04, not sure how to install driver?"
date: 2020-08-26
forum: Networking &amp; Wireless
---

### Post by mysteriousmonkey29 on 2020-08-26
Hello, I am running ubuntu 18.04, kernel 5.4.0-42-generic. Last week, the internet randomly stopped working. Turns out the network manager somehow disappeared, so I downloaded the debians on another computer, transferred via USB, and then installed. Now my ethernet works, but my wifi is still not working. When I go to settings and click on wifi, it lists "no wifi adapter found". I figure this must be a software issue, because the wifi was working two weeks ago. I have tried updating the computer, both from command line and software center, but this has not solved the problem.

```
sudo lshw -C network
``` produces:
```
*-network UNCLAIMED       
       description: Network controller
       product: Wireless 8265 / 8275
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:6c:00.0
       version: 78
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:dc500000-dc501fff
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: enx106530d24185
       serial: 10:65:30:d2:41:85
       size: 1Gbit/s
       capacity: 1Gbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8152 driverversion=v1.10.11 duplex=full ip=192.168.1.113 link=yes multicast=yes port=MII speed=1Gbit/s
```

Based on that output, I found this driver here: [https://linux-hardware.org/index.php?id=pci:8086-24fd-8086-9010](https://linux-hardware.org/index.php?id=pci:8086-24fd-8086-9010) that I think is the right one for my wifi adapter. Unfortunately, I'm not sure how to install it. I downloaded the file, and went into software and updates-->additional drivers. Here, I can see listed:

```
Intel Corporation: Wireless 8265/8275
This device is not working.
(option 1) Using iwlwifi driver backport in DKMS format from backport-iwlwifi-dkms (open source)
(option 2) Continue using a manually installed driver
(option 3) Do not use the device
```

Option 3 is selected, and the other two are greyed out. The "revert" and "apply changes" buttons at the bottom are also greyed out.

Any suggestions? Help would be greatly appreciated!

---

### Post by chili555 on 2020-08-26
The correct driver, iwlwifi, has been in Ubuntu versions for some time, including your kernel version 5.4. There is no need to install another. 

What we really need to do is see why the in-built driver isn't working. First, we'll try to load the driver and see if it throws any interesting errors or warnings:

```
sudo modprobe iwlwifi
```

Next, we'll check the message log for more clues:

```
dmesg | grep iwl
```

Please post the result and we'll continue.

---

### Post by mysteriousmonkey29 on 2020-08-26
Ok, thanks for the info.

```
sudo modprobe iwlwifi
```
produces:
```
modprobe: ERROR: could not insert 'iwlwifi': Operation not permitted
```

Any idea what that means? I tried running in su prompt as well, with the same result.

---

### Post by chili555 on 2020-08-26
> modprobe: ERROR: could not insert 'iwlwifi': Operation not permittedVery weird!

Does the module exist in your running kernel?

```
uname -r
modinfo iwlwifi | grep filename
```

If this results in an error, then:

```
sudo updatedb
locate iwlwifi
```

Can you interrupt the boot process at the GRUB menu and boot into an earlier kernel version? Does the wireless work there?

---

### Post by mysteriousmonkey29 on 2020-08-27
I agree it's very strange, haha. Especially how all the internet  disappeared spontaneously (wasn't even installing/uninstalling anything  the day before).

```
uname -r
```
produces: ```
5.4.0-42-generic
```
```
modinfo iwlwifi | grep filename
```
produces: ```
filename:       /lib/modules/5.4.0-42-generic/updates/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko
```

I  will try the earlier kernel version thing later this afternoon, and let  you know. I have a demo before that, and I want to make sure I don't  accidentally mess up my ethernet, or something else, right before that.

Thanks for the help!

---

### Post by mysteriousmonkey29 on 2020-09-14
Hello, sorry for the big delay. We were running some demos at work that depended on my computer, and I didn't want to accidentally mess it up trying to fix the wifi. I just booted to the previous kernel, and encountered the same problem--it still says "no wifi adapter found".

Any other ideas?

Thanks!

---

