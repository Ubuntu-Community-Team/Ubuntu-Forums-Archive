---
title: "Can't Use Wireless. Please help!"
date: 2008-09-15
forum: Networking &amp; Wireless
---

### Post by Zorinea on 2008-09-15
I have a HP 6031EA laptop and I have installed Ubuntu on it but it is not compatible with my wireless card.

If found this about someone with a similar problem but I'm not quite sure what to do.

> Thankfully, there is an easy solution, but it requires that you already have Internet access in some way - and that is to update to the 2.6.25-19 kernel, although versions after that work fine as well. These aren’t included in the stable repositories, so you’ll have to enable the Hardy Proposed repository in Software Sources.

How do I get this "kernal"? Also, do I need internet access on the laptop to do this or could I for example download it onto my PC and copy it across?

---

### Post by Zorinea on 2008-09-15
Can anyone tell me where I can get this kernal and what to do with it?

---

### Post by Zorinea on 2008-09-17
All I need to know now is where do I put the kernal and what commands do I run ect. Help urgently needed. Thanks.

---

### Post by vorgusa on 2008-09-17
8.10 has a newer kernel then that, but it is only in testing right now.  I know you can get newer kernels by going to the repositries, but right now I do not have access to my ubuntu computer.  I believe if you go to system->administrator-> software sources and go to the "Updates" tab you can select "pre-released updates" and get to newer kernels.  Once you do that it rescans the repositories it will find new updates, scroll through and find the kernel, but unselect everything else or you might upgrade software you do not want to upgrade. good luck

---

### Post by Zorinea on 2008-09-18
I don't have internet on the laptop though so I cannot scan for updates.

Is there any way I could do this without connecting to the internet?

---

### Post by Ayuthia on 2008-09-18
Can you provide some information about your card?  If you go into the Terminal and provide the results for:
```
lshw -C network
```
It might produce more than one card.  We will need the product name and version of the card.  If you are able to get that information, can you also get the results of:
```
lspci -nn
```Look for the line that matches the product name that you found from the first command.  Once you find it, can you poste the chipset id and the rev number of the card.  The chipset will look something like [14e4:4315] and the rev will look like (rev 01).

This information will help us determine what you need to get your wireless working.  Thanks!

---

### Post by Zorinea on 2008-09-18
*-network                
       description: Network controller 
       product: BCM94311MCG wlan mini-PCI 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       version: 02 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list 
       configuration: driver=b43-pci-bridge latency=0 module=ssb 
alex@Alex-Laptop:~$ lspci -nm 
00:00.0 "0500" "10de" "02f3" -ra2 "103c" "30b7" 
00:00.1 "0500" "10de" "02fa" -ra2 "103c" "30b7" 
00:00.2 "0500" "10de" "02fe" -ra2 "103c" "30b7" 
00:00.3 "0500" "10de" "02f8" -ra2 "103c" "30b7" 
00:00.4 "0500" "10de" "02f9" -ra2 "103c" "30b7" 
00:00.5 "0500" "10de" "02ff" -ra2 "103c" "30b7" 
00:00.6 "0500" "10de" "027f" -ra2 "103c" "30b7" 
00:00.7 "0500" "10de" "027e" -ra2 "" "" 
00:02.0 "0604" "10de" "02fc" -ra1 "" "" 
00:03.0 "0604" "10de" "02fd" -ra1 "" "" 
00:05.0 "0300" "10de" "0247" -ra2 "103c" "30b7" 
00:09.0 "0500" "10de" "0270" -ra2 "103c" "30b7" 
00:0a.0 "0601" "10de" "0260" -ra3 "103c" "30b7" 
00:0a.1 "0c05" "10de" "0264" -ra3 "103c" "30b7" 
00:0a.3 "0b40" "10de" "0271" -ra3 "103c" "30b7" 
00:0b.0 "0c03" "10de" "026d" -ra3 -p10 "103c" "30b7" 
00:0b.1 "0c03" "10de" "026e" -ra3 -p20 "103c" "30b7" 
00:0d.0 "0101" "10de" "0265" -rf1 -p8a "f03c" "30b7" 
00:0e.0 "0101" "10de" "0266" -rf1 -p85 "103c" "30b7" 
00:10.0 "0604" "10de" "026f" -ra2 -p01 "" "" 
00:10.1 "0403" "10de" "026c" -ra2 "103c" "30b7" 
00:14.0 "0680" "10de" "0269" -ra3 "103c" "30b7" 
00:18.0 "0600" "1022" "1100" "" "" 
00:18.1 "0600" "1022" "1101" "" "" 
00:18.2 "0600" "1022" "1102" "" "" 
00:18.3 "0600" "1022" "1103" "" "" 
03:00.0 "0280" "14e4" "4311" -r02 "103c" "1375" 
alex@Alex-Laptop:~$

---

### Post by Zorinea on 2008-09-23
Could anyone give me a hand in what I should do next?

---

### Post by shanix on 2008-09-23
Seems to be a bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263097](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263097)

---

### Post by Ayuthia on 2008-09-23
You can try this link:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

It is the ndiswrapper route on getting your wireless to work.  There are some problems with the b43 working in the early versions of Hardy.

---

### Post by Zorinea on 2008-09-24
So if I downloaded the most recent version of Ubuntu, would my wireless card work?

---

### Post by Ayuthia on 2008-09-24
> **Zorinea said:**
> So if I downloaded the most recent version of Ubuntu, would my wireless card work?

It might.  I thought that the fix was applied in 2.6.24-19, but I am not for sure.  You can try installing 8.04.1 and see what happens.

---

