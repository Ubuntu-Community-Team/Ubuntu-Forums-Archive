---
title: "Where Is the location of &quot;/&quot; exactly?"
date: 2009-11-20
forum: New to Ubuntu
---

### Post by MehdizLinux on 2009-11-20
I was trying to increase my swap space, so I created a new file:


sudo dd if=/dev/zero of=/swap_file bs=1M count=1000

I can find it by search, but if I go to the properties, the location is "/" . In "/" there are just famous folders. Where is my new swap file? where can I see it?

And, What is /dev/**zero** ? a blank file as a source for swap file or something like that?

Thanks.

---

### Post by dca on 2009-11-20
Swap is a partition, type *sudo fdisk -l* at CLI, the last one is a lower-case 'L' for list...
 
You should see /dev/sda1 as ext3 or ext4 and /dev/sd* as swap...

---

### Post by anewguy on 2009-11-20
As dca mentioned, the virtual memory file in Ubuntu is not a file as it is in some other operating systems, it is actual hard disk partition.

In answer to your title question, "/" is the "root" of the entire directory tree in Ubuntu.  Every directory, file, device, etc., are all accessed starting at "/".  When you were looking in "/dev" you were looking in the directory were Ubuntu logically "connects" devices - the "/" says start at the root, and the "dev" says look for the "dev" directory there.

Dave :)

---

### Post by NoaHall on 2009-11-20
> **anewguy said:**
> As dca mentioned, the virtual memory file in Ubuntu is not a file as it is in some other operating systems, it is actual hard disk partition.

In answer to your title question, "/" is the "root" of the entire directory tree in Ubuntu.  Every directory, file, device, etc., are all accessed starting at "/".  When you were looking in "/dev" you were looking in the directory were Ubuntu logically "connects" devices - the "/" says start at the root, and the "dev" says look for the "dev" directory there.

Dave :)

You can have swap file, which he is trying to make.

Try this.

```

sudo dd if=/dev/zero of=/mnt/swap.swap bs=1M count=1024
sudo mkswap /mnt/swap.swap
sudo swapon /mnt/swap.swap

```

Then
```

gksudo gedit /etc/fstab
and post onto the end of the file * don't delete anything in that file* -
/mnt/swap.swap  none  swap  sw  0 0

```

---

### Post by juancarlospaco on 2009-11-20
[B]cd /
pwd[/B]

*here is, your are there...*

---

### Post by Bölvaður on 2009-11-20
> **NoaHall said:**
> You can have swap file, which he is trying to make.

]

how much slower is it to have it as a file?
not like swap memory has any use anymore except for hibernation

---

### Post by NoaHall on 2009-11-20
> **Bölvaður said:**
> how much slower is it to have it as a file?
not like swap memory has any use anymore except for hibernation

Swap is used on systems with low ram or ones which use a lot of ram.

It's not slower at all. It's pretty much the same.

---

### Post by bodhi.zazen on 2009-11-20
Windows a partition is lettered, ie C:\

In Linux they are numbered and can be referenced by either device (dev/sdxy or UUID or LABEL) or more often by mount point.

So / = C:\

If you have additional partitions, in Windows they would be D:\ or E:\ ect

In Linux they are /dev/sdxy or /media/mount_point

See:

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018&highlight=partitioning") 

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

@ NoaHall , nice post, you saved me much typing :p

---

### Post by MehdizLinux on 2009-11-20
Thanks everybody. I already created the swap file, secured it, enabled it (make on) and added the last line: 

/swap_file       none            swap    sw              0       0

in fstab file. After restart I found my swap file in "/" which solved my question. Now the main problem:

I cannot Suspend my HP 4400 workstation. I found lots of other posts about that all same as me and no solution for them. So I tried to Hibernate. It doesn't work too! So I thought my swap space may not be enough. I increased it to 1.5 of my RAM on that machine. No chance. It seems Ubuntu makers never turn off their machines, so they are not interested to solve this issue!!

You know, after Vista, I've been thinking "in this case, my friend  grandma could write an OS too!". But after starting to do my daily work with Ubuntu, I realized that I may be mistaken. Come on... It is a basic feature inside the OS itself!!!

---

### Post by NoaHall on 2009-11-20
Can you post the output of "free -m" ? Also, you could take a screenshot of system monitor showing the swap size reported there (it can be different).

---

### Post by MehdizLinux on 2009-11-21
Here it is NoaHall:
```

             total       used       free     shared    buffers     cached
Mem:          2013        499       1513          0         26        231
-/+ buffers/cache:        241       1771
Swap:         3094          0       3094

```

---

### Post by lavinog on 2009-11-21
I find that the video driver tends to cause a lot of suspend/hibernation issues.

What video driver are you using?

---

### Post by MehdizLinux on 2009-11-21
Well It seems they already know the mess there:

[http://brainstorm.ubuntu.com/idea/94/](http://brainstorm.ubuntu.com/idea/94/)

I wish I could help them to fix it faster...

---

### Post by MehdizLinux on 2009-11-21
I updated the driver to the latest version. I have NVIDIA. and I downloaded the driver from them and installed it manually. How ever I cannot see the version in the result of lshw:

```

 *-display
                description: VGA compatible controller
                product: G71 [Quadro FX 1500]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:e1000000-e1ffffff memory:d0000000-dfffffff(prefetchable) memory:e2000000-e2ffffff ioport:1000(size=128) memory:e0000000-e001ffff(prefetchable)

```

I added nvidia to "MODULES_WHITELIST="" " in  " /etc/default/acpi-support" No result...

Anyway, how can I lunch the NVIDIA application to check the driver version, etc ?

---

### Post by anewguy on 2009-11-21
> **NoaHall said:**
> You can have swap file, which he is trying to make.

Try this.

```

sudo dd if=/dev/zero of=/mnt/swap.swap bs=1M count=1024
sudo mkswap /mnt/swap.swap
sudo swapon /mnt/swap.swap

```

Then
```

gksudo gedit /etc/fstab
and post onto the end of the file * don't delete anything in that file* -
/mnt/swap.swap  none  swap  sw  0 0

```

Since that seems to be the case from what you say, then I would only ask "why"? (not trying to be a smart *ss or anything, I really am curious as to why when swap is normally set up as a partition).

I would imagine it's not the case anymore, but years ago *some* OS's (don't know if Unix was one of them or not) would build channel programs for virtual memory at the maximum track size allowed for the device the virtual memory file was on.  This usually made transfers in/out faster.  One of the OS's I used to work with was one of those.  Can you or someone else point me to the tech details on swap (ideal blocksize,etc.) so I can get a better tech understanding of the swap details?

Thanks
Dave :)

---

### Post by NoaHall on 2009-11-21
> **MehdizLinux said:**
> Here it is NoaHall:
```

             total       used       free     shared    buffers     cached
Mem:          2013        499       1513          0         26        231
-/+ buffers/cache:        241       1771
Swap:         3094          0       3094

```

Hm.. Is there any message when it goes wrong?

@anewguy:
Having a swap file is pretty much exactly the same a swap partition. Having a swap partition is only faster if you are using a NTFS filesystem, as it will wipe the data(therefore, "defragging it" in a sense).

---

### Post by gn2 on 2009-11-21
Does having the swap partition on a different hard drive make it any faster?

---

### Post by NoaHall on 2009-11-21
> **gn2 said:**
> Does having the swap partition on a different hard drive make it any faster?

It depends on the speed of the hard drive. If it's a faster hard drive, it'll be a faster swap.

---

### Post by anewguy on 2009-11-21
Maybe another left over doesn't apply anymore either - doesn't having a separate swap partition on a different drive on a different controller make a difference?

Thanks
Dave :)

---

### Post by anewguy on 2009-11-24
I've been waiting for someone to post the obvious question here, but since no one has, I'll go ahead.

Since swap can be a file, why doesn't Ubuntu:

(1) Automatically create the file on installation, saving having to make a partition for swap (since after install someone could create a swap partition and make it active if they wanted to)?

(2) Automatically (or perhaps it does??) resize the swap file on the fly?

Just curious......

There apparently is no advantage to a swap partition unless it is perhaps on a different disk (for space concerns) and possibly a different controller (for performance concerns), at least that is the idea I'm getting from the responses in this post.  So why not do like (GASP!!) that OTHER OS and just make the file automatically?

Dave :)

---

