---
title: "Sony VAIO"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by JohnPta on 2009-01-15
I have a Notebook Sony VAIO model number: VGN-NR31MR/S. Can I put Ubuntu on that machine and will everything work?

---

### Post by Cloudy on 2009-01-15
Hardware detection for Ubuntu is pretty good, so I'd think you would have little to no problems.

---

### Post by nothingspecial on 2009-01-15
I have a completely different vaio and it has the best hardware recognition of any laptop I`ve installed Ubuntu on.

Getting the web cam working was an effort though but it works.

---

### Post by clive littlewood on 2009-01-15
Hi

Always best to download and run the live CD

This will enable you to see what is detected and what is not without disturbing your current OS.

If you then have any problems pitch the individual probs to the forum.

Hope this helps         :p

Clive

---

### Post by JohnPta on 2009-02-02
I did install Ubuntu and indeed everything works like a dream, except my wireless there I am still fighting with the setup. But I must admit it is probably me and NOT Ubuntu.

---

### Post by leonardo_neo on 2009-02-02
> I have a Notebook Sony VAIO model number: VGN-NR31MR/S. Can I put Ubuntu on that machine and will everything work?

I have installed Ubuntu in one of my friend's computer, which was sony vaio VGN-NR series. I don't remember the exact model though. It was installed successfully, and even we could able to configure USB data card wireless network in that. But we had to do some research to find out the exact setting for the data card.

---

### Post by JohnPta on 2009-02-02
> **leonardo_neo said:**
> I have installed Ubuntu in one of my friend's computer, which was sony vaio VGN-NR series. I don't remember the exact model though. It was installed successfully, and even we could able to configure USB data card wireless network in that. But we had to do some research to find out the exact setting for the data card.

Ha, that is exactly the fight I have now on my hand to get the wireless going. However Ubuntu IS recognizing the wireless device. 

See the screen dump.
 
root@jan-laptop:~# sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 15
       serial: 00:1a:80:f8:02:31
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=10.0.0.101 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ce:f3:fe:c0:fd:ae
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

Can you pls give me some hints where I must look to get the wireless working?

Thanx

---

### Post by leonardo_neo on 2009-02-02
> Can you pls give me some hints where I must look to get the wireless working?

Sorry buddy,

I am not an expert in networking. My friend's network device was "Tata Indicom plug 2 surf", which is a USB wireless network device. All I did was searched how to set this device on internet, and I found the answers.

The answer was to change the port id to #700 and to change the login name and password to some default value which I don't remember. (but your device must have some different setting)

One thing which I remember is that Ubuntu has local list of all the major wireless service providers.

You right click on the network icon----> Edit connection settings--->select mobile broadband(in case you have mobile wireless device)----->click 'add'---> a setting wizard will open and I guess your device must be listed there. Try to set the device with the wizard's help.

Even if that doesn't work, then try to search the configuration setting of your device in particular on internet. Hope that works [-o<

---

