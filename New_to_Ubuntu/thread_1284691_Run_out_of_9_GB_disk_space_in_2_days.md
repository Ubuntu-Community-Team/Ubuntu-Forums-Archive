---
title: "Run out of 9 GB disk space in 2 days"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by sgd1977 on 2009-10-06
Hello,

I'm a new Ubuntu user. I installed Ubuntu a couple of days ago after freeing up some disk space from Vista (147GB HDD - Vista freed up 9.5 GB).

I assumed 9.5 GB would be enough to install and evaluate Ubuntu, especially considering the OS fits on one CD (even if it is compressed).

Unfortunately, I have run out of disk space! I went to system monitor and here's the breakup:[http://www.ubuntulinux.org/](http://www.ubuntulinux.org/)
/dev/sda5 [directory: /] 2.3 GB used 2.3 GB left 56 MB free 0. This has been steadily decreasing. It was just 120 MB about 2 hours ago. I don't know what is consuming the space. I even removed Ekiga but that freed up just 12 MB.
lrm [/lib/modules/2.6.28-11/generic/volatile] 879 MB. Almost 100% free.
tmpfs [lib/init/rw and /dev/shm] 879 MB Almost 100% free
udev [/dev] 879 MB. Almost 100% free.
varlock [/var/lock]. 879 MB. Almost 100% free.
varrun [/var/run] 879 MB. Almost 100% free.

[I would've pasted a screenshot instead of typing everything out but there's no space left on disk to save the file :-(]

Questions:
1) Why is 2.3 GB consumed already? I've only installed a 20MB nvidia driver. I had come with the expectation that Ubuntu would be fairly lean given that it fits on the CD with OpenOffice. At 2.3 GB, it is smaller than Vista but more bloated than XP. And I'm not including the other partitions otherwise its more bloated than Vista too (atleast its footprint)
2) Why are so many devices created consuming nearly 900MB but lying empty? Can these be repartitioned? Since tmpfs, udev, varlock and varrun are of type 'tmpfs' cannot all the mounted directories use a single device and that way do better space management?
3) My empty partition before Ubuntu install was 9 GB. The numbers I've mentioned above add up to approx 5.8 GB. Where did the other 3 GB go which is not accounted for by System Monitor.

---

### Post by Paqman on 2009-10-06
> **sgd1977 said:**
> 
Questions:
1) Why is 2.3 GB consumed already?


That's about how much space it takes. The problem here is that you whole partition is only 2.3GB, so it's filled up very quickly. You need to expand your root partition to fill the whole of the 9GB you allocated for it. Sounds like you've been bitten by a common bug in the installer.

> 
2) Why are so many devices created consuming nearly 900MB but lying empty? Can these be repartitioned? Since tmpfs, udev, varlock and varrun are of type 'tmpfs' cannot all the mounted directories use a single device and that way do better space management?


You can ignore these, they're not actual devices or partitions.

> 
3) My empty partition before Ubuntu install was 9 GB. The numbers I've mentioned above add up to approx 5.8 GB. Where did the other 3 GB go which is not accounted for by System Monitor.

As mentioned above, you're actually only using 2.3GB of the 9GB space you created. If you boot into the LiveCD and go to System > Admin > Partition Editor you'll be able to see this, and expand your root partition (sda5) to fill the whole 9GB.

---

### Post by lavinog on 2009-10-06
> 
/dev/sda5 [directory: /] 2.3 GB used 2.3 GB left 56 MB free 0. This has been steadily decreasing. It was just 120 MB about 2 hours ago. I don't know what is consuming the space. 
100Mb can easily be used by firefox cache, thumbnail cache, logs, and config files.

[quote=Paqman]As mentioned above, you're actually only using 2.3GB of the 9GB space you created. If you boot into the LiveCD and go to System > Admin > Partition Editor you'll be able to see this, and expand your root partition (sda5) to fill the whole 9GB.[/quote]
follow this advice.  Just because you cleaned up some space from vista doesn't mean ubuntu gets to enjoy it.
A bit of a warning though: Make sure windows has at least 10% free space, otherwise you can excessivly wear out your drive.

to answer your other question.  You disk drives will typically be labeled /dev/sd[some letter]
The hard drive that you boot to will be /dev/sda, a second drive may be /dev/sdb ...etc.
The number is the partition number.  /dev/sda1 is kind of similar to the c: drive in windows.  You do not access the drive from this handle though...you mount it as a folder...for the most part ubuntu will mount partitions for you, and in your case /dev/sda5 is mounted as / (the root folder)

