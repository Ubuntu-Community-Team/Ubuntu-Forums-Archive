---
title: "ltsp-netboot help"
date: 2006-09-28
forum: Networking &amp; Wireless
---

### Post by subhan on 2006-09-28
Hello,

Iam new to LTSP. In LTSP I tried to boot clients with dhcp-server using etherboo t.For etherboot I downloaded a etherboot(eb-5.4.2-eepro.iso)CD from "http://ROM- o-matic.net" for client NIC.  Using that CD I boot client machine.

I configure ltsp server and dhcp-server properly.

When i tried to boot the client, it starts the network boot, gets an ip address from dhcp, mounts the root partition from server and then fails with the followi ng error.

"eth0 : Media link off".

I checked all network  cables,they are working properly.I tried with different e thernet cards(intel,dlink,advik) and etherboot cd-roms(eb-5.4.2-sis900.iso,eb-5. 4.2-via-rhine.iso,eb-5.4.2-tulip.iso) in the same client machine. But it's givin g same error.

The following is the configuration of server and client i am using.
server machine :
    Intel mother board
    processor : p4
    256 MB SDRAM
    40 GB HDD
    OS : edubuntu-5.0
    server : ltsp-4.2
    Ethernet Card : Intel corp. 82801BD pro/100 VE (LOM)

client machine :
    Intel mother board
    processor: old p3
    64 MB SDRAM
    Ethernet Card : Intel Corp - 82801BD pro/100 VE(LOM)

However when i tried with a relatively new P3 client, it works fine. I counldnt figureout whats the problem with this machine.

please give a solution to this problem.

thanks,
subhan.

---

