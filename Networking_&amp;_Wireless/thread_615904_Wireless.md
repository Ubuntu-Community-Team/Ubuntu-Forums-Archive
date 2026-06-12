---
title: "Wireless"
date: 2007-11-17
forum: Networking &amp; Wireless
---

### Post by indie56 on 2007-11-17
Hello

I have just upgraded to 7.10. When I run "ndiswrapper -l" in the terminal I get " driver installed device present"
What do I do next to get the wireless up and running? The wireless is not listed in the Network Settings.
Thanx

---

### Post by Brautigam on 2007-11-17
is the device plugged in. the disk that comes with it should do it all for you.

---

### Post by shad0w_walker on 2007-11-17
You might want to try instaling ndiswrapper-utils. If memory serves (Been a while since i setup my wireless) it contains the GUI for configuring your wireless. Also, nm-applet should be able to use the ndis enabled cards.

---

### Post by indie56 on 2007-11-17
Hello
It was fine in 7.04. An hour ago I upgraded to 7.10. The device is plugged in and the driver is present. Only I have to make it stand up and start working.

---

### Post by indie56 on 2007-11-17
Can somebody please give me the procedure to get my wireless going? The driver is installed and the device is recognised. However it does not show up in the network settings.

---

### Post by shad0w_walker on 2007-11-17
Have you tried what i suggested? It should add a menu option for wireless network config in the System > Administration menu.

---

### Post by indie56 on 2007-11-17
In 7.10 ndisgtk is the GUI for the wireless. I can see the driver and the device in the 'Wirless Network Devices'. But the card does not show up in the 'Network Setting' How do I make it show up in the "Network Settings"?

---

### Post by shad0w_walker on 2007-11-17
Have you checked the ndis module is definitely loaded? It might be that the drivers are installed and setup but the ndiswrapper module doesn't get loaded at startup.

---

### Post by indie56 on 2007-11-17
How do I do that? I am a big zero in Linux.

---

### Post by shad0w_walker on 2007-11-17
You need to open up a terminal (Applications > Accessories > Terminal) then run this command and post the output.

lsmod

I should be able to see if the ndis module is loaded from the list.

---

### Post by indie56 on 2007-11-17
The output is- 
~$ lsmod 
Module                  Size  Used by 
af_packet              21896  0 
sg                     36124  0 
binfmt_misc            11400  1 
rfcomm                 38684  2 
l2cap                  22788  11 rfcomm 
bluetooth              52324  4 rfcomm,l2cap 
capability              5000  0 
apm                    20564  1 
ppdev                   9348  0 
ipv6                  257700  16 
speedstep_lib           5380  0 
cpufreq_conservative     6560  0 
cpufreq_powersave       1792  0 
cpufreq_ondemand        8084  0 
cpufreq_stats           5508  0 
cpufreq_userspace       4116  0 
freq_table              4740  2 cpufreq_ondemand,cpufreq_stats 
sbp2                   23304  0 
lp                     11460  0 
snd_cmipci             35488  1 
gameport               15240  1 snd_cmipci 
snd_pcm_oss            43264  0 
snd_mixer_oss          16640  1 snd_pcm_oss 
snd_pcm                77320  2 snd_cmipci,snd_pcm_oss 
snd_page_alloc         10504  1 snd_pcm 
snd_opl3_lib           10624  1 snd_cmipci 
snd_hwdep               9220  1 snd_opl3_lib 
snd_mpu401_uart         8576  1 snd_cmipci 
snd_seq_dummy           3844  0 
snd_seq_oss            31872  0 
snd_seq_midi            8704  0 
snd_rawmidi            24832  2 snd_mpu401_uart,snd_seq_midi 
snd_seq_midi_event      7552  2 snd_seq_oss,snd_seq_midi 
snd_seq                50416  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
usblp                  14080  0 
snd_timer              22916  3 snd_pcm,snd_opl3_lib,snd_seq 
snd_seq_device          8332  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
nvidia               3929580  12 
pcspkr                  3072  0 
psmouse                38672  0 
serio_raw               7044  0 
snd                    52356  14 snd_cmipci,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
soundcore               7520  1 snd 
rtc                    13208  0 
via_agp                10368  1 
agpgart                33584  2 nvidia,via_agp 
via686a                16520  0 
i2c_isa                 4224  1 via686a 
i2c_viapro              9108  0 
i2c_core               25104  3 via686a,i2c_isa,i2c_viapro 
parport_pc             36132  1 
parport                35656  3 ppdev,lp,parport_pc 
shpchp                 33556  0 
pci_hotplug            31288  1 shpchp 
evdev                  10240  1 
iptable_nat             7812  0 
nf_nat                 18476  1 iptable_nat 
nf_conntrack_ipv4      18060  2 iptable_nat 
nf_conntrack           62424  3 iptable_nat,nf_nat,nf_conntrack_ipv4 
nfnetlink               6040  3 nf_nat,nf_conntrack_ipv4,nf_conntrack 
iptable_mangle          2944  0 
iptable_filter          3072  0 
ip_tables              12232  3 iptable_nat,iptable_mangle,iptable_filter 
x_tables               14980  2 iptable_nat,ip_tables 
ext3                  129928  1 
jbd                    53416  1 ext3 
mbcache                 8324  1 ext3 
ide_cd                 31776  0 
cdrom                  36512  1 ide_cd 
ide_disk               17408  3 
8139cp                 23680  0 
ata_generic             7556  0 
libata                125040  1 ata_generic 
scsi_mod              146828  3 sg,sbp2,libata 
floppy                 58500  0 
8139too                26112  0 
mii                     5632  2 8139cp,8139too 
ohci1394               35760  0 
ieee1394               94904  2 sbp2,ohci1394 
uhci_hcd               25232  0 
usbcore               136088  3 usblp,uhci_hcd 
via82cxxx               9476  0 [permanent] 
ide_core              114772  3 ide_cd,ide_disk,via82cxxx 
commoncap               7424  1 capability 
fuse                   44948  1

