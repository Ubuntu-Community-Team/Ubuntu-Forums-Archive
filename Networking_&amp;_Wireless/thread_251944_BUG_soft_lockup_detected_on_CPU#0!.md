---
title: "BUG: soft lockup detected on CPU#0!"
date: 2006-09-06
forum: Networking &amp; Wireless
---

### Post by dibblego on 2006-09-06
Installing a D-Link DWL-G510 PCI wireless network card into my system causes an error during the boot sequence - "BUG: soft lockup detected on CPU#0!" immediately after "Loading hardware drivers". This problem is consistently reproducible and consistently goes away if I modify /etc/network/interfaces to not use this device. The kernel was 2.6.15-23 and I hoped an upgrade to 2.6.15-26 would help but it didn't. The machine hangs at this point indefinitely and refuses to boot. Any pointers?

---

### Post by dibblego on 2006-09-10
So I am screwed? I've asked around at many places and nobody seems keen to provide an answer or even a hint at what can be done to resolve this problem.

---

### Post by GadgetsGuy on 2006-10-04
I am also looking for a fix for this

BUG: soft lockup detected on CPU#0!

I have been unable to login for 4 days now, and will pay anybody $50 by paypal that can offer me a solution

there is plenty of documentation of this error online, but no solutions :-k

---

