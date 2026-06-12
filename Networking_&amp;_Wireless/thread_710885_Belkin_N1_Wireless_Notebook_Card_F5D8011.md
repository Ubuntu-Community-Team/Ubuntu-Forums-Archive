---
title: "Belkin N1 Wireless Notebook Card F5D8011"
date: 2008-02-28
forum: Networking &amp; Wireless
---

### Post by kgrayson on 2008-02-28
I am still quite new at Linux and despite searching Google and these forums I have found no solution to getting my Belkin N1 Wireless Notebook Card up and running. The part # is F5D8011. I have used ndiswrapper before in Puppy Linux, but I haven't had any luck this time around. After typing lspci -v | less into the terminal, this is the information I found about it:

Ethernet controller: Atheros Communications, Inc. AR5416 802.11a/b/g/n Wireless PCI Adapter (rev 01)
Subsystem: Belkin Unknown device 8011
Flags: 66MHz, medium devsel, IRQ 10
Memory at 2c000000 (32-bit, non-prefetchable) [disabled] [size=64k]
Capabilitys: <access denied>

For others with my problem I have found these links:
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin)

[http://ubuntuforums.org/showthread.php?t=340673](http://ubuntuforums.org/showthread.php?t=340673) (but my card is not a Marvell Chipset as stated in this thread and that driver did not work)

If anyone can help, it would be greatly appreciated - this is the last step to perfecting my setup! If anyone has been successful, please be extremely detailed in explaining the setup process as I really am quite new at this.

---

### Post by uberlube on 2008-02-28
Do you have the windows version of the driver? And if you have already tryed to install it, what method did you use?

---

### Post by kgrayson on 2008-02-29
I do have it and I attempted to use ndiswrapper, but no go. I have the F5D8011v1 drivers (the card I have is version 1) as well as the accompanying files that came with it all nicely organized into one folder. I can install the driver with ndiswrapper (but I get a "forcing parameter MapRegisters from 256 to 64" message). When I initiate ndiswrapper with "sudo modprobe ndiswrapper" the power goes on for the card as indicated by the LED on the card itself, but the whole system freezes.

---

### Post by kgrayson on 2008-02-29
I have read that some people have had success with the latest "trunk" of MadWifi. Unfortunately I don't know how I would go about installing that - my current chipset is not listed on their main compatibility page: [http://madwifi.org/wiki/Compatibility](http://madwifi.org/wiki/Compatibility)

Perhaps someone could provide a detailed explanation as to what I would need to do that?

---

### Post by kgrayson on 2008-03-01
Can anyone even point me in the right direction?

---

