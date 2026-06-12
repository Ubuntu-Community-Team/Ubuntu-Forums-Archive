---
title: "No wireless network interface showing"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by SoyChulo on 2008-05-02
I have a bit of a different problem.  8.04 installed without a hitch.  AR5006EX recognized and installed no problem.  But I got curious and decided to use ndiswrapper as an experiment.  Installed ndiswrapper through Synaptic, then downloaded zip file from atheros site.  Disabled HAL and Atheros support from restricted drivers support.  Rebooted.  Navigated to the inf file with ndiswrapper gui and used that driver.

Now I want to revert to the original setup.  Uninstall ndiswrapper.  Reboot.  Enable HAL and Atheros support.  Reboot.  When I click on the network icon there is no option for "enable wireless networking".

Here is the state of my affairs:
```
scrib@dell-laptop:~$ sudo lshw -C network
[sudo] password for scrib: 
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0

```

My wireless does not even have an ID.  What do I do to enable wireless networking again?  In the restricted drivers panel even both boxes are checked as 'enabled"  the line following says, "Not in use" and has a red button.  How do I put them into use?

Thanks in advance.:confused:

---

