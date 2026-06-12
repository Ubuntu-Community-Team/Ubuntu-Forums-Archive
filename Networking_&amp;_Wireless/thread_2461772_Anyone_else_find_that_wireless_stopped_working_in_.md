---
title: "Anyone else find that wireless stopped working in 21.04?"
date: 2021-05-06
forum: Networking &amp; Wireless
---

### Post by davidahillman on 2021-05-06
I have an Acer Aspire 5 laptop with a Qualcomm Atheros QCA6174 wireless card in it.  It's been running Kubuntu for about two years now - 18.x, 20.x, and I upgraded it to 21.04 a few days after that was released.  Everything worked fine.

Three days ago, not coincident to any update or other change, it ceased to be able to connect to my 802.11 wireless network.  All other devices on that network still work fine.  Wired ethernet continues to work fine, the problem is confined to wireless.  Even the bluetooth continues to work ( the Atheros card handles that, as well ).

I tried all manner of things to restore wireless connectivity without success.  Finally I rolled the laptop back to my last known-good 20.10 backup, and it again worked fine.  After that test confirmed the hardware was all working fine, I re-installed 21.04, and it again refuses to connect.  The wifi radio works, and it sees my network and those of my neighbors, but it cannot negotiate a connection.  I rolled it back to 20.10 again, and wireless functionality was immediately restored.  I just booted the laptop off a freshly-downloaded 21.04 image on a USB stick, and even the installer process cannot connect wirelessly.

Obviously, a solution is to simply run 20.10, but that's sub-optimal.  I'd like to know what changed in 21.04, and/or how to work around it, so I'm not permanently stuck with 20.10.

Any ideas?  Thanks.

---

### Post by davidahillman on 2021-05-09
Update, in the unlikely event that anyone ever reads this thread.

I booted an ancient MacBook Pro with the same 21.04 ISO image on a USB stick.  On that machine, the installer is able to connect to an 802.11 network.  So the problem appears to relate to something in 21.04 -- that's not present in 20.10 -- having a negative interaction with the Qualcomm Atheros card in the Aspire 5 laptop.

---

### Post by hk42 on 2021-05-14
In such cases I would try to replace the  /usr/lib/firmware  directory of the non working
installation with the one that is working.
Keep backups.

---

### Post by scorp123 on 2021-05-15
> **davidahillman said:**
>  Obviously, a solution is to simply run 20.10, but that's sub-optimal.  I'd like to know what changed in 21.04, and/or how to work around it, so I'm not permanently stuck with 20.10. 

Why not stay with long-term releases, e.g. 20.04?? That's what I do. Those "LTS" releases are super stable, well-tested and you get 5 years of updates and support. 

> **davidahillman said:**
>  Any ideas? 

**New kernel versions = new bugs.  Always.**  And 21.04 has a newer kernel than the releases before it (20.10, 20.04 ...) which means there are also going to be newer bugs and newer problems. Wireless cards suddenly ceasing to work being a typical candidate for that because some WiFi chip manufacturers make a big deal about how their chip exactly works, e.g. they claim it's a "Trade Secret" and they refuse to disclose the information needed to make their chipset work properly under Linux.

I own several "Archer T9UH" USB WiFi adapters which use the "Realtek 8814 AU" chip. Those adapters used to work "out of the box" in the past. But now? Not anymore. With any Linux distribution released after 2019 I need to manually download the correct driver and compile the package myself. No more *"it works out of the box"* for me. When I do that these USB WiFi adapters will work with the Linux 5.4.xx kernels and every update I get in that version, e.g.  5.4.0-70, 5.4.0-71, 5.4.0-72 and so on. But they never work with the newer 5.8.xx or higher kernels. So if I want to use those adapters I am stuck with kernel 5.4.xx for now and Ubuntu 20.04 ... until maybe one day whichever problem causes those adapters not to work in 5.8+ kernels gets fixed.

You might be in the same boat. Or at least somewhere in that same ocean...

---

### Post by Ski_K2 on 2021-05-20
> **davidahillman said:**
> I have an Acer Aspire 5 laptop with a Qualcomm Atheros QCA6174 wireless card in it.  It's been running Kubuntu for about two years now - 18.x, 20.x, and I upgraded it to 21.04 a few days after that was released.  Everything worked fine.

Three days ago, not coincident to any update or other change, it ceased to be able to connect to my 802.11 wireless network.  All other devices on that network still work fine.  Wired ethernet continues to work fine, the problem is confined to wireless.  Even the bluetooth continues to work ( the Atheros card handles that, as well ).

I tried all manner of things to restore wireless connectivity without success.  Finally I rolled the laptop back to my last known-good 20.10 backup, and it again worked fine.  After that test confirmed the hardware was all working fine, I re-installed 21.04, and it again refuses to connect.  The wifi radio works, and it sees my network and those of my neighbors, but it cannot negotiate a connection.  I rolled it back to 20.10 again, and wireless functionality was immediately restored.  I just booted the laptop off a freshly-downloaded 21.04 image on a USB stick, and even the installer process cannot connect wirelessly.

Obviously, a solution is to simply run 20.10, but that's sub-optimal.  I'd like to know what changed in 21.04, and/or how to work around it, so I'm not permanently stuck with 20.10.

Any ideas?  Thanks.

New XPS 15 with fresh 21.04 install two weeks ago. 
 
I'm having issues, twice in the past 2 weeks, on my new XPS 15 9500 and 21.04 with wifi working fine initially then not available. lspci shows the card. 
 
After trying numerous troubleshooting options found online in desperation I usb boot back to 20.10. wifi isn't available there either. 
 
Reboot to installed 21.04 and mysteriously wifi is back on. 
 
I have no idea if booting into trial 20.10 fixed it or if it is incidental??? 
 
pathp@XPS-15-9500:~$ sudo lshw -C network 
[sudo] password for pathp:  
  *-network                  
       description: Wireless interface 
       product: QCA6390 Wireless Network Adapter [AX500-DBS (2x2)] 
       vendor: Qualcomm 
       physical id: 0 
       bus info: pci@0000:6c:00.0 
       logical name: wlp108s0 
       version: 01 
       serial: 9c:b6:d0:3f:10:89 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=ath11k_pci driverversion=5.11.0-17-generic firmware=N/A ip=192.168.1.16 latency=0 link=yes multicast=yes wireless=IEEE 802.11 
       resources: irq:170 memory:b4200000-b42fffff

---

