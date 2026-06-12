---
title: "Lost Ethernet after PC-BSD adventure"
date: 2007-12-16
forum: Networking &amp; Wireless
---

### Post by dada1958 on 2007-12-16
Yesterday I installed PC-BSD on an old Compaq Deskpro EN Series SFF PIII, just for fun I thought. Installation of AbiWord didn't work so I left PC-BSD and I wanted to install Xubuntu 7.10 from the alternate CD but the network card wasn't recognized.
After the installation I ran 'sudo lshw':

 *-network UNCLAIMED
             description: Ethernet controller
             product: 82557/8/9 Ethernet Pro 100
             vendor: Intel Corporation
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             configuration: latency=66 maxlatency=56 mingnt=8

Fortunately I had an old DSL Live-CD to learn that the Ethernet card wasn't dead, I could surf the web with Firefox.
But with the Xubuntu alternate CD the network card still can't be recognized :confused:
So I searched here for a solution and I found [this thread]("http://ubuntuforums.org/showthread.php?t=409281&page=2&highlight=lost+ethernet"), the part with Intel's PROBOOT.exe which I have to copy to a bootable CD. I downloaded a FreeDOS fullcd.iso because I have no floppy drives here at the moment. My questions are: am I on the right track and how do I copy the PROBOOT.exe to the iso?
TIA

---

