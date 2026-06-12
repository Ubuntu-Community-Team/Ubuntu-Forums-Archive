---
title: "ubuntu 18.04lts wifi adapter not found msi MEG-X570-ACE"
date: 2020-03-05
forum: Networking &amp; Wireless
---

### Post by ale3385-3 on 2020-03-05
Hi I have ubuntu  18.04lts 
ale3385@ale-ramos:~$ uname -a
Linux ale-ramos 5.3.0-40-generic #32~18.04.1-Ubuntu SMP Mon Feb 3 14:05:59 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
My motherboard is [https://www.msi.com/Motherboard/MEG-X570-ACE](https://www.msi.com/Motherboard/MEG-X570-ACE)
And the wifi is not working, when I try to go settings / wifi , it says "wifi adapter not found".


Any guess?.


thanks

---

### Post by CelticWarrior on 2020-03-05
Welcome.

Your motherboard has no WiFi, only Ethernet.
If you added a WiFi adapter it's that one we need to know about in order to troubleshoot, not the motherboard.

---

### Post by ale3385-3 on 2020-03-05
Hi Celticwarrior
Yes it have, this motherboard includes it:
[https://www.msi.com/Motherboard/MEG-X570-ACE/Overview](https://www.msi.com/Motherboard/MEG-X570-ACE/Overview)

[h=2]Unique infinity and high-class golden design with rich specification. Win games and set records with 12+2+1 IR digital power, Mystic Light Infinity, Triple Lightning M.2 with Shield Frozr, Audio Boost HD, Game Boost and dual LAN with 2.5G gaming LAN plus WIFI 6 solution[/h]
[LIST]
[*]Supports 2nd and 3rd Gen AMD Ryzen&#8482; / Ryzen&#8482; with Radeon&#8482; Vega Graphics and 2nd Gen AMD Ryzen&#8482; with Radeon&#8482; Graphics Desktop Processors for AM4 socket
[*]Supports DDR4 Memory, up to 5000+(OC) MHz
[*]Mystic Light Infinity: Customize and set up your own color scheme with MSI Mystic Light, combining exclusive mirror reflection to generate the special endless light effects, the ACE makes your system come alive and infinity.
[*]Lightning Fast Game experience: PCIe 4.0, Triple Lightning Gen4 x4 M.2 with M.2 Shield Frozr, StoreMI, AMD Turbo USB 3.2 Gen2.
[*]Dual LAN with latest Wi-Fi 6 solution: Onboard 2.5G plus Gigabit LAN with gaming LAN manager, combining latest Wi-Fi 6 solution which supports MU-MIMO and BSS color technology, delivering the best online gaming experience.
[*]Frozr Heatsink Design:  Designed with the patented fan and double ball bearings to provide the best performance for enthusiast gamers and prosumers.
[*]Extended Heat-pipe Design: Enlarge the surface of heat dissipation, connecting from VRM heatsink to chipset heatsink.
[*]Audio Boost HD: Isolated audio with dedicated processor combining ESS audio DAC with amplifier, deliver the breathtaking, game-changing sound to create the most exciting gameplay.
[*]Pre-installed I/O Shielding: Better EMI protection and more convenience for installation
[/LIST]

---

### Post by CelticWarrior on 2020-03-05
You're correct, my mistake. They actually mention it. 
And looking at the Windows drivers available there's one for Intel WiFi. 

Now we have a problem...
Intel WiFi is usually supported out of the box. IF yours isn't it must be one of two situations:
[LIST=1]
[*]It's a brand new chipset not yet supported with the original kernel present in 18.04. But installing the same release with the current point release (the number after 18.04, e.g. the current 18.04.4) may already support it.
[*]Disable in UEFI.
[/LIST]

#2 is much more likely. So, please check it before anything else and enable it if disabled. That should be enough. If already enebaled and the problem persists please post the relevant line of 'lspci' in terminal.

---

### Post by chili555 on 2020-03-05
> 
5.3.0-[COLOR="#FF0000"]40[/COLOR]-generic
Can you boot into an earlier kernel at the GRUB menu? Does the wireless work then?

What does this report?```
lspci -nnk | grep 0280 -A3
dmesg | grep iwl
```

---

### Post by ale3385-3 on 2020-03-05
now, I'm at work, I can respond later in the afternoon :)

---

### Post by CelticWarrior on 2020-03-05
OK.

Please try chili555's suggestion first. Apparently there are a few issues with the exact kernel version you're running.

---

### Post by ale3385-3 on 2020-03-05
Hi again.
Sorry for the late, here are my results for chili555's:

ale@ale-3385:~$ lspci -nnk | grep 0280 -A3
28:00.0 Network controller [0280]: Intel Corporation Device [8086:2723] (rev 1a)
    Subsystem: Intel Corporation Device [8086:0084]
    Kernel modules: iwlwifi
2a:00.0 Non-Essential Instrumentation [1300]: Advanced Micro Devices, Inc. [AMD] Device [1022:1485]
ale@ale-3385:~$ 
ale@ale-3385:~$ dmesg | grep iwl
[    7.806373] iwlwifi 0000:28:00.0: enabling device (0000 -> 0002)
[    7.892068] iwlwifi: probe of 0000:28:00.0 failed with error -110
ale@ale-3385:~$ 

And by the way,my correct version of my home computer is the next one, as before I just posted the work env by mistake:
ale@ale-3385:~$ uname -a
Linux ale-3385 5.5.7-050507-generic #202002281805 SMP Fri Feb 28 18:08:42 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
ale@ale-3385:~$ 

 


Thanks in advance.

---

### Post by chili555 on 2020-03-05
> 
iwlwifi: probe of 0000:28:00.0 failed with error -110
Is this a dual-boot with Windows? Please check here: [https://bugzilla.kernel.org/show_bug.cgi?id=201319](https://bugzilla.kernel.org/show_bug.cgi?id=201319)> 
For me, the bug occurs whenever I boot into Windows and then back into Linux. The bug goes away when I boot again into Linux, no matter whether I shut down and turn the machine back on, or just reboot.[https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi#about_dual-boot_with_windows_and_fast-boot_enabled](https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi#about_dual-boot_with_windows_and_fast-boot_enabled)

---

### Post by ale3385-3 on 2020-03-06
Hi, this is dual boot windows 10 and ubuntu 18.04lts, you are correct but it does not think that is a bug with the dual boot. I just did the shutdown as was mention on your link above but nothing happens. Also whenever I start in windows, the WiFi works perfectly.

---

### Post by ale3385-3 on 2020-03-06
Any idea on how to troubleshoot it?.

---

### Post by ale3385-3 on 2020-03-06
Hi again, I just disable the fast boot in windows and WiFi start to work again!. :)

---

### Post by CelticWarrior on 2020-03-06
> **ale3385-3 said:**
> Hi again, I just disable the fast boot in windows and WiFi start to work again!. :)

It's Fast Startup (Fast Boot is a UEFI thing) but yes, it makes sense. Actually I was about to suggest that as an easy troubleshooting step, even if it had no effect it would do no hard.

---

### Post by chili555 on 2020-03-06
> 
Hi again, I just disable the fast boot in windows and WiFi start to work again!. Awesome! Glad it's working.

Please use thread tools at the top to mark Solved. A great many searchers with the same problem will appreciate it.

---

