---
title: "Bluetooth quit working after upgrade 14.04 to 15.04"
date: 2015-08-24
forum: Networking &amp; Wireless
---

### Post by joachim_altmann on 2015-08-24
After upgrading from 14.04 to 15.04 bluetooth stopped working on my Lenovo B590. Please find below the output of
uname -a; lspci -nnk | grep -iA2 net; lsusb; dmesg | grep -i bluetooth; dmesg | grep -i firmware; lsmod | grep bluetooth

Linux joachim-Lenovo-B590 3.19.0-26-generic #28-Ubuntu SMP Tue Aug 11 14:16:32 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
02:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Lenovo Device [17aa:0611]
    Kernel driver in use: wl
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
    Subsystem: Lenovo Device [17aa:5002]
    Kernel driver in use: r8169
Bus 004 Device 003: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 004 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 004: ID 04f2:b2fa Chicony Electronics Co., Ltd 
Bus 003 Device 003: ID 105b:e065  
Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[    3.320824] thinkpad_acpi: rfkill switch tpacpi_bluetooth_sw: radio is unblocked
[    0.133975] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored

This is the relevant output of usb-devices
T:  Bus=03 Lev=02 Prnt=02 Port=03 Cnt=01 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=ff(vend.) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=105b ProdID=e065 Rev=01.12
S:  Manufacturer=Broadcom Corp
S:  Product=BCM43142A0
S:  SerialNumber=8056F2DB6F7A
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=01 Prot=01 Driver=(none)
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=01 Prot=01 Driver=(none)
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 0 Cls=fe(app. ) Sub=01 Prot=01 Driver=(none)

In the meantime I installed Ubuntu 15.04 from scratch on a spare partition on the same laptop with exactly the same result. So the reason for this problem is obviously not the upgrade. 

The laptop has a multi-boot including windows 7. Bluetooth is working there without a problem, so - yes, there is not a sign of bluetooth in the commandline-output shown above, but there is a working device under windows. Somehow this does not look right for me &#8230;

Hope somebody's able to help me.

Regards, Jo

---

### Post by joachim_altmann on 2015-09-05
OK, it's working by now, at least on a prototypical basis. The problem has been loading the firmware, this broadcom (BCM43142) chipset needs to load the firmware upon loading the driver. This functionality has been included in the btusb module, but the entry for this very chipset lacked. So, I did the following (in my experimental environment):
Download the kernel sources, change the btusb.c module so that for my chipset the firmware is loaded upon module-load, compile and install the new kernel, extract the firmware from a windows-driver, convert it from hex to hcd and copy it to the correct firmware-directory. Voilá &#8230; Luckily there are instructions for all this available, otherwise I would have been severely stuck :-)
This is a quite convoluted and makeshift solution, but it works &#8230;. I will try to create a true patch for my working environment and publish it here, if anybody has the same problem. Then I will close the Thread as solved.

Regards, Jo

---

### Post by jeremy31 on 2015-09-05
Please file a bug report so this might get fixed
Info on filing bug reports can be found 
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

