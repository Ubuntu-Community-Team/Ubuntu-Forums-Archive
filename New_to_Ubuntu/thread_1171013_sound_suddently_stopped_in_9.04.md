---
title: "sound suddently stopped in 9.04"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by gordonsmall@bellsouth.net on 2009-05-26
The sound had been working just fine on my Ubuntu 9.04 (AMD 64).  However, it suddenly stopped making any sounds - even when logging on.  The speaker volume is up, and I have tried to get sound from any sources with no luck.

Any ideas?

Gordon Small

---

### Post by zeroseven0183 on 2009-05-27
What is the last thing you did before this issue happen?

---

### Post by shifty_powers on 2009-05-27
have you checked alsamixer? (in a terminal)

---

### Post by gordonsmall@bellsouth.net on 2009-05-27
The last thing I did before the sound went was reading my e-mail, and opened up a youtube video. Video was fine, but the sound was not there.  Got checking then, and found I had no sound.

BTW, I have a dual boot machine with Windows - sound is fine in Windows, so presume that addresses hardware issues.

Gordon

---

### Post by gordonsmall@bellsouth.net on 2009-05-27
Hmmm - I am pretty much of a Newbie here.  I did go to System/Preferences/Sound. I found that the Sound Events, Music and Movies, and Audio Conferencing (Sound Playback) were all set on Autodetect which is what I believe they were set on when the sound was working.  I tried a few other settings, but no other setting would produce a test sound either, so I put them back on Autodetect.

I had also searched the Internet for possible solutions, and added a suggested line of code to the bottom of the Alsa file, but no change.

Gordon

---

### Post by nandemonai on 2009-05-27
What sound chip are you running?

In terminal:

```
lspci | grep Audio
```

Post the output please.

---

### Post by NHArticleTen on 2009-05-27
totally off-topic, but relevant nevertheless...

for what it's worth...

email address harvesters are going wild here...

your mileage may vary...

---

### Post by jackmetal on 2009-05-27
I just had the same thing happen.  

Sound was working fine last night.  Noticed sound didn't work a little bit ago and tried a reboot.  Still same issue....No sound!  REALLY weird!

I'll let you know if I find the issue on mine.

-edit-

OK, found my issue.  This is dang strange, as I had made absolutely NO CHANGES at all.  
I checked my alsamixer settings (all was correct)
Checked my sound settings under System>Preferences (changed my default mixer to the correct setting, changed all other options from AutoDetect to PulseAudio; then made sure my mixer was also set correctly in volume properties and checked "ALL" other mixer options for any that were Muted).

Sounds is back!  I wish I knew what happened to change it.  The ONLY thing I had done before I lost sound, is sudo aptitude update and sudo aptitude upgrade.  WEIRD!!!

---

### Post by gordonsmall@bellsouth.net on 2009-05-28
I entered the lspci | grep Audio command in the terminal, and nothing happened. Just went back to the command prompt.

Gordon

---

### Post by nandemonai on 2009-05-28
> **gordonsmall@bellsouth.net said:**
> I entered the lspci | grep Audio command in the terminal, and nothing happened. Just went back to the command prompt.

Gordon

That's odd. Maybe it's not picking up the sound chip for some reason..

Try pasting the output of:

```
lspci
```

and

```
lshw
```

---

### Post by gordonsmall@bellsouth.net on 2009-05-29
Here is what I got with lspci - 

gordonsmall@gordonsmall-desktop:~$ lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GS] (rev a1)
05:07.0 Serial controller: 3Com Corp, Modem Division 56K FaxModem Model 5610 (rev 01)
05:08.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value
05:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
gordonsmall@gordonsmall-desktop:~$ 

Here is what I got with lshw -

