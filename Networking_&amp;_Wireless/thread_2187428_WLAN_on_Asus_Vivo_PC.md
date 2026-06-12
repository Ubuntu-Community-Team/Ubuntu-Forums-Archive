---
title: "WLAN on Asus Vivo PC"
date: 2013-11-12
forum: Networking &amp; Wireless
---

### Post by thomas-galley on 2013-11-12
Hello,

I just receivced my new computer, an Asus Vivo PC. Everything seems to work fine under Ubuntu 12.04 LTS, with the notable exception of the WLAN... I fortunately can use an old USB WLAN-stick for the time being, but I would of course prefer the chip that comes with the computer. Anyone has any ideas on that?

Thank you very much in advance,

Thomas

---

### Post by praseodym on 2013-11-12
Please open a terminal with CTRl+ALT+T and show the outputs of:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by thomas-galley on 2013-11-12
Here is the output of the commands:

```
Linux tgalley-VM40B 3.8.0-33-generic #48~precise1-Ubuntu SMP Thu Oct 24 16:28:06 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8821]
    Subsystem: ASUSTeK Computer Inc. Device [1043:85b4]
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8554]
    Kernel driver in use: r8169
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0e8d:1806 MediaTek Inc. 
Bus 001 Device 004: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business
Bus 001 Device 005: ID 046d:c05a Logitech, Inc. Optical Mouse M90
Bus 002 Device 003: ID 0b05:17dc ASUSTek Computer, Inc. 
Module                  Size  Used by
nls_utf8               12557  1 
isofs                  40280  1 
rfcomm                 47864  12 
bnep                   18258  2 
parport_pc             28284  1 
ppdev                  17113  0 
coretemp               13596  0 
snd_hda_codec_hdmi     37463  1 
snd_hda_codec_realtek    79916  1 
snd_hda_intel          44339  3 
snd_hda_codec         141761  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
joydev                 17613  0 
hid_generic            12540  0 
snd_hwdep              13668  1 snd_hda_codec
kvm                   455932  0 
usb_storage            61749  1 
snd_pcm               102477  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
usbhid                 47346  0 
hid                   105826  2 hid_generic,usbhid
snd_seq_midi           13324  0 
snd_rawmidi            30417  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61930  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29989  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
ghash_clmulni_intel    13259  0 
btusb                  22431  0 
bluetooth             247165  24 rfcomm,bnep,btusb
i915                  620571  3 
drm_kms_helper         49597  1 i915
snd                    69533  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   287564  4 i915,drm_kms_helper
cryptd                 20501  1 ghash_clmulni_intel
soundcore              12680  1 snd
lpc_ich                17144  0 
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
lp                     17799  0 
i2c_algo_bit           13564  1 i915
psmouse                97873  0 
mei                    41820  0 
parport                46562  3 parport_pc,ppdev,lp
eeepc_wmi              13151  0 
asus_wmi               24581  1 eeepc_wmi
sparse_keymap          13890  1 asus_wmi
video                  19652  2 i915,asus_wmi
microcode              23017  0 
mac_hid                13253  0 
serio_raw              13215  0 
wmi                    19256  1 asus_wmi
r8169                  68716  0 
ahci                   25879  2 
libahci                31606  1 ahci
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```

---

### Post by praseodym on 2013-11-12
Wow, a completely new device, which I haven’t seen before.

Is there a driver CD with a driver, maybe even a Linux driver? Which driver version is it, if any?

---

### Post by wildmanne39 on 2013-11-12
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by thomas-galley on 2013-11-13
Thank you for the hint, Wild Man :-)

---

### Post by thomas-galley on 2013-11-13
There is indeed a CD that even contains a folder linux_drivers, but there is nothing than a text file with a message please upgrade to latest kernel. Tried a live version of 13.10 this morning, same frustrating result. Should I try to install 13.10 and then see with the updates ?

---

### Post by florian.nussmuelle on 2013-11-25
I have exactely the same Problem and already tried to install 13.10 and the newest updates... nothing changed. Still no Wifi connection.

Has anyone figured out a solution yet?

---

### Post by praseodym on 2013-11-25
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Try the latest mainline kernel 3.12

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-saucy/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-saucy/)

You will need allpossible files for 32 and 64bit, respectively. Also the all.deb files. Save them in "Downloads" and install via
```

sudo dpkg -i ~/Downloads/*.deb
```
Reboot.

---

### Post by florian.nussmuelle on 2013-11-25
3.12 didn't help either :(
But thank you anyway!

---

### Post by thomas-galley on 2013-11-27
Hello,

I wrote an email to Asus Support about the problem. All they replied was that they don't support Linux... Well, the way to go if you would like to be embarrassed in front of your customers.