The other filesystems you see use ram for storage.  When you reboot, the files in these mount points will go away, and be rebuilt on next reboot.
the /dev/shm mount point can be used for temp storage...so you can take a screenshot and save it there...don't fill it up though, some programs may require some free space there.

---

### Post by freak42 on 2009-10-07
```
df -Th
``` (in a console) gives you a nice overview of all your disks, partitions and how much space they provide/consume and so on

hth

---

### Post by lavinog on 2009-10-07
```
df -Th|grep -v tmpfs
```
can be used to ignore the temp filesystems

---

### Post by sgd1977 on 2009-10-07
Thank you for the partitioning tool help. I was able to add another 7 GB. I understand now the tmpfs device type is not real.
sdesai@Orion:~$ df -Th
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda5     ext3    9.3G  2.3G  6.6G  26% /
tmpfs        tmpfs    880M     0  880M   0% /lib/init/rw
varrun       tmpfs    880M  104K  880M   1% /var/run
varlock      tmpfs    880M     0  880M   0% /var/lock
udev         tmpfs    880M  168K  880M   1% /dev
tmpfs        tmpfs    880M   96K  880M   1% /dev/shm
lrm          tmpfs    880M  2.4M  878M   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sdc      vfat    1.9G  1.8G  184M  91% /media/SIDDHARTH D
/dev/sdd1  fuseblk     75G   32G   43G  43% /media/MAXTOR
sdesai@Orion:~$

---

### Post by seamushc on 2009-10-07
Also, if you want to see where your disk is being used try this:

```
du -ka / | sort -n
```

---

### Post by tiras_dude on 2009-10-15
hello,

I believe that [sgd1977]("http://ubuntuforums.org/member.php?u=925217") is on to something.

I have been testing karmic since beta and have been experiencing problems with lacking root partition space since the .31-13 kernel with updates came out.

Machine 1

AMD 64 Dual Core running Karmic Beta AMD from Flash Drive (4 GB)

SDA1 100 MB with /boot
SDA2 3.6 GB with /
Swap is shared with the 9.04

After second update ran out of space 

Please note that on 9.04 my / never exceeded 3.1 GB

But in this case I may concede that 4 gigs may be small. Also note that /home is not used at all (except for config files)

Machine 2

Celeron 2.4 running Karmic Beta i386 on 40 GB HDD

SDA1 100 MB with /boot
SDA2 764 MB swap
SDA3 6.4 GB with /
SDA4 29.5 GB /home

After second update the / partition is full! No packages besides ubuntu-restricted-extras and VLC have been installed.

Cleaning /var/cache/apt/archives saves max 400 MB

What is going on?

---

### Post by lavinog on 2009-10-15
> **tiras_dude said:**
> 
What is going on?
One thing that may be happening is that the old kernels are still installed.  A kernel update does not replace old kernels

You may want to install a minimal install if you are only going to have 4-6g
[thread]1155961[/thread]

---

### Post by tiras_dude on 2009-10-15
Hi,

tried cleaning out old kernel sources from /usr/src that saved about 400 MB. Enough to keep working.

But I still don't understand the reason why root is sooo bloated in Karmic. My current 9.04 installation is loaded with packages, including devs and libraries. /root is used up to 4.8 GB and that is with 4 kernels 2.6.28-11 through 15, + vbox modules.

And if karmic is that much bigger than Jaunty, than what is the ideal size for / partition in Karmic?

Thanks

---

### Post by lavinog on 2009-10-15
> **tiras_dude said:**
> Hi,

tried cleaning out old kernel sources from /usr/src that saved about 400 MB. Enough to keep working.

But I still don't understand the reason why root is sooo bloated in Karmic. My current 9.04 installation is loaded with packages, including devs and libraries. /root is used up to 4.8 GB and that is with 4 kernels 2.6.28-11 through 15, + vbox modules.

And if karmic is that much bigger than Jaunty, than what is the ideal size for / partition in Karmic?

Thanks
did you compile your kernel from source?
how much space does /boot take?
```
du -h /boot
```
mine is 39M

---

### Post by louieb on 2009-10-15
Got my curiosity up - I dual boot Jaunty and Karmic on my laptop.  Have about the same software on each.  Have a separate /home for each. I never get rid of a kernel.  Both fully up to date as of last night. 

