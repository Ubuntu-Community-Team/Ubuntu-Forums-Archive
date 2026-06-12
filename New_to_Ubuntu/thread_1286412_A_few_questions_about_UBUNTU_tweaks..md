---
title: "A few questions about UBUNTU tweaks."
date: 2009-10-08
forum: New to Ubuntu
---

### Post by BT1 on 2009-10-08
Now I know that two or more operating systems aren't going to have the same options/tweaks as the others, but there were a few options that I saw in windows that I liked, and a few that exist in both ubuntu and windows that I was curious about.

1.) Booting with 2 or more cores when using multi-core processors.
-In Windows XP and Vista, you have the option of changing (through MSCONFIG) the number of cores your computer uses to boot up the system. If unchanged, a dual core (or quad core) will only register as one CPU, but you can change the setting to recognise both (or all four) cores to help share the start up load.

*Does Ubuntu have an equivilent to this?*

2.) Ramdisk.
-In Windows XP/Vista there is the option (some may have to look it up or learn about it) to use Ram as a temporary virtual storage device. There are programs out there that can take a gig or two of ram to spare (for people like me who's got a desktop that has 8gigs and barely hits 4 with full use) and make it a volital virtual drive that you can temporarily store files on for quick use. This is useful for such things as playing games that read/write from the disk alot as you can download programs to run ISOs (like Daemon Lite) and the load times from disk are nearly instant.

*Does Ubuntu have an equivilent to the ramdisk option?**

*I know that some distros of linux let you run the whole OS in ram like DSL (Damn Small Linux), but I'm looking for making virtual ram drives. But if Ubuntu can be run purely in ram with the ability to store and save onto a physical hard drive, that would be awesome too

3.) Daemon Lite.
-Does Linux have any software that can make virtual drives from which to run ISOs?

4.) Ubuntu, as far as I saw, has an app that lets you choose the speed of your processor (or processors if you make another of the same app but change the cpu option) but every time I restart, it doesn't save my settings and it goes back to a conservative setting. Is there any way to make my CPUs go full out balls to the wall fast 24/7, or am I doomed to keep modifying those applets to keep my speed topped out?

I had more questions, but my ADD has gotten hold of me.

These are questions I really would like to find out about, so once again I look to the Gurus for guidance! :guitar:

---

### Post by scorp123 on 2009-10-09
> **BT1 said:**
>  1.) Booting with 2 or more cores when using multi-core processors.  Ubuntu's default kernel has multi-core support already turned on. But there is a boot option that allows you to limit the number of cores the Linux kernel would be able to use ... But mere mortals should not ever need to use that option. This stuff is mostly used for troubleshooting things on servers that badly misbehave. Or if Oracle consultants come knocking on your door and claim that your Oracle instance isn't licensed to run on your 32-core system ... so you might be forced to turn off a few cores until you have paid up for the license... Or something like that.

So there's no need for brain-dead CPU tweaking as on Windows. Ubuntu will automatically detect and use all cores that you have. Just sit back and relax.

If you want to make sure simply enter this command into a terminal:
```
cat /proc/cpuinfo
```

This should spit out the number of CPU cores that the kernel sees. Example from my hp desktop PC:
```
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Quad CPU    Q9400  @ 2.66GHz
stepping	: 10
cpu MHz		: 2000.000
cache size	: 3072 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 4
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority
bogomips	: 5333.20
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Quad CPU    Q9400  @ 2.66GHz
stepping	: 10
cpu MHz		: 2000.000
cache size	: 3072 KB
physical id	: 0
siblings	: 4
core id		: 1
cpu cores	: 4
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority
bogomips	: 5333.23
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 2
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Quad CPU    Q9400  @ 2.66GHz
stepping	: 10
cpu MHz		: 2000.000
cache size	: 3072 KB
physical id	: 0
siblings	: 4
core id		: 2
cpu cores	: 4
apicid		: 2
initial apicid	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority
bogomips	: 5333.24
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 3
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Quad CPU    Q9400  @ 2.66GHz
stepping	: 10
cpu MHz		: 2000.000
cache size	: 3072 KB
physical id	: 0
siblings	: 4
core id		: 3
cpu cores	: 4
apicid		: 3
initial apicid	: 3
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority
bogomips	: 5333.24
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:
```

So it starts counting at CPU #0 and finishes counting at CPU #3, so the cores are numbered: 0,1,2,3 .... which makes this a 4-core system. 


