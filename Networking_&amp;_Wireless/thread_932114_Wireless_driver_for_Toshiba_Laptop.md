---
title: "Wireless driver for Toshiba Laptop"
date: 2008-09-28
forum: Networking &amp; Wireless
---

### Post by MajinSaha on 2008-09-28
Hi, I recently bought Toshiba Satellite M305D-S4829 with Vista on it. I installed Ubuntu a bit later. It couldn't find any internet at all ! Neither wireless, nor through cabel. Internet works perfectly on Vista, but no effect on Ubuntu. This means I probably need a driver. Is there a dirver for Atheros AR5008X Wireless Network Adapter or Marvell Yukon 88E8040T PCI-E Fast Ethernet Controller ? If yes, then how can I install it ? I'm new to Ubuntu, so please help.
Thanks.

---

### Post by jualin on 2008-09-28
The first step is to go to the terminal and type > lspci this will give us more information about your wireless card. Second I'll try to connect using an Ethernet Cable (wired) and check that it works.

---

### Post by MajinSaha on 2008-09-29
This is what I got :

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Toshiba America Info Systems Unknown device 9602
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780MC [Radeon HD 3100 Graphics]
[B]02:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 4355 (rev 12)
06:00.0 Network controller: Atheros Communications Inc. AR5418 802.11abgn Wireless PCI Express Adapter (rev 01)[/B]
09:01.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:01.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
09:01.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)

Ethernet is not working. Even lights are not flashing. Some people say there's no driver for my relatively new model yet. What do you say ?

---

### Post by jualin on 2008-09-30
I found [this online]("https://bugs.launchpad.net/ubuntu/+bug/239852") which is related to your ethernet card. Maybe you should give it a try. Keep us posted, and feel free to ask if you don't understand something.

---

### Post by MajinSaha on 2008-10-01
I did what they told and almost understood all I needed but stopped at the very last point. I didn't know how to modify the file sky2.ko. I wanted to go to the offset they were talking about but didn't know how. Everything else seems clear. Please tell me which editor I should use and how I can modify the needed ID information in the file.

What about wireless ? Do I have to use ndiswrapper ?

---

### Post by jualin on 2008-10-01
You have to go to the terminal and run the commands suggested > rmmod sky2
cd /lib/modules/2.6.24-16-generic/kernel/drivers/net
sudo cp -p sky2.ko{,.orig}
perl -pe 's/\0\0\x6c\x43/\0\0\x55\x43/g' sky2.ko.orig > sky2.ko
modprobe sky2

---

### Post by MajinSaha on 2008-10-02
I did it ! Although it took a while, but ethernet is working now ! Thanks a lot !

So can anybody help me with Wireless driver ? My card configuration is given in the third post. I don't have an ethernet connection at home, so I had to carry my laptop all the way to my office. But there's a wireless route in my living area so it would be cool if I could connect to wireless. This way I'll have an internet in my house.

---

### Post by jualin on 2008-10-03
Glad to hear the ethernet is working!
Now we only have to figure out the wireless. I'll look for a solution during the weekend. Hang in there buddy!

---

### Post by jualin on 2008-10-03
Found [this on the forums]("http://ubuntuforums.org/showthread.php?t=780741"), maybe you should give it a shot.

---

### Post by jualin on 2008-10-03
If the above suggestion doesn't work try [this other thread.]("http://ubuntuforums.org/showthread.php?t=578778")
Feel free to ask if you don't understand something. If you try the Ndiswrapper method, there is a tutorial on my signature which will help you understand Ndiswrapper better. However I would give the first suggestion a try (linux native driver).  Hope this helps!

---

### Post by MajinSaha on 2008-10-03
The first suggestion worked ! It's been 1 hour since I started using wireless. Give me a few more tryouts to be fully confident. 
There's still one thing that bothers me. Ubuntu can't find both wireless and ethernet at every reboot. I have to type the following :
sudo modprobe sky2 (for ethernet)
sudo modprobe ath_pci (for wireless)
and then it finds conncetions. I understand, my complain is stupid, but I believe there's a way to fix this small trouble and save 5 seconds of my time at each reboot.

And the last thing : could anyone explain me what those commands meant in the first suggestion concerning wireless ? I'm learning Ubuntu and want to understand all I'm doing, not just copying guru's suggestions. Thanks.

If anything else happens regarding internet, I'll let you know.
THANKS !

---

### Post by Ayuthia on 2008-10-03
> **MajinSaha said:**
> The first suggestion worked ! It's been 1 hour since I started using wireless. Give me a few more tryouts to be fully confident. 
There's still one thing that bothers me. Ubuntu can't find both wireless and ethernet at every reboot. I have to type the following :
sudo modprobe sky2 (for ethernet)
sudo modprobe ath_pci (for wireless)
and then it finds conncetions. I understand, my complain is stupid, but I believe there's a way to fix this small trouble and save 5 seconds of my time at each reboot.

And the last thing : could anyone explain me what those commands meant in the first suggestion concerning wireless ? I'm learning Ubuntu and want to understand all I'm doing, not just copying guru's suggestions. Thanks.

If anything else happens regarding internet, I'll let you know.
THANKS !

You can try the following:
```
echo sky2 | sudo tee -a /etc/modules
echo ath_pci | sudo tee -a /etc/modules
```
They will add the two modules to /etc/modules.  The system should go through that file when it boots up and load any drivers in there.  If that does not work, a couple of commands can be added to /etc/rc.local to make it start up also.

---

### Post by jualin on 2008-10-04
I am glad the wireless is working for you now. Try Ayuthia's suggestion regarding the commands. Keep us posted and good luck!

---

