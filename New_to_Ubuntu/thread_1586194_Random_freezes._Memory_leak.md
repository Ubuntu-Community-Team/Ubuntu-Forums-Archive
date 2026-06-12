---
title: "Random freezes. Memory leak?"
date: 2010-10-01
forum: New to Ubuntu
---

### Post by NinjaWizard on 2010-10-01
Hi. My first post here. :)

I installed Ubuntu 10.04 on my ASUS X70ID laptop about 2 weeks ago, and I absolutely love it. However I'm having some problems with random freezes. I tried to isolate the problem to a specific program, but it happens too randomly. Even when I'm away from the laptop and it starts the screen saver, it suddenly just stops up.

It freezes on whatever it is showing at the time, and you can't move the mouse, the clock freezes etc. Once I was watching a youtube video when it happened, and the sound kept repeating a 1 second segment again and again. On the keyboard the caps lock/num lock lights don't respond and even alt + SysRq + reisub did absolutely nothing. I just have to kill the power to start it up again.

After some googling I read about memory leak being the potential culprit, and when I ran
free -m -s 5
I could see that my free memory kept being eaten away. When I log in I have about 3700 free from 4000 total, but after a while, while running mutorrent through wine and firefox, it went down to 600 free just dropped to 180 in about 5 minutes until I restarted manually.

I suspect this is a memory leak, but I don't really know what to do from here. Some help would be appreciated!

---

### Post by NinjaWizard on 2010-10-01
Right after I posted I checked my free memory, which had dropped to about 1800, and a few seconds later it froze up again. Perhaps the memory leak wasn't the problem after all.

This is very frustrating, and I'm afraid I'm going to damage something on my computer with these frequent power downs.

Perhaps I should install Windows 7 again... :(

---

### Post by endotherm on 2010-10-01
well, memory leaks and lockups are differant kinds of animals(though a sever leak could cause a deadlock condition).

if you mouse has stopped responding, then the it is probably a crash or a deadlock, and it goes all the way down to your kernel (bad driver perhaps?).

after it happens and you reboot, go to system -> Administration -> Log file Viewer, and look at dmesg.0.log. this should be the dmesg log from your last boot. check all the way down at the bottom and you should see the last item logged prior to the freeze up. do you see anything? how about messages in Kern.log, System.log or Messages.log that correspond to the time that the lockup occurred?

---

### Post by endotherm on 2010-10-01
> **NinjaWizard said:**
> Right after I posted I checked my free memory, which had dropped to about 1800, and shortly after it froze up again. Perhaps the memory leak wasn't the problem after all.

This is very frustrating, and I'm afraid I'm going to damage something on my computer with these frequent power downs.

Perhaps I should install Windows 7 again... :(
I think what you are seeing is cache memory. when ubuntu reads off the disk, it keeps the data it pulled in in ram in what they call "IO cache", just in case you call for it again later. cache memory is just accumulated as you run the PC, but when you need the ram for an application, the system clears part of the cache to make room for you. 

you can use Bleachbit to clear your cache memory, and my guess is that then 'free' will show you back to close your original used amount. 

low ram will make your PC slow, but it won;t completely lock it. now bad data or blocks of damaged ram can though. you can check the integrity of your ram with the MemTest option in the grub boot menu.

---

### Post by NinjaWizard on 2010-10-01
Okay, thanks for answering. I checked the logs as you recommended, but it's all kind off jibberish to me. :)

In the Sys logs I couldn't tell where it crashed and where it started.
(Yeah, I called my laptop the 'Dominator') ;)

**dmesg.0**
> [   10.802087] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   10.802182] type=1505 audit(1285963181.835:9):  operation="profile_load" pid=969 name="/usr/bin/evince"
[   10.810458] type=1505 audit(1285963181.843:10):  operation="profile_load" pid=969 name="/usr/bin/evince-previewer"
[   10.815815] type=1505 audit(1285963181.847:11):  operation="profile_load" pid=969 name="/usr/bin/evince-thumbnailer"
[   11.176044] hda_codec: ALC662 rev1: BIOS auto-probing.
[   11.396113] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:08.0/input/input12**kern.log**
> Oct  1 22:41:12 Dominator kernel: [   13.465977] nvidia 0000:00:03.5: PCI INT B -> Link[LPMU] -> GSI 22 (level, low) -> IRQ 22
Oct  1 22:41:13 Dominator kernel: [   14.334394] nvidia 0000:02:00.0: PCI INT A -> Link[LN0A] -> GSI 17 (level, low) -> IRQ 17
Oct  1 22:41:13 Dominator kernel: [   14.334405] nvidia 0000:02:00.0: setting latency timer to 64
Oct  1 22:41:13 Dominator kernel: [   14.334410] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Oct  1 22:41:13 Dominator kernel: [   14.334655] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.24  Thu Apr 22 09:18:20 PDT 2010
Oct  1 22:41:21 Dominator kernel: [   22.788058] eth0: no IPv6 routers present**messages.log**
> Oct  1 22:41:12 Dominator kernel: [   13.465973] ACPI: PCI Interrupt Link [LPMU] enabled at IRQ 22
Oct  1 22:41:12 Dominator kernel: [   13.465977] nvidia 0000:00:03.5: PCI INT B -> Link[LPMU] -> GSI 22 (level, low) -> IRQ 22
Oct  1 22:41:13 Dominator kernel: [   14.334394] nvidia 0000:02:00.0: PCI INT A -> Link[LN0A] -> GSI 17 (level, low) -> IRQ 17
Oct  1 22:41:13 Dominator kernel: [   14.334410] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Oct  1 22:41:13 Dominator kernel: [   14.334655] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.24  Thu Apr 22 09:18:20 PDT 2010

---

### Post by oldsoundguy on 2010-10-01
Some recent memory leak issues have been observed in FireFox.  Current version is NO exception.  Not as bad as before .. now takes 2 or 3 DAYS of on line usage for it to show up.
The REALLY bad one is FaceBook.  You have to have a fresh sign in, in order to use their uploader for images!

---

### Post by teresaejunior on 2010-10-02
I found this thread while looking for help on some memory leaks I'm having. But, the lockups in your machine seem to do with high temperatures. If you have not tested it yet, do the following:

Open a terminal and paste the following command, which will watch your temperature updating each 2 seconds:

```
watch grep temperature /proc/acpi/thermal_zone/*/temperature
```

EDIT: I should have paid a bit more of attention to your problem, but you can try this anyway...

---

### Post by formaldehyde_spoon on 2010-10-02
I don't have anything helpful to add, but yeah me too: as soon as I see or hear ''random'' I think ''hardware''. 

EDIT: hmm, I sound sarcastic there, but I'm not meaning to...

---

