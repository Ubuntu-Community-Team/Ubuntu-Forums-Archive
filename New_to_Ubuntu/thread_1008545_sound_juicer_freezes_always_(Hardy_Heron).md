---
title: "sound juicer freezes_always (Hardy Heron)"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by lazylew on 2008-12-11
using Sound Juicer is impossible; it always freezes after a few minutes and I have to do a cold start (and Linux doesn't like that I believe)

any idea what causes this?
should I throw it out and try another cd-ripper? if so, any suggestions which one?

thanks
ps there's also a freeze problem in Audacity at times, as I posted in another (unanswered) thread, but with sound juicer it's chronical

---

### Post by Michael.Godawski on 2008-12-11
hi lazylew, 
what happens if you run sound juicer in terminal?

```
sound-juicer
```

and error messages?

---

### Post by sneeks on 2008-12-11
you could always try asunder,i prefer it myself.

---

### Post by lazylew on 2008-12-11
> **Michael.Godawski said:**
> hi lazylew, 
what happens if you run sound juicer in terminal?...
It starts up, then I click the button to extract and after 5 minutes everything's come to a halt... got the terminal in view and there's no error report, but I also can't continue in terminal or anywhere - it's all frozen and I have to cold start again.

---

### Post by lazylew on 2008-12-11
> **sneeks said:**
> you could always try asunder,i prefer it myself.
synaptic doesn't find it though...

---

### Post by lazylew on 2008-12-12
meanwhile I found asunder on getdeb.net and installed it

it looked promising but stopped ripping at 50% total progress (rip 80% encoding 20%)
everything frozen...

I also tried changing device (now again with sound juicer, not seeing how to change it in asunder) and that didn't improve things - it had the same result

ctrl alt backspace also never works when this freezing happens (my backspace button doesn't work in firefox browsing either, for going back a page, but I don't know if in ubuntu it is supposed to do that)

music is my main thing, so I really use an application like this a lot
I'm stuck... :confused:

---

### Post by nothingspecial on 2008-12-12
Try grip. If you have a lot of cds to get through you can set it to automatically rip on insert and eject when finished, so theres no mouse clicking or button pushing, you just keep on putting them in.

---

### Post by lazylew on 2008-12-12
> **nothingspecial said:**
> Try grip... 
I downloaded it and, again, this looked promising but broke down after a few minutes.

I think this proves it is not Sound Juicer, Asunder or Grip showing a flaw, but something in Ubuntu or (more likely?) my hardware??

I hope it's solvable without complicated kernel-surgery or the likes, because that's unknown terrain to me.

---

### Post by sydbat on 2008-12-12
If you have tried all these different programs and get the same result, I would suggest that it may be a hardware problem. 

On your next reboot, go to memtest in the grub menu. It will let you know if your RAM is OK. If that works, it might be anything from your sound card to your processor or anything else hardware related.

Also, can you post the specs for your computer (processor, RAM, video card, etc). It might be your hardware is simply not sufficient to run the programs you want.

---

### Post by sneeks on 2008-12-12
as above mate,post the specs and it will give us a better idea

---

### Post by lazylew on 2008-12-12
> **sneeks said:**
> as above mate,post the specs and it will give us a better idea
I'm not too familiar with codes yet; what do I type in the terminal to get the output for all these specifics?

---

### Post by nothingspecial on 2008-12-12
list your hardware with

```
lshw
```

and
```

lspci
```

---

### Post by NullHead on 2008-12-12
I agree too, run memtest. I had something similar happen to me. I eventually figured out that I had one of my two sticks of ram were bad. It would only crash the computer when I start a program such as what you're running or start a game.

---

### Post by lazylew on 2008-12-12
> **nothingspecial said:**
> list your hardware... 
this is it:

hardy                     
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 479MiB
     *-cpu
          product: AMD Duron(tm)
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 6.7.1
          size: 1300MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up ts
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 64KiB
     *-pci
          description: Host bridge
          product: 740 Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-sis latency=32 module=sis_agp
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
        *-isa
             description: ISA bridge
             product: SiS962 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 25
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
             configuration: driver=sis96x_smbus latency=0 module=i2c_sis96x
        *-ide
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=pata_sis latency=128 module=pata_sis
        *-usb:0
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 maxlatency=80 module=ehci_hcd
        *-network
             description: Ethernet interface
             product: SiS900 PCI Fast Ethernet
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 90
             serial: 00:0d:87:18:3d:fe
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 ip=84.198.238.91 latency=64 maxlatency=11 mingnt=52 module=sis900 multicast=yes
        *-multimedia
             description: Multimedia audio controller
             product: SB Audigy LS
             vendor: Creative Labs
             physical id: 9
             bus info: pci@0000:00:09.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=CA0106 latency=64 maxlatency=20 mingnt=2 module=snd_ca0106

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 740 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:09.0 Multimedia audio controller: Creative Labs SB Audigy LS
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter

---

### Post by lazylew on 2008-12-13
> **NullHead said:**
> I agree too, run memtest... 
This was my very first memtest ever, so I didn't know what to expect.
I presumed when it ran for 1,5 hour and the "pass" was on 2, that the test was repeating, so then I booted again.

The test didn't find any errors.

---

### Post by NullHead on 2008-12-13
> **lazylew said:**
> This was my very first memtest ever, so I didn't know what to expect.
I presumed when it ran for 1,5 hour and the "pass" was on 2, that the test was repeating, so then I booted again.

The test didn't find any errors.

About an hour is good enough. You'll know if there's any errors. There will be a large red thingy that'll show on the bottom.

---

### Post by lazylew on 2008-12-13
> **NullHead said:**
> ... if there's any errors. There will be a large red thingy that'll show on the bottom.
No errors, so it remains a mystery for now what the problem is... :confused:

---

### Post by mc4man on 2008-12-13
What happens if you just try to copy an audio cd? 
R. click on icon -> copy disc (output to a file, the .iso will be worthless, but you'll see if the disk can be read in a timely fashion.

---

### Post by lazylew on 2008-12-13
> **mc4man said:**
> What happens if you just try to copy an audio cd? 
R. click on icon -> copy disc (output to a file, the .iso will be worthless, but you'll see if the disk can be read in a timely fashion.
well I've done a cd-burn today for an .iso (putting xubuntu on a very old machine to at least always have internet if this one goes wrong)

the burn was successfull

---

### Post by mc4man on 2008-12-13
It appears then your failing on encoding. Most of the gui rippers won't give any useful info when started from the terminal, for that you'd need to use a cli ripper/encoder. (rubyripper is one

I'd go back to grip and have it rip and encode to ogg 1 track only, while it's working click on the status tab and see if anything useful shows up. (if it succedds on 1 then do the next 2 or 3 and see.

Ripping and burning aren't very cpu intensive, encoding is, don't know if there is some local issue there.

---

### Post by lazylew on 2008-12-14
> **mc4man said:**
> It appears then your failing on encoding. Most of the gui rippers won't give any useful info when started from the terminal, for that you'd need to use a cli ripper/encoder. (rubyripper is one

I'd go back to grip and have it rip and encode to ogg 1 track only, while it's working click on the status tab and see if anything useful shows up. (if it succedds on 1 then do the next 2 or 3 and see.

Ripping and burning aren't very cpu intensive, encoding is, don't know if there is some local issue there.

I downloaded rubyripper but typing it's name in terminal doesn't start the program.

I then started the GUI-way to at least try the program; all it gives is a "vorbis.log" like the one below here - I don't see any ripped tracks though!?

```
Starting to rip track 44, trial #1
Starting to rip track 44, trial #2
Analyzing files for mismatching chunks
Every chunk matched 2 times :)
MD5 sum: 60f9e80823753e4f06d390c5ff8ab7b3

WARNING: Encoding to vorbis exited with an error with track 44!
```Next I'll try grip again and look for that tab you mention.
EDIT: In grip I ripped without encoding and that worked very good.
Then I tried 1 track with encoding; good too (only, it didn't auto-eject), so I got brave and wanted to rip 4 tracks.
Whilst marking which tracks to rip it happened again.
Unfortunately I was in the "tracks" tab of course, not the "status", at that point.

---

