---
title: "Broadcom 4312"
date: 2014-05-04
forum: Networking &amp; Wireless
---

### Post by Kevin_Rockitter on 2014-05-04
I installed lubuntu 14.04 on my wifes old netbook. I cannot get the wireless to work. Initially installed STA dirver but it did not work. I then removed it and installed the b43 driver. Synaptice Package Manager shows that firmware-b43-lpphy-installer and b43-fwcutter are installed and that bcmwl-kernel-source is not installed.

            
                        Yet when I go to the additional drivers screen is says that Broadcom BCM4312 is not working and is using bcmwl-kernel-source (which I know is not installed). It also shows "unknown device" and gives me the option to continue using manually installed driver. If I try to do so, nothing happens. There is also a greyed out option that says using non-free firmware for linux kernel from linux-firmware-non-free.  It is not a blacklist issue either.

            
            Any help would be appreciated. I am at my wits end and the wife is threatening to go buy a windows computer.

---

### Post by Rex Bouwense on 2014-05-04
Does this help?
[http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by Kevin_Rockitter on 2014-05-04
Unfortunately, no.  The correct low power driver is installed, but for some reason the wireless network adapter is not using it.  This is really driving me crazy.

---

### Post by Hadaka on 2014-05-04
Hi Kevin, you can pretty much just ignore additional drivers
as it is rarely accurate. please post the following..
```
uname -a
lspci -nnk | grep -iA3 net
lsmod
rfkill list all
cat /etc/modules
cat /etc/network/interfaces
```
thanks.

---