Still have 4 or 5 packages to add to Karmic Thunderbird probably the largest. (VirtualBox, BlueFish, PCManFM, GnomeCommander are the others)

Jaunty / (root) comes in at 3.5GB and Karmic is at 3.2GB. once I add the other packages suspect they will both be about the same. 

Early on I noticed I was downloading source code too when Karmic updated. May have been a bug. I edited /etc/apt/sources.list and commented out the the source repositories. My guess is downloading source along with the binaries could easily double the size needed by the / (root) partition. Might want to check the size of you usr/src/ directory.

---

### Post by sloggerkhan on 2009-10-15
> **tiras_dude said:**
> Hi,

tried cleaning out old kernel sources from /usr/src that saved about 400 MB. Enough to keep working.

But I still don't understand the reason why root is sooo bloated in Karmic. My current 9.04 installation is loaded with packages, including devs and libraries. /root is used up to 4.8 GB and that is with 4 kernels 2.6.28-11 through 15, + vbox modules.

And if karmic is that much bigger than Jaunty, than what is the ideal size for / partition in Karmic?

Thanks

Might want to try clearing your apt-cache.

---

### Post by tiras_dude on 2009-10-16
[lavinog]("http://ubuntuforums.org/member.php?u=118273") - I am at 27.1 mb with -14 kernel version only

[louieb]("http://ubuntuforums.org/member.php?u=120176") - I think this may be a bug of sorts, I have seen a bug where grub2 was taking up rediculous amounts of space, but on my system that directory is small (/usr/lib/grub)

[sloggerkhan]("http://ubuntuforums.org/member.php?u=176924") - done that a bit earlier (saved about 380 mb)

The laptop dual boot situation is more or less explainable.

The situation with my other laptop (dell inspiron 1000) is what is bothering me the most at the moment. (6.5 gig root partition full)

---

### Post by tiras_dude on 2009-10-16
found something!

/var/log is 4.3 GB!!!!

on my current system it is 29 mb.

sys.log is 1.7 GB

kern.log is 1.6 GB

 messages are 700 mb

WTF? Bug report time.

Thanks all for help.

---

### Post by lavinog on 2009-10-16
wow!
Is there a message that is repeated alot?

---

### Post by tiras_dude on 2009-10-16
Filed the bug report

