---
title: "dual boot partitioning nightmare"
date: 2009-07-11
forum: New to Ubuntu
---

### Post by mystmaiden on 2009-07-11
I've been checking out virtualbox the last couple of days (thanks to all who helped me figure it out!) but decided instead to try a dual boot with windows xp and ubuntu 8.04. Everything went really well and I was feeling nice and geeky  until I got Ubuntu loaded and tried to update. The update manager went pretty much haywire - so badly that I decided just to reinstall Ubuntu. Much to my chagrin, I managed not to just wipe that drive and reinstall Ubuntu, instead I managed to get 2 copies of Ubuntu (or at least one full and one partial, as soon as I realized what had happened I stopped the second install). 

Now when I boot it shows two instances of Ubuntu and Windows xp.

fdisk -l net this:

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1940    15583018+   7  HPFS/NTFS
/dev/sda2            1941        7474    44451855    5  Extended
/dev/sda5            7216        7474     2080386   82  Linux swap / Solaris
/dev/sda6            1941        6993    40588159+  83  Linux
/dev/sda7            6994        7215     1783183+  82  Linux swap / Solaris

What would be the best way to fix this little gem? I'm entirely open to suggestions!
Also before I started all this I used simple backup - can I use it to restore any or all of my linux stuff now that the system has changed?

Thanks!
myst

---

### Post by Bradtek on 2009-07-11
You may aswell start again with Ubuntu install but this 
time when it comes to partitioning use MANUAL.

Then delete the linux and linux swap partitions.

Once you have done that you will have ONE unused free space

Assuming you want 1 partition for / and /home combined

Creat ONE EXT3 (or EXT4) Partition, Mount Point / 
leaving enough free space for a Swap Area

Apply etc

Creat Swap Area
Apply etc

---

### Post by mystmaiden on 2009-07-11
I did try to do that but it said one was in use and did not give me a delete option (greyed out) for the swap partitions.  I'll definitely try again and post my results

thanks
myst

---

### Post by ajgreeny on 2009-07-11
Depending on your hardware and amount of ram, you may be able to get to the partitioning stage of install and just unmount the swap partitions, as this is why the delete option was not available.  I'm not absolutely sure if it is possible at that point of the install, but you can do it easily in terminal in any case with ```
swapoff -a
```I am not sure if it needs sudo, but try it out.

You can also run gparted from the live CD, right click and choose swapoff from the context menu that appears there.  Then go ahead and delete the swap partitions and reinstall on the free space.

---

### Post by nothingspecial on 2009-07-11
You have to do the partitioning from the live cd.

You cannot partition a mounted drive.

---

### Post by mystmaiden on 2009-07-11
Thanks everyone, what I wound up doing was booting windows and deleting the partitions with the windows partitioner. I tried doing it another install of Ubuntu then, and it was still trying to put hardy on a little piece of a partition. A foray into manual partitioning proved to me I am simply not knowledgeable enough for that yet. I solved the entire thing by just loading Ubuntu as the only os for now. I learned a lot with this exercise but I've got a long way to go yet.

thanks again :)
myst

---

### Post by LewRockwell on 2009-07-11
proper partitioning is important to efficient operations, especially when it comes to storing important data and performing back-ups/images/clones/etc

.

---

### Post by mystmaiden on 2009-07-12
I'm learning a bit more with each passing hour how accurate that is Lew! 

My computer has been running a bit oddly, so I checked gparted, and sure enough the partitioning is still doesn't look right, even after doing the regular install.

Filesystem        Mountp.            Size                      Used        Unused

/dev/sda1 ext3         /         55.27GiB      16.44       38.83 GiB boot
/dev/sda2 extended               1.98           --         --   
/dev/sda/5 linux swap            1.98     


/dev/sda2 needs a boost I think. Could someone tell me what the right amount of space for it would be?

Grub is still showing two instances of Ubuntu as well, but I think there is actually only one now.

And is it possible to snag some of my settings and such from the Simple Backup file I stashed on my external before all this started? I haven't tried yet because I've had so much craziness going on otherwise, I didn't want to further upset a delicate balance.

---

### Post by egalvan on 2009-07-12
a screen shot of gparted would help us visualize the layout.

also a repeat of your

```
sudo fdisk -l
```

and post in inside "code" tags to make it a little easier to read.

And how much RAM does your machine have?

---

### Post by mystmaiden on 2009-07-13
Hope fully this will work - 

[IMG]http://i18.photobucket.com/albums/b134/mystmaiden/partitions.jpg[/IMG]

```
 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7215    57954456   83  Linux
/dev/sda2            7216        7474     2080417+   5  Extended
/dev/sda5            7216        7474     2080386   82  Linux swap / Solaris 
```


I have a little over 700 mb of ram, I can never remember the multiples than ram sticks come in.

Thanks
myst

---

### Post by Elfy on 2009-07-13
Looks ok to me - sda2 is the extended holding your swap partition (sda5) - size of that is ok given your RAM. The other partition sda1 is your actual installed ubuntu.

If grub does infact show your old install it will be at the bottom - if however you are referring to the fact you have 2 lines at the top before the memtest option - that is normal. The first line boots your normal install, the second is the recovery option.

---

### Post by mystmaiden on 2009-07-13
Nope there are 4 lines on grub before the memtest option

I thought the extended partition should have more space included on it some how, instead of just a gig or two.

thanks

myst

---

### Post by Elfy on 2009-07-13
> Nope there are 4 lines on grub before the memtest optionkernel updates they are, for there to be a previosu install there it would be seperated out and referenced similar to "Previous installs on /dev/sdxy"

---

### Post by mystmaiden on 2009-07-13
hmm okay, well they say exactly the same thing as the first two and appeared when I accidentally added the second Ubuntu so I thought I'd check. 

myst

---

### Post by Elfy on 2009-07-13
If you want to be sure - run this in a terminal, post it here and soemone will lokk at it :)

```
cat /boot/grub/menu.lst
```

---

### Post by mystmaiden on 2009-07-14
Forestpixie, thanks much  :)

```
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=918b0032-3c32-430f-8679-fb329bcb288d ro single
initrd        /boot/initrd.img-2.6.24-24-generic

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=918b0032-3c32-430f-8679-fb329bcb288d ro quiet splash
initrd        /boot/initrd.img-2.6.24-23-generic
quiet

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=918b0032-3c32-430f-8679-fb329bcb288d ro single
initrd        /boot/initrd.img-2.6.24-23-generic

title        Ubuntu 8.04.3 LTS, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

```

---

### Post by mikechant on 2009-07-14
Your print of menu.lst looks truncated - you said you had four entries before the memtest and there are only two and a half!
  
Anyhow from what is there it seems pretty clear you have two entries for Kernel 2.6.24-24, one normal and one recovery mode, then two more entries for kernel 2.6.24-23, and all four entries relate to a single install and are OK.

---

### Post by mystmaiden on 2009-07-15
that's good news, thanks for having a look at it mikechant. I appreciate it

myst

---

