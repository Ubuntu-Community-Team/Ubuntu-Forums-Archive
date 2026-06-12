---
title: "Atheros AR93xx"
date: 2014-06-10
forum: Networking &amp; Wireless
---

### Post by Victor_Beaumont on 2014-06-10
Hey!

I am very new to Ubuntu so naturally I have many questions.  I am trying to install a AR93xx Wireless Network Adaptor from Qualcomm Atheros onto my computer.  I have placed the hardware in the proper place and it shows up when I use the command "lspci". Now I have to install a driver to get it working but I am stuck.  What driver should I use and how do I install it once I have found one?  Thanks in advance!

Victor

---

### Post by Vladlenin5000 on 2014-06-10
Hi, welcome.

Do you have an Ethernet (wired) connection available? If so you can try that. There's a good chance Ubuntu will get what's needed to work with your hardware automatically. If not, while connected, try System Settings > Software & Updates > Additional drivers; wait a few moments and check if there's something regarding your wireless device in which case you should select and confirm and let it download and install. Reboot and you should be good to go.

---

### Post by Victor_Beaumont on 2014-06-10
I do have an Ethernet connection, but Ubuntu neither automatically installed the software nor did it find any additional drivers in the System Settings.  I have been looking for additional drivers on the internet but I am having difficulty installing them properly. I believe that ath9k should be an appropriate driver for the wireless card, but how do I install it?

---

### Post by ajgreeny on 2014-06-10
I am pretty certain that ath9k driver should be already installed in the kernels these days; it is the driver that my netbook uses and I have not installed any additional drivers for that.

---

