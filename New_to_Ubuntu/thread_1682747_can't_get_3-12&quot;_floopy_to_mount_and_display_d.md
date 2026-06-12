---
title: "can't get 3-1/2&quot; floopy to mount and display different floppy contents"
date: 2011-02-06
forum: New to Ubuntu
---

### Post by s1baker on 2011-02-06
hi,
I am trying to get my drive for my 3-1/2" floppys mounted and I am having trouble. ( I know, 3-1/2" disks are outdated, but I have disks that have data on them that I am trying to pull off onto Ubuntu ) 
.
I have used this code :
```
sudo mount -o loop /dev/fd0
```
to mount a floppy that is in the drive, and it works ok. I get an icon on my deskktop that shows the icon with the label "floppy0",
and when I mouse click on the icon I can see the contents of the floppy. The problem is that when I insert another floppy into the drive and I mouse click on the icon, I get the previous listing of the floppy that was in the drive when the drive was mounted. Removing the floppy and re-inserting it does not work, still get the reading of the first floppy that was in the drive when the drive was mounted.
 Any help would be appreciated.

---

### Post by coffeecat on 2011-02-06
A couple of comments. Floppies are handled differently in Linux from  the way they are in Windows. You must unmount the floppy drive before you remove the floppy disc otherwise any writes may not be committed. By unmounting the first disk, you will get the contents of the second read when you mount it. 

Also, you may find this command to be better:

```
udisks --mount /dev/fd0
```It avoids having to invoke root privilege with sudo and you can right-click on the desktop icon to unmount it.

It's unfortunate that there's a long-standing and unresolved bug affected floppy handling in Ubuntu. You should be able to insert a disc and double-click on the floppy icon in Computer. This is what is meant to happen, but it doesn't work. Highly regrettable that the bug has been neglected, so one is reduced to using a terminal command. For convenience you could put the udisks command in a panel or desktop launcher if you are doing a lot of floppy work.

---

### Post by s1baker on 2011-02-06
I tried ```
udisks --mount /dev/fd0
```
and it worked. I could read the disk and load some of the text files on the disk into the editor, but when I go to 
unmount the disk by right clicking on the icon on the desktop, I get this pop-up window error message:

"Unable to unmount floppy0"
"umount: it seems /media/floppy0 is mounted multiple times"

---

### Post by s1baker on 2011-02-06
also, I failed to mention ( if it matters ) that these 3-1/2" floppy disks I want to be able to mount are windows XP vfat disks.

---

### Post by ron999 on 2011-02-06
> **s1baker said:**
>  but when I go to 
unmount the disk by right clicking on the icon on the desktop, I get this pop-up window error message:

"Unable to unmount floppy0"
"umount: it seems /media/floppy0 is mounted multiple times"

Hi
I think that you need to un-mount the floppy from command line too.
These are the commands that work for me:-
```
sudo mount /dev/fd0 /media/floppy0
```

```
sudo umount /dev/fd0
```

---

### Post by s1baker on 2011-02-06
thanks guys,
these commands in the terminal seem to work for me:

```

to mount:
udisks --mount /dev/fd0
or
sudo mount /dev/fd0 /media/floppy0

to unmount:
sudo umount /dev/fd0
```

although I'm using floppys less and less these days, it would be nice if they would fix the floppys where the floppys would auto mount and unmount.

---

### Post by coffeecat on 2011-02-06
This is relevant:

> **s1baker said:**
> "umount: it seems /media/floppy0 is mounted multiple times"

You'd probably used the mount command several times before the udisks one. Reboot to make sure everything is unmounted and then use the udisks command and then when you right-click to unmount it you won't get that error. Or at least that is my experience. Having used 'sudo mount', you have to use sudo to umount which is why using 'sudo mount' confuses things when you use udisks.

---

