---
title: "Gparted Question"
date: 2011-05-10
forum: New to Ubuntu
---

### Post by TAspr on 2011-05-10
Hi folks,

I have loaded Windows 7 and Ubuntu 11.04 on the same box.  How do I take Linux off>  I think the best way to describe it is by a picture.  Do I still have to do some sort of FIX MBR?

---

### Post by alphacrucis2 on 2011-05-10
> **TAspr said:**
> Hi folks,

I have loaded Windows 7 and Ubuntu 11.04 on the same box.  How do I take Linux off>  I think the best way to describe it is by a picture.  Do I still have to do some sort of FIX MBR?

If you installed it using the dual boot method, then yes, just restore the windows MBR and reclaim the space allocated to ubuntu using the windows disk management applet after booting into windows.

---

### Post by TAspr on 2011-05-11
> **alphacrucis2 said:**
> If you installed it using the dual boot method, then yes, just restore the windows MBR and reclaim the space allocated to Ubuntu using the windows disk management applet after booting into windows.


So, in order;

1.Restore Windows MBR?  By what the Windows 7 start up CD?
2.Reclaim the space, as in delete the partitions?  Which ones do I delete specifically?

---

### Post by seawolf167 on 2011-05-11
Windows 7 Recovery Disks can be found [here]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/").  After running the appropriate commands to recover the MBR, simply boot up into  Windows and use the Windows partition editor to delete the Ubuntu  partition and then resize that now unallocated space into your existing  Windows partition.

```
bootrec /fixmbr
bootrec /fixboot
```

---

### Post by TAspr on 2011-05-11
> **seawolf167 said:**
> Windows 7 Recovery Disks can be found [here]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/").  After running the appropriate commands to recover the MBR, simply boot up into  Windows and use the Windows partition editor to delete the Ubuntu  partition and then resize that now unallocated space into your existing  Windows partition.

```
bootrec /fixmbr
bootrec /fixboot
```


I am dealthy afraid, the last time I tried this, I lost everything and the pc would not boot; go figure...

I will try it.

---

### Post by drs305 on 2011-05-11
You can try a different method before you delete Ubuntu.

Open a terminal and install lilo, then run the second command:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Don't pay attention to the terminal messages that lilo isn't fully configured. Reboot.

If Windows boots from its own bootloader, you can use Windows to delete the Ubuntu partition. If it doesn't, we can easily reinstall Grub from the LiveCD or you can use the Windows CD as described in previous posts.

---

### Post by TAspr on 2011-05-11
> **drs305 said:**
> You can try a different method before you delete Ubuntu.

Open a terminal and install lilo, then run the second command:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```Don't pay attention to the terminal messages that lilo isn't fully configured. Reboot.

If Windows boots from its own bootloader, you can use Windows to delete the Ubuntu partition. If it doesn't, we can easily reinstall Grub from the LiveCD or you can use the Windows CD as described in previous posts.


Thank you sir.

---

### Post by TAspr on 2011-05-15
> **seawolf167 said:**
> Windows 7 Recovery Disks can be found [here]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/").  After running the appropriate commands to recover the MBR, simply boot up into  Windows and use the Windows partition editor to delete the Ubuntu  partition and then resize that now unallocated space into your existing  Windows partition.

```
bootrec /fixmbr
bootrec /fixboot
```

Yes, but which partitons do I delete according to the diagram?  Do I go to the "COMMAND" prompt in windows to delete?

---

### Post by TAspr on 2011-05-15
> **drs305 said:**
> You can try a different method before you delete Ubuntu.

Open a terminal and install lilo, then run the second command:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```Don't pay attention to the terminal messages that lilo isn't fully configured. Reboot.

If Windows boots from its own bootloader, you can use Windows to delete the Ubuntu partition. If it doesn't, we can easily reinstall Grub from the LiveCD or you can use the Windows CD as described in previous posts.


I used the 

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

Now I am booting into windows, but which is safe to delete according to the picture?  Also, when you say recover, how is that done?

---

### Post by Hedgehog1 on 2011-05-15
You have three partitions to delete - two you can see, and one 'extended' partition you cannot see.

You can delete the 74.62 gig partition, and the 5.78 gig partition.

Once they are deleted, that space is still taken my an extended partition.  Right click on the new 'free space' and delete the that partition, too.


Finally, right click on the 'OS C:' partition and select 'extend'. You can then expand it to use all the space you have just made available.


***The Hedge***

:KS

p.s. Here is some examples from another PC, the partitions are not the same number but the IDEA is the same:

Remove Swap Partiton
[IMG]http://img97.imageshack.us/img97/4905/small56deleteswap.png[/IMG]
[IMG]http://img231.imageshack.us/img231/2992/small57freespace.png[/IMG]
Remove Ubuntu Partition
[IMG]http://img96.imageshack.us/img96/5986/small58deleteubuntu.png[/IMG]
Remove extended Partition
[IMG]http://img848.imageshack.us/img848/8053/small59deleteextended.png[/IMG]
Expand windows partition to use all the space
[IMG]http://img3.imageshack.us/img3/7880/small61extendwin7volume.png[/IMG]

---

### Post by TAspr on 2011-05-15
Wow, fantastic!  Thank you so much for this.  I was worried that I would not get it off.  Now are the Ubuntu partitions gone?

---

### Post by Hedgehog1 on 2011-05-15
Yes, they are completely gone and the space they were using is now re-allocated to windows.

It is as if Ubuntu ***was never even there***...

***The Hedge***

:KS

---

### Post by TAspr on 2011-05-15
Just absolutely beautiful!  Thank you very much.  Now on to my other box which has both of the operating systems...

---