### Post by stalkingwolf on 2014-06-10
try here[http://sourceforge.net/projects/ath9k-htc/]("http://sourceforge.net/projects/ath9k-htc/")

---

### Post by Victor_Beaumont on 2014-06-10
ajgreeny, I did not find ath9k on my computer, I have a Ubuntu 12.04 LTS machine if that helps.  

stalkingwolf, I tried the link that you suggested and I was able to install and run the program but after restarting my computer nothing happened.  Was there something I needed to do afterwards?

---

### Post by Hadaka on 2014-06-10
Hi  			 				 				 					 						 	[**[COLOR=#000000]Victor_Beaumont[/COLOR]**]("http://ubuntuforums.org/member.php?u=1928842") and welcome to the forum.
there is a very simple way to determine what driver you
need for a given wireless card. First open a terminal...ctrl/alt/t
and then COPY and paste or enter these commands.
```
lspci -n | grep 0280
```
then do..
```
modinfo ath9k
```
please do both commands,one at a time then
copy and paste the results here
thanks.

---

### Post by Victor_Beaumont on 2014-06-11
Thanks for the help Hadaka!

Here is my code after entering the suggested commands:

```
loria@Picard:~$ lspci -n | grep 0280
03:00.0 0280: 168c:0030 (rev 01)
loria@Picard:~$ modinfo ath9k
filename:       /lib/modules/3.2.0-55-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     426E3BAA91A2633D95E6FD2
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
vermagic:       3.2.0-55-generic-pae SMP mod_unload modversions 686 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)

```

---

### Post by Victor_Beaumont on 2014-06-11
I have inserted a wireless card into my Ubuntu 12.04 but I can't seem to get it to work.  The computer seems to recognize the hardware but it keeps coming up as UNCLAIMED.  Here is some more information:
```

~$ lshw
           *-network UNCLAIMED
                description: Network controller
                product: AR93xx Wireless Network Adapter
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0
                resources: memory:fdec0000-fdedffff memory:fdd00000-fdd0ffff

~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller [8086:29c0] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port [8086:29c1] (rev 02)
00:1a.0 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 02)
00:1a.1 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 02)
00:1a.2 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 02)
00:1a.7 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 02)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 [8086:294a] (rev 02)
00:1d.0 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 02)
00:1d.1 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 02)
00:1d.2 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 02)
00:1d.7 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 92)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801IR (ICH9R) LPC Interface Controller [8086:2916] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA Controller [IDE mode] [8086:2920] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 02)
00:1f.5 IDE interface [0101]: Intel Corporation 82801I (ICH9 Family) 2 port SATA Controller [IDE mode] [8086:2926] (rev 02)
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV620 LE [Radeon HD 3450] [1002:95c5]
01:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] RV620 HDMI Audio [Radeon HD 3400 Series] [1002:aa28]
03:00.0 Network controller [0280]: Qualcomm Atheros AR93xx Wireless Network Adapter [168c:0030] (rev 01)
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 02)

```

I believe that a ath9k driver should work but I do not know why it will not work or how to get it to work. Any suggestions?

---

### Post by wildmanne39 on 2014-06-12
Please open the terminal Ctrl+Alt+T and copy and paste for accuracy:
```
sudo modprobe ath9k
```
Thanks

---

### Post by bapoumba on 2014-06-12
*Thread moved to **Networking & Wireless*** and threads merged.

---

### Post by Victor_Beaumont on 2014-06-12
Thanks for the help Wild Man, but nothing happened.  Any other suggestions?

---

### Post by wildmanne39 on 2014-06-13
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz)depending on the size of the file and it will be placed in your home folder. The wireless information will help to diagnose your wireless issue, the Mac address, WPA key and WEP key are removed for your security, then reply back, click on the paper clip and attach the (wireless-info.txt, or wireless-info.txt.tar.gz) file as a zip file. 

If you do not have ethernet connection then follow the directions at this link for running the script without internet courtesy of Varun .
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385).
Thanks

---

### Post by Victor_Beaumont on 2014-06-16
Thanks Wild Man.  Here is the file I got from running the diagnosis.
[ATTACH]253985[/ATTACH]

---

### Post by wildmanne39 on 2014-06-16
The driver you are using does not support your device, it is for an usb device.

You need the ath9k driver which is included in ubuntu but with your old kernel may not support your device without an upgrade, please remove the driver you installed then do:
```
sudo modprobe ath9k
``` does it come alive? if not post the out put of:
```
modinfo ath9k
```
Thanks

---

### Post by Victor_Beaumont on 2014-06-17
I've been trying to figure this out, but I can't seem to find what driver is connected to the wireless adapter.  Is it possible that there is no driver connected?  Assuming this I tried your suggestion, Wild Man, but it did not work.  How do I tell what driver is connected to the device and how do I remove it?  And does removing the driver uninstall it? I don't want to uninstall it, just remove the connection of the driver to the device.  Anyways, here is the output from "modinfo ath9k":

```

~$ modinfo ath9k
filename:       /lib/modules/3.2.0-55-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     426E3BAA91A2633D95E6FD2
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
vermagic:       3.2.0-55-generic-pae SMP mod_unload modversions 686 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)

```

---

### Post by wildmanne39 on 2014-06-17
This ```
pci:v0000168Cd00000030sv*sd*bc*sc*i*
```is your device and now it is loaded after you ran the command I told you too. So you did not remove the other driver? it does not drive your device and never should have been installed, it is best to get rid of it because it will conflict with this driver and keep your wireless from working. Please run a new script and post a new file after you remove the other driver so we can see what is going on with your system after the changes.
Thanks

---

### Post by Victor_Beaumont on 2014-06-17
I think I might be confused here then.  Here is the output after doing "lspci -v":

```

# lspci -v
...
03:00.0 Network controller: Qualcomm Atheros AR93xx Wireless Network Adapter (rev 01)
    Subsystem: Qualcomm Atheros Device 3116
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at fdec0000 (64-bit, non-prefetchable) [size=128K]
    [virtual] Expansion ROM at fdd00000 [disabled] [size=64K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/4 Maskable+ 64bit+
    Capabilities: [70] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [300] Device Serial Number 00-00-00-00-00-00-00-00
    Kernel modules: ath9k

```

From what I can see is that the only driver that would connect to the device is ath9k, which is what I want.  I don't want to blacklist it since it is the driver I need.  There doesn't seem to be any driver that is connected to the device, and if there were it is the ath9k.  Can someone explain this to me or possibly help me determine which driver is connected to the device?

---

### Post by wildmanne39 on 2014-06-17
You installed this driver [http://sourceforge.net/projects/ath9k-htc/](http://sourceforge.net/projects/ath9k-htc/) it is not the correct driver you need to remove it, so the ath9k driver will load and not conflict with it. The ath9k driver comes with ubuntu and as modinfo shows it drives your device. As I asked please remove the driver you installed and yes it is installed according to the lsmod from the info file you posted.

After you remove it your wireless may connect if not post a new wireless file so we can see the changes.
Thanks

---

### Post by Victor_Beaumont on 2014-06-18
It finally works! You were right Wild Man, I had the wrong driver so I just removed the one I had and connected with ath9k, rebooted, and connected. I also got some help from [http://docs.oracle.com/cd/E19530-01/html/835-0797/nh2ug.gjfbp.html](http://docs.oracle.com/cd/E19530-01/html/835-0797/nh2ug.gjfbp.html), if anyone is experiencing similar problems.  Thank you everyone for the help.

---

### Post by wildmanne39 on 2014-06-18
Glad it is working!

---

