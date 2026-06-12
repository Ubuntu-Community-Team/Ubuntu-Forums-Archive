---
title: "Atheros Wifi Adapter Issue | Ubuntu 22.04"
date: 2022-08-19
forum: Networking &amp; Wireless
---

### Post by salambe19 on 2022-08-19
My laptop cannot detect wifi-adapter  after I upgraded to 22.04. Please kindly help. I will be highly obliged.

---

### Post by chili555 on 2022-08-19
Please run and post:

```
lspci -nnk | grep 0280 -A3
sudo dpkg -s linux-modules-extra-$(uname -r) | grep Status
```

---

### Post by salambe19 on 2022-08-19
inshaalam@insha-IdeaPad-3-15ADA05:~$ lspci -nnk | grep 0280 -A3
01:00.0 Network controller [0280]: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter [168c:003e] (rev 32)
    Subsystem: Lenovo QCA6174 802.11ac Wireless Network Adapter [17aa:0827]
    Kernel modules: ath10k_pci, wl
02:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Picasso/Raven 2 [Radeon Vega Series / Radeon Vega Mobile Series] [1002:15d8] (rev cd)



inshaalam@insha-IdeaPad-3-15ADA05:~$ sudo dpkg -s linux-modules-extra-$(uname -r) | grep Status
Status: install ok installed

---

### Post by chili555 on 2022-08-19
Now do:

```
sudo apt purge bcmwl-kernel-source
sudo dmesg | grep ath
rfkill list all
```

---

### Post by salambe19 on 2022-08-19
I am new to this platform and was having troubles in uploading a screenshot here.
Kindly check the output here [https://ibb.co/fDfrd1S](https://ibb.co/fDfrd1S) 
Thanks

---

### Post by chili555 on 2022-08-19
I think that all of the unknown symbol troubles in your dmesg is related to the incorrect Broadcom driver that we removed. Please reboot and show me:

```
sudo dmesg | grep ath
```

---

### Post by salambe19 on 2022-08-19
After rebooting and 
sudo dmesg | grep ath
This is the output [https://ibb.co/sCdFDjD](https://ibb.co/sCdFDjD)

---

### Post by chili555 on 2022-08-19
I suspect that some other wireless driver is interfering. What else have you installed? 

Let's see:

```
sudo dkms status
```

---

### Post by salambe19 on 2022-08-19
I think, yes.     

[https://ibb.co/Z6pCMZd](https://ibb.co/Z6pCMZd)

---

### Post by chili555 on 2022-08-19
Please do:

```
sudo apt purge backport-iwlwifi-dkms
sudo dkms remove rtl8821ce/5.5.2.1 --all
```

Reboot and show us:

```
sudo dmesg | grep ath
```

---

### Post by salambe19 on 2022-08-19
The screenshot after reboot , [https://ibb.co/L9GCrR6](https://ibb.co/L9GCrR6)
The wifi finally works now.
I have been stuck on this for a long time now and without your help it would not have been possible.
Really appreciate your fast and accurate replies.

---

### Post by chili555 on 2022-08-19
Awesome! Glad it's working. Please use thread tools at the top to mark Solved.

#####################################################################

**NOTE TO SEARCHERS**

This thread is a very good example of the problems created when a new user reads some random forum post and installs a driver, only to find that it doesn&#8217;t work and so, after reading another forum, installs another driver that also doesn&#8217;t work.

In this case, as in many, the newly installed driver installs its own slightly modified version of the common helper modules cfg80211 and/or mac80211 which conflict with the versions already installed.

It will never help to install an Intel driver or a Broadcom driver or a Realtek driver for your Atheros wireless chip.

Always be certain that you are installing the correct driver for your device. First, identify it. If it is an internal, PCI device, run:

```
lspci -nnk | grep 0280 -A3

```
Or if it is USB:

```
lsusb
```

An eight digit identifier will be listed like the above:

```
Network controller [0280]: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter [168c:003e] (rev 32)

```
Search with Google or similar for the identifier, in this example,  168c:003e. You will find that the driver is ath10k_pci and is already built in to all modern kernel versions.

The process for USB is very similar.

You can often find references to the correct driver here and at askubuntu.com.

Please save yourself (and me!) trouble and be sure what you have before you install another incorrect, non-working driver.

#####################################################################

---

