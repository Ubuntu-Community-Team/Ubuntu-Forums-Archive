---
title: "HP x360 Wifi unavailable"
date: 2022-04-04
forum: Networking &amp; Wireless
---

### Post by perry512 on 2022-04-04
I fresh installed Ubuntu onto my laptop but I am unable to get Wifi to work, the UI shows Wifi Unavailable.

Running lshw -C network gives 
```
*-network DISABLED        
       description: Wireless interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 14.3
       bus info: pci@0000:00:14.3
       logical name: wlo1
       version: 20
       serial: 50:2f:9b:48:36:4f
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.13.0-39-generic firmware=63.c04f3485.0 QuZ-a0-jf-b0-63.u latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: iomemory:600-5ff irq:16 memory:600324c000-600324ffff
```

 
Running rfkill list gives 
```
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

and nmcli outputs
```
wlo1: unavailable
        "Intel Wi-Fi"
        wifi (iwlwifi), 50:2F:9B:48:36:4F, hw, mtu 1500
lo: unmanaged
        "lo"
        loopback (unknown), 00:00:00:00:00:00, sw, mtu 65536
```


The wifi chip in the laptop itself should be the "Intel® Wireless-AC 9461 802.11a/b/g/n/ac (1x1) Wi-Fi® and Bluetooth® 5 combo" and I've gone and installed the drivers from Intel's website

I'm unsure of anything else I could do to fix my issue, any help is very much appreciated!


Link to pastebin
[https://pastebin.com/EkbdM7j5](https://pastebin.com/EkbdM7j5)

Interesting note I would like to add, I installed linux mint onto the same laptop last evening, on which the wifi was working again, but the touchpad and touchscreen was not working, so here I am once again on Ubuntu

---

### Post by chili555 on 2022-04-05
You posted the wireless script itself.> #!/bin/bash
#
# Copyright (c) 2012
#
# Authors: Wild Man, Krytarik
# Helpers: chili555
#
# This script gathers the infos necessary for troubleshooting a wireless
# connection and saves them in a text file, wrapping it in an archive if it
# exceeds the 19.5 kB size limit for ".txt" attachments on the Ubuntu Forums.
#
##############################################################################
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
<snip>

 We need the report that is produced when you run the script. Something like this:

> ########## wireless info START ##########

Report from: 14 Sep 2021 10:35 CAT +0200

Booted last: 14 Sep 2021 00:00 CAT +0200

Script from: 25 Jan 2020 03:34 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 20.04.3 LTS
Release:	20.04
Codename:	focal

##### kernel ############################

Linux 5.11.0-34-generic #36~20.04.1-Ubuntu SMP Fri Aug 27 08:06:32 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu
<snip>Your result will, of course, differ.

Please run the script and post the result.

---

### Post by perry512 on 2022-04-05
Above I have added a pastebin link to my file, hopefully the correct one this time

---

### Post by chili555 on 2022-04-05
```
[ 1453.542595] iwlwifi 0000:00:14.3: WRT: Collecting data: ini trigger 5 fired (delay=0ms).
[ 1453.542719] iwlwifi 0000:00:14.3: FW error in SYNC CMD UNKNOWN
[ 1453.542745] iwlwifi 0000:00:14.3: Hardware error detected. Restarting.
```Very interesting! A firmware error AND a hardware error.

Let's dig deeper. Please reboot so that we have a clean slate and run and pastebin this command:

```
sudo dmesg | grep -e iwl -e 14.3
```

---

### Post by perry512 on 2022-04-06
Alright so after a fresh reboot, the dmesg outputs this

[https://pastebin.com/PExt7199](https://pastebin.com/PExt7199)

If there is any way to format these pastebins in a more digestible way, please do not hesitate from informing me

---

### Post by chili555 on 2022-04-06
We see in your paste:

```
[    2.834098] iwlwifi 0000:00:14.3: loaded firmware version 63.c04f3485.0 QuZ-a0-jf-b0-63.ucode op_mode iwlmvm
[    2.997597] iwlwifi 0000:00:14.3: Detected Intel(R) Wireless-AC 9461, REV=0x354
[    3.156477] iwlwifi 0000:00:14.3: base HW address: 50:2f:9b:48:36:4f
[    3.178497] iwlwifi 0000:00:14.3 wlo1: renamed from wlan0
[    4.039714] iwlwifi 0000:00:14.3: [COLOR="#FF0000"]Microcode SW error detected.[/COLOR] Restarting 0x0.
[    4.039803] iwlwifi 0000:00:14.3: Start IWL Error Log Dump:

