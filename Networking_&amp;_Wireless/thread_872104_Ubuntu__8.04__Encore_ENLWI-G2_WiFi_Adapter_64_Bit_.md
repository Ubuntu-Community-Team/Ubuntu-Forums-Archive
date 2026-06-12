---
title: "Ubuntu  8.04  Encore ENLWI-G2 WiFi Adapter 64 Bit Driver"
date: 2008-07-27
forum: Networking &amp; Wireless
---

### Post by wg5o on 2008-07-27
I'm running Ubuntu 8.04 on an AMD Athlon 64 generic PC with two hard drives, one for Windows and one for Linux.
I've been working all summer to get WiFi working for Ubuntu (works fine for Win). 

Actually, I have two questions:

1.  Ubuntu 8.04 has ndiswrapper built-in (System, Administration, Windows Wireless Drivers).  Also, it will unpack an archive for you (rt. click, Extract Here).  Still, every instruction I have found tells the user to manually down load and install ndiswrapper.  What am I missing here?

2.  Using the 'dmesg' output, I finally discovered that my basic WiFi problem seems to be that Ubuntu won't load a 32 bit driver in a 64 bit system.  I found and downloaded a 64 bit Windows XP driver for my Encore ENLWI-G2 adapter [ Chipset ID 128219102 (rev 40)]. It installed OK:

'andy@izzy:~$ ndiswrapper -l
net8185x64 : driver installed
	device (10EC:8185) present'

But it won't load; 'sudo modprobe ndiswrapper' hangs-up.  The cursor just sits there and blinks, and never returns to the prompt.  The Ndiswrapper instructions/FAQ say this indicates a kernel crash and provides some instructions, but I haven't found a solution. 

 Is there a way to proceed?

Here are some of the details:

a. I blacklisted the built-in drivers:

In /etc/modprobe.d:

# Per 3.1 of WidiDocs/Driver/Ndiswrapper-Community Ubuntu..080722
blacklist b43
blacklist b43legacy
blacklist ssb

b.  'sudo depmod -a' indicated no errors (just returned to the prompt).

c. The ndiswrapper instructions say to check for the latest distro.  It is 1.53.  Ubuntu 8.04 seems to be close enough, one behind:

andy@izzy:~$ sudo ndiswrapper -v
[sudo] password for andy: 
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-19-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-19-generic SMP mod_unload 
andy@izzy:~$ 

d.   andy@izzy:/$ dmesg | grep ndiswrapper
[   47.207298] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   47.948736] ndiswrapper (link_pe_images:576): fixing KI_USER_SHARED_DATA address in the driver
[   47.949597] ndiswrapper: driver net8185x64 (Realtek,08/24/2006,5.1081.0824.2006) loaded
[   48.367634] ndiswrapper: using IRQ 16
[   54.494517] Modules linked in: snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc snd_hwdep usblp snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore psmouse serio_raw ndiswrapper i2c_viapro button k8temp i2c_core via_agp parport_pc parport shpchp pci_hotplug evdev pcspkr ext3 jbd mbcache sg sr_mod cdrom sd_mod floppy dmfe via_rhine mii ehci_hcd uhci_hcd pata_via sata_via pata_acpi ata_generic usbcore libata scsi_mod raid10 raid456 async_xor async_memcpy async_tx xor raid1 raid0 multipath linear md_mod dm_mirror dm_snapshot dm_mod thermal processor fan fbcon tileblit font bitblit softcursor fuse
[   54.494655]  [<ffffffff88253034>] :ndiswrapper:deserialized_irq_handler+0x14/0x30
[   54.494678]  [<ffffffff882674f2>] :ndiswrapper:win2lin4+0x14/0x17
[   54.494694]  [<ffffffff882587a1>] :ndiswrapper:kdpc_worker+0xc1/0x140
[   54.494714]  [<ffffffff88258788>] :ndiswrapper:kdpc_worker+0xa8/0x140
[   54.494729]  [<ffffffff882586e0>] :ndiswrapper:kdpc_worker+0x0/0x140
andy@izzy:/$ 

Thank you for any help.  I would surely like to get this working and go on to other needed work.

Andy Pickens
San Antonio, Texas

---

### Post by wg5o on 2008-08-18
I'm replying to my own post.

1.  This appears to be the product of old age.  One must install the GUI ndiswrapper (three components in Synaptic Paclage Manager).  It appears that I did that and forgot about it.

2.  The problem was resolved by going to the 32-bit version of Ubuntu 8.04, and using the 32-bit driver supplied with the card.  See my new post, "What worked for me."

---

