---
title: "Qualcomm Atheros 9569"
date: 2014-01-31
forum: Networking &amp; Wireless
---

### Post by Castania on 2014-01-31
Hi.  Just got a Dell Inspiron 15i with an Atheros 9569 wireless card.

lspci reports
02:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)

iwconfig reports there are no wireless extensions.

There is a physical button {fn - F2}.  Under Xubuntu, it toggles the Bluetooth on the Indicator Plugin.

Now, at [http://wireless.kernel.org/en/users/Drivers/ath9k#Enabling_ath9k](http://wireless.kernel.org/en/users/Drivers/ath9k#Enabling_ath9k), it appears they have what I need.  But, it says

"To enable ath9k, you must first enable mac80211 through *make menuconfig*  when compiling your kernel. If you do not know what this means then  please learn to compile kernels or rely on your Linux distribution's  kernel. Below are the options you need to enable ath9k through *make menuconfig*."

At that point . . . I'm lost.  I've never compiled a kernel.  I've never needed to compile a kerneI.  And I'm not sure it'll be a recurring skillset need in my life.  This is only the third linux laptop I've owned in 10 years.  They work . . . until they wear out.  Still, I'm willing to do the work, but just don't know what to do.  

If anyone can assist . . . maybe with a step-by-step . . . I'd be grateful.  Or, of course . . . if someone knows an easier path . . . I'll try it.  If it gets too messed up, I can always reinstall.

Ken

---

### Post by chili555 on 2014-01-31
We ought to see the pci.id for your device. Let's see:```
lspci -nn
```The -nn flag will give us the numbers we need. Let's also see what Ubuntu version you've installed:```
lsb_release -d
```

I promise we won't compile a kernel. It's too late here and I want to crack this case before bed time!

---

### Post by Castania on 2014-01-31
I'm using
Description:    Ubuntu 12.04.4 LTS

Here is the result from lspci -nn

00:00.0 Host bridge [0600]: Intel Corporation 3rd Gen Core processor DRAM Controller [8086:0154] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04)
00:16.0 Communication controller [0780]: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 [8086:1e3a] (rev 04)
00:1a.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 [8086:1e10] (rev c4)
00:1c.1 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 [8086:1e12] (rev c4)
00:1d.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation HM76 Express Chipset LPC Controller [8086:1e59] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] [8086:1e03] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller [8086:1e22] (rev 04)
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
02:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)

---

### Post by chili555 on 2014-01-31
I  believe ath9k is installed and I think it should cover your device. What does this tell us?```
modinfo ath9k | grep 0036
```If you get this:> alias:          pci:v0000168Cd0000[COLOR="#FF0000"]0036[/COLOR]sv*sd*bc*sc*i*Then you have all you need. Load the driver:```
sudo modprobe ath9k
```See if a wireless interface is created:```
iwconfig
```Is the switch set correctly?```
rfkill list all
```Does it scan?```
sudo iwlist wlan0 scan
```

---

### Post by Castania on 2014-01-31
Okay.  Here's what I got:

modinfo ath9k | grep 0036   returned nothing -- without the pipe/grep, I get

filename:       /lib/modules/3.2.0-58-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     5396C6B49418C30B65FDBC1
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
vermagic:       3.2.0-58-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int

iwconfig:

lo        no wireless extensions.
eth0      no wireless extensions.


rfkill list all

0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


Now -- I played around with ndiswrapper using the original Dell provided windows WLAN drivers.  Ndisgtk says that the athw8x hardware is present.  I did a depmod -a and a modprobe ndiswrapper.

ndiswrapper -l reports

athw8x : driver installed
    device (168C:0036) present

I can start over if needed . . .

---

### Post by chili555 on 2014-01-31
ndiswrapper is a last ditch method. If it were going to work correctly, you wouldn't be asking here; it would be working. I'd remove it:```
sudo ndiswrapper -e athw8x
```Your 3.2.0-xx kernel doesn't yet have the relatively new device included. You can install a later kernel or the backported driver as at post #4 here: [http://ubuntuforums.org/showthread.php?t=2190930](http://ubuntuforums.org/showthread.php?t=2190930)

I'm really surprised that 12.04.4 uses kernel version 3.2.0-xx. I understood it was using 3.11 or so.

Which method do you prefer?

---

### Post by Castania on 2014-01-31
probably a later kernel . . . I'd half way throught about going with salamander instead of penguin . . . . would 13.10 have what I need?  

Scratch that . . . if you can help me get that proper kernel and get it going . . . I and many other Dell owners would be most grateful!

---

### Post by Castania on 2014-01-31
oh . . . and i removed that driver with 

sudo ndiswrapper -e athw8x

---

### Post by chili555 on 2014-01-31
Certainly 13.10 would do it. Here is my modinfo:```
filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     9960BB0B644BE14E4A2F42B
alias:          platform:qca955x_wmac
alias:          platform:ar934x_wmac
alias:          platform:ar933x_wmac
alias:          platform:ath9k
alias:          pci:v0000[COLOR="#FF0000"]168C[/COLOR]d0000[COLOR="#FF0000"]0036[/COLOR]sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000037sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv*sd*bc*sc*i*
<snip>
```You can certainly try the live DVD and be sure. If it all works as expected, install and be all set in about 15 minutes.

---

### Post by Castania on 2014-01-31
I'm on it!  Probably be tomorrow before I get back to you.  It's almost midnight on the east coast . . . 

thanks for your help.  much, much appreciated.

---

### Post by chili555 on 2014-01-31
But if you prefer a later kernel, get this: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-raring/)

Your device is covered mid-3.8 and later. Download the image, headers and all appropriate to your architecture; either 32- or 64-bit. Install:```
cd ~/Desktop   [COLOR="#FF0000"]<--assuming that's where you downloaded the debs.[/COLOR]
sudo dpkg -i linux*.deb
```Reboot and enjoy.

---

### Post by chili555 on 2014-01-31
> **Castania said:**
> I'm on it!  Probably be tomorrow before I get back to you.  It's almost midnight on the east coast . . . 

thanks for your help.  much, much appreciated.I'll check back tomorrow.

---

### Post by Castania on 2014-02-01
Chili555

That was it!  Since this was a new computer with a new install, I just dl'ed Saucy and installed on top of 12.04 LTS.  

13.10 came with the later kernel and recognized the Atheros 9569 right on install; I didn't have to do anything but use network manager to switch from wire to wireless.

If you ask me, that's an easy solve.

My thanks to you, kind sir.  I hope someday I may repay the favor.

Ken Castania
New Bern, NC, USA

---

### Post by chili555 on 2014-02-01
Awesome! Glad it's working. Have fun!

---

