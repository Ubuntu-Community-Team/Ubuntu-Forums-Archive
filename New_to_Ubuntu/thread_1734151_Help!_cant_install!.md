---
title: "Help! cant install!"
date: 2011-04-19
forum: New to Ubuntu
---

### Post by haon14 on 2011-04-19
I am a serious noob at all this stuff. I was a windows slave for so long im not even surd if I remember how to open a bios menu. So I recently decided to make the switch over to linux. So I burn a .iso of 10.10 ubuntu on to a dvd and stick it in my desktop. Sure enough it boots from the cd and everything is goin fine untill I get partitioning the hd. So I switched over to the "bare bones" text based installer to see if it made a difference but to no avail. Although it dis help me narrow down the problem to be partitioning ext 4. It gets to 33% and hangs for a good 5 mins then sends me back to the partitioning menu. I'm sorry if this realy easy to fix but I've searched and searched to no avail.  Btw I'm TRYING to da a "clean" install so I have been clicking on "guided partition" (though I've tried the other ones w/o luck). Thanks in advance!

---

### Post by mörgæs on 2011-04-19
Hi, welcome to the fora.

Please give a thorough description of the hardware.

---

### Post by haon14 on 2011-04-19
1.Thank you
and
2. I'm not sure what's important but I kmow I have an ata maxtor hard drive and I'm on a sony vios desktop computer.

---

### Post by josephmills on 2011-04-19
I think what that person was saying is to put the cd in the drive then when you get the prompt to install or run as a live cd. That person wants you to **Run as a live cd**then got to **Applications-->Accessories-->Terminal** then type in the following ```
free -m
``` then paste that here. Then ```
cat /proc/cpuinfo
``` Then paste that here. Then ```
lshw
``` Then paste that here. I am so glad that More people are using Ubuntu, have fun with it. And Welcome to Ubuntuforums

---

### Post by haon14 on 2011-04-19
Hey thanks! As I said I am super new to this stuff. Gimme a minute here and I'll see what I can come up with

---

### Post by josephmills on 2011-04-20
cool when you paste in the code could you please put [code ] but with-out the space between the e and the ]  at the beginning and at the end of the paste please put in a [/code ] but the same thing no space between the e and the ] thanks, this is what it should look like if you do it right and preview it  ```
this is a sample of code
```And once again welcome to Ubuntuforums

---

### Post by mörgæs on 2011-04-20
You can also get to the CODE tag by clicking 'go advanced'. Remember to use the preview before posting.

---

### Post by josephmills on 2011-04-20
> **mörgæs said:**
> You can also get to the CODE tag by clicking 'go advanced'. Remember to use the preview before posting.
Dear morgaes (sorry don't know how to put the thing above the o or the ae thing v.cool)..........
You:guitar:
Thank you I did not know that. :) but now I do :p
cant wait to see that hw

---

### Post by haon14 on 2011-04-20
Free -m
```
 total       used       free     shared    buffers     cached
Mem:           717        703         13          0         84        368
-/+ buffers/cache:        250        467
Swap:         2246          0       2246
ubuntu@ubuntu:~$ 

```

[FONT=monospace]cat / whatever
```
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 15
model        : 2
model name    : Intel(R) Pentium(R) 4 CPU 2.20GHz
stepping    : 4
cpu MHz        : 2219.758
cache size    : 512 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 2
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up pebs bts
bogomips    : 4439.51
clflush size    : 64
cache_alignment    : 128
address sizes    : 36 bits physical, 32 bits virtual
power management:

ubuntu@ubuntu:~$ 

```