Thanks for the update concerning the 3.12 kernel :-(

---

### Post by praseodym on 2013-11-27
Check:
```

modprobe -c | grep -i "10ec.*8821"
```

---

### Post by thomas-galley on 2013-11-29
Thank you for the help. There simply is no output.

---

### Post by apollothethird on 2013-11-29
> **thomas-galley said:**
> Thank you for the help. There simply is no output.

Hi, Thomas.  Follow the steps provided here substituting your NIC for what is described by Netgear:
[http://faq.apollo3.com/ljames/ubuntu/networksupport](http://faq.apollo3.com/ljames/ubuntu/networksupport)

Basically, as the link described, install the ndiswrapper support and use the windows drivers.  Look for a folder in the Windows install directory that has an *.inf file and load that with the ndiswrapper.  Then you should be good to go.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/~ljames")

---

### Post by praseodym on 2013-11-30
Could you please tell what Realtek driver that is? Maybe we can just add the IDs to a common Realtek driver.

---

### Post by thomas-galley on 2013-12-14
Hello,

I am sorry for having taken so long to respond. Here are the results of my testing. First, I installed [COLOR=#000000]ndiswrapper, then I tried with any of the Windows drivers that I could find on the enclosed DVD. Unfortunately without any result.

Next, I followed the instructions I found on [this site]("http://askubuntu.com/questions/368015/problem-with-building-compiling-a-driver-for-edimax-wireless-adapter-ew-7822uac") and downloaded a driver from [here]("https://github.com/abperiasamy/rtl8812AU_8821AU_linux"). Make and make install worked fine, but still absolutely no result.

I am sorry, I don't have any better news for you. If anyone has still an idea, I am very much open to try it out.

THX for all the support !
[/COLOR]

---

### Post by apollothethird on 2013-12-14
> **thomas-galley said:**
> Hello,

I am sorry for having taken so long to respond. Here are the results of my testing. First, I installed [COLOR=#000000]ndiswrapper, then I tried with any of the Windows drivers that I could find on the enclosed DVD. Unfortunately without any result.

Next, I followed the instructions I found on [this site]("http://askubuntu.com/questions/368015/problem-with-building-compiling-a-driver-for-edimax-wireless-adapter-ew-7822uac") and downloaded a driver from [here]("https://github.com/abperiasamy/rtl8812AU_8821AU_linux"). Make and make install worked fine, but still absolutely no result.

I am sorry, I don't have any better news for you. If anyone has still an idea, I am very much open to try it out.

THX for all the support !
[/COLOR]

Try my suggestion in reply #14.  You'll most likely succeed there.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by thomas-galley on 2013-12-14
> **apollothethird said:**
> Try my suggestion in reply #14.  You'll most likely succeed there.

Hello,

that is exactly what I did first - nothing. The driver will install, but that's all. No connection possible.

---

### Post by apollothethird on 2013-12-14
> **thomas-galley said:**
> Hello,

that is exactly what I did first - nothing. The driver will install, but that's all. No connection possible.

I had the same experience until I performed the steps exact.

I don't mind going over the steps with you to see what is going wrong.  As far as I can see, if the drivers worked in Windows they should work with the ndiswrapper.

If you don't mind going over the steps, could you tell me the name of the inf file and possibly the link to where you downloaded the Windows drivers?

After that I'll have a couple of commands to identify the state of the configuration.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by samuelpiquet on 2013-12-14
Hello,
I'm new to this forum and i'm willing to participate to this thread (and ask for some help) if you're ok with it.
I followed the steps appolothethird mentionned but got the same results than thomas-galley (which means none :) ).

Here is the result of **sudo lshw -class network **:
> 
  *-network NON-RÉCLAMÉ   
       description: Network controller
       produit: Realtek Semiconductor Co., Ltd.
       fabriquant: Realtek Semiconductor Co., Ltd.
       identifiant matériel: 0
       information bus: pci@0000:02:00.0
       version: 00
       bits: 64 bits
       horloge: 33MHz
       fonctionnalités: pm msi pciexpress cap_list
       configuration: latency=0
       ressources: portE/S:e000(taille=256) mémoire:f7d00000-f7d03fff
  *-network
       description: Ethernet interface
       produit: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       fabriquant: Realtek Semiconductor Co., Ltd.
       identifiant matériel: 0
       information bus: pci@0000:03:00.0
       nom logique: eth0
       version: 0c
       numéro de série: ac:22:0b:50:ab:b8
       taille: 100Mbit/s
       capacité: 1Gbit/s
       bits: 64 bits
       horloge: 33MHz
       fonctionnalités: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 ip=192.168.1.2 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       ressources: irq:42 portE/S:d000(taille=256) mémoire:f7c00000-f7c00fff mémoire:f0000000-f0003fff



And **lspci -v** :

> 
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8821
    Subsystem: ASUSTeK Computer Inc. Device 85b4
    Flags: fast devsel, IRQ 255
    I/O ports at e000 [disabled] [size=256]
    Memory at f7d00000 (64-bit, non-prefetchable) [disabled] [size=16K]
    Capabilities: <access denied>

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
    Subsystem: ASUSTeK Computer Inc. Device 8554
    Flags: bus master, fast devsel, latency 0, IRQ 42
    I/O ports at d000 [size=256]
    Memory at f7c00000 (64-bit, non-prefetchable) [size=4K]
    Memory at f0000000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169



Finally **sudo ndiswrapper -l**:

> 
netrtwlane : driver installed
    device (10EC:8821) present


I took the drivers from the asus website located here [https://www.asus.com/ASUS_VivoPC/VivoPC_VC60/#support_Download](https://www.asus.com/ASUS_VivoPC/VivoPC_VC60/#support_Download)
and I installed the Win8X64 drivers located in WiFI_Win7-8-VER1000226/AW_CB161H/WIFI/RTWLANE_Driver/

I don't know if this is enough information.

Thank you for your time and I would be happy to help anyone with anything I can manage :)

---

### Post by apollothethird on 2013-12-14
> **samuelpiquet said:**
> Hello,
I'm new to this forum and i'm willing to participate to this thread (and ask for some help) if you're ok with it.
I followed the steps appolothethird mentionned but got the same results than thomas-galley (which means none :) ).

Here is the result of **sudo lshw -class network **:



And **lspci -v** :




Finally **sudo ndiswrapper -l**:



I took the drivers from the asus website located here [https://www.asus.com/ASUS_VivoPC/VivoPC_VC60/#support_Download](https://www.asus.com/ASUS_VivoPC/VivoPC_VC60/#support_Download)
and I installed the Win8X64 drivers located in WiFI_Win7-8-VER1000226/AW_CB161H/WIFI/RTWLANE_Driver/

I don't know if this is enough information.

Thank you for your time and I would be happy to help anyone with anything I can manage :)

Y0u might have already run it, but please run:

```

$ sudo modprobe ndiswrapper
$ sudo lsusb

```

Show me the output of the two commands.

Also, does the adapter have indicatore light?  If so, do they light up?

Thanks.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by samuelpiquet on 2013-12-14
Hi again,

Thanks for the super fast answer !
Yes I already did the modeprobe command and it did nothing special.
Why do you need the USB devices since it's a builtin wifi device ? Or maybe I'm missing something...
Anyway:
> 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0b05:17dc ASUSTek Computer, Inc. 
Bus 001 Device 004: ID 045e:0780 Microsoft Corp. 
Bus 001 Device 003: ID 046d:c051 Logitech, Inc. G3 (MX518) Optical Mouse
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


In my case, there is no indicator for wifi. Only a useless light for global power and what seems to be a hard drive light monitor...

Thanks again

---

### Post by apollothethird on 2013-12-14
You're right, the USB command isn't necessary.  I forgot this is related to a builtin device.

I'm studying to see what else can be applied.

It took me a long time to get my system working with the windows drivers.  After that I was able to easily repeat it on other computers.  So studying the details I'm hoping I might see something that is just as obvious as the problems I was initially having with my device.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by apollothethird on 2013-12-14
Ok.  I think I might see a potential problem.  I was never able to have success with the Windows 7 drivers.  I had to use the Windows XP drivers with the ndiswrapper on my machine.

Will you give the Windows XP drivers a run for it and tell me how that goes?

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by samuelpiquet on 2013-12-15
I tried XP drivers and I got some errors
> 
sudo ndiswrapper -i netrtwlane.inf
installing netrtwlane ...
couldn't find models section "Realtek" -
installation may be incomplete
couldn't find models section "Lenovo" -
installation may be incomplete
couldn't find models section "ASUS" -
installation may be incomplete
couldn't find models section "Edimax" -
installation may be incomplete

sudo ndiswrapper -l
netrtwlane : invalid driver!


---

### Post by samuelpiquet on 2013-12-15
I also tried the 7 drivers and same result than with 8. I'm trying to find other drivers.

---

### Post by samuelpiquet on 2013-12-15
Hey, found nothing worth mentioning... maybe i'll have to wait for official support...

---

### Post by apollothethird on 2013-12-15
> **samuelpiquet said:**
> I tried XP drivers and I got some errors

No drivers would work on any of the computers that I tried except the XP drivers.  Like you, I had tried the Windows 7 drivers at first because it appeared they would be later and more apt to work.  I kept at it over the course of two days for quiet a few hours.t

Eventually it I got it work the lshw showed the wireless adapter.  I didn't realize at first it was because I had eventually tested the XP drivers.  I tried to duplicate it and spent a long time, and finally realized that it didn't work until I used the XP drivers.  There was some combination of rebooting and using the "-r" parameter to remove the Windows 7 drivers.

When I got it where it worked twice, I went to three other computers.  Two were virtual computers and one was another physical computer and was able to set them up the first time without problems using the steps in the link.  When it worked consistently I tried the Windows 7 drivers.  The Windows 7 drivers consistently failed.  I'll most likely add that part to the FAQ.

I understand why you will test the Windows 7 and 8 drivers.  But you might consider trying only the Windows XP drivers from a fresh boot.

I did a lot of research about tne driver wrapper and the developers believe they will work with the wrapper if it works with Windows.

I didn't specifically install Wine on two of the machines, but might have inadvertently installed it while working with Netflix.  I wrote in the FAQ that wine didn't have to be installed except for a method to extract the driver folder.

Maybe (looking at the errors you got with the XP drivers) the built in adapter is something different and the wrapper is only made for USB.  I'll have to get a hold of a Laptop to experiment with further.

I believe the only new things I have suggested in this current message is that it's not clear to me that you have installed wine (which might not be necessary... but most likely you did), and the that XP drivers test was from a fresh boot without remnants of the Windows 7 and 8 loaded.

By the way, the windows 7 drivers loaded for me without errors.  The adapter just didn't work while the Windows 7 drivers were loaded.

I appreciate your having taken the time to test the steps and help me to learn a little more about the limitations of the ndiswrapper utility.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by thomas-galley on 2013-12-16
> **apollothethird said:**
> I had the same experience until I performed the steps exact.

If you don't mind going over the steps, could you tell me the name of the inf file and possibly the link to where you downloaded the Windows drivers?

After that I'll have a couple of commands to identify the state of the configuration.


Hello,

here goes. I tried out the drivers I found on the enclosed DVD. Actually, there is a whole bunch of drivers for all kinds of Windows flavours. And there seem to be different versions, though I don't know exactly where the difference lies.

The first try was with the drivers in the following directory:

/media/tgalley/VIVOPC/Drivers/BT_WiFi/WIFI_XP/RTWLANE_Driver/WinXP

Each directory contains the files:


[LIST]
[*]netrtwlane.cat
[*]netrtwlane.inf
[*]rtwlane.sys
[/LIST]

This batch of drivers produces the following output:

```

tgalley@tgalley-VM40B:~$ sudo ndiswrapper -i install/driver/netrtwlane.inf 
installing netrtwlane ...
couldn't find models section "Realtek" -
installation may be incomplete
couldn't find models section "Lenovo" -
installation may be incomplete
couldn't find models section "ASUS" -
installation may be incomplete
couldn't find models section "Edimax" -
installation may be incomplete

```

And here the listing:

```

tgalley@tgalley-VM40B:~$ sudo ndiswrapper -l
netrtwlane : invalid driver!

```

Obviously, there was no connectivity, so I removed the driver with ndiswrapper -r

I tried the same procedure with every set of drivers. They seemed to install nicely, there was no error output, and the listing seemed more than OK:

```

tgalley@tgalley-VM40B:~$ sudo ndiswrapper -l
netrtwlane : driver installed
    device (10EC:8821) present

```

But still: No connectivity. I even tried a restart, but still - nothing. I should perhaps mention that bluetooth IS working, strange though it may seem...

Thank you for your support!

Thomas

---

### Post by thomas-galley on 2013-12-16
Hello again!

Two other things:

I did not install Wine.

Here are the last lines from syslog after I removed the USB-Stick and tried to enable the Windowsdriver for the internal Wifi:

```

Dec 16 14:48:24 tgalley-VM40B NetworkManager[657]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/net/wlan0, iface: wlan0)
Dec 16 14:48:24 tgalley-VM40B NetworkManager[657]: <info> (wlan0): device state change: disconnected -> unmanaged (reason 'removed') [30 10 36]
Dec 16 14:48:24 tgalley-VM40B NetworkManager[657]: <info> (wlan0): cleaning up...
Dec 16 14:48:24 tgalley-VM40B NetworkManager[657]: <warn> (3) failed to find interface name for index
Dec 16 14:48:24 tgalley-VM40B NetworkManager[657]: (nm-system.c:766):nm_system_iface_get_flags: runtime check failed: (iface != NULL)
Dec 16 14:48:24 tgalley-VM40B NetworkManager[657]: <error> [1387201704.908448] [nm-system.c:768] nm_system_iface_get_flags(): (unknown): failed to get interface link object
Dec 16 14:48:24 tgalley-VM40B NetworkManager[657]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Dec 16 14:48:24 tgalley-VM40B NetworkManager[657]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Dec 16 14:48:24 tgalley-VM40B NetworkManager[657]: <warn> sysctl: failed to open '/proc/sys/net/ipv6/conf/wlan0/accept_ra': (2) Datei oder Verzeichnis nicht gefunden
Dec 16 14:48:24 tgalley-VM40B NetworkManager[657]: <warn> sysctl: failed to open '/proc/sys/net/ipv6/conf/wlan0/use_tempaddr': (2) Datei oder Verzeichnis nicht gefunden
Dec 16 14:48:24 tgalley-VM40B whoopsie[1010]: offline
Dec 16 14:48:24 tgalley-VM40B NetworkManager[657]: <info> radio killswitch /sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/ieee80211/phy0/rfkill1 disappeared
Dec 16 14:48:25 tgalley-VM40B wpa_supplicant[2201]: Could not read interface wlan0 flags: No such device

```

---

### Post by apollothethird on 2013-12-16
> **thomas-galley said:**
> Hello,

here goes. I tried out the drivers I found on the enclosed DVD. Actually, there is a whole bunch of drivers for all kinds of Windows flavours. And there seem to be different versions, though I don't know exactly where the difference lies.

The first try was with the drivers in the following directory:

/media/tgalley/VIVOPC/Drivers/BT_WiFi/WIFI_XP/RTWLANE_Driver/WinXP

Each directory contains the files:


[LIST]
[*]netrtwlane.cat
[*]netrtwlane.inf
[*]rtwlane.sys
[/LIST]

This batch of drivers produces the following output:

```

tgalley@tgalley-VM40B:~$ sudo ndiswrapper -i install/driver/netrtwlane.inf 
installing netrtwlane ...
couldn't find models section "Realtek" -
installation may be incomplete
couldn't find models section "Lenovo" -
installation may be incomplete
couldn't find models section "ASUS" -
installation may be incomplete
couldn't find models section "Edimax" -
installation may be incomplete

```

And here the listing:

```

tgalley@tgalley-VM40B:~$ sudo ndiswrapper -l
netrtwlane : invalid driver!

```

Obviously, there was no connectivity, so I removed the driver with ndiswrapper -r

I tried the same procedure with every set of drivers. They seemed to install nicely, there was no error output, and the listing seemed more than OK:

```

tgalley@tgalley-VM40B:~$ sudo ndiswrapper -l
netrtwlane : driver installed
    device (10EC:8821) present

```

But still: No connectivity. I even tried a restart, but still - nothing. I should perhaps mention that bluetooth IS working, strange though it may seem...

Thank you for your support!

Thomas

Thanks for the info.

I just got a Lenovo (G570) computer from a customer to configure.  I have finished the Windows work and he has an appointment to pick it up at noon.  I'm going to try, if I have time, to install Ubuntu on a pen drive from his computer and perform the steps for the ndiswapper and let you go.  If the customer comes before I complete the steps, I'll just have to shut the computer down and give it to him.

Hope I have time.  Will give you what I find.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by thomas-galley on 2013-12-16
I forgot... Here is the output from sudo modprobe ndiswrapper:

```

Dec 16 15:08:20 tgalley-VM40B kernel: [ 1907.915666] ndiswrapper: module verification failed: signature and/or required key missing - tainting kernel
Dec 16 15:08:20 tgalley-VM40B kernel: [ 1907.915684] Disabling lock debugging due to kernel taint
Dec 16 15:08:20 tgalley-VM40B kernel: [ 1907.916860] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
Dec 16 15:08:20 tgalley-VM40B kernel: [ 1907.954190] usbcore: registered new interface driver ndiswrapper

```

---

### Post by apollothethird on 2013-12-16
> **thomas-galley said:**
> I forgot... Here is the output from sudo modprobe ndiswrapper:

```

Dec 16 15:08:20 tgalley-VM40B kernel: [ 1907.915666] ndiswrapper: module verification failed: signature and/or required key missing - tainting kernel
Dec 16 15:08:20 tgalley-VM40B kernel: [ 1907.915684] Disabling lock debugging due to kernel taint
Dec 16 15:08:20 tgalley-VM40B kernel: [ 1907.916860] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
Dec 16 15:08:20 tgalley-VM40B kernel: [ 1907.954190] usbcore: registered new interface driver ndiswrapper

```

Thanks.

Unfortunately, at this time I can't test adding support on this Laptop because it's already there when I boot up to the Ubuntu installation disk.  I'll have to keep in mind to run a test every time I get a Laptop until I find one that needs the wrapper.

By the way, while it's probably not neccesary, I don't recall you mentioning if you "apt-get" installed wine.  It probably isn't necessary wouldn't hurt to check.

I'll still be reviewing the thread in case there's something else that might appear to be missed.

> **samuelpiquet said:**
> Hey, found nothing worth mentioning... maybe i'll have to wait for official support...

It would be nice if someone very fluent in using the ndiswrapper would chime in.  It's unlikely that you'd get good support from ASUS on this because they have a contract with Windows which they ship with the computer.  It's my experience with computer manufacturers is that they don't offer support for user perferred OS's.  They usually tell me that they can't offer support for Windows 7 if the computer was purchased with Windows XP, unless you purchase the upgrade from them.

So, most likely we are just about on our own.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~james](www.apollo3.com/~james)

---

### Post by samuelpiquet on 2013-12-16
Hmmm ok... So let's hope a good heart will come to help us :)

---

### Post by merwizard on 2013-12-16
dmesg shows the following result while trying to use XP drivers with ndiswrapper (ubuntu 13.10 32 bit)
```
[   15.372574] ndiswrapper: driver netrtwlane (Realtek Semiconductor Corp.,07/11/2013,2010.3.0610.2013) loaded
[   15.373447] ndiswrapper (NdisWriteErrorLogEntry:188): log: C0001388, count: 1, return_address: f931488b
[   15.373531] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0x605
[   15.373683] ndiswrapper (mp_init:211): couldn't initialize device: C001001E
[   15.373688] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001)
[   15.373693] ndiswrapper (mp_halt:254): device f1c05500 is not initialized - not halting
[   15.373696] ndiswrapper: device eth%d removed
[   15.373885] ndiswrapper: probe of 0000:02:00.0 failed with error -22

```
 The result is no WIFI interface present

---

### Post by graysonpblack on 2014-01-07
I am pretty close to purchasing one of these and would like to dual boot windows and Ubuntu.  I don't know if i will make the purchase without knowing the wireless issue is fixable. I will keep monitoring this thread in hopes that someone will come up with an answer.

---

### Post by apollothethird on 2014-01-07
> **graysonpblack said:**
> I am pretty close to purchasing one of these and would like to dual boot windows and Ubuntu.  I don't know if i will make the purchase without knowing the wireless issue is fixable. I will keep monitoring this thread in hopes that someone will come up with an answer.

If I were you, I would do two things when getting ready to get new computer equipment.  First I'd ensure that it works with my preferred OS (which is Linux... specifically Ubuntu).  I'd do this by communicating with the vendor (if possible).  This would make it easier to get a refund if it doesn't work.

I'd also communicate the brand of product to the community, such as here and over at Linux Questions.  Maybe one of the major support sites such as here and Linux Questions will put up a hardware compatibility section to make it easier for someone to find what is compatible and to report problems to help develop a list of what isn't.

If I found a flagged compatible problem (such as the case of this thread) I'd report it to the vendor (via the thread link) asking for if they would provide drivers.  I understand, they might not.  But if this because a standard practice with the growing Linux community, the manufacturers would soon get the message and start providing drivers.  They won't do it for request from 4 or 5 people.  But again, they'd get the message when the whole community starts asking and it become clear that the manufacturers proving linux drivers actually has people choosing their product as choice from a user base.

The bottom line, the steps I provided would most likely in it current state, eliminate the Asus Vivo PC as a choice purchase.  So, unless you're inheriting the computer without any choice in the brand, you might consider getting a different computer to avoid problems.

For me, I'd be glad to have that brand so that I could try to figure out how to make it work.  But if I were going to get a computer for actually productivity, that brand wouldn't make the list of consideration.

If you get tired of waiting for this thread to close with a resolution and get one anyway, please share your experience with us!

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by praseodym on 2014-01-07
Which Windows driver is it? Win7? Is there a Win XP or Vista driver available?

---

### Post by samuelpiquet on 2014-01-09
Yes, there are Win XP and Vista drivers available but we can't get them to work.

---

### Post by praseodym on 2014-02-03
Finally kernel 3.14 is here and it contains this native driver. Download these packages and save them in Downloads:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14-rc1-trusty/linux-headers-3.14.0-031400rc1-generic_3.14.0-031400rc1.201402022035_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14-rc1-trusty/linux-headers-3.14.0-031400rc1-generic_3.14.0-031400rc1.201402022035_amd64.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14-rc1-trusty/linux-headers-3.14.0-031400rc1_3.14.0-031400rc1.201402022035_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14-rc1-trusty/linux-headers-3.14.0-031400rc1_3.14.0-031400rc1.201402022035_all.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14-rc1-trusty/linux-image-3.14.0-031400rc1-generic_3.14.0-031400rc1.201402022035_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14-rc1-trusty/linux-image-3.14.0-031400rc1-generic_3.14.0-031400rc1.201402022035_amd64.deb)


