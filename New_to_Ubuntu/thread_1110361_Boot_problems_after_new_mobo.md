---
title: "Boot problems after new mobo"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by Noampod on 2009-03-29
Hope someone can help me. I have just installed a new motherboard and now I can't load my Ubuntu. It's a dual boot with hardy and winxp installed.

It boots to grub I select Ubuntu hit enter, Ubuntu splash screen is displayed and the progress bar moves from side to side for a few minuets. Then I get the message below, same thing happens if I try to load the recovery console.

Starting up...
Loading, please wait...
             Check root= bootarg cat /proc/cmdline
             or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/7a2e39d0-cdae-4628-bbdf-5571822bc840 does not exist. Dropping to shell!

BusyBox v1.1.3 (Debian 1:1.1.3-5 ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _ 

Cheers Noam

---

### Post by tad1073 on 2009-03-29
Did you reinstall Ubuntu? Can you boot into xp?

---

### Post by Noampod on 2009-03-29
> **tad1073 said:**
> Did you reinstall Ubuntu? Can you boot into xp?
No I did not reinstall Ubuntu, yes I can boot xp. I can boot the hardy live cd also.

---

### Post by drs305 on 2009-03-29
Boot to a livecd, open a terminal, and run:
```

sudo blkid -c /dev/null

```

Now mount your ubuntu system partition, using the actual device name instead of sdXX:
```

sudo mkdir /mnt/temp
sudo mount /dev/sd[COLOR="DarkRed"]XX[/COLOR] /mnt/temp
cd /mnt/temp
cat boot/grub/menu.lst
cat etc/fstab
```
Check the UUIDs to see if they match what are listed in the fstab and menu.lst files. If any disagree, update them to match the results of the blkid command. If they agree, check the other UUID listings in fstab as well.

---

### Post by Noampod on 2009-03-29
> **drs305 said:**
> Boot to a livecd, open a terminal, and run:
```

sudo blkid -c /dev/null

```

Now mount your ubuntu system partition, using the actual device name instead of sdXX:
```

sudo mkdir /mnt/temp
sudo mount /dev/sd[COLOR="DarkRed"]XX[/COLOR] /mnt/temp
cd /mnt/temp
cat boot/grub/menu.lst
cat etc/fstab
```
Check the UUIDs to see if they match what are listed in the fstab and menu.lst files. If any disagree, update them to match the results of the blkid command. If they agree, check the other UUID listings in fstab as well.
Thanks for your response drs305. A couple of questions:
1.How do I find the actual device name of sdxx?

2.How do I go about checking the uuids?

Sorry I'm a noob when it come to the terminal and what codes to use.

Cheers
Really appreciate your time and patients :)

---

### Post by davec64 on 2009-03-29
When at the busybox shell wait a few minutes and type: 

```
exit
```

Does the system then proceed to boot normally?

---

### Post by Noampod on 2009-03-29
> **davec64 said:**
> When at the busybox shell wait a few minutes and type: 

```
exit
```

Does the system then proceed to boot normally?
I will give this a try. Be back in about 30 minutes.

Thanks davec64

---

### Post by drs305 on 2009-03-29
Here is a sample result of blkid:
> 
/dev/[COLOR="Red"]sda1[/COLOR]: UUID="CEECFF9EECFF7F51" TYPE="[COLOR="Red"]ntfs[/COLOR]" 
/dev/sda4: TYPE="[COLOR="Red"]swap[/COLOR]" UUID="b7d836c2-131b-4a4b-be8c-53694caa9432" 
/dev/sda5: UUID="4d33bfe6-a340-4fb2-8d97-ed9a19a864d7" SEC_TYPE="ext2" TYPE="ext3" [COLOR="Red"]LABEL="intrepid[/COLOR]" 

So you can see one is formatted to "ntfs", which is normally a windows or data partition. You can also see the "swap" partition, as well as any LABELS you may have given a partition.

If you haven't made additional partitions, you probably have a windows partition (ntfs), a swap partition, and a linux partition (ext3). You may also have another ntfs partition which would probably be a windows recovery partition (if it's a laptop).

Your menu.lst would have entries near the bottom that look like this:
> 
title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=[COLOR="DarkRed"]4d33bfe6-a340-4fb2-8d97-ed9a19a864d7[/COLOR] ro i8042.reset vga=769 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

and fstab, you want to check all, but especially the **[COLOR="DarkRed"]/[/COLOR]** and swap UUIDs:
> 
UUID=4d33bfe6-a340-4fb2-8d97-ed9a19a864d7 **[COLOR="DarkRed"]/[/COLOR]** ext3 defaults,errors=remount-ro  0 1
# Entry for /dev/sda4 :
UUID=b7d836c2-131b-4a4b-be8c-53694caa9432 none [COLOR="DarkRed"]swap[/COLOR] sw 0 0


---

### Post by Noampod on 2009-03-29
> **davec64 said:**
> When at the busybox shell wait a few minutes and type: 

```
exit
```

Does the system then proceed to boot normally?
When I type 'exit' I get the same message stated in my 1st post.

Should I do as drs305 suggested? If so I need a step by step guide, as I'm a nood with the terminal and codes. Is sdxx to do with the hard drive?

---

### Post by Noampod on 2009-03-29
Ok, drs305 if I type:

```
sudo blkid -c /dev/null
```

Will that show me what partitions I have?

---

### Post by Noampod on 2009-03-29
I will give your solution a try drs305, only way to learn I guess :)

I worry too much, report back in a while.

---

### Post by drs305 on 2009-03-29
> **Noampod said:**
> Ok, drs305 if I type:

```
sudo blkid -c /dev/null
```

Will that show me what partitions I have?

It will provide the results of the first example I gave in post 8. I use the "-c /dev/null" switch when there are UUID problems, since a UUID that changed may be cached and without the switch could provide a 'stale' or outdated UUID.

---

### Post by Noampod on 2009-03-29
I have run the code:

```
sudo blkid -c /dev/null
```

Here are the results:

ubuntu@ubuntu:~$ sudo blkid -c /dev/null
/dev/loop0: TYPE="squashfs" 
ubuntu@ubuntu:~$ 

What am I doing wrong?

---

### Post by drs305 on 2009-03-29
I am booting to a livecd right now. I just ran it from the livecd Desktop from a terminal and got results similar to the ones I posted. I also get the "/dev/loop0" line but all my partitions, whether mounted or not, are listed.

You can try it without the switch, just as "sudo blkid", but that shouldn't really make a difference and if you do they may be the cached ones.

If I had to guess, I would venture that your BIOS isn't recognizing your drives and that you are going to have to tinker with the BIOS settings. 

I'm not familiar with that hardware issue, so someone else with expertise in that area will hopefully jump in here and be able to provide some insight.

---

### Post by Noampod on 2009-03-31
Thanks for all the help on this. After some more digging I found the solution to my problem. Turns out I had to enable the SATA AHCI mode option in the bios. So good to have me ubuntu back :)

---