lshw
```
WARNING: you should run this program as super-user.
ubuntu                    
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1015MiB
     *-cpu
          product: Intel(R) Pentium(R) 4 CPU 2.20GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.2.4
          size: 2250MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up pebs bts
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 8KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-pci
          description: Host bridge
          product: 650/M650 Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-sis latency=64
          resources: irq:0 memory:ec000000-efffffff
        *-pci
             description: PCI bridge
             product: Virtual PCI-to-PCI bridge (AGP)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:d000(size=4096) memory:eb800000-ebffffff memory:f0000000-febfffff
           *-display UNCLAIMED
                description: VGA compatible controller
                product: 65x/M650/740 PCI/AGP VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: vga_controller cap_list
                configuration: latency=0
                resources: memory:f0000000-f7ffffff memory:eb800000-eb81ffff ioport:d800(size=128)
        *-isa
             description: ISA bridge
             product: SiS961 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-serial
             description: SMBus
             product: SiS961/2 SMBus Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             configuration: driver=sis96x_smbus latency=0
             resources: irq:0 ioport:e600(size=32)
        *-usb:0
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.2
             bus info: pci@0000:00:02.2
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80
             resources: irq:9 memory:eb000000-eb000fff
        *-usb:1
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.3
             bus info: pci@0000:00:02.3
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80
             resources: irq:23 memory:ea800000-ea800fff
        *-ide
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             version: d0
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=pata_sis latency=128
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:b800(size=16)
        *-communication UNCLAIMED
             description: Modem
             product: AC'97 Modem Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.6
             bus info: pci@0000:00:02.6
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: generic cap_list
             configuration: latency=32 maxlatency=11 mingnt=52
             resources: ioport:b400(size=256) ioport:b000(size=128)
        *-multimedia
             description: Multimedia audio controller
             product: AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@0000:00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=32 maxlatency=11 mingnt=52
             resources: irq:21 ioport:a800(size=256) ioport:a400(size=128)
        *-network:0
             description: Wireless interface
             product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: f
             bus info: pci@0000:00:0f.0
             logical name: wlan0
             version: 20
             serial: 00:13:49:54:a2:9a
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=rtl8180 driverversion=2.6.35-22-generic firmware=N/A latency=32 maxlatency=64 mingnt=32 multicast=yes wireless=IEEE 802.11bg
             resources: irq:18 ioport:a000(size=256) memory:ea000000-ea0001ff
        *-network:1
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 10
             serial: 00:e0:18:79:a4:8e
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.45 latency=32 maxlatency=64 mingnt=32 multicast=yes
             resources: irq:17 ioport:9800(size=256) memory:e9800000-e98000ff
        *-firewire
             description: FireWire (IEEE 1394)
             product: uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr
             vendor: NEC Corporation
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=firewire_ohci latency=64 maxlatency=44 mingnt=20
             resources: irq:18 memory:e9000000-e9000fff
ubuntu@ubuntu:~$ 

```

[/FONT]

---

### Post by josephmills on 2011-04-20
before I look at the code that Is a great job with the code tags:P

---

### Post by josephmills on 2011-04-20
did you check the md5sum number? [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) of the cd? you should be able to install but on a side note if you could update your ram that thing would be a beast. what kind of computer is it?

---

### Post by mörgæs on 2011-04-20
The machine can run Ubuntu, though it is not superfast. 

You have a SiS graphics card, which sometimes makes trouble for Ubuntu. Though, the strange part is that the graphics seems to work well, and only the partitioning freezes. Let's wait with this for now...

Have you tried ext3?

A good general approach when having hard drive problems is wiping the disk completely with Killdisk. Just burn the ISO to a CD like you do with Ubuntu and boot it. After erasing the disk you will know if it is in good physical condition.

[http://www.killdisk.com/](http://www.killdisk.com/)

---

### Post by Learning Linux 2011 on 2011-04-20
A couple of things:

You said you burned the ISO to a DVD, is that correct?  Or was it a CD? 

Also, are you sure that your hard drive doesn't have bad sectors and/or is experiencing hardware failure?  If you aren't sure, download the utility from Maxtor's web site to test for hardware failure. (I guess Maxtor was taken over by Seagate)

[http://www.seagate.com/ww/v/index.jsp?locale=en-US&name=SeaTools&vgnextoid=720bd20cacdec010VgnVCM100000dd04090aRCRD](http://www.seagate.com/ww/v/index.jsp?locale=en-US&name=SeaTools&vgnextoid=720bd20cacdec010VgnVCM100000dd04090aRCRD)

---

### Post by mörgæs on 2011-04-20
> **josephmills said:**
> if you could update your ram that thing would be a beast.

I wouldn't say that. The processor is from 2002, but it will be a decent machine with Ubuntu.

---

### Post by josephmills on 2011-04-20
> **Learning Linux 2011 said:**
> A couple of things:

You said you burned the ISO to a DVD, is that correct?  Or was it a CD? 

Also, are you sure that your hard drive doesn't have bad sectors and/or is experiencing hardware failure?  If you aren't sure, download the utility from Maxtor's web site to test for hardware failure. (I guess Maxtor was taken over by Seagate)

[http://www.seagate.com/ww/v/index.jsp?locale=en-US&name=SeaTools&vgnextoid=720bd20cacdec010VgnVCM100000dd04090aRCRD](http://www.seagate.com/ww/v/index.jsp?locale=en-US&name=SeaTools&vgnextoid=720bd20cacdec010VgnVCM100000dd04090aRCRD)
good point if you go to **systems-->addmin-->disk utility** you will see a page like this (see pic) select your hard drive and then run a smart data test (see pic) are there bad sectors ?

---

### Post by haon14 on 2011-04-20
Ok so I did the hard drive check and only thing that was red. Was the "relocated sector count"

And ill have to try killing the drive after work. Ill get back to u then

---

### Post by haon14 on 2011-04-20
And I've tried both a cd and a dvd

---

### Post by haon14 on 2011-04-20
Alright so I just ran the killdisk.iso and it took a while but it ran smooth. Then tried ubunti 10.10 text-based installer and it...........whoa it hung for a long time but it litteraly just went through! Thanks guys!

---

### Post by mörgæs on 2011-04-20
Good, please mark the thread 'solved'.

---

