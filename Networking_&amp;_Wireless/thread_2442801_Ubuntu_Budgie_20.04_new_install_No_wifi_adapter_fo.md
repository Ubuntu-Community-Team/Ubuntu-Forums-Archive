---
title: "Ubuntu Budgie 20.04 new install No wifi adapter found"
date: 2020-05-07
forum: Networking &amp; Wireless
---

### Post by wichura2 on 2020-05-07
Hi,

I've installed a brand new Budgie 20.04 LTS but I keep getting this:** No wifi adapter found. **I've already tried a dozen solutions found on the Internet before coming here, but with no success thus far.

I tried this too: [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

I've installed the distro in parallel to Windows 10 (wifi works there just fine). Laptop: HP Pavilion (some old crap from 2015).

I reinstalled thrice now - with 3rd party software and without. Nothing. 

Any clue how I could resolve this bitch of an issue? :( 

> lspci -nn

08:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM43142 802.11b/g/n [14e4:4365] (rev 01)
09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL810xE PCI Express Fast Ethernet controller [10ec:8136] (rev 08)
0a:00.0 3D controller [0302]: NVIDIA Corporation GM108M [GeForce 840M] [10de:1341] (rev a2)


---

### Post by mörgæs on 2020-05-07
Hi, welcome to the fora.
Please see here: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

### Post by wichura2 on 2020-05-08
> **mörgæs said:**
> Hi, welcome to the fora.
Please see here: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

Hi, thank you for your reply, hello, and sorry for being trigger happy :) With regards to your instruction, I followed it:
1/ did this [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)
2/ then this [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

and nothing still :(

Some more info re hardware:

> ##### lspci #############################

08:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    DeviceName: Broadcom BCM43142 802.11bgn 1x1 WiFi Adapter + BT 4.0 combo adapter
    Subsystem: Hewlett-Packard Company BCM43142 802.11b/g/n [103c:2230]

09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL810xE PCI Express Fast Ethernet controller [10ec:8136] (rev 08)
    DeviceName: Realtek PCIe FE Family Controller
    Subsystem: Hewlett-Packard Company RTL810xE PCI Express Fast Ethernet controller [103c:2281]

I'm starting to think that this is some yet another unique case, although I'm not vain at all and I'd rather not be unique in this case :)

---

### Post by chili555 on 2020-05-08
> 
1/ did this [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)
2/ then this [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

*and nothing still *It's not supposed to fix anything; it's supposed to produce a diagnostic report that you post so that we can see and then propose a solution. Please post the report.

---

### Post by wichura2 on 2020-05-08
> **chili555 said:**
> It's not supposed to fix anything; it's supposed to produce a diagnostic report that you post so that we can see and then propose a solution. Please post the report.

Welp, I'm relatively new to this :)

There you go - see attachment.

---

### Post by chili555 on 2020-05-08
What is the exact response to the terminal command:

```
sudo modprobe wl
```

...after you've disabled Secure Boot in the BIOS/EFI?

---

### Post by wichura2 on 2020-05-11
Hi again, once I disable secure boot, the wifi seems to work. The qn is: can it be fixed with secure boot enabled?

There's no response to sudo modprobe wl, and I mean I type it, press enter and the console just shows another empty command line.

---

### Post by chili555 on 2020-05-11
> The qn is: can it be fixed with secure boot enabled?Please check here: [https://askubuntu.com/questions/760671/could-not-load-vboxdrv-after-upgrade-to-ubuntu-16-04-and-i-want-to-keep-secur](https://askubuntu.com/questions/760671/could-not-load-vboxdrv-after-upgrade-to-ubuntu-16-04-and-i-want-to-keep-secur)

---

