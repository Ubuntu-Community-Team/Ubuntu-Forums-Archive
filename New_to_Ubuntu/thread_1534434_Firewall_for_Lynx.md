---
title: "Firewall for Lynx?"
date: 2010-07-19
forum: New to Ubuntu
---

### Post by nnjond on 2010-07-19
Hi,

I'm running 10.04 without having installed a firewall is that ok?

because, i'm also bugged by audio/video and mouse problems which build up and i must warm boot to remedy. (although the drum fanfare at start-up doesn't sound quite right ether?).

furthermore i would like to open the port for my torrent client Transmission, but the elements of the web pge (192.168.1.1) are flickering. I mention this in the hope there all part of the same syndrome?

Thanks for your time

---

### Post by WRDN on 2010-07-19
You have a firewall installed, it's called "iptables", and by default, all ports are closed, making for a rather secure system.

I can't help you with the A/V problem, but regarding the web page flickering, it could be a bug in the browser (which browser?) or it could be a graphics driver problem.

---

### Post by nnjond on 2010-07-19
Thanks for your interest

Firefox is sooo slooow i must use Chrome, but neither will display this page completely.

All bugs seem to occure simultanouly. I see i am among a number of people who have failed to install the recomended driver, Nvidia-173, Nouvou has also, it seem given me trouble. Have you any further comment Please?

---

### Post by ankspo71 on 2010-07-19
Hi,
Ubuntu has something called IPtables which are the rules that control our networks. Ubuntu comes with a terminal based firewall called UFW to configure these IPtables, but it is not enabled by default, and is command line only. However, there is a nice graphical firewall called GUFW (found in Synaptic or possibly software center) that we can install that makes it much easier to configure the IPtables.

