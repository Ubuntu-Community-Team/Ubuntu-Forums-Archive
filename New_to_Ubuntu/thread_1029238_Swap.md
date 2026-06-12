---
title: "Swap"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by Allin01 on 2009-01-03
[COLOR="Navy"][SIZE="5"]Hi,

I have installed ubunto. I have not created swap partition.

Now I need to have swap for hibernate!

What is the best way to do so?

And what is the optimum swap size?

Regards
[/SIZE][/COLOR]

---

### Post by nemilar on 2009-01-03
If you left some space available on your drive after partitioning (unused space), you can create a swap partition there.  If not, you'll have to resize.  Either way, I recommend you use gparted; if you have to resize, you'll need to download the gparted liveCD and boot it; if you still have some unpartitioned space left on your drive, you can do it from within ubuntu with the 'gparted' command.

gparted liveCD: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)


I hear recommendations usually on the order of swap = 2 * physical memory

which tends to be a good amount.  

Once you've created the swap partition, note what its device number is (e.g, /dev/sda5) and add the following line to your /etc/fstab file:

```
/dev/sda5 none                    swap    defaults        0 0

```

replacing /dev/sda5 with the appropriate device.  

Reboot.

---

### Post by Paqman on 2009-01-03
> **nemilar said:**
> 
I hear recommendations usually on the order of swap = 2 * physical memory

which tends to be a good amount.  


That recommendation tends to be overkill on a modern system. I would advise swap=RAM for hibernation, otherwise swap=1GB.

---

### Post by linux_tech on 2009-01-03
If you have a small amt of RAM, say 256MB, they recommend having a swap file of 2X = 512MB.  If you have more memory, say 2GB, then swap becomes less of an issue and 1X is more than enough (setting swap @ 1GB-2GB is plenty)

---

### Post by linux_tech on 2009-01-03
more info on swap files here-
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by Allin01 on 2009-01-03
[COLOR="Navy"][SIZE="4"]Is it better to have swap file or swap partition?[/SIZE][/COLOR]

---

### Post by taurus on 2009-01-03
> **nemilar said:**
> If you left some space available on your drive after partitioning (unused space), you can create a swap partition there.  If not, you'll have to resize.  Either way, I recommend you use gparted; if you have to resize, you'll need to download the gparted liveCD and boot it; if you still have some unpartitioned space left on your drive, you can do it from within ubuntu with the 'gparted' command.

gparted liveCD: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)


I hear recommendations usually on the order of swap = 2 * physical memory

which tends to be a good amount.  

Once you've created the swap partition, note what its device number is (e.g, /dev/sda5) and add the following line to your /etc/fstab file:

```
/dev/sda5 swap                    swap    defaults        0 0

```

replacing /dev/sda5 with the appropriate device.  

Reboot.

Shouldn't the entry for swap partition in /etc/fstab look like this?

```
/dev/sda5   none   swap   sw   0   0
```

---

### Post by nemilar on 2009-01-03
Actually, reading the manual for fstab, you are correct!  I just copied/pasted what I had... not sure why my fstab was written that way, I sure didn't put it like that...

Verrrrrrry interesting.  Thanks!!

> **taurus said:**
> Shouldn't the entry for swap partition in /etc/fstab look like this?

```
/dev/sda5   none   swap   sw   0   0
```

---

### Post by Paqman on 2009-01-03
> **Allin01 said:**
> [COLOR="Navy"][SIZE="4"]Is it better to have swap file or swap partition?[/SIZE][/COLOR]

Performance wise, I don't believe it makes any difference at all. A swap partition allows you to use hibernation, whereas a swap file won't. By default Ubuntu creates a swap partition.

---

### Post by Allin01 on 2009-01-03
> **Paqman said:**
> Performance wise, I don't believe it makes any difference at all. A swap partition allows you to use hibernation, whereas a swap file won't. By default Ubuntu creates a swap partition.

It says in swapfaqs "Add how to add the swap file to make Ubuntu hibernate to it "????

---