---

### Post by shad0w_walker on 2007-11-17
Looks like your problem is the ndiswrapper module isn't loaded. Try this command from the terminal and see if your card starts working.

```

sudo modprobe ndiswrapper
sudo depmod -a

```

Hopefully this will get your card started, if it does then you can do this to make the system load the module at boot
Run from terminal.

```
gksudo gedit /etc/modules
```

This will open up gedit (the text editor) and load the modules file, add this to the end of the file.

```
ndiswrapper
```

---

### Post by indie56 on 2007-11-17
While setting up the wireless in 7.04, I had used these instructions- 
[https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3)
Now at the command ' sudo modprobe ndiswrapper' I get "fatal module ndiswrapper not found"

---

### Post by shad0w_walker on 2007-11-17
That's very strange. Try running this and then, when you have typed the last part, don't type anything else and press tab a couple of times. It should show a list of all the modules starting with ndis

```
modinfo ndis
```

---

### Post by indie56 on 2007-11-17
From Synaptic I get versions 1.43 for both ndiswrapper common and ndiswrapper utils.
For command 'ndiswrapper -l' , I get  'driver installed , device present'.
That means the device and driver are both loaded. Why then does it not show up in the 'Network Setting'

---

### Post by shad0w_walker on 2007-11-17
You don't have the kernel module for ndis loaded. I told you what you needed to do to try and find the name of the module. I can't help if you don't do what is asked.

---

### Post by indie56 on 2007-11-17
My post #13 was after I had edited the etc/modules file and added ndiswrapper to the end of the file. Subsequent terminal command 'sudo modprobe ndiswrapper' generated   the 'fatal module ndiswrapper not found' 
Your #14 did not give any output, so I got the version from synaptic.

---

### Post by shad0w_walker on 2007-11-17
Ok. Have you tried the modprobe command again after you got the version from synaptic?

---

### Post by indie56 on 2007-11-17
After modification of the etc/modules file, I rebooted, opened the file to verify the line 'ndiswrapper' and then ran the command 'sudo modprobe ndiswrapper' and got the same result 'fatal module ndiswrapper not found'.

---

### Post by shad0w_walker on 2007-11-17
It definately looks like you don't have the ndiswrapper module installed. What ndis related packages do you have installed?

---

### Post by indie56 on 2007-11-17
From synaptic I see - ndisgtk, ndiswrapper common1.43, ndiswrapper utils 1.43. Mind you I upgraded to 7.10 from 7.04 about 4 hrs back.

---

### Post by shad0w_walker on 2007-11-17
Are they all installed? And if so, have you tried uninstalling them then reinstalling?

---

### Post by indie56 on 2007-11-17
Completed uninstall and reinstall. Same result.

---

### Post by shad0w_walker on 2007-11-17
Afraid I don't have any other ideas. Sorry to say, but hopefully this bump will get someones attention and get someone else helping.

