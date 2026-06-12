---
title: "No kernel modesetting drivers detected"
date: 2011-02-02
forum: New to Ubuntu
---

### Post by migrate from windows on 2011-02-02
Hi
I have ubuntu 10.10   installed in my old pc withIntel 82845g/gl (brookdale chipset) it works well with VESA driver .but cannot run fullscreen videos. When i try to enable intel driver I get this message in the xorg log " 

(EE) Intel(0): No kernel modesetting drivers detected

unloading module intel 

Then boots to text mode 
can anyone help

adding i915.modeset=1 in grub did not work

apt update,upgrade everything done

please help.......Trying to wean of from microsoft..this issue is pushing me back to its feet :-)

---

### Post by cariboo on 2011-02-02
What version are you using?

---

### Post by migrate from windows on 2011-02-03
ubuntu 10.10 Kernel 2.6.35

---

### Post by migrate from windows on 2011-02-08
Thnx everybody after weeks of sleepless nights and dreams about kernels...driver $%$*&$   

finally fixed it ...the problem was with ACPI  

Had to add 
GRUB_CMDLINE_LINUX="acpi=force"

to etc/default/grub  
seems like enabling  kms is dependent on ACPI indirectly 


Finally smiling

---

### Post by HendyIrawan on 2011-03-07
> **migrate from windows said:**
> finally fixed it ...the problem was with ACPI  

Had to add 
GRUB_CMDLINE_LINUX="acpi=force"

to etc/default/grub  
seems like enabling  kms is dependent on ACPI indirectly

THANK YOU 'migrate from windows' !!! You are a savior !!

I also had similar problem (Ubuntu 10.10 Maverick Meerkat) but now works fine after adding to GRUB2:


 acpi=force
 

:guitar:



My hardware:

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1e.2 Multimedia audio controller: Intel Corporation 82801G (ICH7 Family) AC'97 Audio Controller (rev 01)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
 
Similar problem in Launchpad Bug #661645 :
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/661645](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/661645)

---