[https://bugs.launchpad.net/ubuntu/+bug/453444](https://bugs.launchpad.net/ubuntu/+bug/453444)

---

### Post by tiras_dude on 2009-10-16
[lavinog]("http://ubuntuforums.org/member.php?u=118273") - no idea, my gedit crashes when i try to open any of them (probably too big for it to handle)

---

### Post by lavinog on 2009-10-16
try
```
tail -n 50 /var/log/messages
```

also you can compress the logs and see if you can post them here.
if there is a repeated message it should compress pretty good.
```
tar cvvzf logs.tar.gz /var/log/messages /var/log/syslog /var/log/kern.log

```
check the size of logs.tar.gz and see if you can upload it.

---

### Post by tiras_dude on 2009-10-16
tail -n 50 /var/log/messages

gives me this:

Oct 15 14:16:45 DELL-1000 kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Oct 15 14:16:45 DELL-1000 kernel: [    0.000000]   Normal   0x00001000 -> 0x0000ddf0
Oct 15 14:16:45 DELL-1000 kernel: [    0.000000]   HighMem  0x0000ddf0 -> 0x0000ddf0
Oct 15 14:16:45 DELL-1000 kernel: [    0.000000] Movable zone start PFN for each node
Oct 15 14:16:45 DELL-1000 kernel: [    0.000000] early_node_map[3] active PFN ranges
Oct 15 14:16:45 DELL-1000 kernel: [    0.000000]     0: 0x00000000 -> 0x00000002
Oct 15 14:16:45 DELL-1000 kernel: [    0.000000]     0: 0x00000006 -> 0x0000009f
Oct 15 14:16:45 DELL-1000 kernel: [    0.000000]     0: 0x00000100 -> 0x0000ddf0
Oct 15 14:16:45 DELL-1000 kernel: [    0.000000] Using APIC driver default
Oct 15 14:16:45 DELL-1000 kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x8008
Oct 15 14:16:45 DELL-1000 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Oct 15 14:16:45 DELL-1000 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Oct 15 14:16:45 DELL-1000 kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Oct 15 14:16:45 DELL-1000 kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
Oct 15 14:16:45 DELL-1000 kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Oct 15 14:16:45 DELL-1000 kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Oct 15 14:16:45 DELL-1000 kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
Oct 15 14:16:45 DELL-1000 kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
Oct 15 14:16:45 DELL-1000 kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Oct 15 14:16:45 DELL-1000 kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d6000
Oct 15 14:16:45 DELL-1000 kernel: [    0.000000] PM: Registered nosave memory: 00000000000d6000 - 00000000000d8000
Oct 15 14:16:45 DELL-1000 kernel: [    0.000000] PM: Registered nosave memory: 00000000000d8000 - 00000000000dc000
Oct 15 14:16:45 DELL-1000 kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
Oct 15 14:16:45 DELL-1000 kernel: [    0.000000] Allocating PCI resources starting at 10000000 (gap: 10000000:eec00000)
Oct 15 14:16:45 DELL-1000 kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
Oct 15 14:16:45 DELL-1000 kernel: [    0.000000] PERCPU: Embedded 14 pages at c11c2000, static data 35612 bytes
Oct 15 14:16:45 DELL-1000 kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 56271
Oct 15 14:16:45 DELL-1000 kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.31-14-generic root=UUID=3f9d97e4-a0a1-4adc-a847-ed39f072af4f ro quiet splash
Oct 15 14:16:45 DELL-1000 kernel: [    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
Oct 15 14:16:45 DELL-1000 kernel: [    0.000000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
Oct 15 14:16:45 DELL-1000 kernel: [    0.000000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
Oct 15 14:16:45 DELL-1000 kernel: [    0.000000] Enabling fast FPU save and restore... done.
Oct 15 14:16:45 DELL-1000 kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Oct 15 14:16:45 DELL-1000 kernel: [    0.000000] Initializing CPU#0
Oct 15 14:16:45 DELL-1000 kernel: [    0.000000] allocated 1136320 bytes of page_cgroup
Oct 15 14:16:45 DELL-1000 kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Oct 15 14:16:45 DELL-1000 kernel: [    0.000000] Initializing HighMem for node 0 (00000000:00000000)
Oct 15 14:16:45 DELL-1000 kernel: [    0.000000] Memory: 208148k/227264k available (4565k kernel code, 18552k reserved, 2143k data, 540k init, 0k highmem)
Oct 15 14:16:45 DELL-1000 kernel: [    0.000000] virtual kernel memory layout:
Oct 15 14:16:45 DELL-1000 kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Oct 15 14:16:45 DELL-1000 kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Oct 15 14:16:45 DELL-1000 kernel: [    0.000000]     vmalloc : 0xce5f0000 - 0xff7fe000   ( 786 MB)
Oct 15 14:16:45 DELL-1000 kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xcddf0000   ( 221 MB)
Oct 15 14:16:45 DELL-1000 kernel: [    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
Oct 15 14:16:45 DELL-1000 kernel: [    0.000000]       .data : 0xc0575554 - 0xc078d308   (2143 kB)
Oct 15 14:16:45 DELL-1000 kernel: [    0.000000]       .text : 0xc0100000 - 0xc0575554   (4565 kB)
Oct 15 14:16:45 DELL-1000 kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Oct 15 14:16:45 DELL-1000 kernel: [    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
Oct 15 14:16:45 DELL-1000 kernel: [    0.000000] NR_IRQS:2304 nr_irqs:256

I will try to upload these logs here but they will be like 150 megs (rar compressed)

---

### Post by tiras_dude on 2009-10-16
guess I can't attach 200 mb here, if you need it, pm me with your email of good ftp location and I will try to upload them there.

---

### Post by lavinog on 2009-10-17
you could try dropbox

see how small 7z can get them ( I find 7z to compress better than rar):
```

7z a -mx=9 messagelog.7z /var/log/messages
7z a -mx=9 syslog.7z /var/log/syslog
7z a -mx=9 kernlog.7z /var/log/kern.log

```

---

### Post by cariboo on 2009-10-17
I usually view logs using mc, but if your text editor crashes trying to view a log, just use cat:

```
cat /var/log/auth.log | less
```

the above command will allow you to page through the log using the space bar.

---

### Post by lavinog on 2009-10-17
I wrote a script to find out what day the most messages occurred

```

python logcheck.py

```

you should get something like:
```

messages
--------------------
Oct 12 : 11
Oct 15 : 1196
Oct 17 : 597
--------------------


syslog
--------------------
Oct 17 : 16
--------------------


kern.log
--------------------
Oct 15 : 1448
Oct 17 : 724
--------------------

```

---

### Post by ibuclaw on 2009-10-17
What most likely happened is that a single driver "soft" locked up, and repeated the same 24 or so lines of logs for the entire time your machine was running that should provide enough backtracing evidence to look into why that happened. But not give you the complete answer.

Did you notice on a day this week that your CPU was blaring away?

Edit:
If you have enough space on a separate device, try this:
```
grep -C 50 "Call Trace" /var/log/messages >~/Desktop/trace.log
```
If the file is still too large:
```
head -n 500 ~/Desktop/trace.logs > ~/Desktop/head.log
tail -n 500 ~/Desktop/trace.logs > ~/Desktop/tail.log
rm ~/Desktop/trace.log

```

Attach the *.log files left on your Desktop.

Regards
Iain

---

### Post by tiras_dude on 2009-10-18
greetings all

lets try this one step at at time.

First thing for you to note. I have copied the logs from the problem machine to another system and they siply reside in the directory, so if you don't mind, please provide instructions for a relative path, ei assuming that I execute commands from the same directory where these files are now.

-to mr. lavinog

running your script from the same directory returned messages
--------------------
Oct 18 : 656
--------------------


syslog
--------------------
Oct 18 : 1065
--------------------


kern.log
--------------------
Oct 17 : 5281
Oct 18 : 783
--------------------
 

But my guess is it is for my current system, can you please modify the script to take in to account the situation described above.

With regards to 7zip (processing at the moment) will update as soon as it is done.


-to mr. [COLOR=Black]**[[COLOR=#D40000][B]**[/COLOR]]("http://ubuntuforums.org/member.php?u=77104")[/B][/COLOR]cariboo907

running your cat command in the form "cat messages | less"

showed that that the computer's cpu temp/speed was normal.

Oct 15 00:42:34 DELL-1000 kernel: [   26.814694] CPU0: Temperature/speed normal
message is issued about 575 times a second for a while =)

After about page 200 I gave up.

running "cat syslog | less"

showed this at about 575 times a second too

Oct 15 00:42:31 DELL-1000 kernel: [   23.568556] CPU0: Temperature above threshold, cpu clock throttled (total events = 13710)
Oct 15 00:42:31 DELL-1000 kernel: [   23.569662] CPU0: Temperature/speed normal

running "cat kern.log | less"

Showed much the same situation as in syslog, with ocasionall intermix of the following below:

Oct 15 00:42:27 DELL-1000 kernel: [   19.676242] b43-pci-bridge 0000:02:00.0: enabling device (0000 -> 0002)
Oct 15 00:42:27 DELL-1000 kernel: [   19.676270] CPU0: Temperature above threshold, cpu clock throttled (total events = 11589)
Oct 15 00:42:27 DELL-1000 kernel: [   19.676302] b43-pci-bridge 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Oct 15 00:42:27 DELL-1000 kernel: [   19.676343] b43-pci-bridge 0000:02:00.0: setting latency timer to 64
Oct 15 00:42:27 DELL-1000 kernel: [   19.680520] ssb: Sonics Silicon Backplane found on PCI device 0000:02:00.0
Oct 15 00:42:27 DELL-1000 kernel: [   19.681424] CPU0: Temperature/speed normal
Oct 15 00:42:27 DELL-1000 kernel: [   19.681880] CPU0: Temperature above threshold, cpu clock throttled (total events = 11590)
Oct 15 00:42:27 DELL-1000 kernel: [   19.683063] CPU0: Temperature/speed normal

So I am not sure is that pc was melting or not =)


 - to mr. tinivole

Running grep -C 50 "Call Trace" messages >trace.log

produced a trace.log file of 0 bytes with nothing in it. I may have modified instructions improperly, please correct if I fd up.


Since I deleted the monster logs and updated the system again, it has been running kinda ok.

Let me know if anyone wants any other info?

And thank you very much for help!



BTW and OT

Anyone had success installing dual boot jaunty and karmic (AMD64 Both) if karmic was installed from alternate install cd? Tried it this weekend in VirtualBox but failed miserably. (If installing karmic from live CD it works)

---

### Post by lavinog on 2009-10-18
> **tiras_dude said:**
> greetings all

lets try this one step at at time.

First thing for you to note. I have copied the logs from the problem machine to another system and they siply reside in the directory, so if you don't mind, please provide instructions for a relative path, ei assuming that I execute commands from the same directory where these files are now.

-to mr. lavinog

I will update it for you.

> 
running your cat command in the form "cat messages | less"

showed that that the computer's cpu temp/speed was normal.

Oct 15 00:42:34 DELL-1000 kernel: [   26.814694] CPU0: Temperature/speed normal
message is issued about 575 times a second for a while =)

After about page 200 I gave up.

running "cat syslog | less"

showed this at about 575 times a second too

Oct 15 00:42:31 DELL-1000 kernel: [   23.568556] CPU0: Temperature above threshold, cpu clock throttled (total events = 13710)
Oct 15 00:42:31 DELL-1000 kernel: [   23.569662] CPU0: Temperature/speed normal

running "cat kern.log | less"

Showed much the same situation as in syslog, with ocasionall intermix of the following below:

Oct 15 00:42:27 DELL-1000 kernel: [   19.676242] b43-pci-bridge 0000:02:00.0: enabling device (0000 -> 0002)
Oct 15 00:42:27 DELL-1000 kernel: [   19.676270] CPU0: Temperature above threshold, cpu clock throttled (total events = 11589)
Oct 15 00:42:27 DELL-1000 kernel: [   19.676302] b43-pci-bridge 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Oct 15 00:42:27 DELL-1000 kernel: [   19.676343] b43-pci-bridge 0000:02:00.0: setting latency timer to 64
Oct 15 00:42:27 DELL-1000 kernel: [   19.680520] ssb: Sonics Silicon Backplane found on PCI device 0000:02:00.0
Oct 15 00:42:27 DELL-1000 kernel: [   19.681424] CPU0: Temperature/speed normal
Oct 15 00:42:27 DELL-1000 kernel: [   19.681880] CPU0: Temperature above threshold, cpu clock throttled (total events = 11590)
Oct 15 00:42:27 DELL-1000 kernel: [   19.683063] CPU0: Temperature/speed normal

So I am not sure is that pc was melting or not =)


This is the actual issue then.



You may need to modify logrotate to limit the size of logfiles also.
[quote=man logrotate]
size size
              Log  files  are rotated when they grow bigger than size bytes. If size is followed by M, the size if assumed to be in megabytes.  If the G suffix is used, the
              size is in gigabytes.  If the k is used, the size is in kilobytes. So size 100, size 100k, and size 100M are all valid.
[/quote]
[s]Maybe this can be added to the bug report you filed as a solution.[/s]
I added a comment to the bug report

---

### Post by lavinog on 2009-10-18
attached is a revised logcheck.py.
now you can specify the logfile to check:
```

python logcheck.py [logfile]

```

you can also have it split the file by date:
```

python logcheck.py -s [logfile]

```

of course if the log only spans one day then it won't have any benefit.  You can also split a log up with the split command:
```

split -C 900k logfile

```
This will make a bunch of files though.

---

### Post by tiras_dude on 2009-10-18
gentleman

uploaded the files to rapidshare 177 mb 7zip compressed

here is the link

[http://rapidshare.com/files/294742673/Dell_Logs.7z.html](http://rapidshare.com/files/294742673/Dell_Logs.7z.html)
 MD5: 4F398F1E3BA31829040234FFEB9E02DC

---

### Post by tiras_dude on 2009-10-18
python logcheck.py -s messages
messages
--------------------
Oct 14 : 480
Oct 15 : 8238668
--------------------

python logcheck.py -s syslog
syslog
--------------------
Oct 15 : 16478398
Oct 16 : 47
Oct 1O : 1
--------------------

python logcheck.py -s kern.log
kern.log
--------------------
Oct 14 : 583
Oct 15 : 16477032
Oct 16 : 46
--------------------

---

### Post by mbobak on 2009-11-17
FYI, I came up with the following workaround for this bug, only to be used till a proper fix is available.

The following is a cut-and-paste from my posting in the bug report, hope it helps someone:

Hi all,

This bug has been a real pain in my backside.  I think I have a reasonable, short-term workaround.  I'm *not* suggesting this is a permanent fix for anyone, nor should this be applied to any source trees anywhere.

This is strictly for someone who, like me, is suffering because of this, and wants a slightly better solution than simply killing off logging systemwide till a proper patch is available.

Here's my hack:
--- /etc/init/rsyslog-kmsg.conf.orig	2009-11-17 01:40:07.000000000 -0500
+++ /etc/init/rsyslog-kmsg.conf	2009-11-17 01:42:36.000000000 -0500
@@ -18,7 +18,7 @@
     chown syslog:syslog /var/run/rsyslog/kmsg
 end script
 
-exec dd bs=1 if=/proc/kmsg of=/var/run/rsyslog/kmsg
+exec dd bs=1 if=`grep -v "CPU[0-7]: Temperature" /proc/kmsg` of=/var/run/rsyslog/kmsg
 
 post-stop script
     rm /var/run/rsyslog/kmsg

Or, for people who don't like dealing w/ patch files, go to /etc/init, make a copy of rsyslog-kmsg.conf.  Then, edit rsyslog-kmsg.conf, find the line near the end of the file that looks like:
dd bs=1 if=/proc/kmsg of=/var/run/rsyslog/kmsg

and replace it with:
exec dd bs=1 if=`grep -v "CPU[0-7]: Temperature" /proc/kmsg` of=/var/run/rsyslog/kmsg

So, all this does is filter out *all* warnings referring to CPU temperature fluctuations (for boxes up to 8 CPUs).  Don't look at me if you don't see the warnings and end up flaming out your CPU. :-)

Hope this helps someone until such time that a proper fix is available.

-Mark

---

### Post by ubername on 2009-11-18
Checking the bug report
[https://bugs.launchpad.net/ubuntu/+bug/453444](https://bugs.launchpad.net/ubuntu/+bug/453444)
it says that the milestone for this is Ubuntu karmic-updates which has an expected date of 2011-04-09!
Does this mean we have to wait until then for the fix??

---

### Post by ubername on 2009-12-11
Seems fixed in kernel 2.6.31-17

---

### Post by LucidStrike on 2010-01-14
> **mbobak said:**
> Or, for people who don't like dealing w/ patch files, go to /etc/init, make a copy of rsyslog-kmsg.conf.  Then, edit rsyslog-kmsg.conf, find the line near the end of the file that looks like:
dd bs=1 if=/proc/kmsg of=/var/run/rsyslog/kmsg

and replace it with:
exec dd bs=1 if=`grep -v "CPU[0-7]: Temperature" /proc/kmsg` of=/var/run/rsyslog/kmsg

So, all this does is filter out *all* warnings referring to CPU temperature fluctuations (for boxes up to 8 CPUs).  Don't look at me if you don't see the warnings and end up flaming out your CPU. :-)

Hope this helps someone until such time that a proper fix is available.

-Mark
I did this and, upon reboot, ran into some issues. No matter what kernel I booted from, I couldn't even get through to the login screen. When I did it from recovery, I noticed that it would hang at 'Setting up keymap' or something. 

I ended up having to bike in the freezing cold to get an Ubuntu disc, because, for whatever reason, I hadn't had the forethought to have one handy. I booted that up and changed rsyslogd-kmsg.conf back and also deleted a few files from /var/log while I was at it. Now, my install is back up, but I'm back to square one with rsyslogd eating up CPU. 

Not complaining. It could well have been a mistake on my part. Just putting it out there. Thanks anyway.

Ending rsyslogd doesn't seem to work out that well. What's a simple temporary solution?

> **ubername said:**
> Seems fixed in kernel 2.6.31-17

Pretty sure I ran into the problem on 2.6.31-18, so the problem still exists.

---

### Post by orkyahaalhai on 2010-04-18
check this link it have a  solution to this problem

[URL="http://http://www.4pmp.com/2009/11/ubuntu-9-10-karmic-koala-temperature-above-threshold-cpu-clock-throttled/"]
http://www.4pmp.com/2009/11/ubuntu-9-10-karmic-koala-temperature-above-threshold-cpu-clock-throttled/[/URL]
I had the same problem , i have only 8 gb in linux,  and now i am happy user with no more disk space gone haywire or cpu always going to 100%


Also note that only kern.log is not the culprit , so are sys.log and messages , all in /var/log 

hope u get the system to work till a patch is released

---

### Post by orkyahaalhai on 2010-04-18
[http://www.4pmp.com/2009/11/ubuntu-9-10-karmic-koala-temperature-above-threshold-cpu-clock-throttled](http://www.4pmp.com/2009/11/ubuntu-9-10-karmic-koala-temperature-above-threshold-cpu-clock-throttled)

this is the right link

---