> **BT1 said:**
>  *Does Ubuntu have an equivilent to the ramdisk option?**  Ubuntu (and all Linux distros in general) will already "out of the box" use parts of your RAM for caching. Just type the command "free" into a terminal and you will see how much RAM is being used for caching and buffering. So there is hardly any need to start messing with RAM-disks.

But sure, the concept is known. There are even several types of RAM-disks that one could use. It's just that tweaks that you suggest are totally not necessary here and won't do anything here. You'd just be decreasing the size of available RAM, that's all.

Please read this:
[http://www.linux-mag.com/cache/7388/1.html](http://www.linux-mag.com/cache/7388/1.html)

> **BT1 said:**
>  -Does Linux have any software that can make virtual drives from which to run ISOs?  Not needed. The Linux "mount" system command can do that since the beginning of time. It's nice to see Windows catching up, LOL
```
sudo mount -t iso9660 -o ro,loop /path/to/file.iso /path/to/mnt-point
```

There are also GUI tools out there that will allow you to show the contents of any *.iso file with a simple click. Search for "iso" in Synaptic, it should spit out a few suggestions.

> **BT1 said:**
>  but every time I restart, it doesn't save my settings and it goes back to a conservative setting. the standard setting should be "On Demand", so it should automagically tweak the CPU speeds when it needs to do more. The laptop I'm typing this on is on AC power but currently it's running at 800 MHz. For typing a bit into a browser window this seems to be more than enough. As soon as I start doing some desktop effects the CPU will go up to 1.66 GHz.

Unless your CPU isn't recognized correctly and the system really feels more sluggish than it should then there is nothing to do here and you can leave everything "as is".

---

### Post by freak42 on 2009-10-09
2. there is already a ramdisk set up for you to use, by default it can only use up to half of your memory size (afaik). Please be advised that whatever you put there will be lost upon shutdown, reboot, or a crash / reset (but I guess you know that, but others might not).

The location of the ramdisk is : /dev/shm

You can of course create your own custom ramdisks: Maybe use this guide or google for it: [http://www.vanemery.com/Linux/Ramdisk/ramdisk.html](http://www.vanemery.com/Linux/Ramdisk/ramdisk.html)

3. There is no Daemon Tools afaik, but you can easily mount .iso files like any other physical disk: see [http://www.tech-recipes.com/rx/2747/ubuntu_how_to_mount_unmount_iso_files/](http://www.tech-recipes.com/rx/2747/ubuntu_how_to_mount_unmount_iso_files/)

4. I don't know, but I've seen other people asking this very question in this forum before: try searches with this keywords: cpu-scaling, [default] governor (reset, reboot, ...)

hth

---

### Post by Paqman on 2009-10-09
If you want a GUI way to mount .iso files, there are several in the repos (eg: gmountiso)

> **BT1 said:**
> 
4.) Ubuntu, as far as I saw, has an app that lets you choose the speed of your processor (or processors if you make another of the same app but change the cpu option) but every time I restart, it doesn't save my settings and it goes back to a conservative setting. Is there any way to make my CPUs go full out balls to the wall fast 24/7, or am I doomed to keep modifying those applets to keep my speed topped out?


CPU scaling is done on the fly, whenever you put a load on the CPU, it'll run at max speed. If there is nothing to use the extra capacity, your CPU will throttle back. Running constantly at full throttle won't give you any extra performance, it'll just make your machine hotter and use more power.

If you want further performance out of your processor, you should overclock through BIOS. Software overclocking is not really very good.

---

### Post by 3rdalbum on 2009-10-09
If you want to run your CPU flat out, disable CPU frequency scaling in your BIOS.

The default in Ubuntu should be Ondemand anyway, which will boost your CPU speed to full as soon as there is appreciable load. It saves power. If your machine is running on Conservative all the time, then you might be either running on battery power, or there's some incompatibility between Linux and your machine's particular ACPI implementation.

EDIT: Also, Ubuntu's boot sequence is multi-threaded already, but most of the waiting time when you start up is because your disks can't access bits of data quickly enough. Ubuntu developers are continuing to work on getting the CPU and I/O (startup disk) to work to full capacity, with neither waiting around for the other to do something. The end result will be a faster bootup. Ubuntu 9.04 already boots faster than 8.10, and 9.10 boots faster than 9.04.

---

### Post by fanglinyong on 2009-10-09
when you used ubuntu for a long time ,you will found that this system is also very good!

---

### Post by HarrisonNapper on 2009-10-09
> **BT1 said:**
> 
4.) Ubuntu, as far as I saw, has an app that lets you choose the speed of your processor (or processors if you make another of the same app but change the cpu option) but every time I restart, it doesn't save my settings and it goes back to a conservative setting. Is there any way to make my CPUs go full out balls to the wall fast 24/7, or am I doomed to keep modifying those applets to keep my speed topped out?

Just to stress the point that essentially anything can be done in *nix, the default can be changed, though if performance is your goal, OnDemand should work just as well as Performance. All Performance does is runs your CPU at full throttle even when it doesn't need to so you're just wasting the life of your CPU. Not that it matters, as by the time it dies, you'll probably have gotten a new one, but in case you're a pack rat like me, I would avoid. I, however, use this to default to conservative as my laptop heats up quickly.

Anyway, this option can be changed in gconf-editor (Pre-9.04):
The option is in gconf-editor under apps->gnome-power-manager->cpufreq

If you have Jaunty or later, you actually have to edit the config file for the cpu scaling applet.

---

### Post by mharrison on 2009-10-09
> **freak42 said:**
> 2. 
3. There is no Daemon Tools afaik, but you can easily mount .iso files like any other physical disk: see [http://www.tech-recipes.com/rx/2747/ubuntu_how_to_mount_unmount_iso_files/](http://www.tech-recipes.com/rx/2747/ubuntu_how_to_mount_unmount_iso_files/)


Actually, you can install gmountiso

You have to create a folder in /media for the iso to mount to, but it graphically allows you to select your iso, mount it to the folder, and also unmount it from the same gui.  I use it to mount my backup copies of my games.

---

### Post by allenbradley on 2009-10-09
and if you can't remember the mount options, install fuseiso:
```
sudo apt-get install fuseiso
``` Its really neat and simple to mount ```
sudo fuseiso ~/<filename>.iso /media/fuseiso
```

---

### Post by BT1 on 2009-10-09
Thanks for the quick responses. :)

I suppose I'm just trying to get the biggest bang for my uh... well not buck cause Ubuntu is free and all :P but you know what I mean. My only concerns (as you might have got the hint from) are the slow(ish) start up times, and a bit of a lagging in the general operation of things.

When I first came to Linux I thought it'd be ":shock:" fast. My first taste of linux was actually DSL which is a quick little devil but lacked the full package feel that Ubuntu has to offer. I thought initially that since linux distros would be minus all the junk MS throws into its operating systems, it would be remarkably faster. I'm coming from a tweaked XP/Vista perspective, and I just see a few things that I would like to go faster, things normal people don't really care about, but things that bug the living daylights out of me. I know that Ubuntu will further put the smackdown on long start ups, but the questions about CPU performance and ramdisks and all are ones that I am concerned about when I think of my daily use and expectations for a 2009 computer system.


1.) The question about the start up cores issue was in regard to me not knowing if that was already active in Linux because of the slower load speed I was encountering. Thanks for the info about this.

2.) Thanks for the Ramdisk info.

3.) The question about the ISO mounting was in regard to the fact that most of my CDs, DVDs, and Game Disks are sitting in multiple external drives due to the fact that: 

[LIST=1]
[*]Multiple CDs + young kids who use them as frisbees = bad
[*]Changing disks out all the time = tiresome and slow
[/LIST]
ISOs are just one more way to enhance longevity of favourite media as well as ensure huge speed gains.

4.) The question about the CPU applet thing was in regard to my concern about the possibility of some sort of overhead from adjusting the CPU frequency back and forth, but from the sounds of it, there seems to only be adjustment. Is this true?

Thanks again for the info!

---

### Post by HarrisonNapper on 2009-10-09
> **BT1 said:**
> Thanks for the quick responses. :)

4.) The question about the CPU applet thing was in regard to my concern about the possibility of some sort of overhead from adjusting the CPU frequency back and forth, but from the sounds of it, there seems to only be adjustment. Is this true?

No.

---

### Post by oldos2er on 2009-10-09
> **BT1 said:**
>  1.) Booting with 2 or more cores when using multi-core processors.:guitar:

 In the file /etc/init.d/rc, change CONCURRENCY=none to CONCURRENCY=shell.

---

