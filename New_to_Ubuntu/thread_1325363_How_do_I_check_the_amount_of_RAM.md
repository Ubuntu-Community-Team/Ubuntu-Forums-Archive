---
title: "How do I check the amount of RAM?"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by mrothgeb on 2009-11-13
My problem is this: I keep having programs lock up on me enough so that I can't get the mouse over to force quit. this is a recent problem with my Ubuntu 9.04 install I use to be able to run several programs and it'd be slow but not lock up.

So I have a few questions:
1) how do I check how much RAM the OS is seeing as installed?
2) what is the Ubuntu equivalent of Crtl-Alt-Del?
3) Crucial.com has a memory check but only works with M$, anyone know a Ubuntu friendly site like crucial?

---

### Post by garvinrick4 on 2009-11-13
type "free" in terminal without qoutes.

reboot:   alt/sys rq/b

---

### Post by ukripper on 2009-11-13
> 
So I have a few questions:
1) how do I check how much RAM the OS is seeing as installed?

in terminal type command:
```
free -m
``` it will give you ram stat in MB

> 2) what is the Ubuntu equivalent of Crtl-Alt-Del?
There is none. But can be added

> 3) Crucial.com has a memory check but only works with M$, anyone know a Ubuntu friendly site like crucial?
What kind of memory check?

---

### Post by doas777 on 2009-11-13
most likely your lockups are not caused by a lack of free ram, but might be a sign of a problem with your ram itself. you can test it with memtest from the grub menu.

---

### Post by 1clue on 2009-11-13
Careful with the ctrl-alt-del thing!

I once set that up in /etc/inittab to put me into single user mode using ctrl-alt-del, and what I did was give non-users access to a root terminal without typing a password.  You could walk up to the PC when nobody was logged in and get root access.

Not what I had planned at all.

---

### Post by durand on 2009-11-13
For the Ctrl-Alt-Del thing, I guess you mean the task manager application? Go to System > Administration > System Monitor. If you right click on the panel, you can add a system monitor applet. To check your ram, you can also use the system monitor. Not sure about the crucial thing though..

---

### Post by Niko Johnson on 2009-11-13
just check your system info places >system info... if you dont have if you can get it from the add/remove under applications

---

### Post by mrothgeb on 2009-11-13
> **ukripper said:**
> in terminal type command:
```
free -m
``` it will give you ram stat in MB


There is none. But can be added


What kind of memory check?


```
   total       used       free     shared    buffers     cached
Mem:           480        474          6          0          7        118
-/+ buffers/cache:        348        131
Swap:            0          0          0
```Thanks. 

Crucial would test your system to see how much RAM you had and how much your board could handle.  I believe it used ActiveX but its been a while.

---

### Post by ukripper on 2009-11-13
As other poster suggested you can use memtest at beginning of boot up to test your RAM. But i don't think RAM is problem here. i think it is your swap which ain't probably working as expected.

---

### Post by mrothgeb on 2009-11-13
> **doas777 said:**
> most likely your lockups are not caused by a lack of free ram, but might be a sign of a problem with your ram itself. you can test it with memtest from the grub menu.

last I did a memtest with grub it tested fine.

---

### Post by ukripper on 2009-11-13
> **mrothgeb said:**
> last I did a memtest with grub it tested fine.

Your swap is not kicking in to help your RAM out. you got to make your swap running

---

### Post by durand on 2009-11-13
How much swap space do you have? I think it tells you in System Monitor.

---

### Post by mrothgeb on 2009-11-13
> **ukripper said:**
> As other poster suggested you can use memtest at beginning of boot up to test your RAM. But i don't think RAM is problem here. i think it is your swap which ain't probably working as expected.

hmmm

My HD is set up like this:
sda1 ext3 9.04 Ubuntu 77 GB
sda3 Linux-swap 4 GB
sda2 ext3 media disk

---

### Post by ukripper on 2009-11-13
> **mrothgeb said:**
> hmmm

My HD is set up like this:
sda1 ext3 9.04 Ubuntu 77 GB
sda3 Linux-swap 4 GB
sda2 ext3 media disk

can you post output of the following command:
```
sudo fdisk -l
```

---

### Post by mrothgeb on 2009-11-13
> **ukripper said:**
> can you post output of the following command:
```
sudo fdisk -l
```
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007f163

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10074    80919373+  83  Linux
/dev/sda2           10619       19457    70999267+  83  Linux
/dev/sda3           10075       10618     4369680   82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by ukripper on 2009-11-13
can you post output of this:
```
cat /proc/swaps
```

---

### Post by mrothgeb on 2009-11-13
> **ukripper said:**
> can you post output of this:
```
cat /proc/swaps
```

```
michael@blackAce:~$ cat /proc/swaps
Filename                Type        Size    Used    Priority
michael@blackAce:~$ 

```

Exact copy  there is nothing listed under the headers.

---

### Post by ukripper on 2009-11-13
That means you swap is not working.

---

### Post by mrothgeb on 2009-11-13
> **ukripper said:**
> That means you swap is not working.

ok.  So now what?

---

### Post by ukripper on 2009-11-13
can you post output of this:
```
cat /etc/fstab
```

---

### Post by mrothgeb on 2009-11-13
> **ukripper said:**
> can you post output of this:
```
cat /etc/fstab
```

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=afae34a9-832a-4c95-ac8a-1199a9f350f2 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3b8c32e8-a46a-4277-8fc8-acadcaac6d4e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by ukripper on 2009-11-13
can you run this command:
```
blkid
```

---

### Post by mrothgeb on 2009-11-13
> **ukripper said:**
> can you run this command:
```
blkid
```

```
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="afae34a9-832a-4c95-ac8a-1199a9f350f2" TYPE="ext3" 
/dev/sda2: UUID="dfb15503-a87b-45e0-a707-f84c5649e656" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: TYPE="swap" UUID="4f55629f-6628-4cc0-aad4-36be4c9d2853" 
```

---

### Post by ukripper on 2009-11-13
> **mrothgeb said:**
> ```
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="afae34a9-832a-4c95-ac8a-1199a9f350f2" TYPE="ext3" 
/dev/sda2: UUID="dfb15503-a87b-45e0-a707-f84c5649e656" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: TYPE="swap" UUID="4f55629f-6628-4cc0-aad4-36be4c9d2853" 
```

Go to fstab:
```
sudo gedit /etc/fstab
```

amend this line > UUID=3b8c32e8-a46a-4277-8fc8-acadcaac6d4e none            swap    sw              0       0


to this:-

```
UUID=4f55629f-6628-4cc0-aad4-36be4c9d2853 none            swap    sw              0       0
```

save and exit.

in terminal type:
```
sudo swapoff -a
```

and then ```
sudo swapon -a
```

and then post output of this command:
```
cat /proc/swaps
```

---

### Post by doas777 on 2009-11-13
kewl! I had no idea that you could toggle swap on the fly. 
learn somthing everyday

---

### Post by ukripper on 2009-11-13
> **doas777 said:**
> kewl! I had no idea that you could toggle swap on the fly. 
learn somthing everyday

Yeh ! There is something new everyday to learn on ubuntuforums.:p

---

### Post by mrothgeb on 2009-11-13
```

michael@blackAce:~$ cat /proc/swaps
Filename                Type        Size    Used    Priority
/dev/sda3           partition    4369672    0    -1

```

---

### Post by mrothgeb on 2009-11-13
Looks like it worked nicely!  Thanks SO much UK!

Going to test it out some more then change this topic to solved.

---

### Post by ukripper on 2009-11-13
yeh output looks good. can you run fowllowing comand:
```
free -m
```

---