---

### Post by indie56 on 2007-11-17
Is there any way to revert to 7.04 and it has to be a clean install?

---

### Post by kevdog on 2007-11-17
I dont understand the problem here -- ndiswrapper installation problems.  Did you try to install this from source or via synaptic??

What does
modinfo ndiswrapper
ndiswrapper -l
show?? (Please post output).

---

### Post by shad0w_walker on 2007-11-17
He has already installed ndiswrapper from synaptic and got the driver installed with it. However he doesn't have the kernel module loaded as best we can tell it isn't present in the system (Module not found when trying to modprobe)

---

### Post by kevdog on 2007-11-17
Lets post some output so we can verify this --- I didnt see any terminal output to confirm these statements.

---

### Post by indie56 on 2007-11-17
I upgraded to 7.10 from 7.04 about 4 hrs ago. The whole thing got downloaded and after the final step of 'Restart' this problem started. 
In the GUI of 'Wireless network Drivers' I can see both the driver and device installed. However it does not show up in the 'Network'

---

### Post by shad0w_walker on 2007-11-17
Ok, go back and read the thread. He posted the output of lsmod and modprobe ndiswrapper.

---

### Post by indie56 on 2007-11-17
Pl tell me the terminal comands. 
The problem is on my desktop and I am using the Laptop (7.04) to post here. So I have to read and type from the desktop. My typing is bit slow

---

### Post by shad0w_walker on 2007-11-17
The terminal commands are the ones I asked you to run earlier. If he had read back one page he would have seen them quite clearly.

---

### Post by kevdog on 2007-11-17
Good luck getting your wireless to work -- All the best!

---

### Post by indie56 on 2007-11-17
> **kevdog said:**
> I dont understand the problem here -- ndiswrapper installation problems.  Did you try to install this from source or via synaptic??

What does
modinfo ndiswrapper
ndiswrapper -l
show?? (Please post output).
For ndiswrapper -l
the output is 'driver installed, device present,

For modinfo ndiswrapper-
Could not find module ndiswrapper

---

### Post by NightCrawler03X on 2007-11-17
> **indie56 said:**
> Hello

I have just upgraded to 7.10. When I run "ndiswrapper -l" in the terminal I get " driver installed device present"
What do I do next to get the wireless up and running? The wireless is not listed in the Network Settings.
Thanx

try;
```

sudo ndiswrapper -m
sudo modprobe ndiswrapper
sudo dmesg

```

Then check to see if your wireless is listed in the Network Settings dialog.
If possible, you should use nm-applet, it's a tool you can use on your gnome/xfce panel, as a frontend to NetworkManager.
That way, you can easily manage your wireless settings.

Anyway, do what I've said and tell me what that does fro you.

---

### Post by indie56 on 2007-11-17
For sudo ndiswrapper -m  I get--module configuration already contains alias directive

For sudo modprobe ndiswrapper  I get-- Fatal ndiswrapper not found

---

