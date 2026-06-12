---
title: "Dapper Drake and nForce 430"
date: 2007-02-04
forum: Networking &amp; Wireless
---

### Post by stein on 2007-02-04
Hi everyone,

I just bought a new server and would like to set up an Ubuntu based Xen development server:

Hardware: AMD X2 3800+ on a nVidia 6100 / nForce 430 ( Gigabyte GA-M61PM-S2 ) motherboard

I attempted installing Dapper Drake as the host OS, but it won't recognize the nForce 430 gigabit networking. As the server is useless without networking, I need to get Ubuntu to play with the built-in nForce 430 gigabit ethernet.

Read several suggestions in the forums for getting Ubuntu to play with nForce 430:

[LIST=1]
[*]Upgrade to 2.6.19 kernel (how do i do that without networking??)
[*]Install Feisty Fawn (isn't it alpha right now? I wouldn't think that'd be the best choice for the Xen host OS)
[*]Install an old PCI networking card, install Dapper Drake, and then use that to download and compile the 2.6.19 kernel (will this work? Will the new kernel automatically detect the nForce 430 and install my nForce 430 gigabit ethernet?)
[/LIST][LIST=1]
[/LIST]

Anyone have any success with any of the above?

I need to get Ubuntu working on this system.

Thanks in advance for any help, advice, or hints!

---

### Post by dolphinholmer on 2007-02-05
Try the suggestions in [this post.]("http://ubuntuforums.org/showthread.php?t=334231")
It suggests installing a few feisty packages, not the whole OS.

---

### Post by SirShaggy on 2007-02-11
> **stein said:**
> Hi everyone,

I just bought a new server and would like to set up an Ubuntu based Xen development server:

Hardware: AMD X2 3800+ on a nVidia 6100 / nForce 430 ( Gigabyte GA-M61PM-S2 ) motherboard

I attempted installing Dapper Drake as the host OS, but it won't recognize the nForce 430 gigabit networking. As the server is useless without networking, I need to get Ubuntu to play with the built-in nForce 430 gigabit ethernet.

Read several suggestions in the forums for getting Ubuntu to play with nForce 430:

[LIST=1]
[*]Upgrade to 2.6.19 kernel (how do i do that without networking??)
[*]Install Feisty Fawn (isn't it alpha right now? I wouldn't think that'd be the best choice for the Xen host OS)
[*]Install an old PCI networking card, install Dapper Drake, and then use that to download and compile the 2.6.19 kernel (will this work? Will the new kernel automatically detect the nForce 430 and install my nForce 430 gigabit ethernet?)
[/LIST][LIST=1]
[/LIST]

Anyone have any success with any of the above?

I need to get Ubuntu working on this system.

Thanks in advance for any help, advice, or hints!


WOW, I never knew there was a problem with the 430b chipset. I have an ASUS m2nbp-vm csm motherboard with the 430b in my system. I put it together in December, installed the then curent 0404 bios and fired off the Edgy cd. Never once had trouble. I just (Friday) updated the bios again to the now newest 0601 that ASUS released, still no trouble. I am using the onboard LAN but not the onboard sound. I have a SoundBlaster for that.....
Maybe a BIOS update could help you?!?! I am not sure why mine works now........

SirShaggy

---