Installation:
```

sudo apt-get remove --purge ndisgtk ndiswrapper*
sudo apt-get install --reinstall build-essential dkms
sudo dpkg -i ~/Downloads/*.deb
sudo reboot
```
Maybe proprietary VGA drivers wont work, but we'll see...Check afterwards:
```

lspci -nnk | grep -iA2 net
iwconfig
lsmod
dmesg | grep rtl8
iwlist chan
sudo iwlist scan
```

---

### Post by samuelpiquet on 2014-02-05
Hey thanks for the tip ! I don't know if I can try that out with my 13.10 without encountering any issues...

---

### Post by praseodym on 2014-02-05
It can easiliy be reverted, if neccessary

---

### Post by samuelpiquet on 2014-02-06
I tried it out but it's not working. It seems the driver is not the right one:

> 
lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8821]
    Subsystem: ASUSTeK Computer Inc. Device [1043:85b4]
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8554]
    Kernel driver in use: r8169


iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.


lsmod
Module                  Size  Used by
parport_pc             32866  0 
ppdev                  17711  0 
rfcomm                 70638  12 
bnep                   19884  2 
snd_hda_codec_hdmi     47124  1 
snd_hda_codec_realtek    62466  1 
snd_hda_codec_generic    69424  1 snd_hda_codec_realtek
nls_iso8859_1          12713  1 
joydev                 17575  0 
hid_generic            12548  0 
usbhid                 53067  0 
btusb                  32542  0 
hid                   106254  2 hid_generic,usbhid
bluetooth             422749  22 bnep,btusb,rfcomm
6lowpan_iphc           18968  1 bluetooth
eeepc_wmi              13151  0 
asus_wmi               24697  1 eeepc_wmi
sparse_keymap          13890  1 asus_wmi
snd_hda_intel          57050  6 
snd_hda_codec         142715  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
snd_hwdep              13613  1 snd_hda_codec
snd_pcm               108860  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
intel_rapl             19228  0 
x86_pkg_temp_thermal    14269  0 
i915                  826464  3 
intel_powerclamp       19077  0 
coretemp               17768  0 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30465  1 snd_seq_midi
drm_kms_helper         53224  1 i915
kvm                   471679  0 
snd_seq                61965  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              30038  2 snd_pcm,snd_seq
drm                   308197  4 i915,drm_kms_helper
crct10dif_pclmul       14250  0 
crc32_pclmul           13160  0 
video                  19859  2 i915,asus_wmi
mac_hid                13253  0 
mei_me                 18496  0 
snd                    69883  24 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
ghash_clmulni_intel    13259  0 
i2c_algo_bit           13564  1 i915
cryptd                 20531  1 ghash_clmulni_intel
mei                    87125  1 mei_me
soundcore              12680  1 snd
psmouse               108621  0 
lpc_ich                21163  0 
wmi                    19363  1 asus_wmi
microcode              24391  0 
serio_raw              13462  0 
lp                     17799  0 
parport                42481  3 lp,ppdev,parport_pc
ahci                   30066  3 
r8169                  73299  0 
libahci                32191  1 ahci
mii                    13981  1 r8169


