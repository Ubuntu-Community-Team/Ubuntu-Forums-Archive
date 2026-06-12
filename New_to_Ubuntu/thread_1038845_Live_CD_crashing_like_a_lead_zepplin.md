---
title: "Live CD crashing like a lead zepplin"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by DigiTan on 2009-01-14
I've been trying for about a week to clone a WinXP HDD using the 7.10 Rescue CD where the progress so far has been mostly verbal.  Now I'm thinking it's rescue disc that needs the rescuing...

Background:
- AMD Athlon 64X2 Dual Core 
- 1GB RAM
- ECS NForce4M-A Mobo
- Leadtek NVidia 7600 GT
- SATA Disks (40GB, 80GB)
- (Passed disc integrity check)

What happens is I'll boot Ubuntu.  And usually within a minute of running Firefox, Gparted, or sometimes doing absolutely nothing the entire system drops dead.

Sometimes it's darkness
Sometimes it's freezes.
Sometimes it's glitches, blotches, and seizes.  

But it always crashes.  Less so with terminal, but still...I can get -at best- 10 minutes of work done before it's all over.  More recently I get "lights out" crashes where my whole system shuts off so fast I want to check for smoke.  Out of all crashes, I've only witnessed one message:

> There was an error starting the GNOME daemon.  Some things such as themes, sounds, or background settings will not work correctly.  The last error was: 

Failed to connect to socket
/tmp/dbus-pUwRUKIBul

Connection refused.  GNOME will still try to restart the setting daemon next time you log in.

...Which I'm taking to mean something's either corrupt or missing.  I can boot in graphics safe mode and the loading screen flickers and the sound is choppier than a spinning rotor.

I'm not badmouthing the OS.  It's got potential.  But I'm sitting here wondering whether in a year I'll be running XP & Linux, or XP and Win7 if you know what I mean.  Before it gets asked: I *am* considering giving v8.04 a try.  My question to that is "what is new about it that will make it run on my setup?"  Thanks.

---

### Post by darrelljon on 2009-01-16
Maybe test your memory because I've never heard of this problem before.

---

### Post by DigiTan on 2009-01-19
I'll check that overnight.  So far, it's worked out just fine in XP.  But I am planning to make a Newegg order this coming week, so the timing isn't 100% awful if I need more, or just something different.

Is there a way to test whether this could be because of my sound or video cards?  I read a thread about a command that would report all of this, but I can't find that topic or that specific command anymore.

---

### Post by b0b138 on 2009-01-19
Did you check the cd for defects?

---

### Post by DigiTan on 2009-01-20
I ran a disc integrity check on the first run and things seemed okay.  I worry about the DVD drive itself sometimes because it runs extremely loud.  Loud to the point where you don't want to stand too close to it.  but it's never failed me in 25 months of service.

---

### Post by tegnoto89 on 2009-01-20
yeah i'd check the dvd drive - i had a drive that would go nutso and if you pressed eject while it was running the disc would be spinning so fast that it would fly out and slide under the carpet.

---

### Post by DigiTan on 2009-01-21
So far, 7.10 definitely isn't my lucky number.  I ran the RAM check tool and it passed with no errors.  I'll be ordering a DVD-RW as soon as my address is settled out--which gives maybe a week before it arrives.  In the meantime, I'm going to put up with 7.10's nonsense and try a straight **dd** clone of the disk.  Which is top priority at the moment.

---

### Post by theozzlives on 2009-01-21
I'd go with a version newer than 7.10. I got Windows 7 Beta in a VirtualBox and I'm not real impressed.

---

### Post by linux phreak on 2009-01-21
May be the PSU is faulty.It has happened to me before.

---

### Post by DigiTan on 2009-01-22
I'm pretty sure it isn't the PSU.  In WinXP can run games and like GTA and numerous other processes without a single glitch.  The case itself has a lot of cooling too and the CPU/Board temps rarely get to 44°C.  I'm wondering if this is a sound/video compatibility shortfall.

---

### Post by DigiTan on 2009-01-30
> **DigiTan said:**
> Is there a way to test whether this could be because of my sound or video cards?  I read a thread about a command that would report all of this, but I can't find that topic or that specific command anymore.

Okay, I think the command I was referring to here was -lshw.  I'll try posting to output of this if I'm lucky enough to not have it crash on me.  Not much has changed since the start of this thread, and the GNOME error seems to be the only indicator of what actually goes wrong.

