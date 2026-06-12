---
title: "Internet Consistently Slow Ubuntu 15.10"
date: 2015-11-16
forum: Networking &amp; Wireless
---

### Post by sam157 on 2015-11-16
Hey All,

I'm new to Ubuntu (and any form of Linux). I've tried searching for this topic, but I haven't come up with much that's helpful. 
I recently installed Ubuntu 15.10 and am dual-booting with Windows 8.1 (I think that's how you say that :/). 
It seems like I constantly have to disconnect and reconnect to the internet because after about 25-30  minutes of use, pages will fail to load on chromium. This happens with all wifi connections - the university's, mine, coffee shops, etc. I've unplugged and replugged my router to see if that just needed to be reset, but that doesn't seem to fix the problem.  It doesn't happen on the windows side. 

I found this link answer in the forums, though I don't know how to post my info like that user did.
[http://ubuntuforums.org/showthread.php?t=2175345](http://ubuntuforums.org/showthread.php?t=2175345)

I tried the commands the responder posted, but when I typed in the second "[COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe -v rt2800 pci nohwcrypt=1"[/FONT][/COLOR] I get "modprobe: FATAL: Module rt2800 not found."

I don't even know if the above link has an answer that's applicable to my problem. 

Any suggestions would be super appreciated. 

Thanks for your help,

Sam.

---

### Post by Geoffrey_Arndt on 2015-11-16
Well, the solution above is for a specific wireless chipset . . . . without knowing if lyou have the same hardware, running modprobes not a good idea.

The forum members here can help, but you make their job easier by posting your machine make, specific model and hardware specs.

If you install inxi (it is available via the Ubuntu Software Center) and after install, open a Terminal window (ctrl + alt + t).

Then input "inxi -Fx" (you don't need the quotes).    Post the output and we'll have a better idea about your hardware.

---

### Post by sam157 on 2015-11-16
Uh. Well, my computer is a Lenovo Flex 2-15. And I think I screwed up somewhere. You know that post I I referenced in my original inquiry? I added the config file, unaware that was going to be an issue. So now I have that file "[COLOR=#000000][FONT=Ubuntu Mono]rt2800pci.conf."

[/FONT][/COLOR]That was before I posted the thread. So, I installed the inxi software like you suggested, but when I tried to input the inxi-Fx command in the terminal, it said that it doesn't exist/can't be found. 

I restarted the computer, but now the WiFi won't even connect or show the wireless networks. The graphics take a long time to load - it's so super slow now that I'm working off the windows side.

---

### Post by Geoffrey_Arndt on 2015-11-17
Uh, yes, you did "mess up" . . . but it's fixable.   At worst, a re-install would fix but with your laptop specs, we can start on the right path.    Just as a side note or to ease your mind a bit.   The internet issue can be addressed via multiple methods.  One method is to ID what wireless hardware and driver you were actually running with (before the modprobe).   Another solution (if other fixes don't work) is to order a $10.00 usb wireless adapter (a mini or nano dongle) that plugs into a free usb port and is known to be compatible with Linux (and it's plug & play - no drivers needed). 

[URL="http://Panda Ultra 150Mbps Wireless N USB Adapter - Windows XP/Vista/7/8/8.1/10, Windows Ce 6.0, Mac 10.4-10.10, Mint, Ubuntu, Fedora, openSUSE, Lubuntu, BackTrack5 R3, Kali Linux, Raspberry Pi/Pi 2"]http://Panda Ultra 150Mbps Wireless N USB Adapter - Windows XP/Vista/7/8/8.1/10, Windows Ce 6.0, Mac 10.4-10.10, Mint, Ubuntu, Fedora, openSUSE, Lubuntu, BackTrack5 R3, Kali Linux, Raspberry Pi/Pi 2

[/URL]

The command won't run until it's entered correctly.  Linux is fussy about that.  Bash commands are case & space sensitive.  So "inxi -Fx" (there is a spce between the i and the dash -, then upper case F, lower case x).    So, when you installed inxi, it was before your reboot and you still had internet?

When you post your output, do a paste from the terminal window, and put your text between code tags  

[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)

---

### Post by sam157 on 2015-11-23
&#8203;Thanks for your help and patience. I was pretty hasty and didn't see that space between the last "i" and the "F".

Here's the output from the terminal - I copied it to an OpenDocument Text file (Libre), saved it, and copied it to the windows side. 
I just got back to this post - I can probably get a wireless usb adapter if this output isn't legible as copied and pasted/moved. 

```

sam@Genevieve:~$ inxi -Fx
System:    Host: Genevieve Kernel: 4.2.0-18-generic x86_64 (64 bit gcc: 5.2.1)
           Desktop: Unity (Gtk 3.16.7-0ubuntu3) Distro: Ubuntu 15.10 wily
Machine:   System: LENOVO product: 20405 v: Lenovo Flex 2-15
           Mobo: LENOVO model: Lenovo Flex 2-15 v: 31900058 WIN
           Bios: LENOVO v: A0CN31WW date: 10/08/2014
CPU:       Dual core Intel Core i3-4030U (-HT-MCP-) cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 7582
           clock speeds: max: 1900 MHz 1: 1900 MHz 2: 1900 MHz 3: 1899 MHz
           4: 1900 MHz
Graphics:  Card: Intel Haswell-ULT Integrated Graphics Controller
           bus-ID: 00:02.0
           Display Server: X.Org 1.17.2 drivers: fbdev,intel (unloaded: vesa)
           Resolution: 1366x768@76.00hz
           GLX Renderer: Gallium 0.4 on llvmpipe (LLVM 3.6, 256 bits)
           GLX Version: 3.0 Mesa 11.0.2 Direct Rendering: Yes
Audio:     Card-1 Intel 8 Series HD Audio Controller bus-ID: 00:1b.0
           Card-2 Intel Haswell-ULT HD Audio Controller bus-ID: 00:03.0
Network:   Card-1: Realtek RTL8723BE PCIe Wireless Network Adapter
           port: 4000 bus-ID: 02:00.0
           IF: N/A state: N/A mac: N/A
           Card-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           port: 3000 bus-ID: 03:00.0
           IF: N/A state: N/A speed: N/A duplex: N/A mac: N/A
           Card-3: Atmel usb-ID: 001-004
           IF: null-if-id state: N/A speed: 12 Mbps duplex: N/A mac: N/A
Drives:    HDD Total Size: 500.1GB (5.3% used)
           ID-1: /dev/sda model: WDC_WD5000LPCX size: 500.1GB
Partition: ID-1: / size: 213G used: 20G (10%) fs: ext4 dev: /dev/sda5
           ID-2: swap-1 size: 6.34GB used: 0.00GB (0%) fs: swap dev: /dev/sda6
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 41.0C mobo: 35.0C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 181 Uptime: 8 min Memory: 579.0/5875.9MB
           Init: systemd runlevel: 5 Gcc sys: 5.2.1
           Client: Shell (bash 4.3.421) inxi: 2.2.16

```


I feel like I've gotten myself into a pretty doofus-y spot. Should I move this problem to a different section of the forum?

---

### Post by sam157 on 2015-12-01
Bump.

---

