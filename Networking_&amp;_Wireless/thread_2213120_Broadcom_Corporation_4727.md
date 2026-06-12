---
title: "Broadcom Corporation 4727"
date: 2014-03-24
forum: Networking &amp; Wireless
---

### Post by elisa2 on 2014-03-24
I know this question has been asked several times but my computer seems to have a little different problem. I have tried everything but couldn't get wifi to work on my ubuntu.
I am using ubuntu lucid. And my laptop is HP pavilion g6.
Please help me with this.

---

### Post by kc1di on 2014-03-25
Hi elisa2  and welcome to Ubuntu Forums,

we need just a little more information to be able to help.  

Could you post the output of these terminal commands:

```
lspci
```

```
rfkill list all
```

That will be a start in sorting it out.

---

### Post by mörgæs on 2014-03-25
Lucid is out of support. Your best option is to begin with a fresh install of something from the 13.10 family.

---

### Post by elisa2 on 2014-03-25
```
lspci
00:00.0 Host bridge: Intel Corporation Device 0104 (rev 09)
00:01.0 PCI bridge: Intel Corporation Sandy Bridge PCI Express Root Port (rev 09)
00:01.1 PCI bridge: Intel Corporation Sandy Bridge PCI Express Root Port (rev 09)
00:01.2 PCI bridge: Intel Corporation Sandy Bridge PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Device 0116 (rev 09)
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 2 (rev b5)
00:1c.2 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 3 (rev b5)
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation Device 1c49 (rev 05)
00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Device 6760
04:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
06:00.0 Class ff00: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)
```


rfkill list all is not giving any output

---

### Post by elisa2 on 2014-03-25
Thanks :). If I don't get any other option then I will install latest version of Ubuntu.

---

### Post by kc1di on 2014-03-25
there was a thread[ here]("http://ubuntuforums.org/showthread.php?t=2124976") that may be of help, 
But as the previous poster said , that's a pretty old copy of Ubuntu and I'm not sure the repositories for it are still active. 
good luck

---

