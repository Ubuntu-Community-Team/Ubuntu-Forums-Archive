---
title: "Bluetooth turned on but it can't detect devices because of kernel 6.1, Ubuntu 23.04"
date: 2023-04-29
forum: Networking &amp; Wireless
---

### Post by avisaziz123 on 2023-04-29
[COLOR=#000000][FONT=Arial]Yesterday, I installed Ubuntu 23.04 on my computer, but I have been having trouble with the Bluetooth feature. Although Bluetooth is turned on, it does not detect any Bluetooth devices. I tried to install Fedora 38, but the problem persisted. I then went back to Ubuntu 23.04 and attempted to install the Bluetooth driver manually, but still no luck.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Here is the information about my Bluetooth card:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]lsusb | grep -i bluetooth[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Bus 001 Device 007: ID 0a5c:21e6 Broadcom Corp. BCM20702 Bluetooth 4.0 [ThinkPad][/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I also attempted to update the firmware using fwupdmgr, but it did not resolve the issue. Additionally, I tried different kernels to see if that was causing the detection problem. The kernels I tried were:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][0]: v5.19.2-051902[/FONT][/COLOR][IMG]https://ubuntuforums.org/attachment.php?attachmentid=292134&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=292134&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=292134&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=292134&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=292134&stc=1[/IMG]
[COLOR=#000000][FONT=Arial][1]: v5.19.17-051917[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][2]: v6.0.19-060019[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][3]: v6.1.26-060126[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][4]: v6.2.13-060213[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][5]: v6.3.0-060300[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]After trying these kernels, I found that the problem appeared in kernel version 6.1.26, while there was no issue in kernel 6.0.19 or earlier.[/FONT][/COLOR]

My main question is: Am I stuck with kernel 6.0 foerever? as later kernel versions (6.1, 6.2, 6.3) don&#8217;t fix my Bluetooth problem. Alternatively, is there a workaround or solution to fix the issue in kernel versions 6.1 and above?

---

### Post by luizaleixo on 2023-05-02
same issue here
lsusb | grep -i bluetooth
Bus 003 Device 008: ID 05ac:821f Apple, Inc. Built-in Bluetooth 2.0+EDR HCI
Bus 003 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)

---

### Post by morrownr on 2023-05-02
I have the following bt adapter and it is working fine on 23.04:

ID 0a5c:21e8 Broadcom Corp. BCM20702A0 Bluetooth 4.0

My point being that this issue may be specific to certain adapters.

---

### Post by #&amp;thj^% on 2023-05-02
> **morrownr said:**
> I have the following bt adapter and it is working fine on 23.04:

ID 0a5c:21e8 Broadcom Corp. BCM20702A0 Bluetooth 4.0

My point being that this issue may be specific to certain adapters.

+1 All is well here:
```
 lsusb | grep -i bluetooth
Bus 003 Device 008: ID 0b05:17cb_ ASUSTek Computer, _Inc.** Broadcom BCM20702A0 **Bluetooth


```
Forgot to add: " Kernel: 6.2.0-20-generic"

---

### Post by chili555 on 2023-05-02
> I found that the problem appeared in kernel version 6.1.26, while there was no issue in kernel 6.0.19 or earlier.I suggest that you file a bug report: [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by jeremy31 on 2023-05-02
Try ```
cd /lib/firmware/brcm
sudo wget https://github.com/winterheart/broadcom-bt-firmware/raw/master/brcm/BCM20702A1-0a5c-21e6.hcd
```
Reboot

---

### Post by craig108 on 2023-05-09
> **jeremy31 said:**
> Try ```
cd /lib/firmware/brcm
sudo wget https://github.com/winterheart/broadcom-bt-firmware/raw/master/brcm/BCM20702A1-0a5c-21e6.hcd
```
Reboot

This worked for me. Thanks.

---