dmesg | grep rtl8


iwlist chan
eth0      no frequency information.

lo        no frequency information.


sudo iwlist scan
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.


---

### Post by samuelpiquet on 2014-02-06
And now I have a message saying "Unable to find the transceiver" during the boot. I did not notice other changes.

---

### Post by praseodym on 2014-02-06
Check
```

sudo modprobe -v rtl8821ae
iwconfig
dmeg | grep rtl8
```

---

### Post by metoikos on 2014-02-07
Seems driver not included to latest kernel due to the some problem. [https://github.com/torvalds/linux/commit/d7216f8f02da54f8f235c5cca562a55b7f52210d](https://github.com/torvalds/linux/commit/d7216f8f02da54f8f235c5cca562a55b7f52210d) 
You can check config-3.14... file at /boot folder it says: 
> # CONFIG_R8821AE is not set

---

### Post by metoikos on 2014-02-07
Finally i make it work. Here is the answer under the Wifi Notes 
[http://www.linlap.com/asus_transformer_book_trio_tx201la](http://www.linlap.com/asus_transformer_book_trio_tx201la)

I found answer at this topic: [http://askubuntu.com/questions/384246/realtek-8821-wifi-chipset](http://askubuntu.com/questions/384246/realtek-8821-wifi-chipset) 

```

metoikos@rocko ~ $ uname -a
Linux rocko 3.14.0-031400rc1-generic #201402022035 SMP Mon Feb 3 01:37:33 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```
```

metoikos@rocko ~ $ lsmod | grep 8821
rtl8821ae             575664  0 
mac80211              672805  2 zd1211rw,rtl8821ae
cfg80211              531468  3 mac80211,zd1211rw,rtl8821ae

```

Update: I just checked and it is working with 3.11 too.

```

metoikos@rocko ~ $ lsmod | grep 8821
rtl8821ae             579760  0 
mac80211              597268  2 zd1211rw,rtl8821ae
cfg80211              480503  3 mac80211,zd1211rw,rtl8821ae
metoikos@rocko ~ $ uname -a
Linux rocko 3.11.0-15-generic #25-Ubuntu SMP Thu Jan 30 17:22:01 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by samuelpiquet on 2014-02-08
I followed the same answer and it also works with 3.11 kernel. Thanks a lot !

---

### Post by Tomas_Buteler on 2014-02-10
I got the WiFi working following the same instructions, but Ubuntu doesn't find my network. I know it's broadcasting and working because I'm connected with another computer. I can't make it work by adding a 'hidden' network... could this be a driver problem?

**Update: **Nevermind, I fixed it by chaning the security settings of the network (which I saw on [this post]("http://ubuntuforums.org/showthread.php?t=2172619#post12779960")). Thanks!

---

### Post by thomas-galley on 2014-02-11
I made it work (13.10) by following the instructions indicated by praseodym and metoikos. Great ! Biog thumbs up to all who participated and made it happen :-) !

---

### Post by dominic5 on 2014-02-12
It seems to work for me (13.10), but it won't connect to my network or either detect it. Any ideas? It's a Xubuntu 13.10...

```
root@vivopc:~# uname -aLinux vivopc 3.11.0-15-generic #25-Ubuntu SMP Thu Jan 30 17:22:01 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
root@vivopc:~# lsmod | grep rtl88
**rtl88**21ae             579760  0 
mac80211              597268  1 **rtl88**21ae
cfg80211              480503  2 mac80211,**rtl88**21ae
```

```
root@vivopc:~# iwlist wlan0 scanning
wlan0     No scan results
```

```
[  391.073555] rtl8821ae-0:rtl_pci_start():<0-0> rtl_pci_start OK
[  391.074159] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  391.688539] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  393.092822] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  394.677095] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  396.081331] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  417.681282] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  419.085522] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  450.691287] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  452.095550] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  493.703121] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  495.107367] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  546.708778] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  548.113025] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  609.720254] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  611.124500] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  672.731720] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  674.136005] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  712.246931] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  713.651174] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  735.743204] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  737.147488] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
```

---

### Post by metoikos on 2014-02-14
Since yesterday I am struggling with same problem too.
Didn't figure out yet what just going on,

---

### Post by praseodym on 2014-02-15
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14-rc2-trusty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14-rc2-trusty/)

Check RC2 of the 3.14 kernel

---

### Post by 3v1n0 on 2014-03-03
FYI, as per [bug 1287298]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1287298") the module is about to be included in trusty kernel, please someone test [linux-image-3.13.0-15-generic_3.13.0-15.35~R8821AE_amd64.deb]("http://people.canonical.com/~ppisati/R8821AE/linux-image-3.13.0-15-generic_3.13.0-15.35~R8821AE_amd64.deb") to check if it works. You also need the last [linux-firmware package]("http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.125_all.deb"), if you don't already have the rtl8821aefw.bin in your /lib/firmware.

Once you've tested it, please reply to the bug report to let the dev to know if this is safe to be included in Trusty or not.
Thanks.

---

### Post by klas3 on 2014-03-04
Is there anyone having the same problem with the builtin 100/1000 ethernet aswell?

The Ubuntu Installer dont find any network device on my Asus Vivo PC WM40B.

---

### Post by Stergios_Galanis on 2014-04-23
> **metoikos said:**
> Finally i make it work. Here is the answer under the Wifi Notes 
[http://www.linlap.com/asus_transformer_book_trio_tx201la](http://www.linlap.com/asus_transformer_book_trio_tx201la)

I found answer at this topic: [http://askubuntu.com/questions/384246/realtek-8821-wifi-chipset](http://askubuntu.com/questions/384246/realtek-8821-wifi-chipset) 

```

