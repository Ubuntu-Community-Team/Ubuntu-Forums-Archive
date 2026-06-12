---
title: "Frustrated - No WiFi detected"
date: 2011-02-19
forum: New to Ubuntu
---

### Post by trevarez on 2011-02-19
Hello,

I bought a Toshiba laptop C660 D which runs on Windows 7. I installed Ubuntu 10.04.2 on it, the newer version didn't work.
It is not possible to connect to the wireless network as it doesn't even detect it.
I downloaded the driver for linux from the realtek website, opened the windows location in ubuntu and copied it into my home window.
It seems like I need to know more about computers than I actually do, I cannot make it work, also I have to switch it off and restart in Windows every time I want to use the internet in order to get help. Very frustrating.
Any answers and suggestions in plain English would be appreciated!

Many thanks,
Kai

---

### Post by ronnielsen1 on 2011-02-19
> 
I bought a Toshiba laptop C660 D which runs on Windows 7.Yeah, it probably came with that installed. A laptop coming installed with Linux will also work good.

Can you post the output of lspci -v from a terminal?

---

### Post by lkraemer on 2011-02-19
Open a Terminal Window (Console) and use these commands to get more
information on your hardware, wireless, Windows loaded drivers, and
Linux drivers that are currently blacklisted. Copy & Paste to prevent
errors!

```

lspci
lsusb
lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist.conf
iwconfig

```
iwconfig will show what the wireless is detected as......wlan0, ath0, etc.
post the output of each command........


lk

---

### Post by PaulReaver on 2011-02-19
is that the one with the atheros AR5007EG wifi card?



is it not possible for the computer to detect the wifi network?

or

is it not possible for ubuntu to detect the wifi card?


run lspci in a terminal and post the output please :)

---

### Post by trevarez on 2011-02-22
I have figured out that the wired connection works, but the computer does not recognise the wifi adapter.
I have downloaded what I hope to be the right driver for it, a file called 

rtl8192ce_linux_2.6.0005.1116.2010

but what do I do with it? Where do I download it to? Here is the lspci output:

kai@kai-laptop:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: Toshiba America Info Systems Device 9602
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
kai@kai-laptop:~$

---

