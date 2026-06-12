---
title: "Can i tell in advance if upgrade will break something?"
date: 2008-11-09
forum: Networking &amp; Wireless
---

### Post by zenithdave on 2008-11-09
Hello, i have installed 4 different distros today to see how the wireless is affected on my eee 900 (ath242 wireless adapter)

All got the wireless working OOTB then i did the updates, yes i have been sat around a lot today watching installs.

All broke the wireless after updates!!!!!! so i have stopped updating. How can i find out how which part of update does the damage so i can switch it off, or shall i just not update?

In tried

eeeubuntu, ubuntu 8:10 and 8:04 , xubuntu.

Thanks in advance for your patience for silly questions.

---

### Post by mapes12 on 2008-11-09
IMHO stay with 8.04 LTS for the time being.

Did the different versions all work with your wifi prior to updating?

Try posting the output to:

```
iwconfig
```

```
sudo lshw
```

and I'm sure the network wizards on the forum will be able to help you from there.

---

### Post by zenithdave on 2008-11-09
Yes my friend they all worked after install, impressive.

My wireless is currently working as i am using eeeubuntu at the mo which is currently my favorite.

I do have the red down pointing arrow informing me i have 79 updates but ill not do that as yet as i know it will break the wireless.

Thanks for your input.

Iwconfig shows no wireless adapters but its working fine, most odd.

