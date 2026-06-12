---
title: "&quot;Kernel Panic Not Syncing Attempted to Kill init!&quot;"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by nxnn14 on 2009-02-03
Hi,

I have been using Ubuntu 8.10 for a few weeks now and not had too many problems. Today when I came back to my computer after being away for a couple of hours the graphics for my compiz-fusion desktop were a bit weird. The effects seemed grainy as if the graphics card was not working properly. So I decided to restart. Once I restarted I got an error that said "Unsupported PM Caps regs version(7)" Then there was an about a "segfault" and a line that said "kernel panic not syncing attempted to kill init!" I did some searching and found that the first error may be an incompatibility in a pci slot. I thought maybe the graphics card was a problem, so I removed it. The first error when away but the other two remained. More research revealed it could be a problem with the memory so I can memtest. There were no errors with the memtest so I am at a loss. I have 2 gb of crucial ballistix ram, an intel pentium dual core e2200, and a Biostar G31 motherboard. Any info is greatly appreciated. Hopefully someone can help me out. 

Just to recap I changed no settings and performed no updates from the last working boot and now it errors and will not boot.

Thanks,

Nick

---

### Post by lykwydchykyn on 2009-02-03
You might want to scan the disk for problems.  Boot to the liveCD, open a terminal and run:
```

sudo badblocks -v /dev/sda

```
That will scan your drive for bad spots.  You also might want to scan the filesystem.  Assuming your root filesystem is /dev/sda1, you'd run:
```

sudo fsck /dev/sda1

```

---

### Post by icanfly0307 on 2009-02-03
Have you tried booting into the recovery mode (second option in grub)? Also, if you have a second kernel from previous system updates, try booting into them.

---

### Post by nxnn14 on 2009-02-03
I have tried to boot in both of the other kernels as well as all three recovery modes to no avail. I am going to try the disk scans this evening and will let you know how that goes. 

Thanks,

Nick

---

### Post by nxnn14 on 2009-02-04
So, it have me the same error messages when trying to boot with an ibex live usb, so I made a Hardy one and that booted. I then ran the two commands you suggested and this was the output:
For the disk scan;

ubuntu@ubuntu:~$ sudo badblocks -v /dev/sda
Checking blocks 0 to 78184007
Checking for bad blocks (read-only test): 237593603759360/       78184007
237594123759412/       78184007
237594133759413/       78184007
237594143759414/       78184007
237594153759415/       78184007
23759416
23759417
23759418
23759419
23759420
23759421
23759422
23759423
23759424
23759425
23759426
23759427
23759428
23759429
23759430
23759431
23759432
23759433
23759434
23759435
23759436
23759437
23759438
23759439
23759440
23759441
23759442
23759443
23759444
23759445
23759446
23759447
23759448
23759449
23759450
23759451
23759452
23759453
23759454
23759455
23759456
23759457
23759458
23759459
23759460
23759461
23759462
23759463
23759464
23759465
23759466
23759467
23759468
23759469
23759470
23759471
23759472
23759473
23759474
23759475
23759476
23759477
23759478
23759479
23759480
23759481
23759482
23759483
23759484
23759485
23759486
23759487
23759488
23759489
23759490
23759491
done                                
Pass completed, 81 bad blocks found.

For the filesystem scan:

ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
/dev/sda1 has been mounted 25 times without being checked, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda1: 263950/4702208 files (0.9% non-contiguous), 6438202/18802066 blocks

Looks like a bad hdd I guess?? It is pretty old anyway.

Thanks,

Nick

---

### Post by lykwydchykyn on 2009-02-05
Yeah, that disk is done.  Best replace it.

---

### Post by nxnn14 on 2009-02-05
Thanks for the help. Two questions though. First do you think that is the only issue and if I replace the HDD all the errors will be gone? Second is there any way to migrate my system, ie files, settings, and programs to another hard drive so that I dont have to start from scratch? When I boot from the live usb I can see the HDD and all my files so that shouldn't be a problem as far as retrieving them, mainly just the settings and programs. 

Thanks,

Nick

---

### Post by lykwydchykyn on 2009-02-05
> **nxnn14 said:**
> Thanks for the help. Two questions though. First do you think that is the only issue and if I replace the HDD all the errors will be gone? 

Who can say?  But if you have system files sitting on those bad sectors, it's definitely going to cause strange issues like you're having.  Between a working HDD and a new install, a lot of issues ought to get sorted out.

> 
Second is there any way to migrate my system, ie files, settings, and programs to another hard drive so that I dont have to start from scratch? When I boot from the live usb I can see the HDD and all my files so that shouldn't be a problem as far as retrieving them, mainly just the settings and programs. 

Thanks,

Nick

Well, your personal settings will all be in your home directory.  As for installed programs and system-wide settings, there are ways to do it but I'd be leery of copying too much over from a bad HDD.  If you back up /etc you should have at least a fallback if you just can't remember how you set up some service or other.

---

### Post by abah01 on 2009-02-05
Hi All,

I am wit's end. I have similar problem as Nick, however check says 0 blocks found - so I guess my SSD is OK? I am using AA1 8G SSD, and previously I had successfully migrated to Ubuntu and got all the necessary bits and pieces working. Until this problem. Since then I have reinstalled 3 times, each time the system is Ok at first, but after a few times of turning on the computer, Kernel Panic happens again! I am currently running from LiveUSB.

Can anybody help me? I am contemplating returning to Linpus Lite (AA1's original OS)....

Thank you all

---

