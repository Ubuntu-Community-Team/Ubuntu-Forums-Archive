---
title: "hibernating doesn't work"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by libihero on 2008-12-31
when i choose hibernate, the screen just goes black and there is a "text prompt thing" (no, i am not able to type anything into the text prompt)
with vista, hibernate was very important for me, since it basically shut off my power and saved all the work i was doing.
is there any way for me to fix it so that ubuntu does the same??

---

### Post by phantomjoker on 2008-12-31
would you know how many gbs of swap space you have?

you need at least this many as your ram - since your ram is temporaroly placed in the swap during hibernation - if your swap is less than your ram, you can't.

---

### Post by libihero on 2008-12-31
how would i find that out?

---

### Post by Paqman on 2008-12-31
System > Admin > System Monitor > Resources

---

### Post by libihero on 2008-12-31
ok it says i have zero swap space, 
how can i make it so that i have swap space?

---

### Post by nhasian on 2008-12-31
when you installed ubuntu did you create a swap partition?  what is the output of:

```
cat /etc/fstab
```

---

### Post by libihero on 2009-01-02
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=0f3297f1-4c61-4f3e-95df-8bb0ed052513 /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

that's what i get

---

### Post by nhasian on 2009-01-02
it looks like the only partition in your /etc/fstab is your root partition.  Boot off the liveCD and go to System-Administration-Partition Editor.  This will launched gparted.

your linux EXT3 root partition is /dev/sda3.  if you dont have any swap partitions, you can resize the partition to make room for a swap partition.  Just select the partition you want to use, click the shrink button, then drag the mouse over to make room for a new partition.  if you have 2 gigs of ram, you'll want 2048-3072Gigs of swap (1-1.5x).

once you've made some empty space click the *new* button select the SWAP option and you should be ready to go.

Please be advised resizing partitions carries a small risk of data loss if something goes wrong like power outage, etc.  be sure to backup any critical files before continuing.

---

### Post by amaroKer on 2009-01-02
Here's my output

```
logan@logan-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=66ad2293-aa34-4c2a-bae3-de46a91100a5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=464077d5-f2af-4a22-9267-102b71554f8b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

It appears that my swap is mounted, but System Monitor > Resources says I still have 0 bytes swap.  This makes me confused.

---

### Post by footprint on 2009-01-03
It seems I have a similar problem. Hibernate has stopped working(I don't know when as I don't often use it).
The error messages indicate there is no active swap partition.
I can't activate swap using "swapon -a" as root, but I can activate it by clicking <swapon> in GParted and hibernate then works. However on reboot the swap partition is no longer active. Following an old forum thread I removed the UUID from fstab but this has achieved nothing.

[code]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=34458741-dd01-48fa-88d6-e95d1577c2c3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=0c5fd73a-18e5-4b3b-be54-416f13286d17 /home           ext3    relatime        0       2
# /dev/sda7                               none            swap    sw              0       0
[code]
------------------------
[code]
martin@martin-netbook:~$ free
             total       used       free     shared    buffers     cached
Mem:       1024248     662204     362044          0      23344     287928
-/+ buffers/cache:     350932     673316
Swap:            0          0          0
martin@martin-netbook:~$ 
[code]
--------------------------
after activating swap from GParted:-
[code]martin@martin-netbook:~$ free
             total       used       free     shared    buffers     cached
Mem:       1024248     731948     292300          0      31396     322288
-/+ buffers/cache:     378264     645984
Swap:      1269092          0    1269092
martin@martin-netbook:~$ 
[code]

What is going on?

---

### Post by libihero on 2009-01-07
bumpp

---

### Post by nhasian on 2009-01-08
libihero, did you create a swap parition and turn it on? you should see how much swap space you have when you type *free* at a command prompt.

footprint & amaroKer, you should each start your own threads to make it easier for people to help you troubleshoot as you have a different issue from libihero.  in your opening post include the output of the following commands:

```
dmesg | grep -i swap
sudo fdisk -l
ls /dev/disk/by-uuid/
cat /etc/fstab
```

---

### Post by eisbaar on 2010-01-08
I can't even start my computer after hibernate, and after hard power off, can anyone help? I only get blank screen and reboot. I can't even see the boot-loader nor bios screen...

---

### Post by libihero on 2010-01-08
here is the result when i type in "free"
```
             total       used       free     shared    buffers     cached
Mem:       1930844     825720    1105124          0      44384     406908
-/+ buffers/cache:     374428    1556416
Swap:      3903752       5684    3898068

```
do i have enough swap space? my memory is 2 gigs

---

### Post by audiomick on 2010-01-08
the results of free show 1930844 as your RAM, and 3903752 as your swap, so that is enough for hibernate to work.

---

### Post by libihero on 2010-01-08
woah nevermind i thought this was the other thread i opened
my hibernate works with karmic, but my sleep doesnt.  it falls asleep but when i turn it back on, my laptop screen wont turn on

---

### Post by mikechant on 2010-01-08
> my hibernate works with karmic, but my sleep doesnt.

Probably best to open a new thread for that to avoid confusion and mark this one solved as hibernate is working.

---

### Post by libihero on 2010-01-08
ya i had a new thread i opened a long time ago, just thought this one was it sry

---

