---
title: "Tyan 2892 Networking problem"
date: 2006-09-26
forum: Networking &amp; Wireless
---

### Post by witcompe on 2006-09-26
I looked though the fourms and could not find a resolution to my issue.  Here is a run down of the hardware:

Tyan 2892 (BIOS rev 2.02)
2 x Opteron 280
4 x 1GB ECC/REG DDR RAM
nVidia 7900GTX
Ubuntu 6.06 Dapper Drake x64

On the motherboard there are 3 NICs.  2 x Broadcom BCM5704 and 1 x Intel 82551QM.  THe system "sees" all three NICs and has eth0, eth1 and eth2 like it should.  However it cannot bring up the NICs at all.  Starting networking using "/etc/init.d/networking restart" just gives, "Failed to bring up eth#."  Manually running dhclient gives a segmentation fault.  At this point I am at a loss.  None of the 3 NICs will resolve an IP, but I boot into Knoppix and the NICs work without issue.  Any ideas?  Any help at all will be much appreciated.  Also let me know if more info is needed.  Thanks in advance!

---

### Post by witcompe on 2006-09-27
Anyone?  Bueller...  Bueller...

---

### Post by mips on 2006-09-27
What does **lspci -v**  & **ifconfig** tell you ?

---

