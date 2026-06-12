---
title: "Ubuntu 8.04 madwifi problems"
date: 2008-11-22
forum: Networking &amp; Wireless
---

### Post by danifilth198666 on 2008-11-22
Hi i'm pretty much a newbie but i know my way around the system faily well.
I have an acer 5315 and used the codes everyone had posted and got my wifi working, but since having to reinstall ubuntu whenever i try and do it, it keeps coming up with different errors.
Please someone help me out because i've had enough now :(

This is what i've been following:
sudo apt-get install build-essential linux-headers-generic
wget [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz)
tar zxvf madwifi-hal-0.10.5.6-current.tar.gz
cd madwifi-hal-0.10.5.6-r3835-20080801/
make
sudo make install
sudo modprobe ath_pci
sudo reboot

Heres a copy of what's coming up:
****@****:~$ cd madwifi-hal-0.10.5.6-r3835-20080801/
bash: cd: madwifi-hal-0.10.5.6-r3835-20080801/: No such file or directory

Please help:(

Thanks in advance.

---

### Post by Olivier2371 on 2008-11-22
hi there,

what kind of adapter are you using?

---

### Post by danifilth198666 on 2008-11-22
i think its the athos one, i'm not sure how i find out.

---

### Post by danifilth198666 on 2008-11-22
sorry atheros

---

### Post by Joe2Shoe on 2008-11-22
Open up a Terminal and type "sudo lshw -C network" (without the quotes) to find the name of your wifi card.

You can also type "lspci" in a Terminal window.

---

### Post by danifilth198666 on 2008-11-22
This is what i get when i type it in:

 *-network               
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1b:38:dc:bc:ef
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full ip=192.168.1.68 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0

I'm guessing it's the AR242x one.
Hope this right.

---

### Post by Joe2Shoe on 2008-11-22
Yes, you have the Atheros AR242x 802.11abg Wireless PCI Express Adapter

Go to System/Administration/Hardware Drivers, and see it the drivers for this card are listed there.
If so, click on the driver, then click the 'activate' button below.
Reboot.
See if it connects.

---

### Post by Olivier2371 on 2008-11-22
yes it is an atheros. 

Have you downloaded all the update for unbuntu hardy 8.04?

---

### Post by danifilth198666 on 2008-11-22
I tried that earlier and it didn't work at all.
Not sure what else i could do.

---

### Post by Joe2Shoe on 2008-11-22
you must enable all the repositories to be able to download the needed drivers.
Go to System/Administration/Synaptic Package Manager.
Enter password.
Click Settings/Repositories.
Under the "Ubuntu Software" tab, check the first 4 choices, and your region (United States).
Under the "Third-Party Software" tab, check both choices.
Under the "Updates" tab, under "Ubuntu updates", check the first 2 choices.
Under "Automatic Updates", check "Check for updates: daily".
Close.
File/Quit.
Reboot.
Your pc will check all repositories and download all the required updates for your system.

After this, go back to System/Administration/Hardware Drivers and enable the driver, if listed.
Good luck,
Joe2Shoe.

---

### Post by danifilth198666 on 2008-11-22
Just gone and done all that, and now there are no drivers showing in the "Hardware drivers" section.
Any other ideas as to what can be done at all?
Starting to hate ubuntu now lol

---

### Post by eks on 2008-11-22
If you upgrade to 8.10 (Intrepid), the ath5k driver on the linux-backports-modules-intrepid should work. You might have to do some things manually to blacklist the driver you installed in the 8.04, which blacklists ath5k. Take a look at the wiki, it solved for many people:

[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

---

