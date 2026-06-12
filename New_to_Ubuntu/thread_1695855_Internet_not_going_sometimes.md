---
title: "Internet not going sometimes"
date: 2011-02-26
forum: New to Ubuntu
---

### Post by jeannot_unbu on 2011-02-26
I am back to ubuntu, I have installed 10.10 on an old Toshiba laptop. I had the same problem before too by the way, and it is what I got fed up with Linux.
Some website will load very quickly (and I mean very quickly) and sometimes nothing happens. My connection works perfectly with my desktop running XP or my daughter's laptop running Vista (yes I know...). For example today I was on Google map, site comes up quickly, then I type an address, page start loading but the last bit of it don't and I cannot do anything else on that page, ie clicking on direction.
This is quite frustrating as i quite like Linux, but the let down from surfing the net is quite frustating. Anyone with any idea? Thanks
JC

---

### Post by TeoBigusGeekus on 2011-02-26
Wired or wireless connection?
What's your pc specs? Post us the output of
```
lshw
```
Can you give us an example of a site that causes you trouble?
Have you tried with a different browser?

---

### Post by jeannot_unbu on 2011-02-26
> **TeoBigusGeekus said:**
> Wired or wireless connection?
What's your pc specs? Post us the output of
```
lshw
```
Can you give us an example of a site that causes you trouble?
Have you tried with a different browser?
 Teo, thanks for taking the time. I am at work right now so I can't check what you are asking me to check. It is a wireless connection, like I have said working very well with my Windows based machines. Saying when this laptop was running Vista, it had sometimes problem connecting to some site. I have Firefox, and I have installed Google Chromium. Both browsers are causing me the same problem, but sometimes 1 will load the site fine, when the other is struggling. For example, this morning I was looking at some background pics, Google Chromium stopped loading after page 2 when Firefox was ok.
JC

---

### Post by TeoBigusGeekus on 2011-02-27
> I have been able to post it from my linux machine :( had to copy the log onto a usb stick and send it through my XP machine. Hope you can find what is the problem as it is really frustating. Thanks


jeannot@jeannot:~$ lshw
WARNING: you should run this program as super-user.
jeannot                  
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1884MiB
     *-cpu
          product: Intel(R) Celeron(R) M CPU        430  @ 1.73GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.14.12
          serial: 0000-06EC-0000-0000-0000-0000
          size: 1750MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe constant_tsc up arch_perfmon bts aperfmperf pni monitor tm2 xtpr pdcm
     *-pci
          description: Host bridge
          product: ATI Technologies Inc
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
             resources: ioport:9000(size=4096) memory:c0000000-c00fffff memory:d0000000-dfffffff
           *-display
                description: VGA compatible controller
                product: RC410 [Radeon Xpress 200M]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=66 mingnt=8
                resources: irq:17 memory:d0000000-dfffffff ioport:9000(size=256) memory:c0000000-c000ffff memory:c0020000-c003ffff
        *-ide:0
             description: IDE interface
             product: IXP SB400 Serial ATA Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list rom
             configuration: driver=sata_sil latency=64
             resources: irq:22 ioport:8440(size=8) ioport:8430(size=4) ioport:8420(size=8) ioport:8410(size=4) ioport:8400(size=16) memory:c0407000-c04071ff memory:7c000000-7c07ffff
        *-usb:0
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:19 memory:c0404000-c0404fff
        *-usb:1
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:19 memory:c0405000-c0405fff
        *-usb:2
             description: USB Controller
             product: IXP SB400 USB2 Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:19 memory:c0406000-c0406fff
        *-serial
             description: SMBus
             product: IXP SB400 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 82
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0
             resources: irq:0 ioport:8040(size=16) memory:c0407400-c04077ff
        *-ide:1
             description: IDE interface
             product: IXP SB400 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             logical name: scsi1
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list emulated
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:8460(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GMA-4082N
                vendor: HL-DT-ST
                physical id: 0.0.0
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: PT06
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-multimedia
             description: Audio device
             product: IXP SB4x0 High Definition Audio Controller
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=64
             resources: irq:40 memory:c0400000-c0403fff
        *-isa
             description: ISA bridge
             product: IXP SB400 PCI-ISA Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:1
             description: PCI bridge
             product: IXP SB400 PCI-PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
             resources: ioport:a000(size=4096) memory:c0100000-c01fffff memory:78000000-7bffffff
           *-pcmcia
                description: CardBus bridge
                product: CB1410 Cardbus Controller
                vendor: ENE Technology Inc
                physical id: 1
                bus info: pci@0000:09:01.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:20 memory:c0101000-c0101fff ioport:a400(size=256) ioport:a800(size=256) memory:78000000-7bffffff memory:80000000-83ffffff
           *-network:0
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 2
                bus info: pci@0000:09:02.0
                logical name: eth0
                version: 10
                serial: 00:16:36:f9:d7:fb
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 multicast=yes
                resources: irq:9 ioport:a000(size=256) memory:c0100000-c01000ff
           *-network:1
                description: Wireless interface
                product: AR2413 802.11bg NIC
                vendor: Atheros Communications Inc.
                physical id: 4
                bus info: pci@0000:09:04.0
                logical name: wlan0
                version: 01
                serial: 00:16:e3:b3:79:95
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath5k driverversion=2.6.35-25-generic firmware=N/A ip=192.168.11.11 latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
                resources: irq:22 memory:c0110000-c011ffff
jeannot@jeannot:~$


Thanks
JC
PS: The PC has been waiting a few minutes now for this message to go, hence I have had the time to add this last paragraph.  Still waiting...

This was with Google Chromium, finally got an error message:
Internal Server Error

The server encountered an internal error or misconfiguration and was unable to complete your request.

Please contact the server administrator, [no address given] and inform them of the time the error occurred, and anything you might have done that may have caused the error.

More information about this error may be available in the server error log.

So I switched to Firefox


Your wireless card seems to be a bit tricky:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/625692]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/625692")
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/622130]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/622130")
Have you tried nsdiwrapper?
The only thing I can suggest is to wait for natty; perhaps the newest kernel will solve the issues.