### Post by indie56 on 2007-11-17
For dmesg I get
:~$ lsmod 
Module                  Size  Used by 
af_packet              21896  0 
sg                     36124  0 
binfmt_misc            11400  1 
rfcomm                 38684  2 
l2cap                  22788  11 rfcomm 
bluetooth              52324  4 rfcomm,l2cap 
capability              5000  0 
apm                    20564  1 
ppdev                   9348  0 
ipv6                  257700  16 
speedstep_lib           5380  0 
cpufreq_conservative     6560  0 
cpufreq_powersave       1792  0 
cpufreq_ondemand        8084  0 
cpufreq_stats           5508  0 
cpufreq_userspace       4116  0 
freq_table              4740  2 cpufreq_ondemand,cpufreq_stats 
sbp2                   23304  0 
lp                     11460  0 
snd_cmipci             35488  1 
gameport               15240  1 snd_cmipci 
snd_pcm_oss            43264  0 
snd_mixer_oss          16640  1 snd_pcm_oss 
snd_pcm                77320  2 snd_cmipci,snd_pcm_oss 
snd_page_alloc         10504  1 snd_pcm 
snd_opl3_lib           10624  1 snd_cmipci 
snd_hwdep               9220  1 snd_opl3_lib 
snd_mpu401_uart         8576  1 snd_cmipci 
snd_seq_dummy           3844  0 
snd_seq_oss            31872  0 
snd_seq_midi            8704  0 
snd_rawmidi            24832  2 snd_mpu401_uart,snd_seq_midi 
snd_seq_midi_event      7552  2 snd_seq_oss,snd_seq_midi 
snd_seq                50416  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
usblp                  14080  0 
snd_timer              22916  3 snd_pcm,snd_opl3_lib,snd_seq 
snd_seq_device          8332  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
nvidia               3929580  12 
pcspkr                  3072  0 
psmouse                38672  0 
serio_raw               7044  0 
snd                    52356  14 snd_cmipci,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
soundcore               7520  1 snd 
rtc                    13208  0 
via_agp                10368  1 
agpgart                33584  2 nvidia,via_agp 
via686a                16520  0 
i2c_isa                 4224  1 via686a 
i2c_viapro              9108  0 
i2c_core               25104  3 via686a,i2c_isa,i2c_viapro 
parport_pc             36132  1 
parport                35656  3 ppdev,lp,parport_pc 
shpchp                 33556  0 
pci_hotplug            31288  1 shpchp 
evdev                  10240  1 
iptable_nat             7812  0 
nf_nat                 18476  1 iptable_nat 
nf_conntrack_ipv4      18060  2 iptable_nat 
nf_conntrack           62424  3 iptable_nat,nf_nat,nf_conntrack_ipv4 
nfnetlink               6040  3 nf_nat,nf_conntrack_ipv4,nf_conntrack 
iptable_mangle          2944  0 
iptable_filter          3072  0 
ip_tables              12232  3 iptable_nat,iptable_mangle,iptable_filter 
x_tables               14980  2 iptable_nat,ip_tables 
ext3                  129928  1 
jbd                    53416  1 ext3 
mbcache                 8324  1 ext3 
ide_cd                 31776  0 
cdrom                  36512  1 ide_cd 
ide_disk               17408  3 
8139cp                 23680  0 
ata_generic             7556  0 
libata                125040  1 ata_generic 
scsi_mod              146828  3 sg,sbp2,libata 
floppy                 58500  0 
8139too                26112  0 
mii                     5632  2 8139cp,8139too 
ohci1394               35760  0 
ieee1394               94904  2 sbp2,ohci1394 
uhci_hcd               25232  0 
usbcore               136088  3 usblp,uhci_hcd 
via82cxxx               9476  0 [permanent] 
ide_core              114772  3 ide_cd,ide_disk,via82cxxx 
commoncap               7424  1 capability 
fuse                   44948  1

---

