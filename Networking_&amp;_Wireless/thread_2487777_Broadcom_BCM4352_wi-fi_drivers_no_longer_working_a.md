---
title: "Broadcom BCM4352 wi-fi drivers no longer working as of 22.04"
date: 2023-06-14
forum: Networking &amp; Wireless
---

### Post by veleek on 2023-06-14
This is repost of a [question I posted]("https://ubuntuforums.org/showthread.php?t=2486962") before that got no traction.  I have since then tested out the problem on a bunch more versions and it's still not working.  This seems like something that chili555 will be most able to help with but I dunno is there's a good way to get his attention.

If I install ubuntu 20.04 I am able to successfully install drivers and setup a wifi network using this device.  I have tried multiple newer versions and the behavior is the same:
* Lubuntu 22.04
* Ubuntu 22.04 
* Lubuntu 23.04
* Ubuntu 23.04
I am able the successfully install the drivers, everything seems the be valid and correct but no wifi adapter shows up and I'm unable to find or connect to a network.  

I have looked through a whole bunch of other threads and none of them seems to have this issue.  

[https://ubuntuforums.org/showthread.php?t=2487188](https://ubuntuforums.org/showthread.php?t=2487188)
[https://ubuntuforums.org/showthread.php?t=2486962](https://ubuntuforums.org/showthread.php?t=2486962)

I have gathered output from all of the following commands in a gist: [https://gist.github.com/veleek/b7b0e9cf1a05eaa2d6b30d756485a3db](https://gist.github.com/veleek/b7b0e9cf1a05eaa2d6b30d756485a3db)

> uname -r
> sudo apt update && sudo apt -y upgrade
> sudo apt install --reinstall bcmwl-kernel-source
> lspci -nnk | grep 0280 -A3
> sudo dmesg | grep wl                            
> sudo lshw -C network
> ifconfig -a

The gist output is all from the most recent install Lubuntu 23.04 (my preferred version if possible), but the behavior is identical on all versions.

---

### Post by chili555 on 2023-06-16
> This seems like something that chili555 will be most able to help with but I dunno is there's a good way to get his attention.You have my attention. Just for future reference, and for the information of the searchers, you can always sent me a private message to ask if I'll take a look at your question. I'm happy to do so.

Did the module load?

```
lsmod | grep wl
```
Are there informative clues in the message log?

```
sudo dmesg | grep 01:00
```

With your docker and bridge, I wonder if netplan has taken over networking.

```
cat /etc/netplan/*.yaml
```

---

### Post by SeijiSensei on 2023-06-16
Have you tried using the Driver Manager that's in the Settings? It's the most reliable method I've found for updating proprietary drivers.

---

### Post by veleek on 2023-06-19
> **chili555 said:**
> You have my attention. Just for future reference, and for the information of the searchers, you can always sent me a private message to ask if I'll take a look at your question. I'm happy to do so.

Haha, well now that you point out the PM option, it seems so obvious!!! This is my first time posting here and didn't even think to look for that :P.

> **chili555 said:**
> Did the module load?

```
lsmod | grep wl
```

```
> lsmod | grep wl
wl                   6488064  0
cfg80211             1241088  1 wl
```

> **chili555 said:**
> Are there informative clues in the message log?

```
sudo dmesg | grep 01:00
```

Everything in the log _seems_ to be healthy
```
> sudo dmesg | grep 01:00
[    0.500566] pci 0000:01:00.0: [14e4:43b1] type 00 class 0x028000
[    0.500597] pci 0000:01:00.0: reg 0x10: [mem 0xfe800000-0xfe807fff 64bit]
[    0.500616] pci 0000:01:00.0: reg 0x18: [mem 0xfe600000-0xfe7fffff 64bit]
[    0.500770] pci 0000:01:00.0: supports D1 D2
[    0.500775] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    4.656001] bcma-pci-bridge 0000:01:00.0: enabling device (0100 -> 0102)
[    4.657645] bcma-pci-bridge 0000:01:00.0: bus0: Found chip with id 0x4352, rev 0x03 and package 0x00
[    4.657700] bcma-pci-bridge 0000:01:00.0: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x2B, class 0x0)
[    4.657726] bcma-pci-bridge 0000:01:00.0: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x2A, class 0x0)
[    4.657761] bcma-pci-bridge 0000:01:00.0: bus0: Core 2 found: ARM CR4 (manuf 0x4BF, id 0x83E, rev 0x02, class 0x0)
[    4.657797] bcma-pci-bridge 0000:01:00.0: bus0: Core 3 found: PCIe Gen2 (manuf 0x4BF, id 0x83C, rev 0x01, class 0x0)
[    4.657819] bcma-pci-bridge 0000:01:00.0: bus0: Core 4 found: USB 2.0 Device (manuf 0x4BF, id 0x81A, rev 0x11, class 0x0)
[    4.699107] bcma-pci-bridge 0000:01:00.0: bus0: Bus registered
```

> **chili555 said:**
> With your docker and bridge, I wonder if netplan has taken over networking.

```
cat /etc/netplan/*.yaml
```

The behavior was the same prior to installing docker, and the behavior occurs on a "try it" versions of Ubuntu and Lubuntu running fresh off a USB stick, so it's _possible_ that that's compounding the issue, but I don't think it's the cause.

```
File: /etc/netplan/01-network-manager-all.yaml&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;
# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager
```

---

### Post by veleek on 2023-06-19
> **SeijiSensei said:**
> Have you tried using the Driver Manager that's in the Settings? It's the most reliable method I've found for updating proprietary drivers.

Thanks for the pointer, but as far as I can tell the driver has been successfully installed (tried installing it via Driver Manager and various CLI commands).  The driver and the device seem to be perfectly healthy, it's just not creating the WiFi interface.

---

### Post by chili555 on 2023-06-19
Your netplan looks perfect. Let's have a look at:

```
lsmod | grep -e bcma -e b43
sudo dmesg | grep wl
```This is my favorite kind of problem: everything looks great except it just doesn't work.

---

### Post by veleek on 2023-06-20
```
> lsmod | grep -e bcma -e b43
bcma                   86016  0
```

```
>  sudo dmesg | grep wl
[    0.000000] DMI: Hewlett-Packard HP t620 Quad Core TC/21B4, BIOS L40 v02.10 07/03/2015
[    3.944144] integrity: Loaded X.509 cert 'Hewlett-Packard UEFI Secure Boot DB Key: e7203ac28b848d3c03432f6a485dd1f4c7b8e529'
[   21.269832] wl: loading out-of-tree module taints kernel.
[   21.269853] wl: module license 'MIXED/Proprietary' taints kernel.
[   21.280162] wl: module verification failed: signature and/or required key missing - tainting kernel
```

Full dmesg log from a fresh reboot is available here: [dmesg-2023-06-20.txt (github.com)]("https://gist.github.com/veleek/7d648a07049c68a71ddf596903104cda")

---

### Post by chili555 on 2023-06-20
You should have file on your system called /etc/modprobe.d/broadcom-sta-dkms.conf 
 
Mine reads:

```
# wl module from Broadcom conflicts with the following modules:
blacklist b43
blacklist b43legacy
blacklist b44
blacklist bcma
blacklist brcm80211
blacklist brcmsmac
blacklist ssb

```As you see, bcma and others are supposed to be blacklisted. bcma and possibly other conflicting modules are loading in your case.

Please look over your file and amend it as needed. Reboot.

Any improvement?

---

### Post by veleek on 2023-06-25
Sorry for the delay, was out of town for a few days.

My broadcom-sta-dkms.conf file is the same as yours.  But if I understand you correctly, you're saying that the wl module conflicts with bcma, and based on the output from lsmod the bcma module is still being loaded for some reason.  Is that correct?

How do I determine why that module is being loaded (and/or why that blacklist file is NOT being loaded?  *(Also, quick reminder that this behavior repros on a fresh installation)*

---

### Post by veleek on 2023-06-25
Okay... so something has happened (I swear I did not modify the blacklist).  I left the machine on and hooked up to ethernet while I was gone and it looks like something started working.

I just rebooted and now I'm getting completely different output for "sudo dmesg | grep wl"

```
> sudo dmesg | grep 01:00
[    0.499086] pci 0000:01:00.0: [14e4:43b1] type 00 class 0x028000
[    0.499116] pci 0000:01:00.0: reg 0x10: [mem 0xfe800000-0xfe807fff 64bit]
[    0.499136] pci 0000:01:00.0: reg 0x18: [mem 0xfe600000-0xfe7fffff 64bit]
[    0.499289] pci 0000:01:00.0: supports D1 D2
[    0.499294] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[   20.916148] wl 0000:01:00.0: enabling device (0100 -> 0102)
[   21.121490] wl 0000:01:00.0 wlp1s0: renamed from wlan0
```

I'm seeing wl in the output instead of the bcma-pci-bridge, and the device successfully shows up (renamed from wlan0 to wlp1s0 for some reason, but whatever).  I'm able to enumerate wireless networks using nmcli.  bcma no longer shows up in lsmod either.  The ONLY thing I've done since getting home is rebooted the device to respond to this post...

I'd like to see if I can repro the behavior again using a live distro off a USB-key, but to help debug why it's working now is there anything you can suggest looking at?

---

### Post by chili555 on 2023-06-27
Sorry for my delay. I have beed quite ill.

>  is there anything you can suggest looking at?There are only two reasons that I know of that bcma would possibly load in spite of being blacklisted. First, modules that are to be loaded explicitly, are declared in /etc/modules. Please check to see that bcma, ssb nor cordic are declared. If so, remove them.

The second is that certain Broadcom ethernet devices use the driver b44. It's dependencies are ssb and mii. I beleive that it is possible that, in the presence of the driver b44 and ssb, that bcma and all of her noisy sisters will also load.

What is your ethernet device?

```
lspci -nnk | grep 0200 -A3

```

---

### Post by veleek on 2023-06-30
/etc/modules is empty and the Ethernet device is a Realtek, so nothing obvious conflicting there.

```
> lspci -nnk | grep 0200 -A3
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)        Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:21b4]
        Kernel driver in use: r8169
        Kernel modules: r8169
```

That being said, I have a proper repro now. 

First I tried the live distro off a USB key (Lubuntu 23.04).
1. Boot up
2. Check lsmod and verified that b43 and bcma drivers exist and are loaded.
3. Install driver from Additional Drivers window.
4. Since I can't reboot and keep the live distro changes, after installing the driver I manually removed b43 and bcma drivers (sudo modprobe -r b43, etc.)
5. Then manually loaded wl (sudo modprobe wl)
6. Successful wifi connection.

So next steps:
1. Re-install Lubuntu fresh on the machine.
2. Verify same state (b43 and bcma loaded)
3. Install the Broadcom driver
4. Verify that /etc/modprobe.d/broadcom-sta-dkms.conf contains b43 and bcma.
5. Reboot machine
6. lsmod | grep -e b43 -e bcma, shows that bcma is still loaded but not b43.
7. verify that wifi doesn't work.

At this point in time I did some digging and found [Modules loading despite being added to the blacklist - Ask Ubuntu]("https://askubuntu.com/questions/51321/modules-loading-despite-being-added-to-the-blacklist").  The suggestion was to run

```
sudo update-initramfs -u
``` 

as that was required to update the blacklist.  I ran this command, and rebooted and verified that neither b43 or bcma were loaded and wifi worked properly.

So! We know what the problem is, and we know how to fix it.  What's next?  Is there anyway to troubleshoot why the blacklist isn't being respected?  Or why on the earlier version I don't even need to restart after installing the driver for it to work?  Should it really be neccessary to run update-initramfs after changing the blacklist for this to work?  What changed since version 20 for this to break?

---

### Post by chili555 on 2023-07-01
> sudo update-initramfs -uI suspect that this is the key. I also suspect that the process of installing the driver *bcmwl-kernel-source* should, but does not, include that as the final step in it's latest version. 

I recommend that you file a bug report: [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

---

### Post by veleek on 2023-07-02
Bug filed: [https://ubuntuforums.org/showthread.php?t=2487777&page=2&p=14148921#post14148921](https://ubuntuforums.org/showthread.php?t=2487777&page=2&p=14148921#post14148921)

Thanks for the help!  This thread can be marked resolved now.

---

### Post by smikesmith on 2024-04-11
Hi, I've installed a brand-new Ubuntu 22.04LTS, and have this same problem.  Broadcom 4352 802.11ac Wireless Network Adapter is not found.  The system is using "Broadcom Linux STA wireless driver from bcmwl-kernel-source (proprietary)", but I get no function, i.e., no wifi is found.  This built-in adapter has worked perfectly for years with Ubuntu 14.04 and 20.04.  I've tried numerous suggestions across the web, but with no success.  What doe it take, after two years of OS release, to get a working driver?

---

### Post by praseodym on 2024-04-11
Please Show the outputs of

lsmod
cat /etc/modules

Secure Boot is turned off?

---

