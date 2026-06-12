---
title: "iwlwifi detects microcode SW error and crashes, then totally disappears"
date: 2018-09-02
forum: Networking &amp; Wireless
---

### Post by MisterPi on 2018-09-02
I've been having trouble with my wireless (Intel Wireless 7265) with some of the recent kernel versions (currently at 4.15.0-33-generic).  But now it has been just outright crashing.  When it does, the wireless just completely disappears, like it never existed (until I reboot).  (See separate thread [https://ubuntuforums.org/showthread.php?t=2400116&p=13797350#post13797350](https://ubuntuforums.org/showthread.php?t=2400116&p=13797350#post13797350) concerning restarting wifi.)

It seems to start with the network disconnecting spontaneously (i.e., I didn't issue any commands related to wireless).  This is the first line in syslog following a gap of more than 4 minutes:

Sep  2 10:37:49 xxxx wpa_supplicant[897]: wlp1s0: CTRL-EVENT-DISCONNECTED bssid=00:f1:96:6f:ef:c6 reason=4 locally_generated=1

Then it seems to try to reconnect.  At some point it lowers the power level, at which point the failure occurs:

Sep  2 10:37:50 xxxx NetworkManager[896]: <info>  [1535909870.5118] device (wlp1s0): supplicant interface state: 4-way handshake -> completed
Sep  2 10:37:50 xxxx wpa_supplicant[897]: wlp1s0: CTRL-EVENT-SIGNAL-CHANGE above=1 signal=-64 noise=9999 txrate=115600
Sep  2 10:37:50 xxxx kernel: [ 9364.455980] wlp1s0: Limiting TX power to 30 (30 - 0) dBm as advertised by --:--:--:--:--:--
Sep  2 10:37:58 xxxx kernel: [ 9372.339699] iwlwifi 0000:01:00.0: Microcode SW error detected.  Restarting 0x82000000.
Sep  2 10:37:58 xxxx kernel: [ 9372.339858] iwlwifi 0000:01:00.0: Start IWL Error Log Dump:
Sep  2 10:37:58 xxxx kernel: [ 9372.339865] iwlwifi 0000:01:00.0: Status: 0x00000100, count: 6
Sep  2 10:37:58 xxxx kernel: [ 9372.339871] iwlwifi 0000:01:00.0: Loaded firmware version: 29.1044073957.0
Sep  2 10:37:58 xxxx kernel: [ 9372.339877] iwlwifi 0000:01:00.0: 0x00000034 | NMI_INTERRUPT_WDG           
Sep  2 10:37:58 xxxx kernel: [ 9372.339883] iwlwifi 0000:01:00.0: 0x000002B0 | trm_hw_status0
...

The power level change might be a red herring, given the 8 second gap between the change and the error.

The relevant portion of the syslog is attached.

---

### Post by chili555 on 2018-09-02
Does this help? [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1710390](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1710390)

What does this tell us?```
sudo dpkg -s linux-firmware | grep -i version
```

---

### Post by MisterPi on 2018-09-02
> **chili555 said:**
> Does this help? [URL="https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1710390"]https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1710390
[/URL]

Not much.  They suggested a workaround, which was to add something to /etc/NetworkManager/NetworkManager.conf -- but my file already has the change, and the mod date on the file is only a month after the workaround was posted, so looks like the workaround was added to the main repo shortly after that post.

It's interesting that the bug seems to come and go with kernel versions.  If it happens again I can try their data collection suggestions and post to that site.

> **chili555 said:**
> 
What does this tell us?```
sudo dpkg -s linux-firmware | grep -i version
```

Version: 1.173.1

---

### Post by chili555 on 2018-09-03
Is the firmware file somehow corrupted? Let's check:```
md5sum /lib/firmware/iwlwifi-7265D-29.ucode
```I get: ```
31c1bf25ccce3249af88962ad21fa7fd
```If yours is the same, I doubt that the firmware is corrupted.

There is a later vversion of linux-firmware. I downloaded it and the md5sum is the same and there is no later version than -29:> iwlwifi 0000:01:00.0: Loaded firmware version: [COLOR="#FF0000"]29[/COLOR].1044073957.0> wireless just completely disappears, like it never existed (until I reboot)Does it work to unload and reload the driver?```
sudo modprobe -r iwlwifi && sudo modprobe iwlwifi
```I am afraid that I haven't any other ideas.

---

### Post by MisterPi on 2018-09-03
My MD5 matches yours, and 29 is my latest version.  There are lots of versions of this file there, both for 7265 and 7265D.  How can I tell which one is actually used by the driver?  Are the older ones kept just for a fallback?

So presumably it's a driver bug, or the new kernel isn't playing nice with it.  Do you know who supports the driver (Ubuntu, Intel, or the community)?  Maybe they need to be alerted.  Other people are posting about problems with the same unit.

I tried removing/installing with modprobe when it happened; didn't work.  I suspect that when the driver barfed, some module (the network manager, or something) decided to delete the entire interface.  I don't know how to get it back; things like "ifconfig wlp1s0 up" didn't work because ifconfig simply no longer recognized the interface wlp1s0 after the crash.

Do you have any suggestions for bringing the interface back up (short of rebooting)?  This has happened twice already.  (I posted this question to a separate thread but the moderator called it redundant.)

Also note that I have a different problem with the wireless, which is that multiple suspend/wakeup cycles will disable it ([https://ubuntuforums.org/showthread.php?t=2400034](https://ubuntuforums.org/showthread.php?t=2400034)).  But this is different; the crash happens randomly while the system is operating normally (the first occurred while I was playing music from a local file on my disk -- not using the web or wireless -- and I wasn't even typing or executing anything).

---

### Post by chili555 on 2018-09-03
> Do you know who supports the driver (Ubuntu, Intel, or the community)?The answer is in:```
modinfo iwlwifi
```> chili@T440p:~$ modinfo iwlwifi
filename:       /lib/modules/4.15.0-33-generic/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko
license:        GPL
[COLOR="#FF0000"]author[/COLOR]:         Copyright(c) 2003- 2015[COLOR="#FF0000"] Intel Corporation <linuxwifi@intel.com>[/COLOR]
description:    Intel(R) Wireless WiFi driver for Linux
<snip>However, the usual, perhaps canonical method is to file a bug report: [https://bugs.launchpad.net/](https://bugs.launchpad.net/) Search to see if there is already another iwlwifi firmware crashed bug; if so, add to it.> How can I tell which one is actually used by the driver?Your dmesg says:> iwlwifi 0000:01:00.0: Loaded firmware version: 29.1044073957.0When we list the files in /lib/firmware related to 726x, we see only one -29:```
iwlwifi-7265D-29.ucode
```It is also referred to in modinfo:```
chili@T440p:~$ modinfo iwlwifi
filename:       /lib/modules/4.15.0-33-generic/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
description:    Intel(R) Wireless WiFi driver for Linux
<snip>
firmware:       iwlwifi-7265D-29.ucode
<snip>
```> So presumably it's a driver bug, or the new kernel isn't playing nice with it.I doubt that it's a kernel or driver bug; otherwise, instead of one or two complaints, we'd have thousands. Intel wireless devices are quite common. I have one.

Could it be an intermittent hardware issue? Overheating? Low voltage?

Is this dual boot? Does it work perfectly in Windows?

---

### Post by MisterPi on 2018-09-03
> **chili555 said:**
> When we list the files in /lib/firmware related to 726x, we see only one -29:

I have a bunch:

```

$ cd /lib/firmware
$ ls -l iwlwifi-7265*
-rw-r--r-- 1 root root  736844 Mar 29  2017 iwlwifi-7265-10.ucode
-rw-r--r-- 1 root root  880604 Mar 29  2017 iwlwifi-7265-12.ucode
-rw-r--r-- 1 root root  885224 Mar 29  2017 iwlwifi-7265-13.ucode
-rw-r--r-- 1 root root 1180356 Mar 29  2017 iwlwifi-7265-16.ucode
-rw-r--r-- 1 root root 1180412 May 18 11:07 iwlwifi-7265-17.ucode
-rw-r--r-- 1 root root  690452 Mar 29  2017 iwlwifi-7265-8.ucode
-rw-r--r-- 1 root root  697828 Mar 29  2017 iwlwifi-7265-9.ucode
lrwxrwxrwx 1 root root      21 Nov 17  2017 iwlwifi-7265D-10.ucode -> iwlwifi-7265-10.ucode
-rw-r--r-- 1 root root 1002800 Mar 29  2017 iwlwifi-7265D-12.ucode
-rw-r--r-- 1 root root 1008692 Mar 29  2017 iwlwifi-7265D-13.ucode
-rw-r--r-- 1 root root 1384500 Mar 29  2017 iwlwifi-7265D-16.ucode
-rw-r--r-- 1 root root 1383604 Nov 17  2017 iwlwifi-7265D-17.ucode
-rw-r--r-- 1 root root 1385368 Nov 17  2017 iwlwifi-7265D-21.ucode
-rw-r--r-- 1 root root 1028376 Apr 24 07:23 iwlwifi-7265D-22.ucode
-rw-r--r-- 1 root root 1032740 Dec  5  2017 iwlwifi-7265D-27.ucode
-rw-r--r-- 1 root root 1036432 May 18 11:07 iwlwifi-7265D-29.ucode

```
I did a fresh install of Kubuntu 17.10, then upgraded to 18.04 as soon as it came out.  Any idea why the old versions are still there?  Someone's just not cleaning up?  Seems like I could delete them without problems.

---

### Post by chili555 on 2018-09-03
>  Any idea why the old versions are still there? The system doesn't check to see what device you have nor whether, for development reasons, you decide to install an older kernel with its accompanying older driver version. The firmware files take up little room and it's better to have a few too many than to have a mysteriously not-working wireless device. Hard-drive space is cheap.

Slightly off-topic, one could spend hours to eliminate un-needed firmware files, USB-ethernet drivers, PCMCIA drivers, etc., etc. and then fine-tune the kernel to ones exact needs. You might get the system to boot in 5 seconds (instead of my current 8 seconds) but so what? When a later kernel version comes along that includes crucial security updates, will you start over and fine-tune that one, too? And will you do the same with the next version of linux-firmware?

Your device loads the latest available firmware file and none other, as expected. Removing firmware files won't change that one bit.

---

### Post by MisterPi on 2018-09-05
> **chili555 said:**
> 
Could it be an intermittent hardware issue? Overheating? Low voltage?

Is this dual boot? Does it work perfectly in Windows?

Well, I wouldn't know.  It's dual boot, for those times I NEED Windows (app such-and-such doesn't run on Linux, you know the story) but then I haven't needed Windows in a month.  Then again, would Windows even give me a meaningful error message about the driver failure, or would it just BSOD on me?

Anyway, do you know of any good primers or "theory of operations" manuals that describe all the steps in a wireless connection?  IOW, what modules and processes come between the user and the driver (iwlwifi in my case)?  Preferably specific to distro/version (Kubuntu 18.04 in my case), so when I find suggestions online I can filter out those that don't apply.

I have been dealing with other issues:

- For this case, how do I get wireless back after the driver crash, short of rebooting?
- If I suspend and wake up, wireless is fine after the first wakeup, but dead after the second; again, how do I get wireless back without rebooting?

And lot of other people are having issues with their wireless too.  So an explanation of all the relevant modules and what talks to what may help some people diagnose problems on their own before they start posting.  (The sticky thread on this forum just says how to run a script to collect info to post; doesn't really explain what is going on under the hood.)

---

### Post by chili555 on 2018-09-05
>  would Windows even give me a meaningful error message about the driver failure, or would it just BSOD on me?

I think it is more likely that the wireless simply wouldn’t work at all with no way, such as dmesg, to get the first clue as to why. 

> Anyway, do you know of any good primers or "theory of operations" manuals that describe all the steps in a wireless connection? IOW, what modules and processes come between the user and the driver (iwlwifi in my case)? 

I do not. I am, despite my lofty reputation, a decent shade-tree mechanic, not an engineer. I know from experience that the driver loads dependencies that are enumerated in lsmod:

```
$ lsmod | grep iwl
iwlmvm                364544  0
mac80211              778240  1 iwlmvm
iwlwifi               282624  1 iwlmvm
cfg80211              622592  3 iwlmvm,iwlwifi,mac80211
```

I suspect yours are the same. Some older devices load iwldvm instead of iwlmvm.

There is an elaborate file, /etc/modprobe.d/iwlwifi.conf, to assure that the drivers and dependencies unload and reload in the correct order; please be sure yours is intact. By default, It reads:

```
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
```

Cleverly, Intel (as well as Broadcom and some others) looks at the pci.id, 8086:something, and loads the exact required firmware. Your 7265 requires a different firmware than my 7260 or the 3160 or the 9260 series. My somewhat limited understanding is that the kernel sees the device pci.id and loads the correct driver and the driver calls up the correct firmware. An interface, wlp2s0, for example, is created, and systemd, netplan and Network Manager take over.

If the physical device, driver, dependencies and firmware are not in order, as you’ve seen, the process stops. “Your car only has three of its usual four wheels; I can’t allow you on the Autobahn.”

>  how do I get wireless back after the driver crash, short of rebooting?

I am not aware if there is a known, confirmed method to do so. There are only so many things to try:

    1. Turn off and back on the wireless radio:```
sudo rfkill block wlan && sudo rfkill unblock wlan
```A pause between block and unblock may be helpful.
    2. Unload and reload the driver:```
sudo modprobe -r iwlwifi && sudo modprobe iwlwifi
```Again, a pause may be useful.
    3. Suspend (which you’ve tried)
    4. Reboot.

I remain suspicious that it is a hardware issue.

---

### Post by MisterPi on 2018-09-05
I was thinking mainly of outside the driver, which is more-or-less a black box as far as Linux is concerned.  When the crash occurred, I tried removing/reinstalling iwlwifi with modprobe, but that didn't help.  So I assume it's not a driver issue.  Well, of COURSE the crash was CAUSED by the driver, unless it's a hardware issue like you suggested.  But the fact that reinstalling the driver didn't help means that some other module needs to be told to initialize the wireless again.  Which module?  That's the kind of knowledge I'm seeking.  Documentation would help, particularly if it explains the principles involved and describes the relationships of the modules, rather than just "try [magic incantation 1], and if that doesn't work, try [magic incantation 2], etc..."

---

### Post by jeremy31 on 2018-09-05
This might be fixed by intel upstream, try
```
sudo apt-get update && sudo apt-get install git build-essential linux-headers-generic
```
```
git clone https://git.kernel.org/pub/scm/linux/kernel/git/iwlwifi/backport-iwlwifi.git
```
```
cd backport-iwlwifi
```
```
make defconfig-iwlwifi-public
```
```
sed -i 's/CPTCFG_IWLMVM_VENDOR_CMDS=y/# CPTCFG_IWLMVM_VENDOR_CMDS is not set/' .config
```
```
make -j4
```
```
sudo make install
```

Make sure Secure Boot is disabled in UEFI/BIOS after rebooting

---

### Post by chili555 on 2018-09-05
If you want to try the bleeding edge driver, please check here: [https://askubuntu.com/questions/1038242/no-wifi-option-on-ubuntu-18-04-and-16-04](https://askubuntu.com/questions/1038242/no-wifi-option-on-ubuntu-18-04-and-16-04) You probably don't need the disable_msix=1 step.

I just ran 'make' on my 18.04 system and it builds without error or warning.

I am skeptical that it will fix the firmware crash.

---

### Post by chili555 on 2018-09-05
> 

 That's the kind of knowledge I'm seeking. Documentation would help, particularly if it explains the principles involved and describes the relationships of the modules, rather than just "try [magic incantation 1], and if that doesn't work, try [magic incantation 2], etc..."

As I said, I am unaware of any. Perhaps my colleagues will chime in with a suggestion.

---