gordonsmall@gordonsmall-desktop:~$ lshw
WARNING: you should run this program as super-user.
gordonsmall-desktop       
    description: Computer
    width: 64 bits
    capabilities: vsyscall64 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory:0
          description: System memory
          physical id: 3
          size: 1023MiB
     *-cpu
          product: AMD Athlon(tm) 64 Processor 3800+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up rep_good pni lahf_lm
     *-memory:1 UNCLAIMED
          description: Memory controller
          product: CK804 Memory Controller
          vendor: nVidia Corporation
          physical id: 0
          bus info: pci@0000:00:00.0
          version: a3
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: CK804 ISA Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: CK804 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: cap_list
          configuration: driver=nForce2_smbus latency=0 maxlatency=1 mingnt=3 module=i2c_nforce2
     *-usb:0
          description: USB Controller
          product: CK804 USB Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
     *-usb:1
          description: USB Controller
          product: CK804 USB Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
     *-ide:0
          description: IDE interface
          product: CK804 IDE
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          version: f2
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
     *-ide:1
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
     *-ide:2
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
     *-pci:0
          description: PCI bridge
          product: CK804 PCI Bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci bus_master
        *-communication
             description: Serial controller
             product: 56K FaxModem Model 5610
             vendor: 3Com Corp, Modem Division
             physical id: 7
             bus info: pci@0000:05:07.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: driver=serial latency=0
        *-multimedia
             description: Multimedia audio controller
             product: SB0400 Audigy2 Value
             vendor: Creative Labs
             physical id: 8
             bus info: pci@0000:05:08.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=EMU10K1_Audigy latency=32 maxlatency=20 mingnt=2 module=snd_emu10k1
        *-firewire
             description: FireWire (IEEE 1394)
             product: TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
             vendor: Texas Instruments
             physical id: b
             bus info: pci@0000:05:0b.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2 module=ohci1394
     *-bridge
          description: Ethernet interface
          product: CK804 Ethernet Controller
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          logical name: eth0
          version: a3
          serial: 00:17:31:15:3d:90
          width: 32 bits
          clock: 66MHz
          capabilities: bridge bus_master cap_list ethernet physical
          configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.2.2 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
     *-pci:1
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:2
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:3
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:4
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci bus_master cap_list
          configuration: driver=pcieport-driver
        *-display UNCLAIMED
             description: VGA compatible controller
             product: G70 [GeForce 7600 GS]
             vendor: nVidia Corporation
             physical id: 0
             bus info: pci@0000:01:00.0
             version: a1
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
  *-scsi
       physical id: 1
       bus info: scsi@6
       logical name: scsi6
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 26:5b:bd:13:62:79
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
gordonsmall@gordonsmall-desktop:~$

---

### Post by mxboy15u on 2009-05-29
This happened to both of my Jaunty computers yesterday. I fixed it by hitting the "test" button under sound preferences. For whatever reason that made sound work on flash videos. Strange it happened to both my computers about an hour apart.

---

### Post by nandemonai on 2009-05-29
> **gordonsmall@bellsouth.net said:**
>  
05:08.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value

        *-multimedia
             description: Multimedia audio controller
             product: SB0400 Audigy2 Value
             vendor: Creative Labs
             physical id: 8
             bus info: pci@0000:05:08.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=EMU10K1_Audigy latency=32 

Well there it is, and it has been picked up along with a module loaded. Are you certain all your mixer levels are turned up and output isn't muted as suggested earlier in this thread? Another thing to check would be your cabling to the speakers or stereo depending how you have it hooked up. 

Other than that not too sure. You can confirm the pulse audio daemon is running with this command:

```
ps -A | grep pulse
```

---

### Post by gordonsmall@bellsouth.net on 2009-05-30
Here is the result of entering the lspci command:

gordonsmall@gordonsmall-desktop:~$ lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GS] (rev a1)
05:07.0 Serial controller: 3Com Corp, Modem Division 56K FaxModem Model 5610 (rev 01)
05:08.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value
05:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
gordonsmall@gordonsmall-desktop:~$ 

Here is the result from the lshw command:

gordonsmall@gordonsmall-desktop:~$ lshw
WARNING: you should run this program as super-user.
gordonsmall-desktop       
    description: Computer
    width: 64 bits
    capabilities: vsyscall64 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory:0
          description: System memory
          physical id: 3
          size: 1023MiB
     *-cpu
          product: AMD Athlon(tm) 64 Processor 3800+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up rep_good pni lahf_lm
     *-memory:1 UNCLAIMED
          description: Memory controller
          product: CK804 Memory Controller
          vendor: nVidia Corporation
          physical id: 0
          bus info: pci@0000:00:00.0
          version: a3
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: CK804 ISA Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: CK804 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: cap_list
          configuration: driver=nForce2_smbus latency=0 maxlatency=1 mingnt=3 module=i2c_nforce2
     *-usb:0
          description: USB Controller
          product: CK804 USB Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
     *-usb:1
          description: USB Controller
          product: CK804 USB Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
     *-ide:0
          description: IDE interface
          product: CK804 IDE
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          version: f2
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
     *-ide:1
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
     *-ide:2
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
     *-pci:0
          description: PCI bridge
          product: CK804 PCI Bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci bus_master
        *-communication
             description: Serial controller
             product: 56K FaxModem Model 5610
             vendor: 3Com Corp, Modem Division
             physical id: 7
             bus info: pci@0000:05:07.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: driver=serial latency=0
        *-multimedia
             description: Multimedia audio controller
             product: SB0400 Audigy2 Value
             vendor: Creative Labs
             physical id: 8
             bus info: pci@0000:05:08.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=EMU10K1_Audigy latency=32 maxlatency=20 mingnt=2 module=snd_emu10k1
        *-firewire
             description: FireWire (IEEE 1394)
             product: TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
             vendor: Texas Instruments
             physical id: b
             bus info: pci@0000:05:0b.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2 module=ohci1394
     *-bridge
          description: Ethernet interface
          product: CK804 Ethernet Controller
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          logical name: eth0
          version: a3
          serial: 00:17:31:15:3d:90
          width: 32 bits
          clock: 66MHz
          capabilities: bridge bus_master cap_list ethernet physical
          configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.2.2 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
     *-pci:1
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:2
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:3
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:4
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci bus_master cap_list
          configuration: driver=pcieport-driver
        *-display UNCLAIMED
             description: VGA compatible controller
             product: G70 [GeForce 7600 GS]
             vendor: nVidia Corporation
             physical id: 0
             bus info: pci@0000:01:00.0
             version: a1
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
  *-scsi
       physical id: 1
       bus info: scsi@6
       logical name: scsi6
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 2a:20:5d:ae:a5:f5
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
gordonsmall@gordonsmall-desktop:~$