### Post by indie56 on 2007-11-17
Cancel the last post.
For dmesg I get
$ sudo dmesg 
[    0.000000] Linux version 2.6.22-14-386 (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 Sun Oct 14 22:36:54 GMT 2007 (Ubuntu 2.6.22-14.46-386) 
[    0.000000] BIOS-provided physical RAM map: 
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable) 
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved) 
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved) 
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000010000000 (usable) 
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved) 
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved) 
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved) 
[    0.000000] 0MB HIGHMEM available. 
[    0.000000] 256MB LOWMEM available. 
[    0.000000] found SMP MP-table at 000f5c70 
[    0.000000] Entering add_active_range(0, 0, 65536) 0 entries of 256 used 
[    0.000000] Zone PFN ranges: 
[    0.000000]   DMA             0 ->     4096 
[    0.000000]   Normal       4096 ->    65536 
[    0.000000]   HighMem     65536 ->    65536 
[    0.000000] early_node_map[1] active PFN ranges 
[    0.000000]     0:        0 ->    65536 
[    0.000000] On node 0 totalpages: 65536 
[    0.000000]   DMA zone: 32 pages used for memmap 
[    0.000000]   DMA zone: 0 pages reserved 
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0 
[    0.000000]   Normal zone: 480 pages used for memmap 
[    0.000000]   Normal zone: 60960 pages, LIFO batch:15 
[    0.000000]   HighMem zone: 0 pages used for memmap 
[    0.000000] DMI 2.2 present. 
[    0.000000] Intel MultiProcessor Specification v1.4 
[    0.000000]     Virtual Wire compatibility mode. 
[    0.000000] OEM ID: OEM00000 Product ID: PROD00000000 APIC at: 0xFEE00000 
[    0.000000] Processor #0 6:8 APIC version 17 
[    0.000000] I/O APIC #2 Version 17 at 0xFEC00000. 
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs 
[    0.000000] Processors: 1 
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 10000000:eec00000) 
[    0.000000] Built 1 zonelists.  Total pages: 65024 
[    0.000000] Kernel command line: root=UUID=8095115b-d9f4-4e6b-adce-0eee016a427b ro quiet splash 
[    0.000000] mapped APIC to ffffd000 (fee00000) 
[    0.000000] mapped IOAPIC to ffffc000 (fec00000) 
[    0.000000] Enabling fast FPU save and restore... done. 
[    0.000000] Enabling unmasked SIMD FPU exception support... done. 
[    0.000000] Initializing CPU#0 
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes) 
[    0.000000] Detected 797.989 MHz processor. 
[   21.632219] Console: colour VGA+ 80x25 
[   21.632502] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes) 
[   21.632821] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes) 
[   21.657707] Memory: 248980k/262144k available (1929k kernel code, 12576k reserved, 877k data, 348k init, 0k highmem) 
[   21.657733] virtual kernel memory layout: 
[   21.657736]     fixmap  : 0xfffa8000 - 0xfffff000   ( 348 kB) 
[   21.657740]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB) 
[   21.657744]     vmalloc : 0xd0800000 - 0xff7fe000   ( 751 MB) 
[   21.657747]     lowmem  : 0xc0000000 - 0xd0000000   ( 256 MB) 
[   21.657751]       .init : 0xc03c0000 - 0xc0417000   ( 348 kB) 
[   21.657754]       .data : 0xc02e25d5 - 0xc03bda04   ( 877 kB) 
[   21.657758]       .text : 0xc0100000 - 0xc02e25d5   (1929 kB) 
[   21.657766] Checking if this processor honours the WP bit even in supervisor mode... Ok. 
[   21.657870] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1 
[   21.737889] Calibrating delay using timer specific routine.. 1597.66 BogoMIPS (lpj=3195338) 
[   21.737942] Security Framework v1.0.0 initialized 
[   21.737959] SELinux:  Disabled at boot. 
[   21.737976] Mount-cache hash table entries: 512 
[   21.738179] CPU: After generic identify, caps: 0387fbff 00000000 00000000 00000000 00000000 00000000 00000000 
[   21.738204] CPU: L1 I cache: 16K, L1 D cache: 16K 
[   21.738210] CPU: L2 cache: 256K 
[   21.738216] CPU serial number disabled. 
[   21.738221] CPU: After all inits, caps: 0383fbff 00000000 00000000 00000040 00000000 00000000 00000000 
[   21.738241] Compat vDSO mapped to ffffe000. 
[   21.738267] CPU: Intel Pentium III (Coppermine) stepping 03 
[   21.738279] Checking 'hlt' instruction... OK. 
[   21.755038] Early unpacking initramfs... done 
[   22.523919] ACPI: Core revision 20070126 
[   22.524034] ACPI Exception (tbxface-0618): AE_NO_ACPI_TABLES, While loading namespace from ACPI tables [20070126] 
[   22.524046] ACPI: Unable to load the System Description Tables 
[   22.524524] ExtINT not setup in hardware but reported by MP table 
[   22.525015] ENABLING IO-APIC IRQs 
[   22.525372] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0 
[   22.777965] Booting paravirtualized kernel on bare hardware 
[   22.778100] Time: 23:46:22  Date: 10/17/107 
[   22.778171] NET: Registered protocol family 16 
[   22.778395] EISA bus registered 
[   22.810802] PCI: PCI BIOS revision 2.10 entry at 0xfb140, last bus=1 
[   22.810809] PCI: Using configuration type 1 
[   22.810814] Setting up standard PCI resources 
[   22.813251] ACPI: Interpreter disabled. 
[   22.813260] Linux Plug and Play Support v0.97 (c) Adam Belay 
[   22.813279] pnp: PnP ACPI: disabled 
[   22.813289] PnPBIOS: Scanning system for PnP BIOS support... 
[   22.813640] PnPBIOS: Found PnP BIOS installation structure at 0xc00fbdd0 
[   22.813653] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xbe00, dseg 0xf0000 
[   22.816419] PnPBIOS: 15 nodes reported by PnP BIOS; 15 recorded by driver 
[   22.816544] PCI: Probing PCI hardware 
[   22.816578] PCI: Probing PCI hardware (bus 00) 
[   22.816952] PCI quirk: region 6000-607f claimed by vt82c686 HW-mon 
[   22.816961] PCI quirk: region 5000-500f claimed by vt82c686 SMB 
[   22.818866] PCI: Using IRQ router VIA [1106/0686] at 0000:00:07.0 
[   22.818888] PCI->APIC IRQ transform: 0000:00:07.2[D] -> IRQ 11 
[   22.818895] PCI->APIC IRQ transform: 0000:00:07.3[D] -> IRQ 11 
[   22.818904] PCI->APIC IRQ transform: 0000:00:0c.0[A] -> IRQ 11 
[   22.818911] PCI->APIC IRQ transform: 0000:00:0f.0[A] -> IRQ 5 
[   22.818918] PCI->APIC IRQ transform: 0000:00:10.0[A] -> IRQ 11 
[   22.818925] PCI->APIC IRQ transform: 0000:00:11.0[A] -> IRQ 10 
[   22.818931] PCI->APIC IRQ transform: 0000:01:00.0[A] -> IRQ 10 
[   22.871404] NET: Registered protocol family 8 
[   22.871410] NET: Registered protocol family 20 
[   22.871575] pnp: 00:07: iomem range 0x0-0x9ffff could not be reserved 
[   22.871585] pnp: 00:07: iomem range 0xfffe0000-0xffffffff could not be reserved 
[   22.871594] pnp: 00:07: iomem range 0xfee00000-0xfee0ffff could not be reserved 
[   22.871602] pnp: 00:07: iomem range 0x100000-0xfffffff could not be reserved 
[   22.871617] pnp: 00:08: iomem range 0xf0000-0xf3fff could not be reserved 
[   22.871625] pnp: 00:08: iomem range 0xf4000-0xf7fff could not be reserved 
[   22.871633] pnp: 00:08: iomem range 0xf8000-0xfffff could not be reserved 
[   22.871641] pnp: 00:08: iomem range 0xca800-0xcbfff has been reserved 
[   22.872324] PCI: Bridge: 0000:00:01.0 
[   22.872330]   IO window: disabled. 
[   22.872339]   MEM window: e6000000-e7ffffff 
[   22.872346]   PREFETCH window: e4000000-e5ffffff 
[   22.872368] PCI: Setting latency timer of device 0000:00:01.0 to 64 
[   22.872401] NET: Registered protocol family 2 
[   22.873745] Time: tsc clocksource has been installed. 
[   22.909796] IP route cache hash table entries: 2048 (order: 1, 8192 bytes) 
[   22.909886] TCP established hash table entries: 8192 (order: 4, 65536 bytes) 
[   22.910103] TCP bind hash table entries: 8192 (order: 3, 32768 bytes) 
[   22.910216] TCP: Hash tables configured (established 8192 bind 8192) 
[   22.910223] TCP reno registered 
[   22.922032] checking if image is initramfs... it is 
[   24.377715] Freeing initrd memory: 6762k freed 
[   24.378562] audit: initializing netlink socket (disabled) 
[   24.378593] audit(1195343183.616:1): initialized 
[   24.384149] VFS: Disk quotas dquot_6.5.1 
[   24.384201] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes) 
[   24.384507] io scheduler noop registered 
[   24.384514] io scheduler anticipatory registered 
[   24.384519] io scheduler deadline registered 
[   24.384580] io scheduler cfq registered (default) 
[   24.384610] Applying VIA southbridge workaround. 
[   24.384617] PCI: VIA PCI bridge detected. Disabling DAC. 
[   24.384625] PCI: Enabling Via external APIC routing 
[   24.384668] Boot video device is 0000:01:00.0 
[   24.384977] isapnp: Scanning for PnP cards... 
[   24.739541] isapnp: No Plug & Play device found 
[   24.816430] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled 
[   24.816659] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
[   24.817142] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A 
[   24.818716] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
[   24.819283] 00:0e: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A 
[   24.820893] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize 
[   24.821377] input: Macintosh mouse button emulation as /class/input/input0 
[   24.821602] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12 
[   24.822045] serio: i8042 KBD port at 0x60,0x64 irq 1 
[   24.822057] serio: i8042 AUX port at 0x60,0x64 irq 12 
[   24.822428] mice: PS/2 mouse device common for all mice 
[   24.822678] EISA: Probing bus 0 at eisa.0 
[   24.822715] Cannot allocate resource for EISA slot 5 
[   24.822721] Cannot allocate resource for EISA slot 6 
[   24.822737] EISA: Detected 0 cards. 
[   24.822973] TCP cubic registered 
[   24.823010] NET: Registered protocol family 1 
[   24.823068] Using IPI Shortcut mode 
[   24.823285]   Magic number: 15:983:807 
[   24.823458]   hash matches device ptys1 
[   24.823498]   hash matches device snapshot 
[   24.824143] Freeing unused kernel memory: 348k freed 
[   24.849522] input: AT Translated Set 2 keyboard as /class/input/input1 
[   26.356878] fuse init (API version 7.8) 
[   26.372306] Capability LSM initialized 
[   26.427276] thermal: Unknown symbol acpi_processor_set_thermal_limit 
[   27.686071] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2 
[   27.686085] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx 
[   27.688029] VP_IDE: IDE controller at PCI slot 0000:00:07.1 
[   27.688061] VP_IDE: chipset revision 6 
[   27.688066] VP_IDE: not 100% native mode: will probe irqs later 
[   27.688082] VP_IDE: VIA vt82c686b (rev 40) IDE UDMA100 controller on pci0000:00:07.1 
[   27.688096]     ide0: BM-DMA at 0xc000-0xc007, BIOS settings: hda:pio, hdb:DMA 
[   27.688114]     ide1: BM-DMA at 0xc008-0xc00f, BIOS settings: hdc:DMA, hdd:pio 
[   27.688128] Probing IDE interface ide0... 
[   27.790901] usbcore: registered new interface driver usbfs 
[   27.790959] usbcore: registered new interface driver hub 
[   27.791009] usbcore: registered new device driver usb 
[   27.794504] USB Universal Host Controller Interface driver v3.0 
[   27.867735] 8139too Fast Ethernet driver 0.9.28 
[   28.267724] Floppy drive(s): fd0 is 1.44M 
[   28.306698] FDC 0 is a post-1991 82077 
[   28.337108] hdb: MAXTOR 6L040L2, ATA DISK drive 
[   28.393255] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14 
[   28.393358] Probing IDE interface ide1... 
[   29.256914] hdc: HL-DT-ST GCE-8160B, ATAPI CD/DVD-ROM drive 
[   29.592892] ide1 at 0x170-0x177,0x376 on irq 15 
[   29.624257] SCSI subsystem initialized 
[   29.652667] libata version 2.21 loaded. 
[   29.658275] uhci_hcd 0000:00:07.2: UHCI Host Controller 
[   29.659039] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1 
[   29.659090] uhci_hcd 0000:00:07.2: irq 11, io base 0x0000c400 
[   29.660044] usb usb1: configuration #1 chosen from 1 choice 
[   29.660415] hub 1-0:1.0: USB hub found 
[   29.660436] hub 1-0:1.0: 2 ports detected 
[   29.761627] uhci_hcd 0000:00:07.3: UHCI Host Controller 
[   29.761968] uhci_hcd 0000:00:07.3: new USB bus registered, assigned bus number 2 
[   29.762006] uhci_hcd 0000:00:07.3: irq 11, io base 0x0000c800 
[   29.762836] usb usb2: configuration #1 chosen from 1 choice 
[   29.763176] hub 2-0:1.0: USB hub found 
[   29.763194] hub 2-0:1.0: 2 ports detected 
[   29.866530] eth0: RealTek RTL8139 at 0xd080c000, 00:02:2a:d1:aa:ba, IRQ 11 
[   29.866539] eth0:  Identified 8139 chip type 'RTL-8139C' 
[   29.874930] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004) 
[   29.934833] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[10]  MMIO=[e9002000-e90027ff]  Max Packet=[2]  IR/IT contexts=[4/8] 
[   29.941851] ohci1394: fw-host0: Serial EEPROM has suspicious values, attempting to set max_packet_size to 512 bytes 
[   29.967186] hdb: max request size: 128KiB 
[   30.027260] hdb: 78177792 sectors (40027 MB) w/1819KiB Cache, CHS=65535/16/63, UDMA(100) 
[   30.034880] hdb: cache flushes supported 
[   30.034996]  hdb: hdb1 hdb2 < hdb5 > 
[   30.086346] hdc: ATAPI 40X CD-ROM CD-R/RW drive, 2048kB Cache, DMA 
[   30.086366] Uniform CD-ROM driver Revision: 3.20 
[   30.164604] usb 1-2: new full speed USB device using uhci_hcd and address 2 
[   30.328134] usb 1-2: configuration #1 chosen from 1 choice 
[   30.472343] Attempting manual resume 
[   30.472352] swsusp: Resume From Partition 3:69 
[   30.472357] PM: Checking swsusp image. 
[   30.472660] PM: Resume from disk failed. 
[   30.545677] kjournald starting.  Commit interval 5 seconds 
[   30.545703] EXT3-fs: mounted filesystem with ordered data mode. 
[   31.212613] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001106005350d195] 
[   41.546659] ip_tables: (C) 2000-2006 Netfilter Core Team 
[   41.676509] Netfilter messages via NETLINK v0.30. 
[   41.700004] nf_conntrack version 0.5.0 (2048 buckets, 16384 max) 
[   46.155775] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
[   46.391082] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4 
[   46.892341] parport_pc: VIA 686A/8231 detected 
[   46.892351] parport_pc: probing current configuration 
[   46.892372] parport_pc: Current parallel port base: 0x378 
[   46.892422] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP] 
[   46.905405] Real Time Clock Driver v1.12ac 
[   46.916875] Linux agpgart interface v0.102 (c) Dave Jones 
[   46.924523] agpgart: Detected VIA Apollo Pro 133 chipset 
[   46.928166] agpgart: AGP aperture is 64M @ 0xe0000000 
[   46.985861] parport_pc: VIA parallel port: io=0x378, irq=7 
[   48.077084] nvidia: module license 'NVIDIA' taints kernel. 
[   48.090611] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-7185  Mon Apr  2 18:29:54 PDT 2007 
[   48.118711] input: PC Speaker as /class/input/input2 
[   48.309971] input: ImPS/2 Generic Wheel Mouse as /class/input/input3 
[   51.329795] lp0: using parport0 (interrupt-driven). 
[   51.550003] Adding 746980k swap on /dev/hdb5.  Priority:-1 extents:1 across:746980k 
[   51.942288] EXT3 FS on hdb1, internal journal 
[   53.942430] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm 
[   53.942631] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance 
[   53.943069] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance 
[   53.943335] acpi_cpufreq: Unknown symbol acpi_processor_register_performance 
[   55.752494] eth0: link down 
[   58.001610] NET: Registered protocol family 10 
[   58.001880] lo: Disabled Privacy Extensions 
[   58.002005] ADDRCONF(NETDEV_UP): eth0: link is not ready 
[   58.332061] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0. 
[   58.332261] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode 
[   58.332462] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode 
[   58.533577] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0. 
[   58.533796] agpgart: Putting AGP V2 device at 0000:00:00.0 into 0x mode 
[   58.533991] agpgart: Putting AGP V2 device at 0000:01:00.0 into 0x mode 
[   59.059157] ppdev: user-space parallel port driver 
[   59.734581] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac) 
[   61.277205] Capability LSM initialized 
[   61.923140] Bluetooth: Core ver 2.11 
[   61.923365] NET: Registered protocol family 31 
[   61.923372] Bluetooth: HCI device and connection manager initialized 
[   61.923379] Bluetooth: HCI socket layer initialized 
[   61.967298] Bluetooth: L2CAP ver 2.8 
[   61.967312] Bluetooth: L2CAP socket layer initialized 
[   61.998144] Bluetooth: RFCOMM socket layer initialized 
[   61.998319] Bluetooth: RFCOMM TTY layer initialized 
[   61.998326] Bluetooth: RFCOMM ver 1.8 
inderpal@inderpal-desktop:~$

---

### Post by indie56 on 2007-11-17
I have to go now. I will continue tomorrow.
Thanx evryone

---

### Post by indie56 on 2007-11-18
In the terminal for the command 'sudo modprobe ndiswrapper' I get 'module ndiswrapper not found. From synaptic I see that both ndiswrapper packages have been installed v1.43 after upgrade from 7.04 to 7.10 yesterday.
Can somebody pl help?

---

### Post by indie56 on 2007-11-18
I was reading tho this site [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

where it says--
here is a known bug in the Debian package, detailed [WWW] in this thread. If you install from these packages, the kernel module may not get installed, so you may get the error FATAL: Module ndiswrapper not found when you run modprobe ndiswrapper. To avoid this problem, it's best to compile from the source available at [WWW] [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/). This is fairly simple but requires the build-essentials package to be installed. You can install this offline using apt-cdrom from the command line or the synaptic package manager with the ubuntu install CD.


How do I install the builds-essential package?

---

### Post by indie56 on 2007-11-18
Can somebody help me the my post #41

---

### Post by kevdog on 2007-11-18
Take a look at this post:

[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

---

### Post by indie56 on 2007-11-18
Does not work for me. Reverting back to 7.04. At least it works.
Thanx

---