---

### Post by grahammechanical on 2011-02-27
Why do you think that the fault lies with Linux?

If you have three machines connecting to the Internet through one modem/router then this will effect the ability of the modem to pass data on to each machine.

Your laptop is old (you say it). Your CPU is an Intel Celeron. These are not fast CPUs. They are much slower than a Pentium of the same speed and this is what ATI says about your graphic card:

> ATI Radeon Xpress 200M is the shared memory integrated graphic card from  ATI. It is a derivate of the Mobility Radeon X300 graphic card, but  slower because of the lack of own memory and slower clock speed.  Sometimes it is called Mobility Radeon X200. It is a bit faster than the  Intel GMA 950 graphic core and threrefore not really suited for actual  gaming.

Add into the mix a web site that uses display techniques that require a lot of processor power and memory, as well as graphic card power and memory, and what do you get? Exactly what you are getting.

Compare the hardware specification of this laptop with the hardware of the desktop machine and your daughter's laptop. Is this not why you see a difference in operation?

Regards.

---

### Post by jeannot_unbu on 2011-02-27
> **grahammechanical said:**
> Why do you think that the fault lies with Linux?

If you have three machines connecting to the Internet through one modem/router then this will effect the ability of the modem to pass data on to each machine.

Your laptop is old (you say it). Your CPU is an Intel Celeron. These are not fast CPUs. They are much slower than a Pentium of the same speed and this is what ATI says about your graphic card:



Add into the mix a web site that uses display techniques that require a lot of processor power and memory, as well as graphic card power and memory, and what do you get? Exactly what you are getting.

Compare the hardware specification of this laptop with the hardware of the desktop machine and your daughter's laptop. Is this not why you see a difference in operation?

Regards.

Hi Graham, I hear what you are saying but sometimes it is only 1 machine at the time connected to the Internet, and the problem still occurs. I thought, and I may be wrong, that Linux did not need the latest spec PC to run ok. Yes my laptop is old but I thought that it should not have too many problem running an OS like Ubuntu.
THeo, I am going to have a look at nsdiwrapper, do you mean by the way NDISwrapper? Thanks for the input, I will post if I can solve the problem.
JC

---

### Post by davidmohammed on 2011-02-27
can I suggest you connect to the internet via an ethernet cable - that way if you have the same issues you can discount wireless problems

Also - how much RAM does your system have?  If you have 512Mb or less, this may be the source of your issues.

---

### Post by jeannot_unbu on 2011-02-27
> **davidmohammed said:**
> can I suggest you connect to the internet via an ethernet cable - that way if you have the same issues you can discount wireless problems

Also - how much RAM does your system have?  If you have 512Mb or less, this may be the source of your issues.

Hi David, yes I thought about that, I will need to get a cable as all my machines are wireless right now. The laptop has 2gb of memory.
JC

---

### Post by jeannot_unbu on 2011-03-03
Update:
I have the laptop now on an Ethernet cable and no problem at all so far. Went to the sites that were causing me problems and it is working really well. So I guess my wireless card does not work ok with the laptop. I have seen a lot of issues with that specific wireless card. Would buying a USB wireless adapter sort the problem out? I don't mind to spend a few quids if it is going to work. 
Thanks
JC

---

### Post by vaah on 2011-03-03
yes if you buy compatible wireless adapter, so make sure you check [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) before buying. I bought netgear wifi pci adapter, setting up was pita and haven't been able to get it work properly till now. so i use ethernet cable for now.

---

### Post by jeannot_unbu on 2011-03-04
> **vaah said:**
> yes if you buy compatible wireless adapter, so make sure you check [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) before buying. I bought netgear wifi pci adapter, setting up was pita and haven't been able to get it work properly till now. so i use ethernet cable for now.
 
Thanks Vaah, I may get one, i need one anyway for my desktop so if it works i will get a second one. Using the laptop with the cable has been great, no more issues of loading pages.
JC

---

