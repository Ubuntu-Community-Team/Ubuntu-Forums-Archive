---
title: "No Wifi with my HP G5 113CA"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by salochin92 on 2009-04-06
Hey,
I just switched from Vista to Ubuntu, and have been quite pleased, however I am quite confused as to how you set up the Wifi, I have tried forum after forum and have got to no conclusion. Could anyone help me? I know how to use a computer, but not so much Ubuntu. Are there any easy steps? 

Thanks!

---

### Post by anewguy on 2009-04-06
First do the following in a terminal window and post the output back here.  We'll go from there.

lscpi

lsusb



Dave :)

---

### Post by salochin92 on 2009-04-07
Here's what I get dor lspci:

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)



And here's what I get for lsusb:
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by anewguy on 2009-04-07
You will need to use the madwifi drivers for your atheros adapter.  Here is just one post on doing so (it's a little longer than needed because the guy screwed up a couple of times).

[http://ubuntuforums.org/showthread.php?t=895287&highlight=ar242x]("http://ubuntuforums.org/showthread.php?t=895287&highlight=ar242x")

Just ask back here if you have any questions or problems.

Dave :)

---

### Post by salochin92 on 2009-04-07
Thanks a bunch

---

### Post by salochin92 on 2009-04-07
Which link do I use? I have no idea about the programs they're talking about...

---

### Post by anewguy on 2009-04-08
From what I can see, you need to do the following:

In a terminal windows (applications/accessories/terminal):

sudo apt-get update && sudo apt-get install build-essential

wget [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz)

tar xvf madwifi-hal-0.10.5.6-r3835-20080801.tar.gz

cd madwifi-hal-0.10.5.6-r3835-20080801

sudo make

sudo make install

sudo modprobe ath_pci

Then reboot.  From further reading in that thread, it also appears you may want to turn off bluetooth support.  It would also appear that perhaps the light on your adapter may not show the "correct" color but it will probably work anyway.

I don't have experience using that chipset, so I'm basing the above on what I have gleaned from the link.

Dave :)

---

