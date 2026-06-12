---
title: "booting from different hard drive?"
date: 2010-04-13
forum: New to Ubuntu
---

### Post by kakashi_hatake on 2010-04-13
hey, me again, new to Linux. thanks for helping me solve my problems so far (and thank you ubuntu for being free). I wanted to know if you can install ubuntu on a small hard drive (4gb) and boot from it but save all extra things (programs, plugins, added components, ect) on a larger one. I realize this is *possible* but i wanted to know if you can make it so that any new things automatically get saved to the other hard drive? all ubuntu-only files and folders should stay in that hard drive but added things like compiz fusion go to the new one somehow. 

can it be done. I have a feeling its not very possible. oh well im up for the discussion.

thanks again everyone! :)

---

### Post by mick222 on 2010-04-13
The best way is to use a separate /home partition i have never tried this between two drives but it should work. When installing choose manual partitioning create a partition the on your first drive of type ext4 label it / create a partition on your other drive marked /home and a swap partition of about 2gb mark use these partitions . before you install you should see the changes accept them if your happy . That should do it but i would recommend using one drive if you can and making the root  "/" partition about 10gb

---

### Post by undecim on 2010-04-13
Check out 

[https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)

If you want to use two hard drives instead of a CD and a USB drive, you can use the USB Startup Disk Creator or Unetbootin on the small hard drive, then set up the larger one like the USB drive in the link above.

---

### Post by C.S.Cameron on 2010-04-13
It should work to make a ext2, ext3 or ext4 partition on the larger hard drive and name it casper-rw.
If you want a separate home partition create another ext partition and name it home-rw.

If you want persistence when booting the small hard drive press F6 and type <space>persistent

If you want persistence every time you boot the small hard drive you can modify the text.cfg file (usb-creator) or the syslinux.cfg file (UNetbootin) by adding the word "persistent" thus:

append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent

---

### Post by kakashi_hatake on 2010-04-14
Cool, thanks everyone. I'll try your suggestions on a computer I found. It seems almost anything is possible here!

---

### Post by cuberts on 2010-04-14
> **kakashi_hatake said:**
> hey, me again, new to Linux. thanks for helping me solve my problems so far (and thank you ubuntu for being free). I wanted to know if you can install ubuntu on a small hard drive (4gb) and boot from it but save all extra things (programs, plugins, added components, ect) on a larger one. I realize this is *possible* but i wanted to know if you can make it so that any new things automatically get saved to the other hard drive? all ubuntu-only files and folders should stay in that hard drive but added things like compiz fusion go to the new one somehow. 

can it be done. I have a feeling its not very possible. oh well im up for the discussion.

thanks again everyone! :)It depends, if youo want the full version of it, then you wont be able to do it obviously, but I think that it is possible, just there wont be much space for files either

---

### Post by egalvan on 2010-04-14
Broadly speaking (**which means that there *are* exceptions**)...

as long as the directory is *logically* mounted under /,
it does not matter where the partition is *physically* mounted.

Back in the "good old days", many Unix/Linux users used SCSI for the performance enhancements.
One enhancement allowed a large number of hard drives to be utilized.

It was not uncommon to see the system spread over 4, 5, or more hard drives.

The data lived on yet more hard drives.

It was possible to have upwards of 60 drives in a SCSI system.

For several years, my home server consisted of four SCSI drives for the OS (15K-RPM screamers, each on it's own channel),
and 12-16 PATA IDE drives (depending on my wallet) for the data.

So yes, it's absolutly possible to spread the OS out among more than one drive.

I really don't think that current Linux have lost this ability.

And using links can vastly simplify the set-up.

---

