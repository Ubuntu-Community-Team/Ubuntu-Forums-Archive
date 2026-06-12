---
title: "computer slows to a halt when watching video. please help!"
date: 2010-06-27
forum: New to Ubuntu
---

### Post by 124moosi on 2010-06-27
Hello.
I've been having problems with video since updating from version 9 to ubuntu 10.04. Initially when i was streaming something on a website i was finding that the frame rate was about half of what it should have been. After a bit of messing around i released that when i updated to 10.04 it hadn't carried over my video card driver so i installed that and for a couple of weeks everything was fine. 
Just recently it seems to be the case where if i try to watch a .avi file or other downloaded movie, everything goes ok for the first 5 minutes or so but after that the frame rate drops again, and then the computer starts to become so slow that i eventually have to force it to power down, even after closing the video player.
My first though was to go back to the video card driver. There are three options for the driver to use, all of which I've tried and they all do the same thing.
Does anyone have any ideas? I'd really appreciate the help. I don't want to have to go back to that awful windows nightmare i woke up from

---

### Post by nhasian on 2010-06-27
lets get some more info from you.  which video adaptor do you have?
also which driver are you using?  what video playback software are you using?  Also can you give us your system specs?

the following terminal command will give us more info to help you.

```
lshw -C display,cpu,memory
```

---

### Post by 124moosi on 2010-06-27
so heres what i get from the terminal:

*-memory                
       description: System memory
       physical id: 0
       size: 2011MiB
  *-cpu
       product: Intel(R) Core(TM)2 CPU         T5600  @ 1.83GHz
       vendor: Intel Corp.
       physical id: 1
       bus info: cpu@0
       version: 6.15.2
       serial: 0000-06F2-0000-0000-0000-0000
       size: 1GHz
       capacity: 1GHz
       width: 64 bits
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow cpufreq
       configuration: id=0
     *-logicalcpu:0
          description: Logical CPU
          physical id: 0.1
          width: 64 bits
          capabilities: logical
     *-logicalcpu:1
          description: Logical CPU
          physical id: 0.2
          width: 64 bits
          capabilities: logical
  *-display
       description: VGA compatible controller
       product: G72M [Quadro NVS 110M/GeForce Go 7300]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:ed000000-edffffff memory:d0000000-dfffffff(prefetchable) memory:ee000000-eeffffff memory:ef000000-ef01ffff(prefetchable)



I'm using totem movie player 2.30.2 just the standard one that comes with the OS. I'm using a Geforce go 7300. For the driver it's giving me the choice off NVIDIA accelerated graphics driver versions 173 and version 96 also one which says (version current)[Recommended] which is the one i have been mainly using

---

### Post by nhasian on 2010-06-27
okay i can recommend two things.  you can upgrade to the latest nvidia drivers 256.35 by adding the this PPA to your sources:

```
ppa:ubuntu-x-swat/x-updates
```

also you can try [vlc]("apt:vlc") for playback instead.

---

### Post by 124moosi on 2010-06-27
Thanks, I'm downloading vlc now. what exactly do i do with the code? I'm still very new to anything that doesn't involve the GUI. when i type the code into the terminal i get "bash: ppa:ubuntu-x-swat/x-updates: No such file or directory
"

---

### Post by nhasian on 2010-06-27
oops sorry about that.  sometimes i forget to give more detailed instructions.  simply go to System-> Administration-> Software Sources, click on the Other Software tab, then click the add button.  now you can add the ppa:

```
ppa:ubuntu-x-swat/x-updates
```

make sure that nvidia-current is your driver, and then when you do the update-manager it will pick up the latest nvidia driver from this new source.

---

### Post by 124moosi on 2010-06-27
I'm installing the updates now. I've also been running VLC and it's seems to be working alot better.

Thanks so much! You're a star, it's very much appreciated!!!

---

### Post by 124moosi on 2010-06-27
I don't think it's worked after all :( It lasted about 10 minutes and froze up and crashed again. The laptop seems a bit warmer than usual. Could this be related to an over heating problem?

---

### Post by nhasian on 2010-06-27
yes its quite possible.  what are your cpu and gpu temperatures while in ubuntu?

```
sensors
```

> **124moosi said:**
> I don't think it's worked after all :( It lasted about 10 minutes and froze up and crashed again. The laptop seems a bit warmer than usual. Could this be related to an over heating problem?

---

### Post by 124moosi on 2010-06-28
acpitz-virtual-0
Adapter: Virtual device
temp1:       +59.5°C  (crit = +126.0°C)   

is that to high?

---

### Post by lovinglinux on 2010-06-28
> **124moosi said:**
> Could this be related to an over heating problem?

Definitely, specially considering the problem occurs after a couple of minutes watching the video. This used to happen on my machine when watching flash videos with a P4 CPU.

Clean up the CPU fan.

---

### Post by nhasian on 2010-06-28
no 60C not too high.  is that idling or while playing back your videos?

---

### Post by 124moosi on 2010-06-28
I've just turned the laptop on after having been off for a couple of hours. I checked the sensors and it was sitting at 36.5°C when idle. after a few minutes idle it remained the same. I've been running video and its to rise in temp around 5°C per minute. I'm currently sitting at 57.5°C where it seems staying fairly steadily now.  (when i switched it off about 4 hours ago it felt much hotter). It has lasted longer without crashing though since updating and running vlc. Might just be coincidence

---

### Post by 124moosi on 2010-06-28
it's slowing down now as if it's about to crash. it's at 61.5°C

---