### Post by trevarez on 2011-02-22
kai@kai-laptop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 04f2:b1d6 Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
kai@kai-laptop:~$ lshw
WARNING: you should run this program as super-user.
kai-laptop                
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2767MiB
     *-cpu
          product: AMD Athlon(tm) II P340 Dual-Core Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 15.6.3
          size: 800MHz
          capacity: 800MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a 3dnowprefetch osvw ibs skinit wdt nodeid_msr cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-pci:0
          description: Host bridge
          product: RS780 Host Bridge Alternate
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=32
        *-pci:0
             description: PCI bridge
             product: Toshiba America Info Systems
             vendor: Toshiba America Info Systems
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master cap_list
             resources: ioport:e000(size=4096) memory:ff400000-ff5fffff ioport:c0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: M880G [Mobility Radeon HD 4200]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:18 memory:c0000000-cfffffff(prefetchable) ioport:e000(size=256) memory:ff500000-ff50ffff memory:ff400000-ff4fffff
        *-pci:1
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 2)
             vendor: Advanced Micro Devices [AMD]
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:d000(size=4096) memory:ff600000-ff6fffff
           *-network UNCLAIMED
                description: Network controller
                product: Realtek Semiconductor Co., Ltd.
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0
                resources: ioport:d000(size=256) memory:ff600000-ff603fff
        *-pci:2
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 3)
             vendor: Advanced Micro Devices [AMD]
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:c000(size=4096) ioport:d0100000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 05
                serial: 88:ae:1d:ea:ba:3b
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.107 latency=0 multicast=yes
                resources: irq:27 ioport:c000(size=256) memory:d0104000-d0104fff(prefetchable) memory:d0100000-d0103fff(prefetchable)
        *-storage
             description: SATA controller
             product: SB700/SB800 SATA Controller [AHCI mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage bus_master cap_list
             configuration: driver=ahci latency=32
             resources: irq:26 ioport:f040(size=8) ioport:f030(size=4) ioport:f020(size=8) ioport:f010(size=4) ioport:f000(size=16) memory:ff708000-ff7083ff
        *-usb:0
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:ff707000-ff707fff
        *-usb:1
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:ff706000-ff7060ff
        *-usb:2
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:ff705000-ff705fff
        *-usb:3
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:ff704000-ff7040ff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 42
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 40
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=32
             resources: irq:16 memory:ff700000-ff703fff
        *-isa
             description: ISA bridge
             product: SB700/SB800 LPC host controller
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master vga_palette
     *-pci:1
          description: Host bridge
          product: K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K10 [Opteron, Athlon64, Sempron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K10 [Opteron, Athlon64, Sempron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K10 [Opteron, Athlon64, Sempron] Link Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
  *-scsi:0
       physical id: 1
       bus info: scsi@6
       logical name: scsi6
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-scsi:1
       physical id: 2
       bus info: scsi@7
       logical name: scsi7
       capabilities: scsi-host
       configuration: driver=usb-storage
kai@kai-laptop:~$

---

### Post by trevarez on 2011-02-22
kai@kai-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: ioport:d000(size=256) memory:ff600000-ff603fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 05
       serial: 88:ae:1d:ea:ba:3b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.107 latency=0 multicast=yes
       resources: irq:27 ioport:c000(size=256) memory:d0104000-d0104fff(prefetchable) memory:d0100000-d0103fff(prefetchable)
kai@kai-laptop:~$

---

### Post by trevarez on 2011-02-22
kai@kai-laptop:~$ ndiswrapper -l
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
kai@kai-laptop:~$

---

### Post by trevarez on 2011-02-22
kai@kai-laptop:~$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
kai@kai-laptop:~$

---

### Post by trevarez on 2011-02-22
kai@kai-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

kai@kai-laptop:~$

---

### Post by trevarez on 2011-02-22
All this means very little to me and I really appreciate all your help!

Many thanks in advance,
Kai

---

### Post by bkratz on 2011-02-22
Look at posts 29 and 30 of this thread

[http://ubuntuforums.org/showthread.php?t=1689148&page=3](http://ubuntuforums.org/showthread.php?t=1689148&page=3)


Actually the whole thread is pretty good

---

### Post by trevarez on 2011-02-23
Thanks for the reply, I have followed most of the instructions by the letter but struggle somewhat with this one:

[I]Last but not least, edit /etc/modprobe.d/blacklist.conf using whatever program you want, and add these lines :
Code:

blacklist rtl8192e_pci
blacklist rtl8192se_pci[/I] 


Can anyone clarify and tell me what exact;y the code has to look like?

Many thanks,
Kai

---

### Post by trevarez on 2011-02-23
kai@kai-laptop:~$ iwconfig lo
lo        no wireless extensions.

kai@kai-laptop:~$ iwconfig eth0
eth0      no wireless extensions.

kai@kai-laptop:~$ iwconfig wlan0
wlan0     No such device

kai@kai-laptop:~$

---

### Post by alphacrucis2 on 2011-02-23
> **trevarez said:**
> Thanks for the reply, I have followed most of the instructions by the letter but struggle somewhat with this one:

[I]Last but not least, edit /etc/modprobe.d/blacklist.conf using whatever program you want, and add these lines :
Code:

blacklist rtl8192e_pci
blacklist rtl8192se_pci[/I] 


Can anyone clarify and tell me what exact;y the code has to look like?

Many thanks,
Kai


```
gksudo gedit /etc/modprobe.d/blacklist.conf
```

You will most likely find a number of modules already blacklisted in that file so you can see for comparison. Just insert the extra two lines into the file:

```
blacklist rtl8192e_pci
blacklist rtl8192se_pci
```

and then save the file. You will then need to reboot for this to have any effect.

---

### Post by trevarez on 2011-02-23
Like this?

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

blacklist rtl8192e_pci
blacklist rtl8192se_pci

---

### Post by trevarez on 2011-02-23
"ugly and loud noise" I see you guys have a healthy sense of humour ;-)

---

### Post by trevarez on 2011-02-23
It still doesn't detect the network. Do I need to delete the two lines?

---

### Post by walt.smith1960 on 2011-02-23
> **trevarez said:**
> It still doesn't detect the network. Do I need to delete the two lines?

Based on the other thread, you just need to edit those two lines. 
```
gksudo gedit /etc/modprobe.d/blacklist.conf
```then change  "rtl8192e_pci"  to "r8192e_pci"
  change "rtl8192se_pci" to "r8192se_pci"

and save 

This is the gist of #33 in the previously mentioned thread.

Here's just a thought if none of your other efforts pan out.  Try to download and create a LiveCD of Natty Alpha2.  It's still pretty crude but seems to support OOB* WiFi adapters that are problematic in earlier versions.  If that works and I were you, I'd enable wireless backports in Maverick if you haven't already.  Enabling backports may or may not work with the other mods you've made unless you're able to reverse those changes.  I'd probably start with Natty though--you can do that without making any changes to your existing installation.

*out of the box

---

### Post by trevarez on 2011-02-23
Thanks for the clarification. I have done that now, but still no change. This is what is looks like. When I referred to deleting those two lines, I actually meant to say: delete the space between those two new lines. Now I changed the rtl to r - should I change back to rtl and try the natty approach? Is this even the right name for the driver or whatever it is I am blacklisting?

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist r8192e_pci
blacklist r8192se_pci


Many thanks,
Kai

---

### Post by walt.smith1960 on 2011-02-23
Sorry to hear you're still having problems.  If you download the Natty liveCD, it will run entirely off the CD and is not dependent on your current installation.  You will need to be sure your machine will boot off the CD before the hard drive.

---

### Post by bodhi.zazen on 2011-02-23
After making those edits, reboot.

---

### Post by bodhi.zazen on 2011-02-23
> **ronnielsen1 said:**
> Yeah, it probably came with that installed. A laptop coming installed with Linux will also work good.

Can you post the output of lspci -v from a terminal?

> **lkraemer said:**
> Open a Terminal Window (Console) and use these commands to get more
information on your hardware, wireless, Windows loaded drivers, and
Linux drivers that are currently blacklisted. Copy & Paste to prevent
errors!

```

lspci
lsusb
lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist.conf
iwconfig

```
iwconfig will show what the wireless is detected as......wlan0, ath0, etc.
post the output of each command........


lk

Looking back at this thread, when requesting such information (lengthy output from multiple commands) please consider either :

1. Use grep to shorten the output to the relevant information.

2. Advising the OP attach the output as a file.

3. Explain what output you are looking for.

This way the OP does not post lengthy unnecessary output, which is a bit of a hassle to post and makes the thread difficult to read.

---

### Post by trevarez on 2011-02-27
I just tried this command again:

kai@kai-laptop:~$ lspci -v
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
    Subsystem: Toshiba America Info Systems Device fd3c
    Flags: bus master, 66MHz, medium devsel, latency 32
    Capabilities: <access denied>

00:01.0 PCI bridge: Toshiba America Info Systems Device 9602
    Flags: bus master, 66MHz, medium devsel, latency 32
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: ff400000-ff5fffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
    Capabilities: <access denied>
    Kernel modules: shpchp

00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: ff600000-ff6fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Prefetchable memory behind bridge: 00000000d0100000-00000000d01fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] (prog-if 01)
    Subsystem: Toshiba America Info Systems Device fd3c
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 26
    I/O ports at f040 [size=8]
    I/O ports at f030 [size=4]
    I/O ports at f020 [size=8]
    I/O ports at f010 [size=4]
    I/O ports at f000 [size=16]
    Memory at ff708000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
    Subsystem: Toshiba America Info Systems Device fd3c
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at ff707000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
    Subsystem: Toshiba America Info Systems Device fd3c
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at ff706000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
    Subsystem: Toshiba America Info Systems Device fd3c
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at ff705000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
    Subsystem: Toshiba America Info Systems Device fd3c
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at ff704000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
    Flags: 66MHz, medium devsel
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c-piix4

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
    Subsystem: Toshiba America Info Systems Device fd3c
    Flags: bus master, slow devsel, latency 32, IRQ 16
    Memory at ff700000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
    Subsystem: Toshiba America Info Systems Device fd3c
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40) (prog-if 01)
    Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=64

00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
    Flags: fast devsel
    Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
    Flags: fast devsel
    Capabilities: <access denied>

00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
    Flags: fast devsel

01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
    Subsystem: Toshiba America Info Systems Device fd3c
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at e000 [size=256]
    Memory at ff500000 (32-bit, non-prefetchable) [size=64K]
    Memory at ff400000 (32-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeon

02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device 8181
    Flags: bus master, fast devsel, latency 0, IRQ 11
    I/O ports at d000 [size=256]
    Memory at ff600000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
    Subsystem: Toshiba America Info Systems Device fd3c
    Flags: bus master, fast devsel, latency 0, IRQ 27
    I/O ports at c000 [size=256]
    Memory at d0104000 (64-bit, prefetchable) [size=4K]
    Memory at d0100000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

kai@kai-laptop:~$ 

It looks like it lists all the components of the laptop, but why is access denied? How can I override that?

Kai

---

### Post by fidodido222 on 2011-02-27
update the system then go to additional drivers in administration and activate your wireless then try again 
Hope it works :)

---

### Post by trevarez on 2011-02-27
I can't find "additional drivers" in Administration. There is only "Hardware Drivers"...

---

### Post by trevarez on 2011-02-27
I have solved the problem thanks to this post by ELEE:
[http://ubuntuforums.org/showthread.php?t=1689148&page=3](http://ubuntuforums.org/showthread.php?t=1689148&page=3)

[I]I am now wireless... I found this answer it worked for me.....:grin:

BY [COLOR=Blue] canucked[/COLOR]
on this thread
[COLOR=Red]Re: toshiba L655, 10.10 wireless card issues[/COLOR]


[COLOR=Navy]sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms[/COLOR]

I rebooted and I am wireless.... I do not understand.... just kept looking[/I]      

Thanks to everyone for their support and help!

Kai

---

### Post by walt.smith1960 on 2011-03-01
excellent!!  Persistence wins again :).

---

