---
title: "Help with DLink DFE-530TX"
date: 2005-12-02
forum: Networking &amp; Wireless
---

### Post by tmartindub on 2005-12-02
I have a DLink DFE-530TX NIC and it is not working with the current Ubuntu installation.  I have done the full install and am not using the live CD.

The card comes with the Linux drivers and the instructions tell you to compile it then go in and change an alias to use the driver.  Thing is, being totally new to Linux I have NO idea of how to compile the driver and make the changes.  The instructions evidently assume you are Linux knowledgeable.  I am not.

Can someone help a newbee get this going?  Everything else works except the NIC and I am sure it is the driver.

Thanks.

Tommy

---

### Post by mips on 2005-12-03
I dont think you need to install the drivers that came with the card. 
The DFE-530TX uses Via Rhine chipset and the DFE-530TX+ uses Realtek 8139 chipset.

Follow the procedure in the link below. Post your output after each command so we can see where things get stuck.
[http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)

Possibly also try editing the /boot/grub/menu.lst file and go to the line with the kernel entry and add: acpi=force pci=noacpi

---

### Post by indianatom on 2005-12-20
Try going to System->Administration->networking

If you see "Ethernet connection", click on that, then properties, then set it to dhcp or static (whatever you use), then click "Activate" and OK.  

I have the same card and for some reason it wasn't activated upon installation.  Let me know if this helps you.

---