metoikos@rocko ~ $ uname -a
Linux rocko 3.14.0-031400rc1-generic #201402022035 SMP Mon Feb 3 01:37:33 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```
```

metoikos@rocko ~ $ lsmod | grep 8821
rtl8821ae             575664  0 
mac80211              672805  2 zd1211rw,rtl8821ae
cfg80211              531468  3 mac80211,zd1211rw,rtl8821ae

```

Update: I just checked and it is working with 3.11 too.

```

metoikos@rocko ~ $ lsmod | grep 8821
rtl8821ae             579760  0 
mac80211              597268  2 zd1211rw,rtl8821ae
cfg80211              480503  3 mac80211,zd1211rw,rtl8821ae
metoikos@rocko ~ $ uname -a
Linux rocko 3.11.0-15-generic #25-Ubuntu SMP Thu Jan 30 17:22:01 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```


[FONT=arial]Hello everyone![/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]I was wondering if someone can PLEASE help out with the following issue I'm having.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]It's about installing Ubuntu on a X551MA-SX020D ASUS laptop.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]The aforementioned laptop comes with an integrated Intel ValleyView Gen7 (rev 0c) graphics board and a Realtek rtl8821ae chip for wireless connectivity.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Upon installation of Ubuntu 13.10 [default 3.11.0-12-generic kernel] all the devices are functional, *except* the rtl8821ae chip which the system simply cannot see.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]By either upgrading just the kernel to 3.14 or the whole installation to 14.04 [Trusty Tahr] what I get is a functioning rtl8821ae chip and a *blank screen* [seems to just go off] just before the graphical interface is about to show...[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]After TONS of research I found *this* thread, which points to:[/FONT]
[FONT=arial]http://www.linlap.com/asus_transformer_book_trio_tx201la[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial][the instructions on which I am incapable of reproducing on Ubuntu][/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]And also this thread:[/FONT]
[FONT=arial]https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1287298[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial][which is about upgrading the kernel to 3.13, meaning my screen goes off just before the graphical interface][/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]What I care about is to get both the monitor's resolution and the wireless chip to function properly.[/FONT]
[FONT=arial]What I do NOT care about is on which kernel or version of Ubuntu.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Thank you in advance for any help!![/FONT]

