---
title: "First-time Wi-Fi setup"
date: 2015-01-16
forum: Networking &amp; Wireless
---

### Post by James_McAuliffe on 2015-01-16
Hi,
I'm completely new to any form of Linux whatsoever and so I've installed  Xubuntu, and I can't seem to get the wireless working. I'm using a  Belkin Play Wireless USB Adapter.
Following chapter 7 of the documentation tells me: 
> "If you are connecting to a wireless network for the   first time, security details may be needed. If so, a dialog box will   open. In most cases, the security type will be detected automatically.   If not, select the security type from the *Wi-Fi Security* drop-down box, enter the authentication details and press **Connect**."


 
Yet I can't seem to see a connect button of any sort. Moving on to the  troubleshooting section I'm told to click the NetworkManager icon and  check "enable wi-fi", but no such option exists either. :S

Wat do?

---

### Post by JeQhdMD on 2015-01-16
Your adapter may not be compatible "out of the box".  So, you can go to Belkin's website and see if any drivers offered for Linux . . . OR . . . you can purchase an inexpensive but known compatible adapter.

See this thread for a similar situation and note the last post:   [http://ubuntuforums.org/showthread.php?t=2259513](http://ubuntuforums.org/showthread.php?t=2259513)

---

### Post by DuckHook on 2015-01-16
> **James_McAuliffe said:**
> ...I'm using a Belkin Play Wireless USB Adapter....Hi James_McAuliffe and welcome to Linux, Xubuntu and the forums.

Please don't double post as it dilutes efforts to help (we helpers end up chasing too many rabbits). If you don't get a response after 24 hrs, just bump the old thread to top of page.

Let's assume the simple things first and only move on to more complex if needed:

Network Manager button should invoke a pull down menu. One entry should read "wired connection 1" (assuming you have a wired Ethernet connection) and another entry should be for wireless, which varies in description, depending on what SSID you've given your wireless network. You have to click on this entry to bring up the *connection* dialogue.

If nothing but the "wired connection 1" entry is present, then click edit>add and fill in the name of your SSID and your WPA password (you are using WPA, right?). Rest is self-explanatory. Close all dialogues.

If nothing happens post back and we go to second stage.

PS Getting late here and I will be signing off soon. If you don't hear back from me immediately, this will be why.> **JeQhdMD said:**
> Your adapter may not be compatible "out of the box"...Let's not jump to this conclusion too quickly. The referenced thread refers to a known problematic adaptor using the Broadcom chipset. We don't know what chipset is in OP's system. His problem may simply be not knowing how to navigate through the menus, or it may be something more. Even if more, these things can usually be solved by loading the proper Linux module.

@OP

If above doesn't work, please open a terminal, then cut, paste and run the following commands and post results back to this thread:```
lsusb
``````
lspci -nnk | grep -iA2 net
```

---

### Post by James_McAuliffe on 2015-01-16
Thanks for the response. I have no ethernet (browsing on my Win7 partition), and there was no wireless connection. Filling in the wireless details didn't seem to do anything. I tried the commands, here's the output:

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 050d:615a Belkin Components F7D4101 / F9L1101 802.11abgn Wireless Adapter [Broadcom BCM4323]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c51a Logitech, Inc. MX Revolution/G7 Cordless Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:0752 Microsoft Corp. Wired Keyboard 400
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 09)
    Subsystem: ASUSTeK Computer Inc. P8H77-I Motherboard [1043:8505]
    Kernel driver in use: r8169

---

### Post by sandyd on 2015-01-16
> **DuckHook said:**
> 
Please don't double post as it dilutes efforts to help (we helpers end up chasing too many rabbits). If you don't get a response after 24 hrs, just bump the old thread to top of page.


FTR: I have closed other thread

---

### Post by ajgreeny on 2015-01-16
See the sticky thread at [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110) for problems such as yours with broadcom chipsets.

Come back again if that does not work or you don't understand what it says.

---

### Post by slickymaster on 2015-01-16
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by Rob Sayer on 2015-01-16
> **JeQhdMD said:**
> Your adapter may not be compatible "out of the box".  So, you can go to Belkin's website and see if any drivers offered for Linux . . . OR . . . you can purchase an inexpensive but known compatible adapter.

See this thread for a similar situation and note the last post:   [http://ubuntuforums.org/showthread.php?t=2259513](http://ubuntuforums.org/showthread.php?t=2259513)

After a search I have to agree ... actually I'd go further.  Users of older ubuntu releases couldn't even get ndiswapper to work with that adapter.

Ndiswrapper is a last ditch Hail Mary Pass solution.  If using windows drivers worked all that well, why wouldn't everyone just do that instead of coming up with open source drivers?  If there's anything I know about computer programmers it's that they don't like reinventing the wheel.

I'm afraid my recommendation is getting a wireless adapter that is supported in linux.

---

### Post by James_McAuliffe on 2015-01-16
Okay, I tried running the command lspci -nn -d 14e4: but nothing happened. No error message, no output.

---

### Post by ajgreeny on 2015-01-16
> **James_McAuliffe said:**
> Okay, I tried running the command lspci -nn -d 14e4: but nothing happened. No error message, no output.
If that is exactly how you typed the command it was incorrect, I'm afraid.
You need ```
lspci -nnk | grep -iA2 net
```
Note the | mark which pipes, or sends, the output of lspci -nnk to grep, which itself reports only lines containing [B]-iA2 net

[/B]Try again.

---

### Post by chili555 on 2015-01-16
>  ID [COLOR="#FF0000"]050d:615a[/COLOR] Belkin Components F7D4101 / F9L1101 802.11abgn Wireless Adapter [Broadcom BCM4323]Please see: [http://askubuntu.com/questions/394159/belkin-n600-usb-wireless-adapter-on-ubuntu-12-04](http://askubuntu.com/questions/394159/belkin-n600-usb-wireless-adapter-on-ubuntu-12-04) Please note that the usb.id 050d:615a is identical.

I suggest you try the process I outline there.

---

### Post by chili555 on 2015-01-16
> **ajgreeny said:**
> If that is exactly how you typed the command it was incorrect, I'm afraid.
You need ```
lspci -nnk | grep -iA2 net
```
Note the | mark which pipes, or sends, the output of lspci -nnk to grep, which itself reports only lines containing [B]-iA2 net

[/B]Try again.I believe lspci is for PCI devices; his is USB.

---

### Post by James_McAuliffe on 2015-01-16
>It was incorrect
I can't see any differences. Are you saying there's a typo, or that I'm using the wrong code?

I already have the output of  lspci -nnk | grep iA2 net. I got:

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168]  (rev 09)
    Subsystem: ASUSTeK Computer Inc. P8H77-I Motherboard [1043:8505]
    Kernel driver in use: r8169

[10ec:8168]  (rev 09) is unsurprisingly not on the list.

---

### Post by James_McAuliffe on 2015-01-16
> **chili555 said:**
> Please see: [http://askubuntu.com/questions/394159/belkin-n600-usb-wireless-adapter-on-ubuntu-12-04](http://askubuntu.com/questions/394159/belkin-n600-usb-wireless-adapter-on-ubuntu-12-04) Please note that the usb.id 050d:615a is identical.

I suggest you try the process I outline there.

Unfortunately I can't access Ethernet from where I am.

---

### Post by chili555 on 2015-01-16
I believe ajgreeny made a mistake; yours isn't a Broadcom and your wireless isn't a PCI device; it is USB. lspci-anything tells us nothing useful as relates to your wireless.

I suggest you proceed with the process I linked above.

---

### Post by chili555 on 2015-01-16
> **James_McAuliffe said:**
> Unfortunately I can't access Ethernet from where I am.Are you likely to be somewhere that offers ethernet soon or do we need to download things on a different computer and transfer it?

---

### Post by James_McAuliffe on 2015-01-16
I'm running Xubuntu on a partition so I could transfer the files from Windows (assuming that's possible). No Ethernet any time soon I'm afraid.

---

### Post by chili555 on 2015-01-16
> **James_McAuliffe said:**
> I'm running Xubuntu on a partition so I could transfer the files from Windows (assuming that's possible). No Ethernet any time soon I'm afraid.In order to know which exact versions to download, I need to know the results of:```
uname -r
lsb_release -d
arch
```You can start by getting the Broadcom_bcm43xx_USB_32_64bit_v2_amended.zip file referenced in the link. I suggest you get all the packages, including that, in Windows first, and then we'll move them over all at once.

You can move them over with a USB drive or similar.

---

### Post by James_McAuliffe on 2015-01-16
uname -r:
3.13.0-32-generic

lsb_release -d:
Description: Ubuntu 14.04.1 LTS

arch:
X86_64

---

### Post by chili555 on 2015-01-16
Please downoad ndiswrapper-common here: [http://mirrors.kernel.org/ubuntu/pool/universe/n/ndiswrapper/ndiswrapper-common_1.59-2_all.deb](http://mirrors.kernel.org/ubuntu/pool/universe/n/ndiswrapper/ndiswrapper-common_1.59-2_all.deb) and ndiswrapper-utils-1.9 here: [http://mirrors.kernel.org/ubuntu/pool/universe/n/ndiswrapper/ndiswrapper-utils-1.9_1.59-2_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/universe/n/ndiswrapper/ndiswrapper-utils-1.9_1.59-2_amd64.deb) 

Along with the driver package I reference before, transfer all to the desktop of the Ubuntu machine. First we install the ndiswrapper packages. Open a terminal and do:

```
cd ~/Desktop
sudo dpkg -i ndiswrapper*.deb
```

Right-click the Broadcom driver package and select 'Extract Here.' Now back to the terminal:

```
cd Broadcom_bcm43xx_USB_32_64bit_v2_amended
sudo ndiswrapper -i bcmn43xx64.inf
sudo ndiswrapper -ma
sudo modprobe ndiswrapper
```

You should be all set but, as always, post back if you have trouble or get stuck.

---

### Post by ajgreeny on 2015-01-16
> **chili555 said:**
> I believe lspci is for PCI devices; his is USB.

Whoops! Yes, sorry about that.

It is my fault for coming into this thread and not reading everything written in the posts at the start properly.

---

### Post by chili555 on 2015-01-16
> **ajgreeny said:**
> Whoops! Yes, sorry about that.

It is my fault for coming into this thread and not reading everything written in the posts at the start properly.I believe you have helped me out of an oops or two over the years. We all make them!

No problem!

---

### Post by JeQhdMD on 2015-01-16
> **James_McAuliffe said:**
> I'm running Xubuntu on a partition so I could transfer the files from Windows (assuming that's possible). No Ethernet any time soon I'm afraid.

James, 

Are you saying that Xubuntu is installed on it's own partition (which is normal), on the "SAME" computer where Windows has access to the internet via the same usb wireless adapter (because location of internet source AP)?  Some folks with the right wiring can setup access via powerline ethernet.

  By the way, I have gone through the loading these drivers via the standard linux build process . . . can be a real PITA sometimes . . . so for me, $10 for a plug & play cross -platform wireless adapter is money well spent.  (it can always be used as a backup also for MacOS, Windows or Linux).

---

### Post by DuckHook on 2015-01-16
> **JeQhdMD said:**
>  . . . can be a real PITA sometimes . . . so for me, $10 for a plug & play cross -platform wireless adapter is money well spent.+1

I was waiting for maestro *chili555* to finish working his magic before floating this same suggestion, but you beat me to it. I don't deal with Broadcom stuff if I can help it, and a USB stick that can be replaced for the equivalent of four cups of coffee is just not worth the root canal I must submit to after every install.

---

### Post by James_McAuliffe on 2015-01-16
> **chili555 said:**
> Please downoad ndiswrapper-common here: [http://mirrors.kernel.org/ubuntu/pool/universe/n/ndiswrapper/ndiswrapper-common_1.59-2_all.deb](http://mirrors.kernel.org/ubuntu/pool/universe/n/ndiswrapper/ndiswrapper-common_1.59-2_all.deb) and ndiswrapper-utils-1.9 here: [http://mirrors.kernel.org/ubuntu/pool/universe/n/ndiswrapper/ndiswrapper-utils-1.9_1.59-2_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/universe/n/ndiswrapper/ndiswrapper-utils-1.9_1.59-2_amd64.deb) 

Along with the driver package I reference before, transfer all to the desktop of the Ubuntu machine. First we install the ndiswrapper packages. Open a terminal and do:

```
cd ~/Desktop
sudo dpkg -i ndiswrapper*.deb
```

Right-click the Broadcom driver package and select 'Extract Here.' Now back to the terminal:

```
cd Broadcom_bcm43xx_USB_32_64bit_v2_amended
sudo dpkg -i bcmn43xx64.inf
sudo ndiswrapper -ma
sudo modprobe ndiswrapper
```

You should be all set but, as always, post back if you have trouble or get stuck.


Worked up until here, where I got an error message:



```
james@james-System-Product-Name:~/Desktop/Broadcom_bcm43xx_USB_32_64bit_v2_amended/Broadcom_bcm43xx_USB_32_64bit_v2$ sudo dpkg -i bcmn43xx64.inf
dpkg-deb: error: `bcmn43xx64.inf' is not a debian format archive
dpkg: error processing archive bcmn43xx64.inf (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 bcmn43xx64.inf
```

---

### Post by chili555 on 2015-01-17
Wow! If you want to see an oopsie, there is a big, ugly one! My apologies for my mis-step. Please substitute:```
sudo ndiswrapper -i bcmn43xx64.inf
```In case the searchers see this thread, I will edit my answer, too.

---

### Post by ajgreeny on 2015-01-17
> **chili555 said:**
> Wow! If you want to see an oopsie, there is a big, ugly one! My apologies for my mis-step. Please substitute:```
sudo ndiswrapper -i bcmn43xx64.inf
```In case the searchers see this thread, I will edit my answer, too.
LOL!!! I see what you mean!

---

### Post by James_McAuliffe on 2015-01-18
Seems to have done something, but I'm still getting errors:

```
james@james-System-Product-Name:~/Desktop/Broadcom_bcm43xx_USB_32_64bit_v2_amended/Broadcom_bcm43xx_USB_32_64bit_v2$ sudo ndiswrapper -i bcmn43xx64.inf
[sudo] password for james: 
couldn't find SourceDisksFiles section - continuing anyway...
installing bcmn43xx64 ...
james@james-System-Product-Name:~/Desktop/Broadcom_bcm43xx_USB_32_64bit_v2_amended/Broadcom_bcm43xx_USB_32_64bit_v2$ sudo ndiswrapper -ma
module configuration information is stored in /etc/modprobe.d/ndiswrapper.conf
james@james-System-Product-Name:~/Desktop/Broadcom_bcm43xx_USB_32_64bit_v2_amended/Broadcom_bcm43xx_USB_32_64bit_v2$ sudo modprobe ndiswrappermodprobe: FATAL: Module ndiswrapper not found.
james@james-System-Product-Name:~/Desktop/Broadcom_bcm43xx_USB_32_64bit_v2_amended/Broadcom_bcm43xx_USB_32_64bit_v2$ cd /etc
james@james-System-Product-Name:/etc$ sudo modprobe ndiswrapper
modprobe: FATAL: Module ndiswrapper not found.
james@james-System-Product-Name:/etc$ cd modprobe.d
james@james-System-Product-Name:/etc/modprobe.d$ ls
alsa-base.conf          blacklist.conf           blacklist-framebuffer.conf  blacklist-oss.conf           blacklist-watchdog.conf  iwlwifi.conf  ndiswrapper.conf
blacklist-ath_pci.conf  blacklist-firewire.conf  blacklist-modem.conf        blacklist-rare-network.conf  fbdev-blacklist.conf     mlx4.conf     vmwgfx-fbdev.conf
james@james-System-Product-Name:/etc/modprobe.d$ sudo modprobe ndiswrapper
modprobe: FATAL: Module ndiswrapper not found.

```

---

### Post by chili555 on 2015-01-18
> sudo modprobe ndiswrapper
modprobe: FATAL: Module ndiswrapper not found.Did something go wrong when you installed the ndiswrapper .deb files? Let's check:```
sudo dpkg -s ndiswrapper-common | head -n9
sudo dpkg -s ndiswrapper-utils-1.9 | head -n9
```We hope both are installed correctly.

---

### Post by James_McAuliffe on 2015-01-22
My apologies for the delay, I'm just seeing the back of my exam period now :P
Everything seems to have been installed OK as far as I can tell:

```
james@james-System-Product-Name:~$ sudo dpkg -s ndiswrapper-common | head -n9
[sudo] password for james: 
Package: ndiswrapper-common
Status: install ok installed
Priority: optional
Section: misc
Installed-Size: 72
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Source: ndiswrapper
Version: 1.59-2
james@james-System-Product-Name:~$ sudo dpkg -s ndiswrapper-utils-1.9 | head -n9Package: ndiswrapper-utils-1.9
Status: install ok installed
Priority: optional
Section: misc
Installed-Size: 107
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: ndiswrapper
Version: 1.59-2
james@james-System-Product-Name:~$ 

```

No luck, though.

---

### Post by JeQhdMD on 2015-01-31
Geez . . . why not just get the Panda Ultra N usb wifi dongle for $10 from Amazon . . . isn't your time worth more? (and then you can still try to use ndiswrapper when nothing else going on ., . )

---