Here is a link for an overview of GUFW:
[http://www.ubuntugeek.com/gufw-simple-gui-for-ufw-uncomplicated-firewall.html](http://www.ubuntugeek.com/gufw-simple-gui-for-ufw-uncomplicated-firewall.html)

Here is some info on UFW and IPtables:
[http://www.ubuntugeek.com/gufw-simple-gui-for-ufw-uncomplicated-firewall.html](http://www.ubuntugeek.com/gufw-simple-gui-for-ufw-uncomplicated-firewall.html) 
[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

UFW or GUFW, will not be able to configure your router (eg 192.168.1.1) though, that is something that will have to be done through a browser. The only thing I can think of to help in this situation is to try another browser to access your router's configuration page. It might work better in opera or chromium-browser if it is flickering in firefox. <-- Edit, I just saw your post where you said you tried different browsers.

As far as downloading torrents goes, The newer torrent clients should be able to send and receive the necessary data with only an outbound connection, meaning no new firewall rules need to be made to allow inbound traffic. But opening the necessary ports might help other bittorrent services (discovery?) start working within the torrent client. If you are using a router, you would have to open the ports in the router and the IPtables in Ubuntu. Doing this lessens the security of both your router and your ubuntu though.
Hope this helps.

---

### Post by ajgreeny on 2010-07-19
For your **transmission** torrent ports you should use the Network tab in transmission's preferences dialog and set it to use UPnP or NAT-PMP port forwarding, which I think is set by default, but check it.  You should not need to do anything else.

As for your sound/video problems, what is your hardware?

---

### Post by ankspo71 on 2010-07-19
Hi Again,
I was just thinking that if it is a graphics driver related issue, it could be possible to download another linux distribtion live cd and use that to  configure your router during a live session. I would recommend using a non debian/ubuntu derived linux distribution though, to help avoid having the same version driver. (This is not meant to be a solution to the problem but as a possible way around it for now)

---

### Post by nnjond on 2010-07-19
Thanks for your interest. I hope this is what you wanted to see


nnjond@nnjond-desktop:~$ report-hw
uname -a: Linux nnjond-desktop 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux
lspci -knn: 00:00.0 Host bridge [0600]: Silicon Integrated Systems [SiS] 760/M760 Host [1039:0760] (rev 03)
lspci -knn: 	Kernel driver in use: agpgart-amd64
lspci -knn: 	Kernel modules: sis-agp, amd64-agp
lspci -knn: 00:01.0 PCI bridge [0604]: Silicon Integrated Systems [SiS] SG86C202 [1039:0002]
lspci -knn: 	Kernel modules: shpchp
lspci -knn: 00:02.0 ISA bridge [0601]: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] [1039:0964] (rev 36)
lspci -knn: 00:02.5 IDE interface [0101]: Silicon Integrated Systems [SiS] 5513 [IDE] [1039:5513] (rev 01)
lspci -knn: 	Kernel driver in use: pata_sis
lspci -knn: 00:02.7 Multimedia audio controller [0401]: Silicon Integrated Systems [SiS] AC'97 Sound Controller [1039:7012] (rev a0)
lspci -knn: 	Kernel driver in use: Intel ICH
lspci -knn: 	Kernel modules: snd-intel8x0
lspci -knn: 00:03.0 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001] (rev 0f)
lspci -knn: 	Kernel driver in use: ohci_hcd
lspci -knn: 00:03.1 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001] (rev 0f)
lspci -knn: 	Kernel driver in use: ohci_hcd
lspci -knn: 00:03.2 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001] (rev 0f)
lspci -knn: 	Kernel driver in use: ohci_hcd
lspci -knn: 00:03.3 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 2.0 Controller [1039:7002]
lspci -knn: 	Kernel driver in use: ehci_hcd
lspci -knn: 00:04.0 Ethernet controller [0200]: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet [1039:0900] (rev 91)
lspci -knn: 	Kernel driver in use: sis900
lspci -knn: 	Kernel modules: sis900
lspci -knn: 00:05.0 IDE interface [0101]: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] [1039:0180] (rev 01)
lspci -knn: 	Kernel driver in use: sata_sis
lspci -knn: 	Kernel modules: sata_sis
lspci -knn: 00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
lspci -knn: 00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
lspci -knn: 00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
lspci -knn: 00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
lspci -knn: 	Kernel driver in use: k8temp
lspci -knn: 	Kernel modules: k8temp
lspci -knn: 01:00.0 VGA compatible controller [0300]: nVidia Corporation NV34 [GeForce FX 5500] [10de:0326] (rev a1)
lspci -knn: 	Kernel driver in use: nouveau
lspci -knn: 	Kernel modules: nvidiafb, nouveau
lsmod: Module                  Size  Used by
lsmod: binfmt_misc             6587  1 
lsmod: fbcon                  35102  71 
lsmod: tileblit                2031  1 fbcon
lsmod: font                    7557  1 fbcon
lsmod: bitblit                 4707  1 fbcon
lsmod: softcursor              1189  1 bitblit
lsmod: vga16fb                11385  0 
lsmod: vgastate                8961  1 vga16fb
lsmod: snd_intel8x0           25588  3 
lsmod: snd_ac97_codec        100646  1 snd_intel8x0
lsmod: ac97_bus                1002  1 snd_ac97_codec
lsmod: snd_pcm_oss            35308  0 
lsmod: snd_mixer_oss          13746  1 snd_pcm_oss
lsmod: snd_pcm                70662  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
lsmod: snd_seq_dummy           1338  0 
lsmod: snd_seq_oss            26726  0 
lsmod: snd_seq_midi            4557  0 
lsmod: snd_rawmidi            19056  1 snd_seq_midi
lsmod: snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
lsmod: snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
lsmod: hid_a4tech              1910  0 
lsmod: nouveau               467048  1 
lsmod: snd_timer              19098  2 snd_pcm,snd_seq
lsmod: snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
lsmod: ttm                    49943  1 nouveau
lsmod: usbhid                 36110  0 
lsmod: drm_kms_helper         29297  1 nouveau
lsmod: usb_storage            39425  1 
lsmod: ppdev                   5259  0 
lsmod: sis_agp                 4047  0 
lsmod: hid                    67032  2 hid_a4tech,usbhid
lsmod: snd                    54148  15 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lsmod: drm                   162377  3 nouveau,ttm,drm_kms_helper
lsmod: i2c_algo_bit            5028  1 nouveau
lsmod: parport_pc             25962  1 
lsmod: amd64_agp               7025  1 
lsmod: soundcore               6620  1 snd
lsmod: snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
lsmod: k8temp                  3024  0 
lsmod: agpgart                31724  4 ttm,sis_agp,drm,amd64_agp
lsmod: shpchp                 28820  0 
lsmod: lp                      7028  0 
lsmod: parport                32635  3 ppdev,parport_pc,lp
lsmod: sis900                 17048  0 
lsmod: sata_sis                3332  0 
lsmod: mii                     4381  1 sis900
lsmod: floppy                 53016  0 
df: Filesystem           1K-blocks      Used Available Use% Mounted on
df: /dev/sda1            476271664 298201516 153876920  66% /
df: none                    767284       260    767024   1% /dev
df: none                    771504      1152    770352   1% /dev/shm
df: none                    771504       196    771308   1% /var/run
df: none                    771504         0    771504   0% /var/lock
df: none                    771504         0    771504   0% /lib/init/rw
df: /dev/sdb1             15392672    169272  14441476   2% /media/16_GB_Pen
free:              total       used       free     shared    buffers     cached
free: Mem:       1543008    1489172      53836          0      45860     511972
free: -/+ buffers/cache:     931340     611668
free: Swap:      4519928      70852    4449076
/proc/cmdline: BOOT_IMAGE=/boot/vmlinuz-2.6.32-23-generic root=UUID=3c30ba43-6de6-4e68-856b-e5495254bbfa ro quiet splash
/proc/cpuinfo: processor	: 0
/proc/cpuinfo: vendor_id	: AuthenticAMD
/proc/cpuinfo: cpu family	: 15
/proc/cpuinfo: model		: 44
/proc/cpuinfo: model name	: AMD Sempron(tm) Processor 2800+
/proc/cpuinfo: stepping	: 2
/proc/cpuinfo: cpu MHz		: 1599.397
/proc/cpuinfo: cache size	: 256 KB
/proc/cpuinfo: fdiv_bug	: no
/proc/cpuinfo: hlt_bug		: no
/proc/cpuinfo: f00f_bug	: no
/proc/cpuinfo: coma_bug	: no
/proc/cpuinfo: fpu		: yes
/proc/cpuinfo: fpu_exception	: yes
/proc/cpuinfo: cpuid level	: 1
/proc/cpuinfo: wp		: yes
/proc/cpuinfo: flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni lahf_lm
/proc/cpuinfo: bogomips	: 3198.79
/proc/cpuinfo: clflush size	: 64
/proc/cpuinfo: cache_alignment	: 64
/proc/cpuinfo: address sizes	: 40 bits physical, 48 bits virtual
/proc/cpuinfo: power management: ts ttp tm stc
/proc/cpuinfo: 
/proc/ioports: 0000-001f : dma1
/proc/ioports: 0020-0021 : pic1
/proc/ioports: 0040-0043 : timer0
/proc/ioports: 0050-0053 : timer1
/proc/ioports: 0060-0060 : keyboard
/proc/ioports: 0064-0064 : keyboard
/proc/ioports: 0070-0073 : rtc0
/proc/ioports: 0080-008f : dma page reg
/proc/ioports: 00a0-00a1 : pic2
/proc/ioports: 00c0-00df : dma2
/proc/ioports: 00f0-00ff : fpu
/proc/ioports: 0170-0177 : 0000:00:02.5
/proc/ioports:   0170-0177 : pata_sis
/proc/ioports: 01f0-01f7 : 0000:00:02.5
/proc/ioports:   01f0-01f7 : pata_sis
/proc/ioports: 0290-0297 : pnp 00:02
/proc/ioports: 02f8-02ff : serial
/proc/ioports: 0376-0376 : 0000:00:02.5
/proc/ioports:   0376-0376 : pata_sis
/proc/ioports: 0378-037a : parport0
/proc/ioports: 03c0-03df : vga+
/proc/ioports: 03f2-03f2 : floppy
/proc/ioports: 03f4-03f5 : floppy
/proc/ioports: 03f6-03f6 : 0000:00:02.5
/proc/ioports:   03f6-03f6 : pata_sis
/proc/ioports: 03f7-03f7 : floppy
/proc/ioports: 03f8-03ff : serial
/proc/ioports: 04d0-04d1 : pnp 00:02
/proc/ioports: 0800-0805 : pnp 00:02
/proc/ioports: 0cf8-0cff : PCI conf1
/proc/ioports: 1000-1003 : ACPI PM1a_EVT_BLK
/proc/ioports: 1004-1005 : ACPI PM1a_CNT_BLK
/proc/ioports: 1008-100b : ACPI PM_TMR
/proc/ioports: 1016-1016 : ACPI PM2_CNT_BLK
/proc/ioports: 1020-1023 : ACPI GPE0_BLK
/proc/ioports: 1030-1033 : ACPI GPE1_BLK
/proc/ioports: 4000-400f : 0000:00:02.5
/proc/ioports:   4000-400f : pata_sis
/proc/ioports: e000-e0ff : 0000:00:02.7
/proc/ioports:   e000-e0ff : SiS SI7012
/proc/ioports: e400-e4ff : 0000:00:04.0
/proc/ioports:   e400-e4ff : sis900
/proc/ioports: e800-e87f : 0000:00:02.7
/proc/ioports:   e800-e87f : SiS SI7012
/proc/ioports: e900-e907 : 0000:00:05.0
/proc/ioports:   e900-e907 : sata_sis
/proc/ioports: ea00-ea03 : 0000:00:05.0
/proc/ioports:   ea00-ea03 : sata_sis
/proc/ioports: eb00-eb07 : 0000:00:05.0
/proc/ioports:   eb00-eb07 : sata_sis
/proc/ioports: ec00-ec03 : 0000:00:05.0
/proc/ioports:   ec00-ec03 : sata_sis
/proc/ioports: ed00-ed0f : 0000:00:05.0
/proc/ioports:   ed00-ed0f : sata_sis
/proc/iomem: 00000000-0000ffff : reserved
/proc/iomem: 00010000-0009f7ff : System RAM
/proc/iomem: 0009f800-0009ffff : reserved
/proc/iomem: 000a0000-000bffff : Video RAM area
/proc/iomem: 000c0000-000cf7ff : Video ROM
/proc/iomem: 000cf800-000cffff : pnp 00:00
/proc/iomem: 000f0000-000fffff : reserved
/proc/iomem:   000f0000-000fffff : System ROM
/proc/iomem: 00100000-5fedffff : System RAM
/proc/iomem:   00100000-00591292 : Kernel code
/proc/iomem:   00591293-007a2e87 : Kernel data
/proc/iomem:   0084d000-008dbeb7 : Kernel bss
/proc/iomem: 5fee0000-5fee2fff : ACPI Non-volatile Storage
/proc/iomem: 5fee3000-5feeffff : ACPI Tables
/proc/iomem: 5fef0000-5fefffff : reserved
/proc/iomem: 5ff00000-5fffffff : RAM buffer
/proc/iomem: 60000000-6001ffff : 0000:00:04.0
/proc/iomem: d0000000-dfffffff : PCI Bus 0000:01
/proc/iomem:   d0000000-dfffffff : 0000:01:00.0
/proc/iomem: e0000000-e7ffffff : 0000:00:00.0
/proc/iomem:   e0000000-e7ffffff : aperture
/proc/iomem: e8000000-e9ffffff : PCI Bus 0000:01
/proc/iomem:   e8000000-e8ffffff : 0000:01:00.0
/proc/iomem:   e9000000-e901ffff : 0000:01:00.0
/proc/iomem: ea020000-ea020fff : 0000:00:03.1
/proc/iomem:   ea020000-ea020fff : ohci_hcd
/proc/iomem: ea021000-ea021fff : 0000:00:03.2
/proc/iomem:   ea021000-ea021fff : ohci_hcd
/proc/iomem: ea022000-ea022fff : 0000:00:03.3
/proc/iomem:   ea022000-ea022fff : ehci_hcd
/proc/iomem: ea023000-ea023fff : 0000:00:04.0
/proc/iomem:   ea023000-ea023fff : sis900
/proc/iomem: ea024000-ea024fff : 0000:00:03.0
/proc/iomem:   ea024000-ea024fff : ohci_hcd
/proc/iomem: fec00000-fec00fff : IOAPIC 0
/proc/iomem:   fec00000-fec00fff : reserved
/proc/iomem: fee00000-fee00fff : Local APIC
/proc/iomem:   fee00000-fee00fff : reserved
/proc/iomem: ffee0000-ffefffff : pnp 00:00
/proc/iomem: fffe0000-fffeffff : pnp 00:00
/proc/iomem: ffff0000-ffffffff : reserved
/proc/iomem:   ffff0000-ffffffff : pnp 00:00
/proc/interrupts:            CPU0       
/proc/interrupts:   0:         49   IO-APIC-edge      timer
/proc/interrupts:   1:      47194   IO-APIC-edge      i8042
/proc/interrupts:   3:          2   IO-APIC-edge    
/proc/interrupts:   4:          2   IO-APIC-edge    
/proc/interrupts:   6:          2   IO-APIC-edge      floppy
/proc/interrupts:   7:          1   IO-APIC-edge      parport0
/proc/interrupts:   8:          0   IO-APIC-edge      rtc0
/proc/interrupts:   9:          0   IO-APIC-fasteoi   acpi
/proc/interrupts:  14:    2683719   IO-APIC-edge      pata_sis
/proc/interrupts:  15:    1086969   IO-APIC-edge      pata_sis
/proc/interrupts:  16:          1   IO-APIC-fasteoi   nouveau
/proc/interrupts:  17:          0   IO-APIC-fasteoi   sata_sis
/proc/interrupts:  18:      41844   IO-APIC-fasteoi   SiS SI7012
/proc/interrupts:  19:    2087413   IO-APIC-fasteoi   eth0
/proc/interrupts:  20:     670512   IO-APIC-fasteoi   ohci_hcd:usb2
/proc/interrupts:  21:         74   IO-APIC-fasteoi   ohci_hcd:usb3
/proc/interrupts:  22:          0   IO-APIC-fasteoi   ohci_hcd:usb4
/proc/interrupts:  23:   18687794   IO-APIC-fasteoi   ehci_hcd:usb1
/proc/interrupts: NMI:          0   Non-maskable interrupts
/proc/interrupts: LOC:   17970347   Local timer interrupts
/proc/interrupts: SPU:          0   Spurious interrupts
/proc/interrupts: PMI:          0   Performance monitoring interrupts
/proc/interrupts: PND:          0   Performance pending work
/proc/interrupts: RES:          0   Rescheduling interrupts
/proc/interrupts: CAL:          0   Function call interrupts
/proc/interrupts: TLB:          0   TLB shootdowns
/proc/interrupts: TRM:          0   Thermal event interrupts
/proc/interrupts: THR:          0   Threshold APIC interrupts
/proc/interrupts: MCE:          0   Machine check exceptions
/proc/interrupts: MCP:        358   Machine check polls
/proc/interrupts: ERR:          1
/proc/interrupts: MIS:          0
/proc/meminfo: MemTotal:        1543008 kB
/proc/meminfo: MemFree:           53216 kB
/proc/meminfo: Buffers:           45860 kB
/proc/meminfo: Cached:           512128 kB
/proc/meminfo: SwapCached:        16612 kB
/proc/meminfo: Active:           710940 kB
/proc/meminfo: Inactive:         715772 kB
/proc/meminfo: Active(anon):     426232 kB
/proc/meminfo: Inactive(anon):   465264 kB
/proc/meminfo: Active(file):     284708 kB
/proc/meminfo: Inactive(file):   250508 kB
/proc/meminfo: Unevictable:           0 kB
/proc/meminfo: Mlocked:               0 kB
/proc/meminfo: HighTotal:        662408 kB
/proc/meminfo: HighFree:           5704 kB
/proc/meminfo: LowTotal:         880600 kB
/proc/meminfo: LowFree:           47512 kB
/proc/meminfo: SwapTotal:       4519928 kB
/proc/meminfo: SwapFree:        4449076 kB
/proc/meminfo: Dirty:              1148 kB
/proc/meminfo: Writeback:             0 kB
/proc/meminfo: AnonPages:        866440 kB
/proc/meminfo: Mapped:           141200 kB
/proc/meminfo: Shmem:             22772 kB
/proc/meminfo: Slab:              35148 kB
/proc/meminfo: SReclaimable:      24468 kB
/proc/meminfo: SUnreclaim:        10680 kB
/proc/meminfo: KernelStack:        2744 kB
/proc/meminfo: PageTables:        10568 kB
/proc/meminfo: NFS_Unstable:          0 kB
/proc/meminfo: Bounce:                0 kB
/proc/meminfo: WritebackTmp:          0 kB
/proc/meminfo: CommitLimit:     5291432 kB
/proc/meminfo: Committed_AS:    2207352 kB
/proc/meminfo: VmallocTotal:     122880 kB
/proc/meminfo: VmallocUsed:       28696 kB
/proc/meminfo: VmallocChunk:      87764 kB
/proc/meminfo: HardwareCorrupted:     0 kB
/proc/meminfo: HugePages_Total:       0
/proc/meminfo: HugePages_Free:        0
/proc/meminfo: HugePages_Rsvd:        0
/proc/meminfo: HugePages_Surp:        0
/proc/meminfo: Hugepagesize:       4096 kB
/proc/meminfo: DirectMap4k:       16376 kB
/proc/meminfo: DirectMap4M:      892928 kB
/proc/bus/input/devices: I: Bus=0019 Vendor=0000 Product=0001 Version=0000
/proc/bus/input/devices: N: Name="Power Button"
/proc/bus/input/devices: P: Phys=PNP0C0C/button/input0
/proc/bus/input/devices: S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
/proc/bus/input/devices: U: Uniq=
/proc/bus/input/devices: H: Handlers=kbd event0 
/proc/bus/input/devices: B: EV=3
/proc/bus/input/devices: B: KEY=100000 0 0 0
/proc/bus/input/devices: 
/proc/bus/input/devices: I: Bus=0019 Vendor=0000 Product=0001 Version=0000
/proc/bus/input/devices: N: Name="Power Button"
/proc/bus/input/devices: P: Phys=LNXPWRBN/button/input0
/proc/bus/input/devices: S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
/proc/bus/input/devices: U: Uniq=
/proc/bus/input/devices: H: Handlers=kbd event1 
/proc/bus/input/devices: B: EV=3
/proc/bus/input/devices: B: KEY=100000 0 0 0
/proc/bus/input/devices: 
/proc/bus/input/devices: I: Bus=0017 Vendor=0001 Product=0001 Version=0100
/proc/bus/input/devices: N: Name="Macintosh mouse button emulation"
/proc/bus/input/devices: P: Phys=
/proc/bus/input/devices: S: Sysfs=/devices/virtual/input/input2
/proc/bus/input/devices: U: Uniq=
/proc/bus/input/devices: H: Handlers=mouse0 event2 
/proc/bus/input/devices: B: EV=7
/proc/bus/input/devices: B: KEY=70000 0 0 0 0 0 0 0 0
/proc/bus/input/devices: B: REL=3
/proc/bus/input/devices: 
/proc/bus/input/devices: I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
/proc/bus/input/devices: N: Name="AT Translated Set 2 keyboard"
/proc/bus/input/devices: P: Phys=isa0060/serio0/input0
/proc/bus/input/devices: S: Sysfs=/devices/platform/i8042/serio0/input/input3
/proc/bus/input/devices: U: Uniq=
/proc/bus/input/devices: H: Handlers=kbd event3 
/proc/bus/input/devices: B: EV=120013
/proc/bus/input/devices: B: KEY=4 2000000 3803078 f800d001 feffffdf ffefffff ffffffff fffffffe
/proc/bus/input/devices: B: MSC=10
/proc/bus/input/devices: B: LED=7
/proc/bus/input/devices: 
/proc/bus/input/devices: I: Bus=0003 Vendor=09da Product=0006 Version=0100
/proc/bus/input/devices: N: Name="A4Tech USB Optical Mouse"
/proc/bus/input/devices: P: Phys=usb-0000:00:03.0-2/input0
/proc/bus/input/devices: S: Sysfs=/devices/pci0000:00/0000:00:03.0/usb2/2-2/2-2:1.0/input/input4
/proc/bus/input/devices: U: Uniq=
/proc/bus/input/devices: H: Handlers=mouse1 event4 
/proc/bus/input/devices: B: EV=17
/proc/bus/input/devices: B: KEY=3f0000 0 0 0 0 0 0 0 0
/proc/bus/input/devices: B: REL=143
/proc/bus/input/devices: B: MSC=10
/proc/bus/input/devices: 
dmidecode: /dev/mem: Permission denied
dmidecode: # dmidecode 2.9
nnjond@nnjond-desktop:~$

---