---

### Post by thomas-galley on 2014-04-28
Hello all,

I thought this might interest you. Last weekend I upgraded my Vivo tu Unbunto 14.04 LTS. WLAN was ready instantly without any interaction on my part. So I would advise those of you still encounter problems with the chipset to try the latest distribution.

Greetings from Germany,

Thomas

---

### Post by carlos66 on 2014-09-28
> **thomas-galley said:**
> Hello all,

I thought this might interest you. Last weekend I upgraded my Vivo tu Unbunto 14.04 LTS. WLAN was ready instantly without any interaction on my part. So I would advise those of you still encounter problems with the chipset to try the latest distribution.

Greetings from Germany,

Thomas

Ok, I'm curious. I have an Asus VivoPC VM40B, too, installed Ubuntu 14.04, and am getting sketchy WiFi reception.

I recently moved into my girlfriends house. There she has Xfinity with Comcast. She also has a Windows 7 laptop, and a smartphone that connects to a wireless network without issue. Before moving in, however, I used to have a Mac Mini running Mavericks. I used to have an issue connecting to the wifi network. It was either really slowor simply wouldn't work. It gave me DNS like problems. After much troubleshooting, I accepted there wasn't a solution, and simply didn't use my Mac Mini on her wireless network. I recently bought this Asus VivoPC VM40B and used it with Windows 8 for a couple of days at my house. I have been moved into our house, and had an issue again connecting to a WiFi network. It was the same issue I had with my Mac Mini. I installed mint 17 and was able to connect to the wifi, but after 10 or 20 minutes of use, the wifi would drop. I then installed ubuntu, and am having the same problem.