---

### Post by gordonsmall@bellsouth.net on 2009-06-29
> **nandemonai said:**
> Well there it is, and it has been picked up along with a module loaded. Are you certain all your mixer levels are turned up and output isn't muted as suggested earlier in this thread? Another thing to check would be your cabling to the speakers or stereo depending how you have it hooked up. 

Other than that not too sure. You can confirm the pulse audio daemon is running with this command:

```
ps -A | grep pulse
```
Been out of town - unfortunately the sound did not fix itself in my absence:)

Here is what I get when I checked pulse audio:

gordonsmall@gordonsmall-desktop:~$ ps -A | grep pulse
 3181 ?        00:00:01 pulseaudio
gordonsmall@gordonsmall-desktop:~$ 


The question mark looks interesting - does this tell you anything about where to look next?

Gordon

---

### Post by jackmetal on 2009-07-14
There's a few things you can try.  

1) from a terminal, run ***alsamixer***
   and make sure that nothing it muted.
2) Check your sound settings under System>Preferences
   and just for the heck of it, do like _mxboy15u_ and press "Test" to see if you hear any sound.  If you still don't, verify that the correct Mixer is set and maybe change the options from "Auto Detect" to "Pulse Audio"
3) Open the Volume Applet (in the system tray), select the correct device and make sure nothing is muted there either.  On mine, Just to be safe (when this issue popped up for me a while back) I selected each one of the devices and made sure that NONE of them were muted.  ;-)

This fixed it for me..  I'm not sure how it happened, but 'apparently' the configuration changed after an update and a few of the devices were muted on mine.  At least that's what the issue was on mine when this occurred.  Your configuration (from what I see) looks fine, so hopefully this 'might' help you get sound back.

---

### Post by gordonsmall@bellsouth.net on 2009-08-15
Shortly after the last post I restored the audio by the process I have copied below.  Everything has been fine until yesterday, and the sound disappeared again.  I am confident that this is being done by a certain updates.  However, I don't know which updates would be the likely villian, and I also can't find a way to identify or find all the recent updates.I would like to try to be able to remove recent updates until the sound comes back.Can this be done?

Here is the process that worked last time - but not this time.

Gordon Small

Getting the ALSA drivers from a *fresh* kernel

Sometimes, sound might be configured correctly, but for some reason or another (tinkering) it stops working. One way to go back to the old setup is to reinstall Ubuntu. However, this step is actually quite unnecessary since you are reinstalling everything because of one thing.

A faster way, is to just remove the problematic packages and reinstall them cleanly.

(1) Remove these packages
Code:

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils


(2) Reinstall those same packages
Code:

sudo apt-get install linux-sound-base alsa-base alsa-utils

[list][*]
VERY IMPORTANT NOTE: Ubuntu (GNOME) users have reported that packages 'gdm' and 'ubuntu-desktop' are removed after removing the linux-sound-base packages. If this happens, then do the following
Code:

sudo apt-get install gdm ubuntu-desktop


(3) Reboot
[*][left]
VERY IMPORTANT NOTE: Xubuntu (XFCE) users have reported that packages 'gdm' and 'xubuntu-desktop' are removed after removing the linux-sound-base packages. If this happens, then do the following
Code:

sudo apt-get install gdm xubuntu-desktop


(3) Reboot
Now you may ask "I already had the packages, so why did I go through the trouble of removing them, then installing them". The answer lies in the --purge option which removes all the extra information that accumulated from tinkering and upgrading. After doing a purge then install, the packages are unpackaged as if it they are brand new.
(4) At this point, try using
Code:

 aplay -l

you should get your soundcard listed.

    * Success - Your soundcard is detected. Go onto the Using alsamixer section, then try playing something on your music or media player.
    * Failure - Your card was not detected. You should try compiling your driver, so go onto ALSA drive Compilation.

---

### Post by lenn-art on 2009-08-18
Some days ago, my sound stopped too. 

I followed above instructions (reinstall Alsa) with no succes. If i enter aplay -l, i see my card listed (as DAC, 2nd DAC and PCI). Everything is on, nothing muted (also not with CLI > alsamixer). 

What could be wrong? :confused:

What kind of sound should you hear when you play test? Selecting DAC on the analog boxes gives a loud annoying beep and poor sound on MP3's

---

### Post by lenn-art on 2009-08-18
ps -A | grep pulse =>

3552 ?        00:00:02 pulseaudio

Also an ?. Like Gordon said before: a clue?

---

