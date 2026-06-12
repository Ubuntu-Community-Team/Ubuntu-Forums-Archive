---
title: "increase swap space"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by gkraju on 2009-08-17
i checked my swap space using top command  and it showed
Swap:        0k total,        0k used,        0k free,   391396k cached

how to increase swap space? 
thanks

---

### Post by rednano12 on 2009-08-17
```
sudo apt-get install gparted
```

Then run terminal and run this command:
```

sudo gparted
```

Then you can change it within there.

---

### Post by philcamlin on 2009-08-17
You can use the installer to resize partitions. You can use the live cd. You cannot change the start of a partition, just the end. You need to shrink the partition which comes before it, delete the swap and recreate it beginning at the newly created space.

so right now you have no swap at all 

goood luck

---

### Post by gkraju on 2009-08-17
> **rednano12 said:**
> ```
sudo apt-get install gparted
```

Then run terminal and run this command:
```

sudo gparted
```

Then you can change it within there.

i have gparted  
do i have to format a partition ?

---

### Post by Mauler5858 on 2009-08-17
If you have a partition you can use right off you can use the mkswap command to make a "swap filesystem" in the space.

From there if you want to test it, you can mount the space using the swapon command.  Dont forget to put it in your /etc/fstab file so it will persist a reboot.

---

### Post by kansasnoob on 2009-08-17
You'll need to use gparted (aka: partition editor) from the Live CD as all partitions must be unmounted to resize or move them. You'll also need to select "swapoff" on the swap partition.

**Note: after moving or resizing swap you'll almost cetainly end up in UUID hell - you'll likely lose the "quiet usplash" and the "persistance" of swapon at reboot.**

Give me a few minutes and I'll post the uuid fix here also.

---

### Post by PGScooter on 2009-08-17
just thought I would add that the following command is useful for seeing which swapfiles are currently being used:
```
cat /proc/swaps
```

---

### Post by kansasnoob on 2009-08-17
Assuming you are successful with the partitioning and now just need to straighten out the UUID problems from recreating or resizing SWAP.

We'll be working from terminal:

```
sudo blkid -c /dev/null
```


That will display something like this:

> /dev/sda1: UUID="5A3CAE183CADEEE7" TYPE="ntfs"
/dev/sda5: UUID="3f6a93da-cbc0-4203-92ce-42ff70394f0a" TYPE="ext3"
/dev/sda6: TYPE="swap" UUID="5b397135-2a82-4933-aefd-00d7ff23b413"
/dev/sda7: UUID="cb8d8925-8059-46bc-8312-9ce5f42afa91" SEC_TYPE="ext2" TYPE="ext3" 



The UUID #'s are in parenthesis. DO NOT include the parenthesis when you replace the UUID's in the following files! BTW the "-c /dev/null" is necessary because if you run blkid without options it reads from its cache file. If you've run it before and any partition has changed you'll get erroneous results.

Now:

```
cat /etc/fstab
```

You'll undoubtedly see that the UUID's for SWAP are different. Here I like to create a simple backup of the original /etc/fstab using copy-n-paste and either Abiword or Open Office so if I hose things I can put things back in their original state! Do NOT be concerned at this point if the partition #'s are different! DO NOT change a partition #! Change nothing but UUID's!

To edit that file:

```
gksudo gedit /etc/fstab
```

It's much, much easier to cut- copy-n-paste! Just be careful! And when you're done editing remember to click on Save, then go to File > Quit!

Now on to /etc/initramfs! Run:

```
cat /etc/initramfs-tools/conf.d/resume
```

That UUID should (but won't) match the UUID for SWAP in blkid so to edit:

```
gksudo gedit /etc/initramfs-tools/conf.d/resume

```


Again be sure to save > file > quit! Now one last important thing:

In terminal:

```
sudo update-initramfs -u
```

Be patient! It takes a minute or two to run! Wait until the command prompt (like lance@lance-desktop) shows up again!

You should now have "persistent" swap and a quiet usplash.

---