The computer has a realtek 8821 chipset for WiFi (or so I read on a message board). I currently have the computer connected to the network via Ethernet. I am only going to stay at her house for 2 months or so. My question is this, though. Is my computer compatible to use WiFi with Ubuntu? I still have time to return it. Should I return it? I am thinking the issue is with Comcast Xfinity, as I had a similar issue with Windows 8 and my Mac Mini.I don't mind waiting this out for 2 months until I move out and get a different Internet service provider and different router. how do I find out if my wireless card is compatible with Linux? And how do I find out if it is a Comcast Xfinity problem instead?

---

### Post by chris_wood2 on 2015-02-01
I would not say that this issue is really SOLVED. And would ask that Canonical investigate a bit - please!

I have just bought a VivoPC VM42. Whilst 14.04LTS gives WiFi connectivity and initially it installs as 65Mbs - once you give it a bit of work it drops to 6Mbs - Other older PC's I have running against the same gateway and exact same Ubuntu release give me 65Mbs. Also whilst the Ethernet shows a 1000Mbs connection and the Fibre line I have is 100Mbs - the data flow is VERY sporadic.

Whist I really do not want to use Windows - I tried a Win7 install. Even using the supplied drivers WiFi connectivity is VERY flakey. It cuts out a lot and attenuates bandwidth to way under what I am prepared to accept (65Mbs) - Closer to 6Mbs. Ethernet also a bit flakey but not as bad as with Ubuntu.

Frustrated - I installed Win 8.1. Installed the drivers. Goes like a rocket-ship. Very depressing. I have a very defined set of tasks for this device that will always run stand alone - but a swine having to use Windows.

The minute I know Ubuntu(Mint) runs as I need - It'll go to Linux in two shakes of a lambs tail.

---

### Post by mirsoft on 2015-02-02
The issue really does not seem to be solved. On ASUS VivoMini (RTL8821AE 802.11ac PCIe Wireless Network Adapter) and Kubuntu 14.10 (latest Kernel Update: 3.16.0-30-generic), the built-in wireless card did not find any wireless network in range. Before update it worked, however, I used it only for a few days since I bought the PC a week ago.

As my personal workaround (and also to exclude possible issue on the other ends) I plugged in the cheap USB WiFi card (TP-Link TL-WN821N) - worked flawless out of the box!

Any help will be appreciated!

---