### Post by basfrank on 2006-10-06
so am I. same device, same error.:(

---

### Post by ppetrovic on 2006-10-17
Similar situation with plain installation of Ubuntu 6.06 from CD and CNet's CWP-854 wifi card (rt61 driver). The driver modules
loads fine into kernel on boot, but when trying to activate the connection, the system hangs with this error message.

---

### Post by ppetrovic on 2006-10-17
Here the problem got resolved by using the same version of kernel, but for 386. The bug was occuring only with "linux server" kernel (2.6.15-26). When switched to usual kernel for 686, there was no more bug, but the CPU utilization went up to 100% and the iwconfig or iwlist processes could not even be killed, hanging on the network card, still the rest of the system working fine (however rebooting had to be suppored by the red button). Finally, changing to 386 kernel, the wifi card started to work normally. The machine is some usual Intel P3 with !only 256 MB RAM, MX34 mainboard and phoenix bios. Appart from the wifi card, there is only 1 ATI RAGE AGP (but the X was not running), and one Intel 100/pro Ethernet.

---

### Post by sylvester_0 on 2006-10-18
I'm currently experiencing this on my Dell Inspiron 600m with IPW2200 wireless built in :( I'm using the generic kernel right now (gotta love that name) but if this continues I'm going to figure out how to compile my own or switch to debian.

---

### Post by cnbiz850 on 2006-10-18
I am experiencing this on my new Dell Inspiron 6400 Core 2 Due laptop.  There is Intel 3945 card in it.  I just installed Edgy on it.  The hangup occurred to not during using wireless networks as some others' situation -- in fact, I didn't get it to work yet --, but at startup time.  I did have iwconfig to config the card -- the card became active but I could not connect to anything yet.  I did also install Network-Manager-Gnome, but it didn't help at all in setting up the network.  And once the hangup occurred, I can not use the system at all and it seems to hang indefinitely.  Last time, having no clue what happened, I re-installed the system.  Does anyone know another work-around without re-installing the system?  I am prepared to turn off the wireless as it is not critical to me at this time.

---

### Post by cnbiz850 on 2006-10-19
I noticed that just before the hangup during boot time, there is a message which I wonder could be related to the soft lockup.  It says: "sda5 (my /): superblock last write time is in the future, Fixed".  Why is it in the future?  I guess sometimes th system time is messed up with Windows' (I have dual-booting).

Can anyone comment on this?

---

### Post by brothert on 2006-10-25
According to the kernel sources (kernel/softlockup.c) the error "soft lockup detected" means a CPU in kernel code didn't reschedule for 10 seconds or more (watchdog timeout). It may be caused by driver code (IDE/SATA/NIC?) that processes hardware interrupts for more than 10 seconds without rescheduling other threads.

I've also experienced this problem on a dual core notebook (2GB RAM, ICH7 SATA controller on ata_piix/libata, Edgy SMP kernel linux-image-2.6.17-10-generic). It only occurs while booting.

The system usually manages to boot after 0-3 reboots and the error doesn't occur when the system is up. Playing with the "quiet" / "splash" boot options seems to help...

---

### Post by makro on 2006-10-27
Same problem here....
Centrino DUO 1.66 Ghz

I've tried to reboot for 10 times in a row... at the end edgy started when I switched on wireless light before boot... maybe this is only a coincidence...

Another strange thing is that sometimes boot hangs while fsck is working....

Linux 2.6.17-10-generic

---

### Post by makro on 2006-10-28
BUG: soft lockup detected on CPU#0!...
It has just happened again! 2 times in a row...
Then I switched on the wireless button... and OK!

---

### Post by Tenzer on 2006-10-30
I can confirm that this has something to do with the wireless network card. I couldn't boot up my IBM ThinkPad T60 with the wireless network card disabled, but when trying with the card enabled, it boots up normally.

---

### Post by makro on 2006-10-30
I'm absolute sure about that... especially now.

Sometimes boot hangs during/after fsck... but I suppose for the same reason, something about wireless card...

Is this kind of bug posted somewhere?

---

### Post by joris1977 on 2006-10-30
I have the same problem. Since i upgraded to edgy, my labtop hangs often on bootup. When i do recovery restart i sometimes get the [17179609.344000] Bug: soft lockup detected on cpu#0 

Note that i have my wireless not enabled on bootup. On dapper that was necessary, but on edgy it starts working when i put the button. 

i have intel dual core on Acer aspire 5610. 

This bug is already reported on lunchpad sometimes linked to wireless sometimes to uplash and other issues.

see: [https://launchpad.net/distros/ubuntu/+bugs?field.searchtext=bug%3A+soft+lockup+detected+on+cpu%230&orderby=-importance&search=Search&field.status%3Alist=Unconfirmed&field.status%3Alist=Confirmed&field.status%3Alist=In+Progress&field.status%3Alist=Needs+Info&field.status%3Alist=Fix+Committed&field.assignee=&field.owner=&field.omit_dupes=on&field.has_patch=&field.has_no_package=](https://launchpad.net/distros/ubuntu/+bugs?field.searchtext=bug%3A+soft+lockup+detected+on+cpu%230&orderby=-importance&search=Search&field.status%3Alist=Unconfirmed&field.status%3Alist=Confirmed&field.status%3Alist=In+Progress&field.status%3Alist=Needs+Info&field.status%3Alist=Fix+Committed&field.assignee=&field.owner=&field.omit_dupes=on&field.has_patch=&field.has_no_package=)

Will follow this threat, because it seems the most active
but these threats are also about more or less the same issue:

[http://www.ubuntuforums.org/showthread.php?t=286843&highlight=Bug%3A+soft+lockup+detected+on+cpu%230](http://www.ubuntuforums.org/showthread.php?t=286843&highlight=Bug%3A+soft+lockup+detected+on+cpu%230)
[http://www.ubuntuforums.org/showthread.php?t=277922&highlight=Bug%3A+soft+lockup+detected+on+cpu%230](http://www.ubuntuforums.org/showthread.php?t=277922&highlight=Bug%3A+soft+lockup+detected+on+cpu%230)

some people think it is skype related: 
[http://forum.skype.com/lofiversion/index.php/t64990.html](http://forum.skype.com/lofiversion/index.php/t64990.html)

edit: I found out that i could run edgy without problems in the old kernel 2.16.15-27.686. So i thought my problems might be kernel related. Searching on the forums, i found this threat: 
[http://ubuntuforums.org/showthread.php?t=282956](http://ubuntuforums.org/showthread.php?t=282956)

i reinstalled the kernel with the commands i found in the threat:

sudo mkinitramfs -o /boot/initrd.img-2.6.17-10-generic 2.6.17-10-generic
sudo update-initramfs -u -k 2.6.17-10-generic
sudo update-grub
sudo aptitude reinstall linux-restricted-modules-2.6.17-10-generic



not sure what these commands do exactly but it seems that it worked, because i don't have any troubles at starting up anymore. Ofcourse i don't  know if it will work for other people, but you problems could be kernel related as well...

edit2: Well it worked... for a few days: this morning i had the same bug again. Strange... did it again see how long it lasts
edit3: I gave up, just did a fresh install of edgy and everything seems to work fine now. Hope it stays that way.

edit4: It still works... but the troubles come back when  my wireless is enabled when i´m starting up. So i guess in my case it´s related to the 802.11a/b/g wireless LAN. I´ve seen the patch, but not sure exactly how to apply it. I can work around it, so i´&#314;l hope feisty will solve this issue permanent.  

This threat on the kubuntu forums suggests that the problem might be dual-core related:
[http://kubuntuforums.net/forums/index.php?topic=10019](http://kubuntuforums.net/forums/index.php?topic=10019)

---

### Post by farbridges on 2006-10-31
I am confronted with the same bug. It appeared the first time after installing the linux-restricted-modules-generic. I could not boot into the system anymore. It hung after the fschk.

After removing the restricted-modules package (using the rescue option on the alternate CD to mount my root file system), my system booted successfully again.

Afterwards, I installed the restricted modules again to see what would happen. Now I could work with my system for some hours. After a cold reboot and working for 5 minutes, my system suddenly hung again (the display was distorted for a few seconds). I forced the system to shut down and then turned it on: it did not even load BIOS anymore, but just turned off immediately. After waiting 3 minutes, it would start, but resulted in the same result as before: it hung after fschk with the same BUG.

Again, I removed the restricted modules and could boot the system again. Have not had the problem after that anymore.

Fact is that I need the restricted modules for my IntelPRO wirless 3945ABG and the nvidia graphics card.

The system is a Dell Latitude D820 with 
- Core 2 Duo T7200,
- NVIDIA Quadro NVS 110M graphics with 256 MB
- Intel PRO Wireless 3945 802.11a/g

---

### Post by HansAlbertMarkus on 2006-11-03
[QUOTE=joris1977;1689150]I have the same problem. Since i upgraded to edgy, my labtop hangs often on bootup. When i do recovery restart i sometimes get the [17179609.344000] Bug: soft lockup detected on cpu#0 

I am using a Kontron board with a Mobile Celeron, Intel 855GME chipset, Intel Extreme 2 graphic, realtek ALC 655 codec..
No wireless or dual core at all. 
I have built up 3 identical systems (cloned harddisks)
but error appears up to now only at one system. 

Here the story how it happened: 
Yesterday i removed the harddisk, copied to another harddisk 1:1. Then i mounted the originally disk in my system again. When i switched the system on, an i/o error at one sector of the disk was reported. 
Press Ctrl D or log in for maintenance: 
Then i logged in for maintenance and started fsck manually. The the BUG appeard after some time. I pressed then Enter and now the system is continoisly acssesing the hard disk (the led is on) but the screen is black and also the num-lock at the keyboard doesn't work anymore.  

I will now test the same system with the cloned harddisk

Markus

---

### Post by HansAlbertMarkus on 2006-11-03
Now i have tested it wuth the "cloned" harddisk. Same effect.
I guess its a bug in fsck or in the IDE driver. 
My problem is that i have now no Ubuntu system more running to test somethings. May anybody run a fsck on his well running system manually and look what happens ?

Markus

---

### Post by farbridges on 2006-11-03
I strongly doubt wether it is a bug in the fsck or IDE driver. What filesystem are you using? fsck is a frontend to many fs-specific progs. I am using reiserfs.

Anyway: I have a SATA disk, so the IDE driver is not used.

Note that I only have the problem when I have the restricted-modules installed.

---

### Post by HansAlbertMarkus on 2006-11-04
I continued my research;-). I started the system, altr the GRUB menu, in the recoverey mode (same kernel 2.6.15-26) During booting at two points thea "DriveReady Seek complete Error" appears, but 
the "soft lockup error" didn't appear. 
Then i started fsck manually, and it reported some errors, some of the high sectors where not found, and stop then. 
Thats possible true, because i cloned this WD disk from a Maxtor disk with 200MByte or so more. 

So i think the problem appears when ubuntu starts the fsck (for any reason) during the boot procedure. 
I will now try to reduce the numbers of  sectors with fdisk, and try to finish
fsck in the recovery mode w/O errors. Then i will try to boot ubuntu in the standard mode again.

Markus

---

### Post by m_bridge on 2006-11-16
same problem (but on CPU#1..)
the system worked fine for the last month when i got this new machine and installed edgy with a wmp54g (rt61) the only things i changed during last session were installing skype from automatix and sun java JDK.
Now i'm getting the error somethimes during the boot sometimes after few minutes where it seems to work

---

### Post by farbridges on 2006-11-16
Replacing the ipw3945 driver with a patched one solved the problem for some users (including myself):

See:

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/63418](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/63418)

---

### Post by lir on 2006-11-16
Hey everyone,

Firstly, I can *safely* say that this i not related to linux cause I'm dual-booting with Windows XP Home Edition on my laptop (Acer Aspire 5562) and I'm experiencing these short lockups on Windows as well so no idea...

I've started experiencing these weird freezes and lockups that happen almost continously every several minutes for 2-4 seconds each time.

It has gotten worse and freezed up the entire system, the logfiles show:
/var/log/syslog:

Nov 17 00:38:20 localhost kernel: [17197168.972000] psmouse.c: TouchPad at isa0060/serio4/input0 lost synchronization, throwing 5 bytes away.
Nov 17 00:39:13 localhost kernel: [17197220.344000] ata2: dev 0: ATAPI check failed
Nov 17 00:39:13 localhost kernel: [17197220.344000] ata2: PIO error
Nov 17 00:39:13 localhost kernel: [17197220.344000] ata2: translated ATA stat/err 0x59/40 to SCSI SK/ASC/ASCQ 0x3/11/04
Nov 17 00:39:24 localhost kernel: [17197232.812000] BUG: soft lockup detected on CPU#0!
Nov 17 00:39:24 localhost kernel: [17197232.812000]
Nov 17 00:39:24 localhost kernel: [17197232.812000] Pid: 0, comm: swapper
Nov 17 00:39:24 localhost kernel: [17197232.812000] EIP: 0060:[handle_IRQ_event+24/112] CPU: 0
Nov 17 00:39:24 localhost kernel: [17197232.812000] EIP is at handle_IRQ_event+0x18/0x70
Nov 17 00:39:24 localhost kernel: [17197232.812000] EFLAGS: 00200246 Tainted: P (2.6.15-27-686)
Nov 17 00:39:24 localhost kernel: [17197232.812000] EAX: 00000001 EBX: df8a3820 ECX: df8a3820 EDX: c03a7f80
Nov 17 00:39:24 localhost kernel: [17197232.812000] ESI: 00000000 EDI: c03a7f80 EBP: c03a113c DS: 007b ES: 007b
Nov 17 00:39:24 localhost kernel: [17197232.812000] CR0: 8005003b CR2: 080a1dd0 CR3: 2a3c6000 CR4: 00000690
Nov 17 00:39:24 localhost kernel: [17197232.812000] [__do_IRQ+157/272] __do_IRQ+0x9d/0x110
Nov 17 00:39:24 localhost kernel: [17197232.812000] [do_IRQ+25/48] do_IRQ+0x19/0x30
Nov 17 00:39:24 localhost kernel: [17197232.812000] [common_interrupt+26/32] common_interrupt+0x1a/0x20
Nov 17 00:39:24 localhost kernel: [17197232.812000] [pg0+943861403/1069167616] acpi_processor_idle+0x184/0x32d [processor]
Nov 17 00:39:24 localhost kernel: [17197232.812000] [cpu_idle+111/192] cpu_idle+0x6f/0xc0
Nov 17 00:39:24 localhost kernel: [17197232.812000] [start_kernel+415/512] start_kernel+0x19f/0x200
Nov 17 00:39:24 localhost kernel: [17197232.812000] [unknown_bootoption+0/496] unknown_bootoption+0x0/0x1f0
Nov 17 00:40:01 localhost kernel: [17197269.596000] BUG: soft lockup detected on CPU#0!
Nov 17 00:40:09 localhost kernel: [17197269.596000]
Nov 17 00:40:09 localhost kernel: [17197269.596000] Pid: 0, comm: swapper
Nov 17 00:40:09 localhost kernel: [17197269.596000] EIP: 0060:[handle_IRQ_event+24/112] CPU: 0
Nov 17 00:40:09 localhost kernel: [17197269.596000] EIP is at handle_IRQ_event+0x18/0x70
Nov 17 00:40:09 localhost kernel: [17197269.596000] EFLAGS: 00000246 Tainted: P (2.6.15-27-686)
Nov 17 00:40:09 localhost kernel: [17197269.596000] EAX: 00000001 EBX: df8a3820 ECX: df8a3820 EDX: c03a7f80
Nov 17 00:40:09 localhost kernel: [17197269.596000] ESI: 00000000 EDI: c03a7f80 EBP: c03a113c DS: 007b ES: 007b
Nov 17 00:40:09 localhost kernel: [17197269.596000] CR0: 8005003b CR2: b0bad000 CR3: 106fd000 CR4: 00000690
Nov 17 00:40:09 localhost kernel: [17197269.596000] [__do_IRQ+157/272] __do_IRQ+0x9d/0x110
Nov 17 00:40:09 localhost kernel: [17197269.596000] [do_IRQ+25/48] do_IRQ+0x19/0x30
Nov 17 00:40:09 localhost kernel: [17197269.596000] [common_interrupt+26/32] common_interrupt+0x1a/0x20
Nov 17 00:40:09 localhost kernel: [17197269.596000] [pg0+943861403/1069167616] acpi_processor_idle+0x184/0x32d [processor]
Nov 17 00:40:09 localhost kernel: [17197269.596000] [cpu_idle+111/192] cpu_idle+0x6f/0xc0
Nov 17 00:40:09 localhost kernel: [17197269.596000] [start_kernel+415/512] start_kernel+0x19f/0x200
Nov 17 00:40:09 localhost kernel: [17197269.596000] [unknown_bootoption+0/496] unknown_bootoption+0x0/0x1f0

also:

Nov 17 00:50:52 localhost kernel: [17197921.200000] apm: BIOS not found.
Edit/Delete Message

---

### Post by m_bridge on 2006-11-18
> **farbridges said:**
> Replacing the ipw3945 driver with a patched one solved the problem for some users (including myself):

See:

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/63418](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/63418)

Thanks, i'll try that as soon as i have some time, so far i solved removing the rt61.ko from the kernel 

what i really can't understand is why that worked fine for the last month!

---

### Post by herculez on 2006-11-23
Has anyone found a solution yet?  I get this problem at the beginning of the installation process (just after I select the install option from the bootup menu), for both 6.10 and 6.06 install CDs.

[17179681.156000] BUG: soft lockup detected on CPU#0! 

I'm running a single core Pentium 4 processor, so I doubt the problem is related to dual cores.  

Judging from the number of views on this thread, we're not the only ones having the issue.  

Someone please help!

---

### Post by herculez on 2006-11-24
It seems from this bug report that there's a working patch out there:
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/63418](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/63418)

But what does this mean for those of us trying to install Ubuntu?  Do we have to wait until an updated install image is released?

---

### Post by pdub on 2006-11-28
I was getting this error during the install of Edgy on a Dell D820 dual core with Intel ipw3945 wireless adapter. If I tried to install with the wireless card turned off, I get the soft lockup ..., if I turn the card on, the install completes fine.

---

### Post by herculez on 2006-11-28
Hmmm... I don't have a wireless on/off switch.  

> **pdub said:**
> I was getting this error during the install of Edgy on a Dell D820 dual core with Intel ipw3945 wireless adapter. If I tried to install with the wireless card turned off, I get the soft lockup ..., if I turn the card on, the install completes fine.

---

### Post by qhuyvu on 2006-12-16
I installed Ubuntu 6.10, the same happen, I'm using Core Duo 2250, Toshiba.
It's terrible, and I have checked all possible things can changed with my Wireless and NIC, not help.
It happen so offent :(

---

### Post by lduperval on 2007-01-05
I am also seeing this. In my case, it seems to be related to an external USB drive.

The drive is an Acomdata drive and it has a reiserfs filesystem. When I copy files to the USB drive, it will hang. I have found that it hangs on specific files.

Another anomaly I found is that I had the same file repeded dozens and dozens of times in the same directory. I removed 5 of those files using rm <filename> and the file count dropped by about 1500 in that directory.

A resiserfsck is flagging some problems, so I am thinking the filesystem may be partly corrupt and causing this.

L

---

### Post by jjrr on 2007-01-10
i just saw this on a thinkpad z61m with edgy. probably it can be solved by switching wireless on (?), at least it seems. system came up then for the first time after several failed reboots. the notebook has such a kind of switch to disable wireless completely... 
i'll try to make a new kernel now i guess...

---

### Post by Freeshadow on 2007-01-18
I'm experiencing the same problem with a NETGEAR WG511 v1 card. (Firmwarefile: isl3890)

I installed via alternate CD and had to turn off networking recognition in order to finish install
As soon as I boot with wifi running it's just a question of time the box freezes completely.

---

### Post by RythmDivine on 2007-01-24
> **herculez said:**
> 
[17179681.156000] BUG: soft lockup detected on CPU#0! 


I have the same issue: cannot install edgy at all. however i noticed i have a different number than herculez in the prefix to the errortext...

[17179713.052000] BUG: soft lockup detected on CPU#0! 

I tried to boot with just the live image, adding the irqpoll option, no HDDs connected at all, but again without success. This machine has neither wifi nor skype, so that shouldnt be related either. The machine used to have a working windows XP on it, before i reformatted that drive in my frustating hunt for success, wich leads me to belive this isnt hardware-related at all? But i am so new to linux that i couldnt tell...](*,)

---

### Post by joris1977 on 2007-01-24
RhythmDivine try to install dapper and see if the problem remains. It seems the soft lockup is somehow related to the new kernel in edgy. Sometimes in combination with the wifi or skype  . There is probably no real reason why you need edgy. Dapper is in many ways more or less the same. If you really need edgy and you have  no problems in dapper you can upgrade to edgy but keep using the old dapper kernel.

wait for the next release and see if the polishing on the new kernel solved the problem

Edit 1: Ok sorry Freeshadow, didn´t know some people had this bug in dapper as well, I didn´t have it in dapper and switching back to the old kernel solved the problem. Maybe it is  a solution for some people.

---

### Post by Freeshadow on 2007-01-24
It cannot be related to edgy only, since I'm experiencing the mentioned lockup on dapper.
so what now?
for me it is wifi for somebody else usb-storage.
i know it can't be reiser since I used ext3
so it seem we have no clue at all WHERE the problem actually IS

:( :( :(

---

### Post by snc on 2007-01-30
Well in my case bug only occurs when laptop works on battery. When i plug it in to the external power supply, turn laptop off and on, ubuntu boots with no problem. I have core 2 duo 7200, and as far as I know this processor works different when laptop works on battery (AFAIR it can turn off non-working core). Maybe kernel has some problems with battery mode, when 2-core processors wants to save energy.

---

### Post by Freeshadow on 2007-01-30
this cannot be the reason since i tried it on a single core so the search goes on :(

---

### Post by AloneOverSeas on 2007-01-31
for me this problem occurs only when im running Skype the system freezes for a couple of mins and it comes back with this error, otherwise the system rock solid. so for the time been i stopped using skybe till i find a solution. :D Linux Newbie ...

---

### Post by MaleqAlhaq on 2007-02-02
I'm experiencing the same Problem:
Dell 640m / e1405
Core 2 Duo T5600 1,83GHz
2 GB RAM
Intel Pro Wireless (for a/b/g)
Bluetooth
Up to date Edgy (2.6.19.??)
When I boot with WiFi and BT active, the kernel hangs, if I disable it before booting, Edgy starts w\o a problem. WiFi & BT activated --> Hangup
(I don't know if BT has anything to with it, but I can only switch on both or neither...)
Hope it helps...

---

### Post by mlakilud on 2007-02-02
Same problem with my brand new HP nx7300(T5500, intel3945).

Except , I get soft lockup on CPU#0 only when starting on battery. When I am on AC it all goes fine.
Also when I switch to battery, I get system freezes for 2-5sec every 2min.

Anybody?

---

### Post by mlakilud on 2007-02-02
Done some research. This patch should help you if you all have intel3945 wireless card.
[http://kmr.nada.kth.se/~mini/ubuntu/](http://kmr.nada.kth.se/~mini/ubuntu/)

I will try it tonight and post my experiences.

---

### Post by herta on 2007-02-06
As herculez already asked: any hope for those of us who would like to install [k]ubuntu on a new system? 

hw: brand new Dell Inspiron 6400
tried with wireless switched on and off

With wireless switched on, the boot hangs with the infamous "BUG: soft lockup detected on cpu#0"
With wireless switched off, the system will boot to runlevel 2 in life mode.  No gui, though.  

Windows XP installs fine.  Fedora Core 5 ditto.

---

### Post by Dogmatica on 2007-02-14
For the moment, while awaiting a kernel (or ipw) update , I solved the problem by disabling the second cpu (core) in the BIOS.
It was a long shot, but apparently it works perfectly.

---

### Post by luispinho on 2007-02-16
Same problem here with Ubuntu Feisty Herd3.

```
* Mounting local filesystems...
[  38.204000] BUG: soft lockup detected on CPU#0!
```

As someone said before in this thread, and after several tries to boot Ubuntu, I've finally succeded by switching on Wireless.

---

### Post by muggsy on 2007-02-16
Disabling the second cpu fixes this problem, but I also found using the previous kernel works fine.. I forget the version.. but .10

No problems in MEPIS or PCLinuxOS...

---

### Post by Tribe on 2007-02-16
Yeh same prob here with a MacBook Pro Core 2 Duo, always when trying to configure network interfaces during boot, so in my case its clearly wireless-related.

I've tried the patch found here [http://kmr.nada.kth.se/~mini/ubuntu/](http://kmr.nada.kth.se/~mini/ubuntu/) in my 2.6.17-10-generic with no success.

> With wireless switched on, the boot hangs with the infamous "BUG: soft lockup detected on cpu#0"
 With wireless switched off, the system will boot to runlevel 2 in life mode. No gui, though. 

Excuse my ignorace, but that does mean "switch on/off" in here? What's the way to do it?

Bye

---

### Post by herta on 2007-02-19
> **Dogmatica said:**
> For the moment, while awaiting a kernel (or ipw) update , I solved the problem by disabling the second cpu (core) in the BIOS.
It was a long shot, but apparently it works perfectly.
Thanks for the suggestion.  Unfortunately, it doesn't work for me.  Still no gui, and still stuck in runlevel 2.

> **luispinho said:**
> Same problem here with Ubuntu Feisty Herd3.
That's bad news.  I was hoping the next release might fix this.  Looks like Ubuntu isn't for me (yet ?). :-(

> **Tribe said:**
> 
Excuse my ignorace, but that does mean "switch on/off" in here? What's the way to do it?

When you power on your computer, you can usually press a function key (one of the Fn keys at the top row of a qwerty keyboard) to enter your BIOS settings.  On a Dell, it's usually the F2 key. One of the BIOS settings that you change is whether you want to enable or disable the wireless card, or the dual core feature.

Kind regards,

Herta

---

### Post by Rallyus on 2007-02-20
Oops! I'm new here (and in Ubuntu) and I have just posted this on the General Help Forum:


> Hi,


I need some help, a month ago I decided to give Linux a try, and installed Kubuntu Edgy in my new laptop (HP Pavillion dv9082eu).


I´m having some trouble getting a working DSL conection at home, so last saturday I went to my girlfriend´s and used her connection.

There was a huge ammount of upgrades to download (120!) and after installing them and trying to restart, I was left stranded in the middle of the booting.

The symptoms are:

At every first boot into Kubuntu with the new Kernel 2.6.17-11 Generic, it freezes in the middle of the boot, after shutting down and trying again I have no problems.

Booting into the old 2.6.17-10 Generic I have no problems.

I removed the bootsplash to check out what was wrong and it freezes during boot with the following message:

[17179603.972000] BUG: SOFT LOCKUP DETECTED ON CPU#0!


I'm a newbie and need some help please!



And after doing some research on what was causing the problem I posted this:

> Ok, tried to investigate a litle further ...


My Laptop has a Intel 3945 a/b/g wireless card, and I have noticed that the soft lockup only happens when I have the wireless and bluetooth conection disabled on the switch.



Please explain, to a newbie to this stuff, how to fix this :(

---

### Post by f3ua on 2007-02-20
I can confirm the issue on my laptop with intel pro wireless adapter and centrino core 2 duo cpu. (dell xps) I've tried many times and it seems to be a random bug because sometimes hungs with the message:

```
BUG: soft lockup detected on CPU#0!
```

But, if I switch off with force (pwr button > 4 sec) and restart, there isn't any problem and this is the dmesg output:

```

* Detecting network interfaces
[17179585.664000] ipw3945: Radio Frequency Kill Switch is On:
[17179585.664000] Kill switch must be turned off for wireless networking to work.

```

And all works perfectly. May be a previous usage of windows without switching off completly the laptop the cause of this issue?

---

### Post by nickdolan on 2007-02-25
I had this problem on a Dell D820 Dual core Intel. I upgrade the BIOS to release 6 from 1 and then it all seemed to work.:)

---

### Post by luispinho on 2007-02-27
Today, a new update to Ubuntu Feisty.
Now it doesn't hangup while booting no matter if wireless is On or Off, but now I don't have Wireless at all.

---

### Post by luispinho on 2007-02-27
New update.
No hangup's with wireless switched On or Off, and now wireless works again.

---

### Post by farbridges on 2007-02-28
> **nickdolan said:**
> I had this problem on a Dell D820 Dual core Intel. I upgrade the BIOS to release 6 from 1 and then it all seemed to work.:)

Still working with wireless killswitch on and off, Ubuntu Edgy? I also have a Dell D820 (bios version 3), so if it the solution truly is upgrading the bios, that would be nice.

---

### Post by CrazyTn on 2007-03-04
I just got the same problem today.

Was messing around with wifi radar and network manager. Then my laptop stop booting.

This is how I fixed it.

To boot up:
Turn off your wireless card before boot up.

Uninstalled: all wireless applications
                  uninstall linux-restricted-modules-generic

Reboot and wifi still works.

It works for me so Don't know if it will for you

---

### Post by elias_a on 2007-03-06
I thought I fried my new Thinkpad R60 as I received the error mentioned in the subject while booting. Glad I found this thread ;-)

My laptop, TP R60, Type 9461-DXG does not boot with kernel 2.6.17-11-generic when the wireless/bluetooth switch is in off position. Switching it on made the laptop boot again.

---

### Post by Sparticuz on 2007-03-06
I have tried it:
Wireless on, no battery
wireless off, no battery
wireless on, battery
wireless off, battery

Every single time it does soft lockup, I finally got Ubuntu to install using the alternate disk with text install. 

I have a compaq presario v3000Z AMD Turion64 (32 bit ubuntu) with a BCM4311 wireless.

---

### Post by Alfdog on 2007-03-10
I'm also experiencing this on my dell xps m1210, anyone have any ideas?

edit: got it working, not sure if it was the whole playing with the switch thing, or taking out a SD card I had in, still took like 5-6 attempted boots.

---

### Post by GordSellar on 2007-03-13
I've been getting the error but only, it seems, when I have a 2-Gig memory card in the built-in slot. Otherwise, not a problem. Anyone know why that might be? (I'm on an HP dv2000.)

---

### Post by Twomby on 2007-03-15
Hi all,

I've been raging for a few months now, because of this CPU LOCKUP on my XPS M1210 Dell Laptop.  I just read the two last posts before mine (this one), and it seems like it really is the SD card in which causes the problem ! I never thought about removing it before !! What may cause this problem ?  Anyway, I just booted in the Live CD, and preparing to Install ! Thanks for the posts on this thread, it finally helped me to get it working !

---

### Post by Rheuh on 2007-03-18
Same here, with a XUbuntu 6.10 on a single-core Pentium III 600Mhz.

The issue occured after install Serialmonkey's RT61 driver for my MSI PC54G3 wireless PCI card. Still haven't found how to start my computer, as it even hangs in rescue (single) mode ! Normal booting leads to a total freeze when X starts up (got the X cursor on the black-and-white screen, no more, can't move anything, can't even turn numlock on/off) ; and I got the "soft lockup" message when booting in single mode.

I'm gonna try to remove that damn wireless card...

(Edit)
[COLOR="Red"]**-- SOLVED !! --**[/COLOR] (at least it seems so) by using the latest CVS version of SerialMonkey's RT61 driver.

---

### Post by orb9220 on 2007-03-20
Latest edgy update with nividia and envy.

I just receieved this the first time. Never have I seen it before.

> 17179734.90000 Bug: Soft Lockup detected CPU#0

This was after an linux-restricted-common upgrade on the 18th. Of course this broke my x-server
so I login and run envy from command prompt. At the write xconf prompt is when I got the error.

System was locked nothing worked had to hard boot. And ran envy againg this time I entered y for yes to write xorg.conf and y to restartx and everything back to normal.

---

### Post by tommyj27 on 2007-03-22
I have also just experienced this issue, though on a box with no wireless card. It's been a test server for quite some time and has been very reliable. It appears that in my case, a hub going bonkers was to blame, the machine managed to boot after the soft lockup error but was not available on the network.

Just thought I'd toss my experience in.

---

### Post by js.opdebeeck on 2007-03-26
Same for Me ...

BUG : Soft lockup detected on CPU#0! ...

DEL Latitude D600, but Feisty BETA ... no problems with HERDS 3,4 and 5 .

Wifi Card is Simens, but problem continues without it .

Any idea ??? I'd like to post a crash report to Dev TEam ... but system freeze completly without more   info in logs ...

Js

---

### Post by Cannaregio on 2007-03-28
Something similar happened to me, and the following could be useful for people with similar problems. Maybe. Maybe not. Worth a try.

```
BUG: soft lockup detected on CPU#0!
```

Seems to happen also
[LIST]
[*]when you have a dual boot config
[*]when you TURNED YOUR WIRELESS OFF inLinux
[*]when you did reboot in windows after that
[*]when you now tried to reboot in linux with wireless still off
[/LIST]

Solution (worked for me)
[LIST]
[*]Reboot in windows
[*]Return wireless on
[*]shutdown windoze and reboot linux
[/LIST]

So the point is to RESET WIRELESS ON.
Why this kind of bug/error 
should be/could be/probably is 
related with wireless beats me.

(this rig was 2.6.17-11-generic, 3945 ABG Intel wireless, ubuntu edgy on a Siemens Amilo S that has an annoying flashing wireless light that you always like to turn off if there's no connection even if it is actually not necessary: let it flash and avoid the problem)

---

### Post by f3ua on 2007-03-29
Partial good news...

I tried to upgrade my BIOS (A6 rev) on my DELL XPS M1210 and did not solved the problem. So I tried many triks i've found around the web and some of these can help:

1) Try the pci=routeirq param to the kernel on boot
2) If you have it, always keep OFF the frequency kill switch when booting (so keep the card on). In my system the error happens only when this switch is on but not always.
3) Try removing auto configuration to wireless network interfaces on boot... go to /etc/network/interfaces and comment out the lines

auto eth_x_

where _x_ is the number of your card... usually ubuntu calls eth0 the ethernet card and eth1 the wireless card. If there are other interfaces comment out it all.

This helped me and now my system seems to be right.

---

### Post by Jookbox on 2007-04-01
this is my first experience with ubuntu. oh well.

---

### Post by Corinna on 2007-04-04
> **f3ua said:**
> Partial good news...

I tried to upgrade my BIOS (A6 rev) on my DELL XPS M1210 and did not solved the problem. So I tried many triks i've found around the web and some of these can help:

1) Try the pci=routeirq param to the kernel on boot
2) If you have it, always keep OFF the frequency kill switch when booting (so keep the card on). In my system the error happens only when this switch is on but not always.
3) Try removing auto configuration to wireless network interfaces on boot... go to /etc/network/interfaces and comment out the lines

auto eth_x_

where _x_ is the number of your card... usually ubuntu calls eth0 the ethernet card and eth1 the wireless card. If there are other interfaces comment out it all.

This helped me and now my system seems to be right.


I had the same problem... For the moment it works fine if I turn the wi-fi on before booting. I turn it off after I log on.
The next step is trying the above solution. I tend to forget to turn on the wireless card

---

### Post by Jump on 2007-04-04
> **Twomby said:**
> Hi all,

I've been raging for a few months now, because of this CPU LOCKUP on my XPS M1210 Dell Laptop.  I just read the two last posts before mine (this one), and it seems like it really is the SD card in which causes the problem ! I never thought about removing it before !! What may cause this problem ?  Anyway, I just booted in the Live CD, and preparing to Install ! Thanks for the posts on this thread, it finally helped me to get it working !

This worked for me as well. Also using an XPS 1210 and it was also a 2gig SD card causing the trouble.

---

### Post by vvlist on 2007-04-05
I'm having this problem in the computer described in my sig. Is anyone else having this problem because it is annoying. It seems every time I leave my computer for twenty minutes or so, I come back to a black and white screen that says "Soft lockup detected on CPU#0", and its completely frozen.

---

### Post by benutne on 2007-04-07
So we can all agree that MOST people having the issue are using laptops and wireless, right?

I just got this bug last night.  I'm using a Toshiba Satellite 1405 with an MSI mini-PCI network card from Newegg and the driver straight from RALink (not SerialMonkey's).  I was back in the bedroom (which just happens to be the farthest point from the router) with the laptop and I got the error.  When I turned the thing off and took the laptop back into the computer room and turned it on, it works great.  So at first I was thinking it had something to do with not getting a wireless signal. But it boots perfectly at work all the time, which has no wireless.  

The only thing I can think is its trying to configure the wireless card on an ittermittent wireless signal and the rt61.ko module is hanging.

---

### Post by tigerz on 2007-04-08
**This post could be related to an Ubuntu bug filed at**: [https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63418](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63418) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have the same issue on my Dell D620 laptop.

I'm using Ubuntu 6.10, 2.6.17-11-generic kernel.

After I disable wi-fi, it can boot now.

Gonna upgrade to Feisty.

---

### Post by OneST8 on 2007-04-10
I get this exact same error when I'm using my wireless card. Happens seemingly at random but almost 100% reliably when I try to scp something from a remote machine to my laptop but there are other cases where this has happened too.

Overall the wireless functions relatively fine. Just seemingly random operations tend to trigger this "BUG: soft lockup detected on CPU#0".

I haven't tried the ndiswrapper or anything. Just what came out-of-the-box as it works for the most part. Sadly, it can get dang frustrating at times when I forget about the bug and try to scp something.


```
Ubuntu: Edgy (2.6.17)
Laptop: Gateway MX3414
CPU: AMD Turion(tm) 64 X2 Mobile Technology TL-50
WLAN: Realtek (r818x kernel module)
```

---

### Post by ChantCd_com on 2007-04-11
I am getting the same bug. Let's see if my situation has anything in common:

I have an AMD64 3500+ CPU (so the problem is NOT Intel-related)
I have a SATA hard drive for my Linux partition (but I also have an IDE drive -- WinXP -- that is mounted by Ubuntu)
I had my 6 GB FAT32 partition TRASHED for some unknown reason, before this bug slapped me in the face...
I have an MSI Wireless network card -- with RaLink RT2561/RT61 chipset

The wireless RT61 has something to do with it, as does the SATA hard drive, I believe.

Also, this bug happened during INSTALLATION when I tried to install 7.04! Not good news!
Last but not least, it happened most of all when I was using the i386 version (I gave up on AMD64 version -- too many plug-ins, etc. don't work yet...I'll try 64-bit again in 3 years)

17179601.480000 BUG: Soft lockup detected on CPU#0!

Matthew

---

### Post by ChantCd_com on 2007-04-11
You might be on to something here!

I had Ubuntu 6.10 (AMD64) set up and working with NO LOCKUPS EVER, but I wanted to wipe my system to the i386 version.

But I know that I didn't have as many 
eth0
...
eth1

entries as my CURRENT setup, which won't even boot!

I think I need to comment them out. The problem is, I can't even boot SAFE MODE right now... Oh well, maybe I can reformat again.

Matthew


> **f3ua said:**
> Partial good news...

3) Try removing auto configuration to wireless network interfaces on boot... go to /etc/network/interfaces and comment out the lines

auto eth_x_

where _x_ is the number of your card... usually ubuntu calls eth0 the ethernet card and eth1 the wireless card. If there are other interfaces comment out it all.

This helped me and now my system seems to be right.

---

### Post by ChantCd_com on 2007-04-11
That's the ONE THING we both have in common -- we both tried to install a RT61 driver for our MSI wireless PCI card.

Specifically, my MSI card is:

MSI PC60G IEEE 802.11b/g 32bit PCI2.2 Turbo G Wireless Adapter up to 54Mbps Data Rates 64/128-bit WEP, WPA, WPA2, TKIP,AES,802.1x w/ RaLink RT2561/RT61 chipset

I used the driver from [www.ralinktech.com](www.ralinktech.com) though, not SerialMonkey's.

I also can't boot, even in rescue mode.

Maybe I should reformat, and use the SerialMonkey driver? If I did reformat, I would CERTAINLY comment out all the eth0, eth1 and eth2 entries -- I have both my on-board NICs disabled in BIOS.

Matthew


> **Rheuh said:**
> Same here, with a XUbuntu 6.10 on a single-core Pentium III 600Mhz.

The issue occured after install Serialmonkey's RT61 driver for my MSI PC54G3 wireless PCI card. Still haven't found how to start my computer, as it even hangs in rescue (single) mode ! Normal booting leads to a total freeze when X starts up (got the X cursor on the black-and-white screen, no more, can't move anything, can't even turn numlock on/off) ; and I got the "soft lockup" message when booting in single mode.

I'm gonna try to remove that damn wireless card...

(Edit)
[COLOR="Red"]**-- SOLVED !! --**[/COLOR] (at least it seems so) by using the latest CVS version of SerialMonkey's RT61 driver.

---

### Post by blue_Sphere on 2007-04-20
Using the new Fiesty Fawn released April 19th... I cannot even install the OS... 

After 

Loading ACPI... 

(Multiple Programs listed)
Loading Gnome Display Manager... 
(162.788286) BUG: soft lockup detected on CPU#0!

Any suggestions? I want to switch to Linux but it wont even install!!

Here is a link to my bugreport: [https://bugs.launchpad.net/ubuntu/+bug/108355](https://bugs.launchpad.net/ubuntu/+bug/108355)

I added an attachment for you guys to see what I am talking about...

---

### Post by blue_Sphere on 2007-04-21
bump

---

### Post by blue_Sphere on 2007-04-22
Any ideas? I cant even get ubuntu to install in this state!

---

### Post by neveceral on 2007-04-22
install from alternate CD and then in rescue mode (?) install 386 kernel, i did it and now i am writing  this from FF with rt61 wifi chipset.

---

### Post by gabrielstein on 2007-04-23
Hi people,

Well, I win! When trying to make kubuntu Feisty ready with Atheros 5005G, I had this problem. This occurs when to make WPA authentication with KNetworkManager.
My solution is try to put "noapic" on your grub at menu.lst(/boot/grub/menu.lst):

/boot/vmlinuz-2.6.20-15-generic root=UUID=9931c052-462f-4e9a-9927-5a9cf8bbb4ee ro quiet splash **noapic** 

Worked for me.

My hardware: Turion ML-34 1,8GHz 1,5GB RAM - Wireless: Atheros 5005G - Video: ATI 200M

Hugs

---

### Post by blue_Sphere on 2007-04-23
I tried napic with no luck. I cannot even boot feisty. 

Any ideas?

---

### Post by DraxNS on 2007-04-30
The issue here is with (at least in my case) rt61 module for my ralink integrated wifi card (RT2561) on MSI L 710.

Oddly enough, it booted once (first time ever loaded) from Live CD and locked on wireless network at work. Later on, at home I had issues booting it... but it did boot occasionally. 

Once booted, it worked (Live CD) just fine and with good range form AP, so I went and downloaded Kubuntu (yes K ubuntu ;-) ) 7.0.4 DVD to install it, and got this.

There was no way to boot Live DVD.. just no way, so I used text install and hoped for the best, but no luck there also.

On bugreport page [here]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/91192") people stated that blacklisting this module would do the trick, and it did.

So, for time being, best we can do is to log on in rescue mode, start X or not, and in favorite editor add this to the end of **[COLOR="Red"]/etc/modprobe.d/blacklist[/COLOR]**:
```

blacklist rt61

```
make new line and save.

After reboot there will be no lockup error, and system will boot fine.


[COLOR="SeaGreen"]PERMANENT FIX (if you [COLOR="Red"]DO NOT NEED SMP[/COLOR] support): Just open adept and install linux-386 package. Any driver that conflicts with SMP will now work.[/COLOR]

---

### Post by flint_ on 2007-04-30
Greetings,

Just go the bug on a 2.6.17 kernel that I had upgraded to work with the spca5xx video driver...

---

### Post by Baddie on 2007-05-01
I am running AMD Athlon XP 1800+, 1.53GHz, 1GB RAM desktop and using a **D-Link USB wireless WUA-2340** to connect to the internet. There's also a ethernet port but I'm renting a room in the basement and the router's somewhere upstairs so I can't connect that way. 

I installed Feisty from a cd and than installed ndiswrapper via downloads from [http://packages.ubuntulinux.org/feisty/](http://packages.ubuntulinux.org/feisty/) (dual boot from windows).  I then installed the drivers from the D-Link website as many other posts suggest.

```

matrix@matrix-desktop:~$ lsusb
Bus 003 Device 003: ID 07d1:3a08 D-Link System 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 045e:00b9 Microsoft Corp. Wireless Optical Mouse 3.0
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

matrix@matrix-desktop:~$ ndiswrapper -l
neta5agu : driver installed
        device (07D1:3A08) present

```

The system will freeze if I then run "modprobe ndiswrapper".  It will print "soft lockup detected on CPU#0!" during startup (CTRL-SHIFT-F1) after the line that says something to the effect of "inserting ndiswrapper module" **IF** I have the USB plugged in. The system will also lock up if I insert the USB anytime while the ndiswrapper module is loaded.

I've only used ubuntu for a short time but I'm loathed to go back to Windows, but unless I can get this problem fixed, Windows is the only way I can connect to the internet :cry: Any help would be greatly appreciated!

---

### Post by declanmullen on 2007-05-07
I have a Dell Inspiron 8100 (bios A15) with a Netgear WAG511 pcmcia card (chip: atheros AR5212 802.11abg). It's running Ubuntu 7.04 with an up to date software upgrade and with the kernel "linux-image-2.6.20-15-generic version 2.6.20-15.27" with a "uname -a" output of:

> Linux decsdell 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux


If I boot while the card is inserted, then boot sometimes hangs. Ejecting the card allows the boot to resume. After boot, re-inserting the card works fine.

---

### Post by embeemb on 2007-05-26
I've been getting this error as well, but not consistently. I'm running 6.06 with an Intel built in wifi card. I sometimes get it during boot up or shutdown. Holding down the power button and restarting the boot process usually does the trick.

---

### Post by Cuppa-Chino on 2007-06-20
had posted this in a different thread but maybe even more relevant here:

> **Cuppa-Chino said:**
> well this is what has affected me all of a sudden.

I get the softlock and only blacklisting rt61 in **/etc/modprobe.d/blacklist** seems to fix it. Odd thing is that I have used the card sucessfully in Dapper, Edgy and Feisty for a year and all of a sudden this error totally freezes me today . it is really winding me up!

anyhow last thing I installed was skype 1.4 beta but that booted up fine yesterday, so I am pretty clueless any help?:confused::cry:

the really shocking thing was that it came out of the blue - I mean it was working absolutely fine until yesterday evening and then it just stopped working outright.

only way to get computer to boot is to **blacklist rt61** - it would not even boot into recovery mode also independent of kernel (had a couple on my grub menu) so I am really confused. Wireless card seemed to hang right after that but once I had rebooted then I was able (as now) to run from Windows....

Also needed to boot into Live CD (used Knoppix) in order to do a fsck on my ext3 drives....

computer is Core 2 Duo 6300, Asrock 775-Dual VSTA, 2gig ram, nvidia 7900 gto, sound blaster audigy2 zs, twinhan tv card and Ralink Turbo Wireless Card PCI b/g

is there a proper fix for this and why oh why does it come all of a sudden?

---

### Post by Cuppa-Chino on 2007-06-20
wow
* de-installed skype 1.4 beta
* reinstalled kernel and headers (just from synaptic)
* then tried to boot wiht nosplash noapic lockup
* then knoppix fsck again no errors all okay
* then boot and all running again

I am so confused.. skype?

it gets better !

today I reinstall skype (after making a partimage!!!) and it all works again.... odd might have been a kernel file went belly up????

---

### Post by balmar on 2007-07-02
Hi,

I had a perfectly stable and well-working Ubuntu

(Linux 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux)

on my old desktop

(Intel Pentium III 1133 MHz, VT82C694T).

I plugged in a new wireless card

(SMCWPCI-G EU with Realtek chipset RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller 10ec:8185 (rev20)),

installed ndiswrapper with the factory WinXP driver. At every second boot BUG: Soft lockup detected on CPU#0! came up while the splash screen showed "Configuring network interfaces", and the system froze. It then booted okay after doing a hard reset, but next time I restarted it again had the the lockup. Hard reset then ok, next time again lockup and so on... I did this at least a dozen time: locked up on precisely every second boot. 

I tried the kernel boot options "noapic", "pci=routeirq", tried the mkinitramfs tricks (see somewhere at the beginning of this thread), didn't help.

Finally adding the "irqpoll" option to the kernel in /boot/grub/menu.lst solved the problem.

Hope it helps someone.

---

### Post by juje on 2007-07-03
Hi! i'm a newbie too in ubuntu...i've been using feisty for some days and get this same bug. It appears only when my network is not working fine...
I have a core 2 duo 600 and a d-link dwl-510 rev C3...everything is working fine but this...it seems to me that there's no answer to this problem yet isn't it?

---

### Post by Tepher on 2007-07-06
So this is my first post, but... yah I have an inspiron e1505 with an Intel Wifi 4965agn and I'm having very similiar problems. When I put my computer on standby, on wake up, it'll crash and give me the soft lockup message. On reboot, it will lock up once, but after another hard reboot it will go through. Everytime my computer starts back up... I have to reactivate my wireless through my network manage by rechecking the box.

:( hope this problem is fixed soon. i've never had to deal with this junk on my ubuntu desktop

---

### Post by rsalama on 2007-07-14
In my case it was also RT61 related. I removed the Zonet PCMIA card and the system came up w/o any problems.

---

### Post by balmar on 2007-07-15
> **balmar said:**
> 
...
Finally adding the "irqpoll" option to the kernel in /boot/grub/menu.lst solved the problem.

Hope it helps someone.
Ok, I have to admit that this (above in this thread) worked up to the point when I changed channel from 6 to 11 on the wireless router. That immediately gave me the soft lockup, with or without irqpoll. So I changed back to 6 and now things seem back to be normal as I wrote before,,,

---

### Post by flythere on 2007-08-16
Another noobie... Have been using feisty on my old-ish dell 2650 laptop (not using wireless) for a while and it works great. 

Thought I'd try the live CD in an old PIII desktop machine (with a ralink wireless card) and it hangs with the somewhat familiar soft lockup message - different number though - just after the splash screen disappears. I can't even get the system running off the live CD. Too bad.  

Windows it is for the moment...

---

### Post by patrstg on 2007-08-23
Hi,

I got the same problem after putting my integrated sound card to work on Ubuntu 7.04 (snd-hda-intel driver).

Finally I solved it by using the "noapic" boot option in grub (gksudo /boot/grub/menu.lst, add the option at the end of the "kernel" line). This optiion unactivates IRQ sharing, which seems to cause problems with some hardware.

---

### Post by Rumpty on 2007-09-02
I have a couple of other Linux OS installations on this computer, and, amazingly, got rid of this freeze while booting (soft lockup detected on CPU#0) by editing fstab in the new installation to get rid of any file checking on the other Linux OS drives.

Nothing to do with wireless networking or related things, as I don't have that on this computer.

---

### Post by RedPeasant on 2007-09-07
I've been having this issue on my Inspiron 4150 as well. The issue goes away when I remove my wireless card (it's an RT61 card), so it seems that the drivers are messed up in feisty.

---

### Post by trevbo on 2007-09-15
just installed last night, no problems.
this morning i got the same error as everyone here.
ive got a dell inspiron e1405.
if it makes any difference, i was running vista before.

---

### Post by kiloecho7 on 2007-09-16
I am running Gutsy on a Thinkpad x61s and the same thing happened to me.  Changing the SATA setting in the bios to "compatibility" worked fine for me.  Feel free to e-mail me if you want to know exactly how I changed the setting.

---

### Post by entropic_existence on 2007-10-12
I had this problem before and it was a bug with the intel 3945 driver. Hadn't had this problem in a long time.

Currently running Edgy on my Dell Inspiron 9400 (e1505) with the Intel 3945 Wireless chipset. This just started after no recent changes to the kernel (that was a few weeks ago). The only software update I did today was the one that came out for Tk4.8. Now all of a sudden my wireless card, if activated in the bios, causes this soft lock up. Very frustrating.

---

### Post by diex2006 on 2007-10-15
After installing my D-Link DWL-G112 USB wireless into my system i had this problem booting Linux.
BUG: soft lockup detected on CPU#0!

I tried to resolve this problem putting in blacklist this driver: rt73 without any result. Then, I saw the LAN card with the ambar light on. It was alwais on, restarting the Pc or not. So, I disconnet the power for a while. Magically the problem disappeared. I think when I was trying to start my Dlink, somehow my Ethernet card got locked.

Please, try this... could fix the problem.

---

### Post by chichilalescu on 2007-10-17
I am using a laptop with a "level one WPC-301" wireless lan card (pcmcia), and kubuntu 7.04 installed.
it worked when booting the system on battery power (however, I only tried this once, the first time I inserted the card into the computer); it saw the card, it saw a network, but it didn't connect (a free connection in an airport). when i tried it again, this time plugged into the AC adapter, I got this message (BUG:...) when booting, and the computer froze. if i tried to insert the card after the system had booted, it froze again. when in recovery mode, i inserted the card, and nothing happened. but then i started the card (with "ifconfig ra0 up") and the system froze again.
after looking through several threads around here, i tried installing a new kernel. initially i had been using the generic kernel, and now, after switching to the 386 version, it works just fine (still didn't connect though, but the computer doesn't freeze, and that is kind of essential). I will attempt to connect right now, and if I have any problems I will post my conclusions.

---

### Post by jollyollyman on 2007-10-27
I had that error come up as well..Is anyone, other than us two, dual-booting with windows?

---

### Post by sga1980 on 2008-01-21
Same prob. here.
I had read all the post before publish, and solution could be maybe really easy.
It seems that this kernel version for any reason doesn’t support two hardware devices with the same controller needs.
I detected it because I use 2 wifi adapters, this causes to have 2 connection interfaces in the old xp that can manage it, but not in ubuntu (talking about 7.04 - Feisty) where you would see this lockup error.
I solved just disconnecting one of the usb adapters, in another post, people disconnects one of the dual core processors and so on.

Lot of people seems to experience the issue using skype probably because the usb adapter for their skype phones use the same software controller that any other hardware component.

This is only a theory anyway.

Regards!

---

### Post by dannyboy79 on 2008-01-30
just to let everyone know, I don't have a wifi adapter and I got this in my dmesg. also, I haven't changed anything hardware-wise in the machine since I built it. I was messing around DMA settings but not sure if that's related.
here's the dmesg ouput:
[84450.519659] BUG: soft lockup detected on CPU#1!
[84450.519686]  [<c01534dc>] softlockup_tick+0x9c/0xf0
[84450.519706]  [<c0130643>] update_process_times+0x33/0x80
[84450.519716]  [<c01154b0>] smp_apic_timer_interrupt+0x70/0x80
[84450.519725]  [<c01042f8>] apic_timer_interrupt+0x28/0x30
[84450.519737]  [<c01500d8>] audit_receive+0x2e8/0x9f0
[84450.519743]  [<c0262603>] ide_inb+0x3/0x10
[84450.519751]  [<c026370e>] ide_config_drive_speed+0x14e/0x310
[84450.519762]  [<f8899977>] via_set_drive+0x247/0x3e0 [via82cxxx]
[84450.519768]  [<c011e341>] __activate_task+0x21/0x40
[84450.519778]  [<c0120706>] try_to_wake_up+0x46/0x480
[84450.519788]  [<c0187e59>] __d_lookup+0x89/0x110
[84450.519801]  [<f8899cbf>] via82cxxx_ide_dma_check+0x6f/0xc0 [via82cxxx]
[84450.519808]  [<c025f56b>] set_using_dma+0x3b/0x60
[84450.519816]  [<c025f75f>] ide_write_setting+0x5f/0xd0
[84450.519827]  [<c0260848>] generic_ide_ioctl+0x498/0x4d0
[84450.519840]  [<c011e678>] __wake_up+0x38/0x50
[84450.519852]  [<c0239052>] n_tty_receive_buf+0x2e2/0xeb0
[84450.519868]  [<f89d3bac>] idedisk_ioctl+0x2c/0x40 [ide_disk]
[84450.519877]  [<c01e453d>] blkdev_driver_ioctl+0x6d/0x80
[84450.519887]  [<c01e483f>] blkdev_ioctl+0x2ef/0x7d0
[84450.519894]  [<c027e178>] kfree_skbmem+0x8/0x80
[84450.519903]  [<c02849ac>] net_tx_action+0x5c/0x110
[84450.519914]  [<c012b422>] __do_softirq+0x82/0x100
[84450.519928]  [<c0157000>] find_get_page+0x20/0x60
[84450.519937]  [<c0159b41>] filemap_nopage+0x2f1/0x3a0
[84450.519949]  [<c011ddd6>] kmap_atomic+0x86/0xa0
[84450.519953]  [<c011dc1b>] kunmap_atomic+0x6b/0x70
[84450.519962]  [<c0164519>] __handle_mm_fault+0x279/0xa40
[84450.519970]  [<c0102236>] __switch_to+0xc6/0x1f0
[84450.519987]  [<c019b7b8>] block_ioctl+0x18/0x20
[84450.519993]  [<c019b7a0>] block_ioctl+0x0/0x20
[84450.519996]  [<c018268b>] do_ioctl+0x2b/0x90
[84450.520005]  [<c018274c>] vfs_ioctl+0x5c/0x2a0
[84450.520014]  [<c0182a02>] sys_ioctl+0x72/0x90
[84450.520022]  [<c01031f0>] sysenter_past_esp+0x69/0xa9
[84450.520038]  =======================

---

