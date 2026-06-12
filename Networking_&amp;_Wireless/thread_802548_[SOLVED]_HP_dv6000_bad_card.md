---
title: "[SOLVED] HP dv6000 bad card?"
date: 2008-05-21
forum: Networking &amp; Wireless
---

### Post by blackvd on 2008-05-21
I installed hardy on a roommates HP dv6000 and the wifi(broadcom) isn't working after following many of tutorials. Thing is it worked at first off and on using the bcm-fwcutter driver but now it doesn't show up at all in the system>hardware drivers? Also when he was running XP he had to reinstall the drivers constantly. Could the wi-fi card have crapped out? If so how can I test it?

---

### Post by blackvd on 2008-05-21
OK I'm thinking maybe its a BIOS issue, so I'm gonna try upgrading the BIOS. But first I have to figure out where to find them.

---

### Post by Ayuthia on 2008-05-21
> **blackvd said:**
> OK I'm thinking maybe its a BIOS issue, so I'm gonna try upgrading the BIOS. But first I have to figure out where to find them.

It most likely is not a BIOS issue, but a configuration issue.  However, if you go to the HP website ([www.hp.com](www.hp.com)) you should be able to find the BIOS update there.  

If you want some help with your wireless card, you will need to post (from the Terminal)the following information:
```
lspci -nn
lshw -C network
cat /etc/modules|grep -i -e bcm43xx -e b43 -e ssb -e ndiswrapper -e b44
cat /etc/modprobe.d/blacklist|grep -i -e bcm43xx -e b43 -e ssb -e ndiswrapper -e b44
ndiswrapper -l
ndiswrapper -v
```
The reason for so many different items (might be helpful to attach them instead of pasting) is so that we can see what needs to be fixed in order to get the wireless to work with NDISwrapper/b43/bcm43xx.

Please also let us know which option you want (NDISwrapper/b43/bcm43xx/whatever works).

---

### Post by blackvd on 2008-05-23
Awesome thanks for the reply. So as far the BIOS is concerned I only thought it might be that because when the computer boots it says BIOS bug found bunch o numbers, and the problem sorta existed on XP for him. Doesn't matter much though cause when I found the BIOS on HPs site it was an exe for windows only >_>

So here's the outputs of the commands you asked for.

```
$ lspci -nn
00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f0] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
00:05.0 VGA compatible controller [0300]: nVidia Corporation C51 [Geforce 6150 Go] [10de:0244] (rev a2)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
```

```
$ cat /etc/modules|grep -i -e bcm43xx -e b43 -e ssb -e ndiswrapper -e b44

``` nothing happens

```
$ cat /etc/modprobe.d/blacklist|grep -i -e bcm43xx -e b43 -e ssb -e ndiswrapper -e b44
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist bcm43xx

```

```
$ ndiswrapper -l
``` nothing

```
$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-16-generic SMP mod_unload 586
```

And whatever works so I don't have to mess with this laptop anymore.

Thanks!

---

### Post by Ayuthia on 2008-05-23
> **blackvd said:**
> Awesome thanks for the reply. So as far the BIOS is concerned I only thought it might be that because when the computer boots it says BIOS bug found bunch o numbers, and the problem sorta existed on XP for him. Doesn't matter much though cause when I found the BIOS on HPs site it was an exe for windows only >_>

So here's the outputs of the commands you asked for.

```
$ lspci -nn
00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f0] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
00:05.0 VGA compatible controller [0300]: nVidia Corporation C51 [Geforce 6150 Go] [10de:0244] (rev a2)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
```


Ok.  I was wrong.  The card did not show up.  Most of the hardware that listed here was very similar to mine because I have a dv6000 but your card  is not there.  Sorry.

---

### Post by blackvd on 2008-05-23
So maybe it is the BIOs since the card doesn't show up? If it is how can I install the bios from linux? I don't have a floppy drive, do I need to burn a cd for it?

---

### Post by Ayuthia on 2008-05-23
> **blackvd said:**
> So maybe it is the BIOs since the card doesn't show up? If it is how can I install the bios from linux? I don't have a floppy drive, do I need to burn a cd for it?

I am not for sure about how to accomplish this.  You might try creating a thread in General Help.  You might get a better response over there.

---

### Post by highinthemountains on 2008-05-23
there's a recall of the dv-6000 and dv-9000 laptops. the symptoms are the wireless card comes and goes, the laptop doesn't power up, and other strange stuff happens. call hp and they will replace the motherboard for free. be aware that they will wipe and reload the machine with the original os, so backup before sending it in.

hp will send you a shipping box, pay for shipping and it takes 7-10 days for the repair.

---

### Post by blackvd on 2008-05-27
> **highinthemountains said:**
> there's a recall of the dv-6000 and dv-9000 laptops. the symptoms are the wireless card comes and goes, the laptop doesn't power up, and other strange stuff happens. call hp and they will replace the motherboard for free. be aware that they will wipe and reload the machine with the original os, so backup before sending it in.

hp will send you a shipping box, pay for shipping and it takes 7-10 days for the repair.

Good deal. Seems the wi-fi is working for the moment. I'll see about calling HP or looking on there website. Glad to see the problem isn't Ubuntu's fault, or Linux for that matter.

---

