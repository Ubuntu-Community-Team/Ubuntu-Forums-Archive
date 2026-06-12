---
title: "Wireless has become fickle, on/off every few reboots."
date: 2008-08-04
forum: Networking &amp; Wireless
---

### Post by NeuB27 on 2008-08-04
Basically thats it. Every couple of times that I turn the computer on, rather than seeing my nice two dots doing a connection dance, I will see what looks like a phone with the universal red circle and line over it. Sometimes I can log out and when I log back in it will work, but more often I have to restart the computer... sometimes twice. Obviously this isn't a huge problem because so far its worked after a restart or two, but I've had the OS running smooth and made no modifications, program additions or anything for the last month and a half. Then this started happening in the last two weeks and seems to have increased in frequency. Any one with any ideas to fix this or what it is caused by would be appreciated.. I think that is some network restart/reload/reinitialize command that might work but I cannot seem to remember what it was.

---

### Post by pytheas22 on 2008-08-04
```
sudo /etc/init.d/networking restart
```

restarts networking; it may help.  But to figure out what's going on, please post the output of these commands so we know which driver you're using:
```

lspci
lshw -C Network
```

Also, have you been applying Ubuntu system updates regularly?

---

### Post by NeuB27 on 2008-08-05
As far as I know all relevant updates have been applied, as soon as they become available synaptic takes care of notification and then I apply them. Unless there is some other place that one has to get them...

```
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
02:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
05:02.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
05:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)

```
```
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: L1 Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: b0
       serial: 00:1e:8c:ce:4b:80
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=atl1 driverversion=2.0.7 firmware=N/A latency=0 module=atl1 multicast=yes
  *-network
       description: Wireless interface
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 2
       bus info: pci@0000:05:02.0
       logical name: wlan0
       version: 03
       serial: 08:10:74:18:b7:fb
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netmw126 driverversion=1.52+Marvell,12/30/2005,3.2.3.2 ip=192.168.0.108 latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11b

```
Thanks for the help so far, I'll try the networking restart next time it happens.

---

### Post by pytheas22 on 2008-08-05
So you're running ndiswrapper, which is a bit surprising--I was expecting this to be an issue with the latest Intel or Broadcom driver, which do have a tendency to get broken via Ubuntu updates.  ndiswrapper shouldn't really change much.

First of all, this could simply be an issue with the ndiswrapper module not getting automatically loaded like it's supposed to.  If your wireless isn't working and you enter in a terminal:
```

sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo ifconfig wlan0 up
```

and wait a few seconds, are you able to connect then?  If so, the problem is pretty simple to fix permanently.

If that doesn't help, one possible fix to try, if you're up for it, is reinstalling ndiswrapper completely.  This command would remove it:
```

sudo apt-get remove --purge ndiswrapper*
```

And then (note that your wireless will probably be broken at this point, so you would hopefully have a wired connection available) you'd have to reinstall it again with:
```

sudo apt-get install ndiswrapper* ndisgtk
```

and then reinstall your Windows drivers into ndiswrapper.  That may fix the problem.

If that doesn't help or you don't want to deal with reinstalling ndiswrapper, the next best thing to do is to look at dmesg.  The next time you log in and have no wireless, please open a terminal, enter this command:
```

dmesg | grep -e ndiswrapper -e wlan -e netm126
```

and post the output here.

---

