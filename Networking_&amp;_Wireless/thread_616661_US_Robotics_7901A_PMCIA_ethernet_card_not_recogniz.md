---
title: "US Robotics 7901A PMCIA ethernet card not recognized"
date: 2007-11-18
forum: Networking &amp; Wireless
---

### Post by cygtoad on 2007-11-18
Greetings,

I have had trouble with Linux recognizing this card on a number of installs and I never got it to work.  Ironically, the box says it works with Linux, but US Robotics, of course, does not actually support Linux.  I have a good deal of info but I am stuck on not knowing how to recompile 8139too.c

OK here we go...
Let's start with some basic diagnostics

>  
$ lspci
06:00.0 Ethernet controller: U.S. Robotics Unknown device ab06 (rev 10)


I know the card is supposed to use Realtek 8139too driver in order to work properly per US Robotics.

I have already tried...
> modprobe 8139too
This returned no errors, but it didn't resolve the issue.

Here is my e-mail correspondence with US Robotics...

> 
While we do not officially support Linux, the driver included in our package as you have noticed is for Linux kernel 2.4 as it was based off the realtek 2.4 kernel driver.  In Linux kernel 2.6 the 8139 drivers are included as the module 8139too.

What can be done, is the 8139too module can be modified to include the vendor ID for our USR7901a card.

In order to do this, you will need your kernel source and build tools to compile and it.

Open the file drivers/net/8139too.c in a text editor, search for the section:

static struct pci_device_id rtl8139_pci_tbl[] = {
       {0x10ec, 0x8139, PCI_ANY_ID, PCI_ANY_ID, 0, 0, RTL8139 },
       {0x10ec, 0x8138, PCI_ANY_ID, PCI_ANY_ID, 0, 0, RTL8139 },
       {0x1113, 0x1211, PCI_ANY_ID, PCI_ANY_ID, 0, 0, RTL8139 },
       {0x1500, 0x1360, PCI_ANY_ID, PCI_ANY_ID, 0, 0, RTL8139 },
       {0x4033, 0x1360, PCI_ANY_ID, PCI_ANY_ID, 0, 0, RTL8139 },
       {0x1186, 0x1300, PCI_ANY_ID, PCI_ANY_ID, 0, 0, RTL8139 },
       {0x1186, 0x1340, PCI_ANY_ID, PCI_ANY_ID, 0, 0, RTL8139 },
       {0x13d1, 0xab06, PCI_ANY_ID, PCI_ANY_ID, 0, 0, RTL8139 },
       {0x1259, 0xa117, PCI_ANY_ID, PCI_ANY_ID, 0, 0, RTL8139 },
       {0x1259, 0xa11e, PCI_ANY_ID, PCI_ANY_ID, 0, 0, RTL8139 },
       {0x14ea, 0xab06, PCI_ANY_ID, PCI_ANY_ID, 0, 0, RTL8139 },
       {0x14ea, 0xab07, PCI_ANY_ID, PCI_ANY_ID, 0, 0, RTL8139 },
       {0x11db, 0x1234, PCI_ANY_ID, PCI_ANY_ID, 0, 0, RTL8139 },
       {0x1432, 0x9130, PCI_ANY_ID, PCI_ANY_ID, 0, 0, RTL8139 },
       {0x02ac, 0x1012, PCI_ANY_ID, PCI_ANY_ID, 0, 0, RTL8139 },
       {0x018a, 0x0106, PCI_ANY_ID, PCI_ANY_ID, 0, 0, RTL8139 },
       {0x126c, 0x1211, PCI_ANY_ID, PCI_ANY_ID, 0, 0, RTL8139 },
       {0x1743, 0x8139, PCI_ANY_ID, PCI_ANY_ID, 0, 0, RTL8139 },
       {0x021b, 0x8139, PCI_ANY_ID, PCI_ANY_ID, 0, 0, RTL8139 },

You will want to add this line at the top or anywhere within the other listings:

       {0x16ec, 0xab06, PCI_ANY_ID, PCI_ANY_ID, 0, 0, RTL8139 },

This contains the vendor and card ID for the USR7901a.

After adding this line and saving the file, recompile and reinstall your modules, after a reboot (or removing and reloading the 8139too module) your card should activate as eth0.

Due note, this information is provided as a courtesy as we can not officially support Linux. If this doesn't work for you the instructions provided should contain enough information for your Distribution support team to help you build an updated 8139too module with our card supported.



I couldn't find 8139too.c on my machine.  I am assuming it must be in the source code somewhere on the disk.  However even if I found it, I wouldn't know what to do with it.

Anybody know what to do next?  I am assuming this is something Ubuntu would want to add to their distributed compiled code, so others don't have this same issue.  This card is still on the market.

Any direction would be appreciated.

Thanks,

Matt

---

