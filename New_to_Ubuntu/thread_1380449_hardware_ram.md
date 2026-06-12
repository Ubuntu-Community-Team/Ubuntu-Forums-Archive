---
title: "hardware/ ram"
date: 2010-01-13
forum: New to Ubuntu
---

### Post by albert s on 2010-01-13
is there a command to find out what hardware is installed?
specifically the type/speed of ram I have,
thanks

---

### Post by 2blue on 2010-01-13
Usually you can find it under system monitor in Ubuntu, and in Windows it's some where under tools and settings.

---

### Post by albert s on 2010-01-13
that just tells me i have half a gig, which I know.
I was wanting to know what type and speed so I can upgrade it.
was gonna buy a stick tomorrow.

ps, its 9.10 ubuntu

---

### Post by 2blue on 2010-01-13
[This]("http://www.secguru.com/article/finding_hardware_details_your_linux_machine_without_using_screw_driver") page might help you, and [this]("http://www.linuxquestions.org/questions/linux-general-1/to-find-ram-info-in-a-linux-machine-512739/").  Do you mean more RAM or storage memory?

---

### Post by warfacegod on 2010-01-13
Try:

```
uname -a
```

Of course the most sure fire way to know is to take the RAM out of your machine and read it. Another idea would be to go to Crucial's site and use their RAM finder utility. That has always given me excellent results for what my machines will take. Then I go to newegg and buy it for a quarter of the cost.

---

### Post by Salvia on 2010-01-13
This should do it for you:

sudo lshw -C memory

---

### Post by warfacegod on 2010-01-13
> **Salvia said:**
> This should do it for you:

sudo lshw -C memory

I was just going to suggest

```
sudo lshw
```

when I tried yours and as far as I can tell they do the same thing.

---

### Post by albert s on 2010-01-13
*-memory
       description: System Memory
       physical id: 29
       slot: System board or motherboard
       size: 512MiB
       capacity: 1GiB
     *-bank:0
          description: DIMM DDR2
          product: None
          vendor: None
          physical id: 0
          serial: None
          slot: A0
          size: 512MiB
     *-bank:1
          description: DIMM DDR2 [empty]
          product: None
          vendor: None
          physical id: 1
          serial: None
          slot: A1

that done it, thanks salvia
does that mean I can run 1G total, or 1G in each slot.?

---

### Post by warfacegod on 2010-01-13
> **albert s said:**
> *-memory
       description: System Memory
       physical id: 29
       slot: System board or motherboard
       size: 512MiB
       capacity: 1GiB
     *-bank:0
          description: DIMM DDR2
          product: None
          vendor: None
          physical id: 0
          serial: None
          slot: A0
          size: 512MiB
     *-bank:1
          description: DIMM DDR2 [empty]
          product: None
          vendor: None
          physical id: 1
          serial: None
          slot: A1

that done it, thanks salvia
does that mean I can run 1G total, or 1G in each slot.?

It looks like each slot will accept 1 GB.

---

### Post by warfacegod on 2010-01-13
On a second look, I'm not sure. Again, use Crucial's site.

---

### Post by teward on 2010-01-13
The capacity means thats the total capacity you have installed.  You'll need to lookup your information on Google to find the max capacity, and Crucial's memory lookup feature is useful to figure out the max memory your comp can handle.

---

### Post by albert s on 2010-01-13
crucials site only seems to give me a win XP download.?????

---

### Post by warfacegod on 2010-01-13
> **albert s said:**
> crucials site only seems to give me a win XP download.?????

You don't need to install anything. Just put the manufacturer details in the drag down menus here:

[http://www.crucial.com/]("http://www.crucial.com/")

---

### Post by albert s on 2010-01-13
Im confused now cos inputting my motherboard into crucials site is giving me different info to the type of memory already installed on my system, ? :confused:


[http://www.crucial.com/uk/store/listparts.aspx?model=N1996%20OEM%20%28HP-Argon%29](http://www.crucial.com/uk/store/listparts.aspx?model=N1996%20OEM%20%28HP-Argon%29)

atm its currently got 512M of DDR2 533 CL4 installed, but crucials says only DDR ram,,,,,, 

Ive pulled out the stick and copied all the info from the label....

---

### Post by warfacegod on 2010-01-13
> **albert s said:**
> Im confused now cos inputting my motherboard into crucials site is giving me different info to the type of memory already installed on my system, ? :confused:


[http://www.crucial.com/uk/store/listparts.aspx?model=N1996%20OEM%20%28HP-Argon%29](http://www.crucial.com/uk/store/listparts.aspx?model=N1996%20OEM%20%28HP-Argon%29)

atm its currently got 512M of DDR2 533 CL4 installed, but crucials says only DDR ram,,,,,, 

Ive pulled out the stick and copied all the info from the label....

Did you or someone else replace the RAM before? 

Go to the computer manufacturers site and see what they say should be in it. I've never seen Crucial get it wrong, maybe try again making certain you get the right model and all that. Slightly different models can have completely different parts.

---

### Post by albert s on 2010-01-13
pretty sure no one has every replaced the ram before, it was my nieces PC before me, and I put in the actual motherboard model numbers to crucial. it comes up correct with the 1G bit, just not the type, DDR pc3200 as opposed to DDR2 pc2-4200 actual being fitted.
its the PIN numbers that Im now worried about, how do I know how many pins I need.?
I reckon I'll stay safe and just go for 512=1G total.

---

### Post by warfacegod on 2010-01-13
> **albert s said:**
> pretty sure no one has every replaced the ram before, it was my nieces PC before me, and I put in the actual motherboard model numbers to crucial. it comes up correct with the 1G bit, just not the type, DDR pc3200 as opposed to DDR2 pc2-4200 actual being fitted.
its the PIN numbers that Im now worried about, how do I know how many pins I need.?
I reckon I'll stay safe and just go for 512=1G total.

That's what crucial's site said, 1 GB. It could just be a matter of it having faster RAM in it than it can utilize. If that's the case, the computer will simply run the RAM at a slower speed that it can handle.

---

### Post by albert s on 2010-01-13
ok, thanks warfacegod.
hopefully I'll let you know how it goes after I replace it tomorrow.

---

### Post by albert s on 2010-01-16
thanks guys , bought some DDR2 512m RAM today, £10, seems to be spot on.  :D

  *-memory
       description: System Memory
       physical id: 29
       slot: System board or motherboard
       size: 1GiB
       capacity: 1GiB
     *-bank:0
          description: DIMM DDR2
          product: None
          vendor: None
          physical id: 0
          serial: None
          slot: A0
          size: 512MiB
     *-bank:1
          description: DIMM DDR2
          product: None
          vendor: None
          physical id: 1
          serial: None
          slot: A1
          size: 512MiB

---

### Post by warfacegod on 2010-01-16
Glad to here it. That's thing with computers today. Basically if it fits there, it works. Have you noticed an increase in your computers performance?

---

### Post by albert s on 2010-01-16
Ive only been on it about 10mins surfing, but it does seem noticeably quicker, esp if Im listening to music as well or doing more than one thing at a time.
might be time to try 64bit perhaps.

---

### Post by warfacegod on 2010-01-16
> **albert s said:**
> Ive only been on it about 10mins surfing, but it does seem noticeably quicker, esp if Im listening to music as well or doing more than one thing at a time.
might be time to try 64bit perhaps.

That would almost certainly entail buying a new computer. Type this in a Terminal:

```
sudo lshw
```

And scroll around until you find this section of the out put:

```
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.9
          slot: NWD
          size: 2800MHz
          capacity: 3200MHz
          width: 32 bits
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 8KiB
             capacity: 16KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: burst internal write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical

```

Were it says width: 32 bits, that means my processor is a 32 bit and can't run a 64 bit OS.

---

### Post by albert s on 2010-01-16
its a core2duo, this is why I was a bit baffled as to why it would only hold 1G.

mark@mark-desktop:~$ sudo lshw
[sudo] password for mark: 
mark-desktop              
    description: Desktop Computer
    product: PACKARD BELL 755
    vendor: Packard Bell BV
    version: PB82103001
    serial: 123504600313
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=D01AB60B-E9A5-DB11-8000-4E45435F4349
  *-core
       description: Motherboard
       product: Cuba MS-7301
       vendor: Packard Bell BV
       physical id: 0
       version: 1.0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: W7301VP2.306 (12/28/2006)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 CPU          4300  @ 1.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.2
          serial: 0000-06F2-0000-0000-0000-0000
          slot: Socket 775
          size: 1200MHz
          capacity: 1200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq
          configuration: id=1
        *-cache
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits                [COLOR=Red]<<<<<<<<<<-----------[/COLOR]
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits                 [COLOR=Red]<<<<<<<<<<----------[/COLOR]
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 29
          slot: System board or motherboard
          size: 1GiB
          capacity: 1GiB
        *-bank:0
             description: DIMM DDR2
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 512MiB
        *-bank:1
             description: DIMM DDR2
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 512MiB
     *-cpu:1
          physical id: 2
          bus info: cpu@1
          version: 6.15.2
          serial: 0000-06F2-0000-0000-0000-0000
          size: 1800MHz
          capacity: 1800MHz
          capabilities: ht cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             capabilities: logical
     *-pci:0

---

### Post by warfacegod on 2010-01-16
> **albert s said:**
> its a core2duo, this is why I was a bit baffled as to why it would only hold 1G.

Allot of the first duos were actually 32 bit obviously yours is not. It could be that its a 64 cpu in a 32 motherboard although, I don't know if that's possible. Check the out put of that code to see.

---

### Post by albert s on 2010-01-16
that is a very logical statement, although i wondered what you meant for a bit.
it does say 32bits near the top, then further down at the cpu section, it says 64bit,
Im getting more confused now, will open a new thread.
thanks for all your help warfacegod.  :KS

---

### Post by cascade9 on 2010-01-16
> **warfacegod said:**
> Allot of the first duos were actually 32 bit obviously yours is not. It could be that its a 64 cpu in a 32 motherboard although, I don't know if that's possible. Check the out put of that code to see.

There is 2 different types of 'core duos'- the original 'core duos' (32bitn only) and 'core 2 duos' (all 64bit).

T4300 @ intels site- 

[http://ark.intel.com/Product.aspx?id=37253](http://ark.intel.com/Product.aspx?id=37253) 

BTW, did a bit of digging, it appears that you have a VIA PT890 chipset, that should have a max RAM of 4GB- 

> Supports up to 4GB Single Channel DDR2533/400 or DDR400/333/266

[http://www.via.com.tw/en/products/chipsets/p4-series/pt890/](http://www.via.com.tw/en/products/chipsets/p4-series/pt890/)

That could be why crucial told you it was DDR1, I'm pretty sure that the PT890 got DDR2 at the end of its life as a 'hack' and is almost always DDR1.

---

### Post by cascade9 on 2010-01-16
> **albert s said:**
> it does say 32bits near the top

That is your current OS install, not the capabilities of your machine.

---

### Post by albert s on 2010-01-16
thanks cascade9 , i'll read a bit more when I have some spare time, tho I dont really know how much I would really benefit from more RAM (I know you can never have too much!!!) for the expense/effort to change it all.
might try 64bit tho, I have a old 40G HDD I could swap over.

---

### Post by warfacegod on 2010-01-16
> **albert s said:**
> thanks cascade9 , i'll read a bit more when I have some spare time, tho I dont really know how much I would really benefit from more RAM (I know you can never have too much!!!) for the expense/effort to change it all.
might try 64bit tho, I have a old 40G HDD I could swap over.

If you can only put 1 GB RAM on your mother board then switching to 64 bit would be futile. You might see some minor improvements in things like video encoding but with the specs you have, encoding would be a long chore.

---