### Post by NeuB27 on 2008-08-05
It was not entirely easy, and took about a month to get ndiswrapper to work, but I think somehow it was mostly due to ubuntu 7.10 problems. And it seemed to work much faster in 8.04... but I would still rather not uninstall/remove it. A wired interface is available if necessary but its not convenient. So last time it happened I used the dmesg command here is the output.
```
[   47.486079] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   47.544370] ndiswrapper (link_pe_images:576): fixing KI_USER_SHARED_DATA address in the driver
[   47.544854] ndiswrapper: driver netmw126 (Marvell,12/30/2005,3.2.3.2) loaded
[   47.545371] ndiswrapper: using IRQ 18
[   47.605700] Modules linked in: ndiswrapper sbp2 parport_pc lp parport snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc snd_hwdep snd_seq_dummy joydev snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event atl1 snd_seq nvidia(P) mii snd_timer snd_seq_device i2c_core snd soundcore shpchp pci_hotplug evdev button iTCO_wdt iTCO_vendor_support intel_agp pcspkr ext3 jbd mbcache sg sr_mod cdrom sd_mod ata_piix pata_jmicron ata_generic usbhid hid ohci1394 ieee1394 pata_acpi ahci libata scsi_mod ehci_hcd uhci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[   47.605790]  [<ffffffff88b914c7>] :ndiswrapper:win2lin2+0xe/0x11
[   47.605807]  [<ffffffff88b914c7>] :ndiswrapper:win2lin2+0xe/0x11
[   47.605819]  [<ffffffff88b86a74>] :ndiswrapper:IofCallDriver+0x34/0xc0
[   47.605832]  [<ffffffff88b86a9f>] :ndiswrapper:IofCallDriver+0x5f/0xc0
[   47.605845]  [<ffffffff88b8d6f8>] :ndiswrapper:mp_init+0xa8/0x1e0
[   47.605857]  [<ffffffff88b86a74>] :ndiswrapper:IofCallDriver+0x34/0xc0
[   47.605870]  [<ffffffff88b87c80>] :ndiswrapper:IoSyncForwardIrp+0x90/0xd0
[   47.605885]  [<ffffffff88b8d90b>] :ndiswrapper:NdisDispatchPnp+0xdb/0xef0
[   47.605909]  [<ffffffff88b8752b>] :ndiswrapper:IoInitializeIrp+0x3b/0x70
[   47.605924]  [<ffffffff88b914c7>] :ndiswrapper:win2lin2+0xe/0x11
[   47.605935]  [<ffffffff88b86a74>] :ndiswrapper:IofCallDriver+0x34/0xc0
[   47.605948]  [<ffffffff88b86a9f>] :ndiswrapper:IofCallDriver+0x5f/0xc0
[   47.605963]  [<ffffffff88b867b0>] :ndiswrapper:IoAcquireCancelSpinLock+0x10/0x20
[   47.605976]  [<ffffffff88b86a74>] :ndiswrapper:IofCallDriver+0x34/0xc0
[   47.605988]  [<ffffffff88b87a0f>] :ndiswrapper:IoBuildSynchronousFsdRequest+0x2f/0x50
[   47.606002]  [<ffffffff88b8bdec>] :ndiswrapper:IoSendIrpTopDev+0xac/0x100
[   47.606017]  [<ffffffff88b8c0ef>] :ndiswrapper:pnp_start_device+0x4f/0xa0
[   47.606033]  [<ffffffff88b8c35f>] :ndiswrapper:wrap_pnp_start_device+0x21f/0x260
[   47.606048]  [<ffffffff88b8c3f0>] :ndiswrapper:wrap_pnp_start_pci_device+0x50/0x60
[   47.606085]  [<ffffffff88b7b2ef>] :ndiswrapper:loader_init+0x8f/0x140
[   47.606093]  [<ffffffff880720b7>] :ndiswrapper:wrapper_init+0xb7/0xc2

```
I did not try either of the suggested options to fix the problem because I didn't know exactly what they were going to do in reference to removing or upsetting the ndiswrapper balance. Is the first option> ```
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo ifconfig wlan0 up
```
harmless to the configuration? If so I'll try that next time. I did try the networking restart and that didn't do anything. Thanks again for the advice and time.

---

### Post by pytheas22 on 2008-08-05
Thanks for the dmesg.  It does seem that something strange is going on--it looks like the ndiswrapper module is starting to load without a problem, but doesn't fully initialize.  Unfortunately, there's no clear reason why.

I did find a couple of threads that may or may not be related to your problem ([here]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_fireboard/Itemid,27/func,view/id,388/catid,2/") and [here]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/152448")).

To get a better idea of exactly what's going on, I'm going to ask for some more information, though.  The next time you boot and have no wireless, please post the output of:
```

ndiswrapper -l
iwconfig
ifconfig
iwlist scan; iwlists scan
```

One of the things that may be going on is that ndiswrapper is bringing your wireless card up with a MAC address of 00:00:00:00:00:00, which most routers don't like.  The commands above will help determine whether that is in fact happening; if it is, it may be possible to fix by trying to manually reset the MAC address.

> Is the first option
Quote:
Code:

sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo ifconfig wlan0 up

harmless to the configuration? If so I'll try that next time.

Yes, those commands won't make any permanent changes--anything they do will be returned to normal by a reboot.  So please give them a try to see if they make a difference.

---

