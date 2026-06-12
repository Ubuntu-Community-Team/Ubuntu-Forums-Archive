---
title: "Ethernet not connecting gigabyte motherboard"
date: 2016-12-21
forum: Networking &amp; Wireless
---

### Post by Jesse_Johnson on 2016-12-21
Motherboard is gigabyte ga-970 gaming 

Ethernet Bigfoot killer e2200

After fresh install the Ethernet does not work

---

### Post by jeremy31 on 2016-12-21
What version of Ubuntu and please post results from terminal for ```
uname -a; lspci -nnk | grep -iA2 net
```

---

### Post by oldfred on 2016-12-21
Your model Gigabyte needs boot parameter(s). And IOMMU settings in UEFI.

 Some Gigabyte boards need acpi=off boot parameter also
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU GRUB_CMDLINE_LINUX="iommu=soft"
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[http://ubuntuforums.org/showthread.php?t=2292025](http://ubuntuforums.org/showthread.php?t=2292025)
[http://ubuntuforums.org/showthread.php?t=2242023](http://ubuntuforums.org/showthread.php?t=2242023)
[SOLVED] GA-970A-DS3P revision 1 no usb 3.0
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370)

---

### Post by jsmcclure on 2017-07-23
I hope that this is still of some use, at least to people that are able  to locate this thread in the future. The E2200 Killer Network device,  actually, is not the culprit when it comes to the networking issues that  people are experiencing on Linux. It is the motherboard itself. Here  are the steps that I took to get my Network device to finally start  working. *This is achieved on Ubuntu 17.04.*

**Step 1:  **Edit the Grub file.

You will do this by opening up the terminal, going into sudo, and typing

```
nano /etc/default/grub
```

You then need to edit a single line to add "iommu=soft". It should look like

```
GRUB_CMDLINE_LINUX="iommu=soft"
```

Save the file.

**Step 2:  **Change the BIOS

Restart your computer and enter the BIOS.

Navigate to the peripherals section and disable IOMMU.

Save and exit.

**Step 3:  **Enjoy!

*Please  note, however, that it needs to be done in the order listed. Disabling  IOMMU in the BIOS prior to editing the Grub file will, in fact, enable  your networking. It will also disable your USB devices (keyboard, mouse,  etc.). That is why the Grub file needs to have that line edited first.*

---

### Post by praseodym on 2017-07-24
I think you forgot
```

sudo update-grub
```
after saving the file

---

