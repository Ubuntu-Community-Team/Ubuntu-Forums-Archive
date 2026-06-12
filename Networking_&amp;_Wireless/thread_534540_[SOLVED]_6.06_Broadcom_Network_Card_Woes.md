---
title: "[SOLVED] 6.06 Broadcom Network Card Woes"
date: 2007-08-25
forum: Networking &amp; Wireless
---

### Post by Greslore on 2007-08-25
I installed Kubuntu 6.06 on a Dell Optiplex 745.  It did not detect the network card upon installation.  Here is the output from lshw:

        *-pci:2
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@00:1c.4
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network UNCLAIMED
                description: Ethernet controller
                product: Broadcom Corporation
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@03:00.0
                version: 02
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                resources: iomemory:dfbf0000-dfbfffff irq:11

How do I go about getting this thing to work?

---

### Post by jml on 2007-08-25
If I read your output correctly, you are referring to a wired / Ethernet card and not a wireless card.  If that is correct, I would suggest downloading an iso of Feisty Fawn (7.04)  it has better network support and may recoginze your card out of the box.

Joe

---

### Post by Greslore on 2007-08-25
[Long story on not going with Feisty]("http://ubuntuforums.org/showthread.php?p=3246847#post3246847") :(.  I wish I could.

Progress - I found the broadcom driver from broadcom.com.  One problem though, I can't compile it because 'make' is not installed on the machine.

---

### Post by Greslore on 2007-08-25
Problem fixed!!  Here is the solution for anyone else who is having same issue:

[Look here]("http://ubuntuforums.org/showthread.php?t=323667&hi%20ghlight=sc440")

Also, to enable apt-get to use the 6.06 Ubuntu CD as a repository, use the command "sudo apt-cdrom add"

---

