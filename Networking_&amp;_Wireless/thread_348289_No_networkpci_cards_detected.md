---
title: "No network/pci cards detected"
date: 2007-01-28
forum: Networking &amp; Wireless
---

### Post by abitvp6 on 2007-01-28
Bought the book "Ubuntu Unleashed" (copyright 2007)  with 6.06LTS DVD.

It installs ok, but two of my ethernet cards Dlink DFE 530TX+ and Negear FA311 do not seem to work.

Also my PCI128 sound card does not work.

Updated file /etc/modules to include the lines
snd-ens1371
8139cp

Did this for my sound blaster pci128 and my ethernet card DFE 530TX+ to get the modules to load. For the Netgear FA311 I can try the module natsemi. If these are the wrong modules let me know.

Typed: sudo lsmod
Result:
Both the snd related modules and 8139cp module were loaded on bootup.

Updated file /etc/iftab to add the following line:
eth0   mac 00:50:BA:B2:EC:75  
The MAC address for my DFE 530TX+ ethernet card

Typing:
sudo lspci
Result: Nothing

Typing:
sudo lshw
Result:
Processor, IDE, CDROM, motherboard are listed but no sound card or ehternet cards.

Typing:
sudo ifup eth0
Result:
SIOCSFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.

To install ubuntu I removed my 30GB Drive from IDE 0 and used a 10GB drive so I would
not screw up my Windows 2000 installation which works fine. I have also run Fedora 4 at one time on this machine (ABIT V6 Dual Pentium III).

This version of ubunto uses only one of the processors, that's fine for now.

Fedora 5 and 6 seemed difficult to install so I thought ubuntu would be easier. After 2-3 days I'm about hacked out. I'll switch back to Windows 2000 to see if the computer still
ok.

I'm using a Windows XP system to get to the ubunto forum.

Alex

---

### Post by abitvp6 on 2007-01-28
> **abitvp6 said:**
> Bought the book "Ubuntu Unleashed" (copyright 2007)  with 6.06LTS DVD.

It installs ok, but two of my ethernet cards Dlink DFE 530TX+ and Negear FA311 do not seem to work.

Also my PCI128 sound card does not work.

Updated file /etc/modules to include the lines
snd-ens1371
8139cp

Did this for my sound blaster pci128 and my ethernet card DFE 530TX+ to get the modules to load. For the Netgear FA311 I can try the module natsemi. If these are the wrong modules let me know.

Typed: sudo lsmod
Result:
Both the snd related modules and 8139cp module were loaded on bootup.

Updated file /etc/iftab to add the following line:
eth0   mac 00:50:BA:B2:EC:75  
The MAC address for my DFE 530TX+ ethernet card

Typing:
sudo lspci
Result: Nothing

Typing:
sudo lshw
Result:
Processor, IDE, CDROM, motherboard are listed but no sound card or ehternet cards.

Typing:
sudo ifup eth0
Result:
SIOCSFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.

To install ubuntu I removed my 30GB Drive from IDE 0 and used a 10GB drive so I would
not screw up my Windows 2000 installation which works fine. I have also run Fedora 4 at one time on this machine (ABIT V6 Dual Pentium III).

This version of ubunto uses only one of the processors, that's fine for now.

Fedora 5 and 6 seemed difficult to install so I thought ubuntu would be easier. After 2-3 days I'm about hacked out. I'll switch back to Windows 2000 to see if the computer still
ok.

I'm using a Windows XP system to get to the ubunto forum.

Alex

Was able to switch to my windows 2000 30GB disk and come up ok with networking.
I'm using the netgear ethernet card FA311 and SoundBlaster PCI128.
So the motherboard, sound board and ethernet card are ok.

I'm submitting this reply using the same computer that I used for ubuntu.

---

### Post by abitvp6 on 2007-02-01
Based on other threads on this forum, I suspect the problem is with the VIA chip used by my motherboard, ABIT VP6.  

Also both 6.06 and 6.10 run better on my Sony VAIO which is only a year old and does not use the VIA chip. The Video, Sound, and network hardware worked fine.

It seems like if I install the basic 6.06 on my ABIT VP6 computer I might be able to recompile the kernel using the 6.06 alternate CD. The alternate CD has updates and packages needed to support building the kernel. I'm not completly sure about this yet, but I am reading the documentation and experimenting with this idea. When I had 6.06 installed on my hard drive and inserted the alternate CD I was able to bring up the package manager and install the packages on the alternate CD.

The purpose of rebuilding the kernel is to make sure the proper options where chosen to
provide support for a motherboard implemented with the VIA chip. I suspect options where chosen to fit everything on one CD.

Alex

---

