---
title: "Qualcomm Atheros ar8161 ethernet stopped working on Lubuntu 22.04"
date: 2023-02-06
forum: Networking &amp; Wireless
---

### Post by alexis0b on 2023-02-06
Hi everyone!

I'm very new to the Linux world and installed for the first time this system on a old machine I have.
After some trouble I could make it work, since it needed drivers for providing video output (before that I could only use recovery mode or obtain a video output after cleaning and restoring packages each time I switched on the system, with a smaller resolution).
Having successfully installed NVIDIA drivers and getting a full 1920x1080 resolution on the corresponding monitor, I now can't get any network connection with ethernet hardware since then.

Before installing NVIDIA drivers connection was working properly, well, very slow actually, but working...
Now I can't get any connection at all and I've already tried many options found online but they usually require some other kind of connection (Wi-Fi, possibly), for this reason, I installed a spare PCIe wifi card I had, but it makes no difference since Network Manager is empty, even though I restarted it many times and in different ways.

Basically, I think drivers are missing but I can't get any without network connection and I can't find them online to use a usb drive to transfer them on the needed machine (even if I don't even know whether this would be a suitable solution).

I also tried to connect my phone via USB to share internet connection but it does not work.
I report some command on the terminal that may be useful and also a result from a suggestion found in an old thread that could solve the problem

```

alessandro@alessandro-DESKTOP-TJQ301F:~$ sudo lshw -c network
  *-network UNCLAIMED       
       description: Ethernet controller
       product: AR8161 Gigabit Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list
       configuration: latency=0
       resources: memory:feac0000-feafffff ioport:ec00(size=128)
  *-network UNCLAIMED
       description: Network controller
       product: Wireless 7265
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 59
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:febfe000-febfffff
alessandro@alessandro-DESKTOP-TJQ301F:~$ rfkill list
alessandro@alessandro-DESKTOP-TJQ301F:~$ lspci -nn
00:00.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] RS780 Host Bridge [1022:9600]
00:02.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] RS780 PCI to PCI bridge (ext gfx port 0) [1022:9603]
00:04.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 0) [1022:9604]
00:09.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 4) [1022:9608]
00:11.0 SATA controller [0106]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] [1002:4390]
00:12.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:12.1 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0 USB OHCI1 Controller [1002:4398]
00:12.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:13.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:13.1 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0 USB OHCI1 Controller [1002:4398]
00:13.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller [1002:4385] (rev 3c)
00:14.1 IDE interface [0101]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 IDE Controller [1002:439c]
00:14.2 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) [1002:4383]
00:14.3 ISA bridge [0601]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d]
00:14.4 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge [1002:4384]
00:14.5 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399]
00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 10h Processor HyperTransport Configuration [1022:1200]
00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Address Map [1022:1201]
00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 10h Processor DRAM Controller [1022:1202]
00:18.3 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Miscellaneous Control [1022:1203]
00:18.4 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Link Control [1022:1204]
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF104 [GeForce GTX 460] [10de:0e22] (rev a1)
01:00.1 Audio device [0403]: NVIDIA Corporation GF104 High Definition Audio Controller [10de:0beb] (rev a1)
02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8161 Gigabit Ethernet [1969:1091] (rev 10)
03:00.0 Network controller [0280]: Intel Corporation Wireless 7265 [8086:095a] (rev 59)
alessandro@alessandro-DESKTOP-TJQ301F:~$ cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|ssb|witch|wl'
# which ath5k cannot recover. To prevent this condition, stop
blacklist ath_pci
blacklist eth1394
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist uart6850
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \

```

N.B.:
I'm posting from another computer, hence is not so easy to report possible results from terminal actions you are going to suggest me.
Anyway, tell me any information needed for solving this issue and I will find a way to provide them.

Thanks anyone for helping!

---

### Post by chili555 on 2023-02-06
Please run and post:

```
uname -r
sudo dpkg -s linux-modules-extra-$(uname -r) | grep Status
```Can you boot into an earlier kernel version at the GRUB menu and do the networking devices work there?

---

### Post by alexis0b on 2023-02-07
> **chili555 said:**
> Please run and post:

```
uname -r
sudo dpkg -s linux-modules-extra-$(uname -r) | grep Status
```Can you boot into an earlier kernel version at the GRUB menu and do the networking devices work there?

The result from the code you suggested me says that the needed package is not installed and hence unavailable. It suggests to use "dpgk --info" to examine archives, should I do it?

For booting in an earlier kernel version you mean through a usb drive with a bootable older kernel installed?

---

### Post by chili555 on 2023-02-07
> For booting in an earlier kernel version you mean through a usb drive with a bootable older kernel installed?No. 

Run: ```
uname -r 
```Make note of the exact kernel version where networking fails. We'll need that in a moment.

Reboot and interrupt the boot process with the shift key: [https://wiki.ubuntu.com/RecoveryMode#:~:text=With%20BIOS%2C%20quickly%20press%20and,starts%20with%20%22Advanced%20options%22](https://wiki.ubuntu.com/RecoveryMode#:~:text=With%20BIOS%2C%20quickly%20press%20and,starts%20with%20%22Advanced%20options%22).

You will see something like this:

[IMG]https://www.omgubuntu.co.uk/wp-content/uploads/2012/09/grub2-in-ubuntu.jpg[/IMG] 
Press Enter on Advanced Options and you will see a list of two, probably, kernel versions on your system. Use the arrow keys to scroll down to the earlier and press Enter. 

Now does the networking device work? If so, you know that linux-modules-extra *is* installed on that kernel but *not* on the later kernel.

While booted into the earlier kernel version where networking succeeds, do:
```
sudo apt update
sudo apt install --reinstall linux-modules-extra-XXX
```...where XXX is the exact kernel version you found above. For example, you might find 5.19.0-29-generic in uname -r above; that is, where networking fails. So the latter command would then be:

```
sudo apt install --reinstall linux-modules-extra-5.19.0-29-generic
```Reboot and let us know if networking is fixed.

Please post back if you get stuck.

---

### Post by alexis0b on 2023-02-07
> **chili555 said:**
> No. 

Run: ```
uname -r 
```Make note of the exact kernel version where networking fails. We'll need that in a moment.

Reboot and interrupt the boot process with the shift key: [https://wiki.ubuntu.com/RecoveryMode#:~:text=With%20BIOS%2C%20quickly%20press%20and,starts%20with%20%22Advanced%20options%22](https://wiki.ubuntu.com/RecoveryMode#:~:text=With%20BIOS%2C%20quickly%20press%20and,starts%20with%20%22Advanced%20options%22).

You will see something like this:

[IMG]https://www.omgubuntu.co.uk/wp-content/uploads/2012/09/grub2-in-ubuntu.jpg[/IMG] 
Press Enter on Advanced Options and you will see a list of two, probably, kernel versions on your system. Use the arrow keys to scroll down to the earlier and press Enter. 

Now does the networking device work? If so, you know that linux-modules-extra *is* installed on that kernel but *not* on the later kernel.

While booted into the earlier kernel version where networking succeeds, do:
```
sudo apt update
sudo apt install --reinstall linux-modules-extra-XXX
```...where XXX is the exact kernel version you found above. For example, you might find 5.19.0-29-generic in uname -r above; that is, where networking fails. So the latter command would then be:

```
sudo apt install --reinstall linux-modules-extra-5.19.0-29-generic
```Reboot and let us know if networking is fixed.

Please post back if you get stuck.

Actually. I did get stuck.
Trying to enter the earlier kernel version (even if the grub interface was different from the one you posted) I get the following message:

```

mtd device must be supplied (device name is empty)

```

---

### Post by alexis0b on 2023-02-07
> **alexis0b said:**
> Actually. I did get stuck.
Trying to enter the earlier kernel version (even if the grub interface was different from the one you posted) I get the following message:

```

mtd device must be supplied (device name is empty)

```

Wait I could enter it by using the access to the earlier kernel in recovery mode and then booting from recovery. And I've ot network in this kernel, both ethernet and wifi.
I'm following the procedure you provided.
Will update when finished

---

### Post by guiverc on 2023-02-07
> **alexis0b said:**
> 

Before installing NVIDIA drivers connection was working properly, well, very slow actually, but working...


I'm not good with Nvidia drivers so I've mostly kept away from this thread, but I'll add that issue with slowness maybe related to *swap*.

The Lubuntu installer will either install with *no swap* or a 512MB *swapfile *(depending on how you install, options etc), however depending on your hardware or more so your usage of your box, neither is ideal (*and results in a slow system the moment RAM is required, eg. you have a web browser open*).

Lubuntu's SWAP FAQ page is here - [https://discourse.lubuntu.me/t/swap-and-lubuntu-faq/2591](https://discourse.lubuntu.me/t/swap-and-lubuntu-faq/2591) where you'll see a question "*I’ve installed and only have 512MB of swap, how can I increase the size ?" *contains a link useful if you want to create a *swapfile* (including increase its size).

---

### Post by alexis0b on 2023-02-07
> **guiverc said:**
> I'm not good with Nvidia drivers so I've mostly kept away from this thread, but I'll add that issue with slowness maybe related to *swap*.

The Lubuntu installer will either install with *no swap* or a 512MB *swapfile *(depending on how you install, options etc), however depending on your hardware or more so your usage of your box, neither is ideal (*and results in a slow system the moment RAM is required, eg. you have a web browser open*).

Lubuntu's SWAP FAQ page is here - [https://discourse.lubuntu.me/t/swap-and-lubuntu-faq/2591](https://discourse.lubuntu.me/t/swap-and-lubuntu-faq/2591) where you'll see a question "*I’ve installed and only have 512MB of swap, how can I increase the size ?" *contains a link useful if you want to create a *swapfile* (including increase its size).

Thanks a lot!
I'm stil executing the procedures suggested by chili555, in the previous kernel version of my machine. And since I could use network connection I thought that would have been a good idea to proceed with some required updates of the system but these are taking ages.
Anyway, I will check the swap matter and review what you sent me, thanks again!

---

### Post by alexis0b on 2023-02-07
> **chili555 said:**
> No. 

Run: ```
uname -r 
```Make note of the exact kernel version where networking fails. We'll need that in a moment.

Reboot and interrupt the boot process with the shift key: [https://wiki.ubuntu.com/RecoveryMode#:~:text=With%20BIOS%2C%20quickly%20press%20and,starts%20with%20%22Advanced%20options%22](https://wiki.ubuntu.com/RecoveryMode#:~:text=With%20BIOS%2C%20quickly%20press%20and,starts%20with%20%22Advanced%20options%22).

You will see something like this:

[IMG]https://www.omgubuntu.co.uk/wp-content/uploads/2012/09/grub2-in-ubuntu.jpg[/IMG] 
Press Enter on Advanced Options and you will see a list of two, probably, kernel versions on your system. Use the arrow keys to scroll down to the earlier and press Enter. 

Now does the networking device work? If so, you know that linux-modules-extra *is* installed on that kernel but *not* on the later kernel.

While booted into the earlier kernel version where networking succeeds, do:
```
sudo apt update
sudo apt install --reinstall linux-modules-extra-XXX
```...where XXX is the exact kernel version you found above. For example, you might find 5.19.0-29-generic in uname -r above; that is, where networking fails. So the latter command would then be:

```
sudo apt install --reinstall linux-modules-extra-5.19.0-29-generic
```Reboot and let us know if networking is fixed.

Please post back if you get stuck.

EUREKA!
Finally, I'm happy to say that I'm answering from the Lubuntu machine. It worked, even if it took a lot due to other issue I could fix in the journey.

Thank you very much for your help!
I'm solving the thread!

---

### Post by chili555 on 2023-02-07
> EUREKA!
Finally, I'm happy to say that I'm answering from the Lubuntu machine. It worked, even if it took a lot due to other issue I could fix in the journey.
Awesome! Glad it's woking!

---

### Post by alexis0b on 2023-02-07
> **chili555 said:**
> Awesome! Glad it's woking!

Don't know if it is appropriate to write it here but I am now experiencing very slow internet connection and I found this thread you answered [https://ubuntuforums.org/showthread.php?t=2416215&highlight=increase+network+size](https://ubuntuforums.org/showthread.php?t=2416215&highlight=increase+network+size)
and my results from your suggestion are the following
```

root@alessandro-DESKTOP-TJQ301F:/home/alessandro# lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 002 Device 003: ID 8087:0a2a Intel Corp. Bluetooth wireless interface
Bus 002 Device 002: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 258a:1007 SINOWEALTH Wired Gaming Mouse
Bus 003 Device 002: ID 046d:c335 Logitech, Inc. G910 Orion Spectrum Mechanical Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
root@alessandro-DESKTOP-TJQ301F:/home/alessandro# lsmod | grep rtl8
root@alessandro-DESKTOP-TJQ301F:/home/alessandro# 

```

Suggestions?
Thanks

---

### Post by chili555 on 2023-02-08
The thread you linked has nothing whatever to do with your situation. You have no Realtek USB wireless; yours is an Intel PCI device.

I assume that your slow speeds are wireless. Many device and driver combinations, along with Network Manager, struggle to stay reliably connected. Before anything else, consider these steps.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. 

Your wireless may be dropping or slow because of power management; that is, the feature where the card partially powers down to save battery power during periods of inactivity and then, ideally, powers back up seamlessly when activity resumes. Let's disable power saving to see if it helps. From the terminal:

```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```Your wireless may be dropping or slow because there are two wireless access points with the same name and password. This is typical when you have a 2.4 gHz segment and a 5 gHz segment of the same router. Your wireless may be roaming, looking for a better connection. If this is the case, I suggest that you rename the access points; something like myrouter2.4 and myrouter5.

Then connect to the faster of the two, the 5 gHz segment.

After making these changes, reboot the router.

---

### Post by alexis0b on 2023-02-08
> **chili555 said:**
> The thread you linked has nothing whatever to do with your situation. You have no Realtek USB wireless; yours is an Intel PCI device.

I assume that your slow speeds are wireless. Many device and driver combinations, along with Network Manager, struggle to stay reliably connected. Before anything else, consider these steps.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. 

Your wireless may be dropping or slow because of power management; that is, the feature where the card partially powers down to save battery power during periods of inactivity and then, ideally, powers back up seamlessly when activity resumes. Let's disable power saving to see if it helps. From the terminal:

```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```Your wireless may be dropping or slow because there are two wireless access points with the same name and password. This is typical when you have a 2.4 gHz segment and a 5 gHz segment of the same router. Your wireless may be roaming, looking for a better connection. If this is the case, I suggest that you rename the access points; something like myrouter2.4 and myrouter5.

Then connect to the faster of the two, the 5 gHz segment.

After making these changes, reboot the router.

Ok thanks a lot!
I don't know exactly which one of these steps has worked but I've performed them while downloading in STEAM and after your modification things have changed substantially (from the previous 100s Kb/s to the current 4-6 Mb/s)
This way the wifi is ok

I also have ethernet connection on this pc (kept the cable disconnected while applying your suggestions) and it is equally slow (to be noticed that I use an extender for the ethernet cable since the router is in another room). What could I do for this? Similar steps can be performed?

---

### Post by chili555 on 2023-02-09
> I use an extender for the ethernet cable since the router is in another roomIf you walk your laptop into the same room with the router and connect directly, is the behavior improved? If it is, then I suspect either the extender or the cable.

What is the brand and model of the extender?

---

### Post by kshepherd on 2023-03-20
Thank You alexis0b !!! 
I had a similar problem when I upgraded to kernel 5.19 and your procedure fixed it for me.
Specifically my ethernet kernel module was missing (atheros/alx.ko) and my nvidia kernel module would not load (470).
I grub loaded kernel 5.15, and ran:
sudo apt update
sudo apt install --reinstall linux-modules-extra-5.19.0-35-generic
and now I can boot the new kernel.

Thank You alexis0b !!!

---

