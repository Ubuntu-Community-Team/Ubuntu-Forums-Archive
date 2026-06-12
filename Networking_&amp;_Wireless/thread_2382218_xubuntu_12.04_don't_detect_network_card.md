---
title: "xubuntu 12.04 don't detect network card"
date: 2018-01-10
forum: Networking &amp; Wireless
---

### Post by symoleon on 2018-01-10
I'm upgrade xubuntu with apt-get upgrade command and after that my linux don't detect network card

---

### Post by Hadaka on 2018-01-10
Hi, Ubuntu 12.04 reached end of life / support Ubuntu 12.04 LTS -April 2017.
[TABLE]
[TR]
[TD][/TD]
[TD][/TD]
[/TR]
[/TABLE]
Suggest you load Ubuntu 14.04 or 16.04  [Load new not upgrade]
~OR
*If you dont care that your os is expired and may have issues..
we can maybe help you get the wifi going.
Please open a terminal ctrl/alt/t then Copy and paste the following command
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info 
```
This command writes a file to your home directory.The file name is wireless-info.tx
From your directory please copy,paste and post the **wireless-info.txt**
Thanks.

---

### Post by symoleon on 2018-01-10
But I don't have internet connection

---

### Post by Hadaka on 2018-01-10
No problem, please post the output of...
```
lspci -n | awk '/0280/'
```
Thanks.

---

### Post by symoleon on 2018-01-10
I download wirless-info on other computer and it works

---

### Post by Hadaka on 2018-01-10
Ok, we see you have been busy attempting to get it going..

you loaded a broadcom driver.."Kernel modules: wl" broadcom-kernel-source...you dont have a broadcom wifi card.
you have ..**[COLOR=#ff0000]'[/COLOR]**Qualcomm Atheros QCA9565**[COLOR=#ff0000]'[/COLOR]**[COLOR=#ff0000][/COLOR] / AR9565 Wireless Network Adapter [168c:0036]

# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1c.3/0000:09:00.0 (**[COLOR=#ff0000]ath9k[/COLOR]**)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

Open a terminal..ctrl/alt/t.. and do..
```
sudo apt-get remove --purge bcmwl-kernel-source
```
```
sudo modprobe -rf ath9k
sudo modprobe -v ath9k
```
*Good luck

---

### Post by symoleon on 2018-01-10
when i do ```
sudo modprobe -rf ath9k
sudo modprobe -v ath9k
```
I have 
```
FATAL: Module ath9k not found
```

Do you know why?

---

### Post by symoleon on 2018-01-10
I want install newer verison of ubuntu but it isn't my computer

---

### Post by Hadaka on 2018-01-10
Hi, It's not logical to attempt to get your wifi working on an expired Ubuntu 12.04
operating system with zero internet access. Obviously the wireless is not working
and I am guessing you have no hard wired access to a working internet connected
router. Other than load a supported operating system, I have no further suggestions.
Good Luck.

---

### Post by jeremy31 on 2018-01-10
Lets see if the module is present in any kernel
```
locate ath9k.ko
```
Your wifi card is fairly new so I would expect that the computer shouldn't have any issues running 14.04 or 16.04

---

### Post by jeremy31 on 2018-01-10
Lets see if the module is even present in any kernel
```
locate ath9k.ko
```
Your wifi card is fairly new so I would expect that the computer shouldn't have any issues running 14.04 or 16.04

---

### Post by symoleon on 2018-01-11
How can i install ubuntu 16.04 without lose data?

i do 
```
locate ath9k.ko
```
and i have this output:
```

/lib/modules/3.2.0-101-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
/lib/modules/3.2.0-111-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
/lib/modules/3.2.0-126-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
/lib/modules/3.2.0-121-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko

```

Before i use
```
apt-get upgrade
```
my wireless worked without any problems

---

### Post by jeremy31 on 2018-01-11
Post results for ```
modinfo /lib/modules/3.2.0-121-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
```
Are you on an extended service plan for Ubuntu 12.04?
You could likely use the grub menu at boot to boot into the 3.2.0-121 kernel and have wifi

---

### Post by symoleon on 2018-01-11
modinfo resaults:

```
filename:       /lib/modules/3.2.0-121-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k.kolicense:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     B6496E46DA9513077CA606E
alias:          platform:ar934x_wmac
alias:          platform:ar933x_wmac
alias:          platform:ath9k
alias:          pci:v0000168Cd00000037sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000033sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000030sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        ath9k_hw,ath9k_common,mac80211,cfg80211,ath
intree:         Y
vermagic:       3.2.0-121-generic-pae SMP mod_unload modversions 686 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

```

I don't know. I've got this laptop with installed ubuntu

---

### Post by symoleon on 2018-01-13
How can i configure grub to boot other system?

---

### Post by Hadaka on 2018-01-13
Hi..to boot to an older kernel..
*Turn off the computer
*Turn the computer back on while pressing and holding down the SHIFT key
*The computer will boot into the grub recovery mode
*Down arrow to Older Linux Kernel versions..press Enter
*Down arrow to an older kernel and press enter
*The computer will boot to that older kernel
Let us know if you can now get online.
Thanks.

---

### Post by symoleon on 2018-01-15
I run 3.2.0-121-generic-pae and in connections I have unsupported device

---

### Post by symoleon on 2018-01-17
I decided to install xubuntu 16.04 :D

---

### Post by Hadaka on 2018-01-17
Is the wifi working correctly now ?

---

### Post by symoleon on 2018-01-19
Thanks so much.
I installed xubuntu 16.04 and all works :D

---