```
We wonder if the firmware file is somehow corrupted; check:

```
ls -al /usr/lib/firmware/iwlwifi-QuZ-a0-jf-b0-63.ucode
```

We hope the size is 1252744. If not, download and install a fresh copy:

```
cd /usr/lib/firmware/
mv iwlwifi-QuZ-a0-jf-b0-63.ucode iwlwifi-QuZ-a0-jf-b0-63.bak
sudo wget https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/tree/iwlwifi-QuZ-a0-jf-b0-63.ucode
```

Let's also download the newer firmware to see if it helps:

```
sudo wget https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/tree/iwlwifi-QuZ-a0-jf-b0-66.ucode

```
Reboot and paste:

```
sudo dmesg | grep iwl
```

By the way, your paste format is entirely correct; it's just what we need.

---

### Post by perry512 on 2022-04-06
The file size for the first command matched, but I went ahead and reinstalled it once more, and now the file size reads 8328519, but that is also after installing the newer firmware, but I don't know if that should affect it, so I repeated your first step once more and got the same 8328519.

After a fresh install, my dmesg | grep iwl reads what's below
[https://pastebin.com/3YXxbSyF](https://pastebin.com/3YXxbSyF)

---

### Post by chili555 on 2022-04-07
```
Loaded firmware version: 59.601f3a66.0 QuZ-a0-jf-b0-[COLOR="#FF0000"]59[/COLOR].ucode
```Now it loads neither -63 or -66!? Something is very wrong. Let's see:

```
ls -al /usr/lib/firmware | grep  QuZ-a0-jf-b0
```

---

### Post by perry512 on 2022-04-07
That outputs
-rw-r--r--   1 root root 1052608 Mar 10 02:05 iwlwifi-QuZ-a0-jf-b0-48.ucode
-rw-r--r--   1 root root 1163668 Mar 10 02:05 iwlwifi-QuZ-a0-jf-b0-55.ucode
-rw-r--r--   1 root root 1226064 Mar 10 02:05 iwlwifi-QuZ-a0-jf-b0-59.ucode
-rw-r--r--   1 root root 8328519 Apr  6 20:29 iwlwifi-QuZ-a0-jf-b0-63.bak
-rw-r--r--   1 root root 8328519 Apr  6 20:35 iwlwifi-QuZ-a0-jf-b0-63.ucode
-rw-r--r--   1 root root 1262244 Mar 10 02:05 iwlwifi-QuZ-a0-jf-b0-66.ucode
-rw-r--r--   1 root root 8390937 Apr  6 20:25 iwlwifi-QuZ-a0-jf-b0-66.ucode.1

Seems to at least recognize them as far as I can tell

---

### Post by chili555 on 2022-04-07
Please excuse my misstep. I regret my mistake. I gave the wrong link. I will now wipe a few layers of smudge off of my readers!

Please do:

```
cd /usr/lib/firmware
sudo rm iwlwifi-QuZ-a0-jf-b0-6*
sudo wget https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/iwlwifi-QuZ-a0-jf-b0-63.ucode
sudo wget https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/iwlwifi-QuZ-a0-jf-b0-66.ucode

```
Please verify that they are the correct size:

```
ls -al | grep QuZ-a0-jf-b0-

```
They should be 1252744 and 1262244. If so reboot and show me:

```
sudo dmesg | grep iwl
```

---

### Post by perry512 on 2022-04-07
Here we are, the file sizes matched up with what you detailed

[https://pastebin.com/GRfubrs7](https://pastebin.com/GRfubrs7)

---

### Post by chili555 on 2022-04-07
We now try the somewhat experimental approach that I'd hoped we could avoid. Please do:

```
sudo apt update
sudo apt install -y build-essential dkms
wget http://mirrors.kernel.org/ubuntu/pool/universe/b/backport-iwlwifi-dkms/backport-iwlwifi-dkms_9340-0ubuntu4_all.deb
sudo dpkg -i backport*.deb

```
Reboot and show me:

```
sudo dmesg | grep iwl
```

---

### Post by perry512 on 2022-04-07
Alright so upon rebooting, the changes seem to have taken out the functionality of my wifi adapter I've been using for the time being.

I've also noticed that wifi symbol/window within the settings is disappearing and reappearing repeatedly.

Here is the output of dmesg: [https://pastebin.com/sdvv8ak1](https://pastebin.com/sdvv8ak1)

---

### Post by chili555 on 2022-04-07
We are quickly running out of options.

Please try a live session of the upcoming Ubuntu 22.04: [https://cdimage.ubuntu.com/daily-live/current/](https://cdimage.ubuntu.com/daily-live/current/)

If the wireless, bluetooth, graphics, touchpad, etc., etc. are working, I'd install it. 

I regret that I have no other likely productive suggestions.

---

