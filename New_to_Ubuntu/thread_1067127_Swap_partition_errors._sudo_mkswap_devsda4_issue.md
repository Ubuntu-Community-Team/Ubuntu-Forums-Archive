---
title: "Swap partition errors. sudo mkswap /dev/sda4 issue"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by Bendihossan on 2009-02-11
Hey all. Been looking for a solution to this but haven't found anything that has helped here or elsewhere. 

My swap partition is not in use and for whatever reason I cnn't enable it. The OS seems to run fine without it. After running several processer-intensive application the swap still is left inactive. I've tried the following to no avail:

```
sudo swapon -a
``````
sudo mkswap /dev/sda4
```
mkswap /dev/sda4 returns the following strange error:

```
Setting up swapspace version 1, size = 4038606 kB
no label, UUID=0eca6dc5-55eb-41df-8ae8-2974cbbe59c6

```Also /etc/fstab contains the following line:
```
# /dev/sda4
UUID=d58bf1cb-d27a-487d-b337-056767fd5ad6none            swap    sw              0       0
```Also if this helps at all the *free* command returns the following:

```
             total       used       free     shared    buffers     cached
Mem:       2066024    1127408     938616          0      59892     581724
-/+ buffers/cache:     485792    1580232
Swap:            0          0          0

```fdisk -l:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6503dd57

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1274    10233373+  83  Linux
/dev/sda2   *        1275       10383    73162752    6  FAT16
/dev/sda3           10383       18966    68945312+   7  HPFS/NTFS
/dev/sda4           18967       19457     3943957+  82  Linux swap / Solaris

```Any help and progress made is greatly appreciated. :)
Ps. As an after thought: is it preferable to have a swap partition or file to use as swap space? It could also be possible to remove that partition and use a swap file instead if recommended? Thanks again!

---

### Post by fava on 2009-02-11
You have 2gb of ram, and almost 1GB free. The swap file is not being used because its not needed.

You need to run memory intensive apps to exercise swap, not processor intensive.

The mkswap command output is normal, there is no error. If you want a label you need to use mkswap -L yourlabel /dev/sda4

---

### Post by taurus on 2009-02-11
> # /dev/sda4
UUID=d58bf1cb-d27a-487d-b337-056767fd5ad6 **[COLOR="Red"]none[/COLOR]**            swap    sw              0       0
There should be a space between the UUID and the word none in /etc/fstab.

Also, what's the output of this command in a terminal?

```
sudo blkid
```

---

### Post by caljohnsmith on 2009-02-11
> **fava said:**
> You have 2gb of ram, and almost 1GB free. The swap file is not being used because its not needed.

According to the output of "free", Bendihossan does not have any swap even available, so that's the issue right now, not that the swap wasn't needed at the time he ran that command.

Bendihossan, how about trying the following:
```
sudo mkswap -U d58bf1cb-d27a-487d-b337-056767fd5ad6 /dev/sda4
```
Also, it looks like your fstab needs correcting:
[QUOTE=Bendihossan]```
# /dev/sda4
UUID=d58bf1cb-d27a-487d-b337-[COLOR="Red"]056767fd5ad6none[/COLOR]            swap    sw              0       0
```[/QUOTE]
Notice you don't have a space between the UUID and "none", so how about doing:
```
gksudo gedit /etc/fstab
```
And then put a space so it looks like:
```
# /dev/sda4
UUID=d58bf1cb-d27a-487d-b337-056767fd5ad6   none  swap   sw     0       0
```
Then do:
```
sudo swapon -a
free
```
And please post the output.

---

### Post by Bendihossan on 2009-02-11
Thanks for the quick response! The gap was just a copy and paste typo by me, sorry.

Output of blkid was:
```
/dev/sda1: UUID="06c0d619-e529-440d-bd5c-8fbf4721747e" TYPE="ext3" 
/dev/sda2: UUID="C090E58C90E5896C" LABEL="ACER" TYPE="ntfs" 
/dev/sda3: UUID="48EC1C11EC1BF840" LABEL="DATA" TYPE="ntfs" 
/dev/sda4: TYPE="swap" UUID="0eca6dc5-55eb-41df-8ae8-2974cbbe59c6" 
```

and output of sudo mkswap -U d58bf1cb-d27a-487d-b337-056767fd5ad6 /dev/sda4
```
Setting up swapspace version 1, size = 4038606 kB
no label, UUID=d58bf1cb-d27a-487d-b337-056767fd5ad6

```

and output of swapon -a
```
swapon: cannot canonicalize /dev/disk/by-uuid/d58bf1cb-d27a-487d-b337-056767fd5ad6: No such file or directory
swapon: cannot stat /dev/disk/by-uuid/d58bf1cb-d27a-487d-b337-056767fd5ad6: No such file or directory

```

output of free is identical to before.

---

### Post by caljohnsmith on 2009-02-11
OK, how about rebooting, and please post the output of:
```
sudo blkid -c /dev/null
sudo swapon -a
free
```

---

### Post by Bendihossan on 2009-02-11
> **caljohnsmith said:**
> OK, how about rebooting, and please post the output of:
```
sudo blkid -c /dev/null
sudo swapon -a
free
```

Think the above solved it!

```
steffy@bendihossan:~$ sudo blkid -c /dev/null
[sudo] password for steffy: 
/dev/sda1: UUID="06c0d619-e529-440d-bd5c-8fbf4721747e" TYPE="ext3" 
/dev/sda2: UUID="C090E58C90E5896C" LABEL="ACER" TYPE="ntfs" 
/dev/sda3: UUID="48EC1C11EC1BF840" LABEL="DATA" TYPE="ntfs" 
/dev/sda4: TYPE="swap" UUID="d58bf1cb-d27a-487d-b337-056767fd5ad6" 
steffy@bendihossan:~$ sudo swapon -a
steffy@bendihossan:~$ free
             total       used       free     shared    buffers     cached
Mem:       2066024     646212    1419812          0      14504     293548
-/+ buffers/cache:     338160    1727864
Swap:      3943948          0    3943948
steffy@bendihossan:~$ 

```

---

### Post by caljohnsmith on 2009-02-11
Looks like you should be all set now.

---

### Post by Bendihossan on 2009-02-11
Thank you for that. I'll play with it and test just to ensure it will be used when memory gets tight.

---