I'll be burning copies of 8.04, 8.10, and some other distros in the next week.  In case those don't work either, is there a way to boot straight into the command console without using the GUI?  Or can turn off the "loading" screen and see some kind of output?

---

### Post by DigiTan on 2009-01-31
Live CD's being pleasantly stable tonight.

```
ubuntu@ubuntu:~$ lshw
WARNING: you should run this program as super-user.
ubuntu                    
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory:0
          description: System memory
          physical id: 3
          size: 1023MB
     *-cpu
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
          vendor: Advanced Micro Devices [AMD]
          physical id: 5
          bus info: cpu@0
          size: 2200MHz
          capacity: 2200MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy cpufreq
     *-memory:1 UNCLAIMED
          description: Memory controller
          product: CK804 Memory Controller
          vendor: nVidia Corporation
          physical id: 0
          bus info: pci@0000:00:00.0
          version: a4
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
```

I checked with someone who has the same GeForce 7600 GS graphics card and his works just fine with Compiz.  My RAM passed another memory check.  Tonight I only have my WinXP disk connected and the only problem so far was a glitchy Ubuntu load screen.  Is it possible I didn't configure my 2nd disk correctly, and maybe that's causing the crashes?

---

### Post by DigiTan on 2009-01-31
Well it just rebooted at random (was browsing the forums when it happened).  I'm going throw the possibility of PSU limitations back into the ring.  It's just weird that it would happen during something as mundane as web browsing.

Can anyone recommend more ways to test my devices further and try to narrow down the root of this?

---

### Post by DigiTan on 2009-02-01
C'mon, people.  There's got to be **one** person here qualified to answer this.

---

### Post by DigiTan on 2009-02-04
Well, if no one's going to take this seriously, I'm just going to use this topic to chronicle my own process..


I noticed during the last freeze, the DVD-ROM seemed to sag in rpms.  More recently, the bios appeared to fail to boot from CD entirely and reverted to the HDD after revving the CD drive.  Ubuntu was crashing long before this happened, but it does point to drive problems.

The parts order was delayed, so it might be worth the extra trouble to add a bigger PSU to the list.  If nothing else, I'll keep my current one as a backup.

---

### Post by DigiTan on 2009-02-05
Found out today this affliction usually strikes users with socket AM2 motherboards (mainly AMD64X2's).  It happens on every Ubuntu version from 6.06 to 8.10, Kubuntu, and "other distros" according to one person.  Adding "acpi=off" at the boot menu with [F6] should correct the problem for live cd.  Even though I shouldn't be able to load the desktop at all when this is the case, it's worth trying out tonight.

---

### Post by DigiTan on 2009-02-05
Tried the boot menu suggestion.  So far I'm 15 minutes into my session with no crashes--which is already better than average.

In the console, I opened up the syslog to run a search for all occorances "acpi," and three lines stood out to me.  

```
Feb  5 20:38:38 ubuntu kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
Feb  5 20:38:38 ubuntu kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
```

Followed by a cluster of "not found" messages about acpi...

```
Feb  5 20:38:38 ubuntu kernel: [  266.432026] powernow_k8: Unknown symbol acpi_processor_notify_smm
Feb  5 20:38:38 ubuntu kernel: [  266.432061] powernow_k8: Unknown symbol acpi_processor_unregister_performance
Feb  5 20:38:38 ubuntu kernel: [  266.432137] powernow_k8: Unknown symbol acpi_processor_register_performance
Feb  5 20:38:38 ubuntu kernel: [  266.468377] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
Feb  5 20:38:38 ubuntu kernel: [  266.468412] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
Feb  5 20:38:38 ubuntu kernel: [  266.468499] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
Feb  5 20:38:38 ubuntu kernel: [  266.468540] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
```

---

### Post by DigiTan on 2009-02-08
Well it's 2/8/09 and Live CD's been stable ever since I started the acpi trick.  I'm going to call this [SOLVED] for now.  Special thanks to darrelljon, b0b138, the people I PM'ed, and everyone else who at least had the cajones to *try* and help solve this.

---

### Post by MyR on 2009-02-08
Having not read the entire thread because I'm lazy... I would **definitely** recommend giving 8.04 a try. (download the latest 8.04 from ubuntu.com).  It is a **much** more stable livecd.  8.10 *becomes* stable only after applying numerous updates, so the livecd is quite unstable.

---

