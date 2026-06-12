---
title: "Blank screem issue on satrt up ubuntu 9.10"
date: 2010-02-28
forum: New to Ubuntu
---

### Post by durga11 on 2010-02-28
I am using ubuntu 9.10 from past 4  months, today i got a blank screen issue. ubuntu boots up till splash screen and then goes to bank screen. I rebooted and has gone to recovery mode which has stopped displaying a *initramfs* prompt.

 I had no clue on the issue. Can i recover my data on HDD and how can i make my ubuntu back.

Any solutions please?

---

### Post by durga11 on 2010-02-28
While searching through the ubuntu forms, I came across this thread  [http://ubuntuforums.org/showthread.php?t=1405912](http://ubuntuforums.org/showthread.php?t=1405912) which i think has given a solution for the same prob.. While grub loading, add to the kernel boot line,  

 ro quiet splash nomodeset

Can i go ahead with the solution given in the given thread.

---

### Post by bcbc on 2010-02-28
try booting from the live cd - see if it mounts your hard drive, in which case back up your data.

After that I suppose you could try the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") from meierfra to see what it makes of your system and post the results back.

---

### Post by durga11 on 2010-02-28
Thnks for the reply.

. I had booted with the live CD and mounted the hard drive and taken my backup.I am attaching the output of the boot info script.

---

### Post by bcbc on 2010-02-28
It can't detect the file system on sda1: "/dev/sda1: ambivalent result (probably more filesystems on the device)"

Can you boot the live CD again and run the following in terminal?

```
$ sudo hexdump -C -s 0x410 -n 2 /dev/sda1
```

if it returns something like "8f 13" or "7f 13", or "68 24" or "78 24" then you may have been hit by this bug found by meierfra: [https://bugs.launchpad.net/ubuntu/+bug/518582]("https://bugs.launchpad.net/ubuntu/+bug/518582")

If this isn't the case, cut and paste back what you have in your terminal.

If you did get one of the byte outputs above, then to fix it try:
```
$ sudo mount /dev/sda1 -t ext4 /mnt
$ sudo touch /mnt/emptyfile  

```
Wait a bit, and then:
```
$ sudo blkid -p /dev/sda1
```

If that says "ext4" then you should be good to go - reboot and see if it works.

---

### Post by durga11 on 2010-03-01
Hi,


Thanks a lot.

I followed  and it gone well. I welcome any suggestions from you on my current ubuntu configuration. I had a doubt regarding ubuntu. Is there any way of installing ubuntu even though reinstaling wont affect the data with in.I am not sure of this way. But want to know if there is any procedure.

Once again thanks a lot for giving me the solution.

Durga

---

### Post by bcbc on 2010-03-01
> **durga11 said:**
> Hi,


Thanks a lot.

I followed  and it gone well. I welcome any suggestions from you on my current ubuntu configuration. I had a doubt regarding ubuntu. Is there any way of installing ubuntu even though reinstaling wont affect the data with in.I am not sure of this way. But want to know if there is any procedure.

Once again thanks a lot for giving me the solution.

Durga

You're welcome... don't forget to go to the bug report on launchpad and click on 'This bug affects # people...' (you have to login to your launchpad account to do this).

In terms of reconfiguring ubuntu to make it easier to reinstall, I'd have /home on a separate partition (easier to backup and you can reformat and install on your / partition without affecting your data). 
Here is a guide on moving /home to a new partition: [http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

You can also take a list of packages that you've installed and use it to reinstall them following a fresh install. See [HowTo: Create a list of installed packages]("http://ubuntuforums.org/showthread.php?t=261366")

**WARNING**: moving /home can result in disaster if it goes wrong. I haven't followed the guide myself. I recommend trying it first on a non-production computer, or making sure you have everything backed up first.

---