```
IWCONFIG
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:17 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:18  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by mapes12 on 2008-11-09
> Iwconfig shows no wireless adapters but its working fine, most odd.

This appears to be your problem. When the updates come on they don't know about the wifi. Can you post the output to:

```
sudo lshw
```

The network wizards may pick up on something within your spec.

---

### Post by zenithdave on 2008-11-09
All that reports is 

```
PCI (sysfs)
``` and thats it !

---

### Post by Bölvaður on 2008-11-09
this may not be relevant, but I had a laptop running well on 7.10, updated it to 8.04 and all worked perfectly until one day a_ kernel update broke wireless_.
So I moved back to 7.10 which was great.
4 days ago I tried 8.10 and wireless was very good, but videocard was a problem that I wasnt up for fixing so I switched to 8.10 and it worked out perfectly.

---

### Post by zenithdave on 2008-11-09
That is relevant as when i did the 8:04 update i found some info on the forums informing me to change back to the old kernel at grub boot.

After i did that wireless worked again.


Mapes12 has identified the problem, if the new kernel install cannot see the wireless adapter its going to change accordingly, ie there is no wireless so don't install driver. 

Most odd wonder why this is happening.

Also a toggle of the wireless network off FN key will kill it until a reboot.

---

### Post by zenithdave on 2008-11-10
Bump

---

### Post by zenithdave on 2008-11-10
Hello, this is a better titled thread that links to the one at the bottom.

My problem was every time i updated eeeubuntu my wireless broke. Mapes12 on the original thread suggested the upgrade breaks wireless as it does not see an adapter! i tink he's right what could possibly be happening???
```
IWCONFIG
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.




ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:17 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:18  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```


And the output of sudo lshw

```
********-eee              
    description: Notebook
    product: 900
    vendor: ASUSTeK Computer INC.
    version: 0802
    serial: 89OAAQ433018
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: boot=normal chassis=notebook cpus=1 uuid=80CD8150-9683-DD81-3959-002215ADF9D6
  *-core
       description: Motherboard
       product: 900
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: x.xx
       serial: EeePC-0123456789
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0906 (09/11/2008)
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) M processor          900MHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.13.8
          slot: CPU 1
          size: 900MHz
          capacity: 900MHz
          width: 32 bits
          clock: 70MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up bts cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: internal write-back unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             capabilities: internal
     *-memory
          description: System Memory
          physical id: 1f
          slot: System board or motherboard
          size: 1GiB
        *-bank
             description: DIMM Synchronous 400 MHz (2.5 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 1GiB
             width: 64 bits
             clock: 400MHz (2.5ns)
     *-pci
          description: Host bridge
          product: Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Audio device
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:0
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:1
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: L2 100 Mbit Ethernet Adapter
                vendor: Attansic Technology Corp.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: a0
                serial: 00:22:15:ad:f9:d6
                size: 100MB/s
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl2 driverversion=2.0.5 duplex=full firmware=L2 ip=192.168.2.2 latency=0 link=yes module=atl2 multicast=yes port=twisted pair speed=100MB/s
        *-pci:2
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: AR242x 802.11abg Wireless PCI Express Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: wifi0
                version: 01
                serial: 00:22:43:08:17:b3
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g
        *-usb:0
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d4
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801FBM (ICH6M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801FBM (ICH6M) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi1
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: ATA Disk
                product: ASUS-PHISON SSD
                physical id: 0.0.0
                bus info: scsi@1:0.0.0
                logical name: /dev/sda
                version: TST2
                serial: 12345
                size: 15GiB (16GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=ef99ef99
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 787241ce-130f-44a4-8e42-e8463582a05f
                   size: 14GiB
                   capacity: 14GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-11-09 18:00:56 filesystem=ext3 modified=2008-11-09 23:34:37 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-11-09 20:09:15 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@1:0.0.0,2
                   logical name: /dev/sda2
                   size: 690MiB
                   capacity: 690MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 690MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
  *-scsi
       physical id: 1
       bus info: scsi@3
       logical name: scsi3
       capabilities: scsi-host
       configuration: driver=usb-storage
bonehead@bonehead-eee:~$ 


```


Thanks

***THE ORIGINAL THREAD HERE***

[http://ubuntuforums.org/showthread.php?t=976687](http://ubuntuforums.org/showthread.php?t=976687)

---

### Post by bodhi.zazen on 2008-11-10
> **zenithdave said:**
> Hello, this is a better titled thread that links to the one at the bottom.

My problem was every time i updated eeeubuntu my wireless broke. Mapes12 on the original thread suggested the upgrade breaks wireless as it does not see an adapter! i tink he's right what could possibly be happening???
```
IWCONFIG
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:17 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:18  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```Thanks

***THE ORIGINAL THREAD HERE***

[http://ubuntuforums.org/showthread.php?t=976687](http://ubuntuforums.org/showthread.php?t=976687)

Threads merged. Please do not start multiple threads on the same topic , it causes confusion and duplication of effort.

iwconfig clearly shows your wireless card, "ath0"

---

### Post by zenithdave on 2008-11-10
:oops:

Ok it was the bit about no wireless extensions that confused me.

sorry. thought i was being helpfull.

---

### Post by bodhi.zazen on 2008-11-10
> **zenithdave said:**
> :oops:

Ok it was the bit about no wireless extensions that confused me.

sorry. thought i was being helpfull.

:lolflag: I understand completely. I hope you did not take my terse post the wrong way.

---

### Post by zenithdave on 2008-11-11
> **bodhi.zazen said:**
> :lolflag: I understand completely. I hope you did not take my terse post the wrong way.


Not at all this forum is very busy and has lots of posts about the same thing, especially after the update.

Peace.

---

### Post by zenithdave on 2008-11-12
My wireless just broke again :cry::cry::cry::cry:

Ive done nothing, no updates, no upgrades no new software added.

Just switched it on this morning and gone. :confused::confused:

I know loads are having this problem too, just wanted to moan here again.

---

### Post by bodhi.zazen on 2008-11-12
I understand that. Wireless is a bit of a pain, even in Windows.

There are an ever growing number of protocols and drivers and there is not *much* effort into compatibility ...

At any rate, I do not know if it has been suggested, but I struggled for a month with my WPA and wicd fixed it "out of the box"

wicd does not work for everyone, but you might want to give it a try.

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by zenithdave on 2008-11-12
Thats not going to work for me :( but thanks for trying anyway, the wicd is seeing the ath0 interface but 'no wireless networks found'

Same thing, damn hardware :(:(

Ive done all the backport downloads too, checked the bios, again!

I think this has something to do with the script that toggles the wireless adapter on/off on the eee900 FN+F2 when i do that im informed its been switched off a second later the blue light come on again.

I also have this in the /etc/network/interfaces file which the wicd page implied i should remove??????

```
iface ath0 inet dhcp
wpa-psk 74cb05015e178c08841e88c84d77aab27a19c1e756a045c6b9b002975d1bf041
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid *********



auto ath0
```

So i commented out those lines with '#' is that correct? then rebooted, same!

---

### Post by zenithdave on 2008-11-12
As an afterthought could the fact i ran wireshark as root have caused this????? changed some permissions for the wireless files?  :oops: More blushing!

---

### Post by bodhi.zazen on 2008-11-12
If you are using network manager or wicd , those tools will edit /etc/network/interfaces for you so nothing is required.

Try connecting to your wireless via NM/wicd on ath0

---

### Post by zenithdave on 2008-11-12
Think i have exhausted the fixes now..

Just going to have to wait a bit :popcorn: 

Im sure a fix is being brewed up as we speak :D :guitar:

---

### Post by zenithdave on 2008-11-12
I am an idiot, i broke it with wireshark root usage!

Sorry for wasting time, ill install/be punished again tomorrow.

If your not re-installing 3 times a week you cant consider your self a linux idiot, i hold the crown.

---

### Post by zenithdave on 2008-11-13
And it continues!!!!

Started up this morning and the Wicd wireless is working perfectly 
\\:D/ i really don't understand LOL! This linux seems to posses some Voodoo like powers :lolflag:

Only thing i did last night is uninstall wireshark but it did not work last night when i rebooted but doing just fine now!!!!

Updates as they come.

Thanks for the Wicd fix :D

---

