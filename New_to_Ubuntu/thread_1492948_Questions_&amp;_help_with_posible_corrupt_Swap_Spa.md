---
title: "Questions &amp; help with posible corrupt Swap Space"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by bamim2 on 2010-05-25
I have a dual boot PC; Windows XP & Ubuntu 9.10 on the same hard drive. I have another hard drive that I have been using to back up my system by cloning the whole hard drive to the other hard drive. That process has been working fine for over a year now. Since I had a good backup of things I decided to try some fancy partition moving stuff, I hosed up my hard drive & Grub stopped working. That, however, is not my problem.

Since I had a good copy of my hard drive, I deleted the partitions on the hosed up hard drive & cloned my back up hard drive image over the original (hosed up) hard drive & Grub worked again on the original hard drive. I am able to boot into Ubuntu & Windows again.

However, now my problem is that I can no longer clone my hard drive. The drive boots up in Windows & in Linux, but when it shuts down or reboots in Linux I get an error message about the swap slice having a problem. The message only comes up on the screen for a couple of seconds, so I can't provide any more info than that, unless somebody can tell me if there's a log I can read someplace. I've tried looking at dmesg, but I don't see any problems with my swap space in there. 

When I boot up, I've tried to enter the maintenance mode from Grub & see if I can fix things that way, but I get some similarly crazy swap space message that again, goes by very quickly & I'm not sure what to do. 

Should I run fsck to see if I can fix things? I've tried running fsck, but the message pops up to really try to discourage me asking if I'm sure I want to do that because running fsck on an active partition can cause serious damage. Since I've already done more damage than I want to, I didn't proceed. 

I would just leave it this way; Ubuntu seems to work fine & so does Windows, but it won't let me clone my hard drive anymore, so I can't back it up. 

I'm not sure if my explanation of things is very clear, so if I need to do a better job of explaining things please let me know. I'd really appreciate any help I can get on this. Thanks in advance.

---

### Post by BoneKracker on 2010-05-25
Try "reformatting" the swap partition.

Open a terminal and as root (or prepending "sudo" to each of the following commands):
```
swapoff <swap device name>
mkswap -L swap <swap device name>
swapon <swap device name>
```
(where "swap device name" is, for example "/dev/sda6" or whatever)

Really you ought to either enter single-user mode or boot from a CD before that, but if your system isn't heavily using swap at the moment, it will work fine without doing so.  If you suspect the partition may have bad blocks, you can use the "-c" option to the mkswap command (see the mkswap man page).

---

### Post by bamim2 on 2010-05-25
First of all, thank you for your quick response. I may need a little more clarification though. Shouldn't I see the swap space listed in the output of df? Here's df & it's not there. 

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5             55114296  14635960  37678612  28% /
udev                   1030892       476   1030416   1% /dev
none                   1030892       424   1030468   1% /dev/shm
none                   1030892       536   1030356   1% /var/run
none                   1030892         0   1030892   0% /var/lock
none                   1030892         0   1030892   0% /lib/init/rw

But, if I cat /etc/fstab I see it:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=8d579fcb-19c0-4c0c-85f7-fb367dc9323e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2c3db8d0-1f2a-4f8e-b83c-5d689df7a640 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Now what should I do?

---

### Post by BoneKracker on 2010-05-25
No, you won't see swap in df (because it is not "mounted" *per se*).

Here's your swap entry.
> # swap was on /dev/sda6 during installation
UUID=2c3db8d0-1f2a-4f8e-b83c-5d689df7a640 none swap sw 0 0

Per my guidance above, you would do this:
```
swapoff /dev/sda6
mkswap -L swap /dev/sda6
swapon /dev/sda6
```

As I said, you really ought to be in single user mode (or booted from a CD) when you do that (but in reality, you'd probably get away with not doing so).

To be absolutely certain that sda6 is still your swap device (although there is really no reason it wouldn't be unless you manually created another), you could use parted (or gparted) to check.  Alternatively, you could refer to the device by UUID or filesytem label (instead of device name) in your swapoff, mkswap, and swapon commands.
```
UUID="2c3db8d0-1f2a-4f8e-b83c-5d689df7a640"
swapoff -U $UUID
mkswap -U $UUID
swapon -U $UUID
```

Refer to the man pages for swapoff and mkswap (the man page for swapoff and swapon are the same man page).

That process (of "reformatting" the swap space), should resolve any problems stemming from corruption of the filesystem.

You could go one step further, and between swapoff and mkswap, actually delete and recreate the partition.  It is unlikely there are any problems with the partition or partition table, but this would resolve those.  Boot from CD if you do this, and we'll use gparted to make this easier for you).```
swapoff -U 2c3db8d0-1f2a-4f8e-b83c-5d689df7a640

<open up gparted>
<select the swap partition>
<delete the swap partition>
<apply the changes>
<select the empty space where the swap partition used to be>
<create a new partition there>
<create a swap filesystem on the new partition>
<apply the changes>
<close gparted>
<reboot into on-disk system>

```

After doing this, you should check the UUID of the new swap partition and make sure it is in /etc/fstab:
```
grep swap /etc/blkid
<copy and paste the new UUID where the old one was in /etc/fstab 
```
Then either reboot or run swapon.

---

### Post by bamim2 on 2010-05-26
Thank you for helping with this. When I entered "sudo swapoff /dev/sda6" I got an "invalid argument" error. I looked at the man pages & there are too many options for me to just try something, so I thought I'd better come back here & just ask for more help. :) What do you suggest?

---

### Post by bamim2 on 2010-05-27
If I do this:
sudo swapoff -U 2c3db8d0-1f2a-4f8e-b83c-5d689df7a640

I get this as a response:
swapoff: cannot find the device for 2c3db8d0-1f2a-4f8e-b83c-5d689df7a640

So, I guess that's telling me that my swap got moved? I'm still unclear as to what my next step should be. Any suggestions? 

Thanks...

---

### Post by BoneKracker on 2010-05-27
What is the output of
```
sudo blkid |grep swap
```

---

### Post by bamim2 on 2010-05-28
The output of 'sudo blkid |grep swap' yields: '/dev/sda6: TYPE="swap"' 

Thank you.

---

### Post by BoneKracker on 2010-05-28
> **bamim2 said:**
> The output of 'sudo blkid |grep swap' yields: '/dev/sda6: TYPE="swap"' 

Thank you.

Okay.  What happens when you try this (if you can, either boot from cdrom or drop to single-user mode first):
```
sudo swapoff /dev/sda6
mkswap -L swap /dev/sda6
swapon /dev/sda6
```

Also, after you've done that, what happens when you boot normally and then do:
```
sudo blkid |grep swap
```

---

### Post by bamim2 on 2010-05-28
I still get "invalid argument" with "sudo swapoff /dev/sda6"

---

### Post by bamim2 on 2010-05-28
Ok, hopefully this is actually correct. I looked a bit more closely at the man pages for swapoff & tried this:

sudo swapoff -a
sudo mkswap -L swap /dev/sda6
sudo swapon /dev/sda6

Then, I typed:
sudo blkid |grep swap
& got this output:
/dev/sda6: TYPE="swap" LABEL="swap" UUID="e50715d7-71b1-4532-9fc0-683719aaf643"

Does this look like my swap space should be correct now?

thanks.

---

### Post by BoneKracker on 2010-05-29
Yes.

I don't know why it gave you an error, but it looks like 'swapoff - a' worked.  Good that you're using the man pages. :)

Now, just replace the old UUID in your /etc/fstab file with the UUID you just listed (which is the UUID of the new swap filesystem you just created).  Then, you should probably reboot, and you'll be good to go.

I don't know how often your system normally dips into swap, but you might want to monitor it for a little while to see that it's actually able to use the swap.  You should be able to do that using the command 'vmstat' or by watching /proc/swaps (unless you're more comfortable with that performance monitoring thingy in Gnome or conky, which will give you a pretty graph).

---

### Post by bamim2 on 2010-05-29
I did modify the /etc/fstab file & rebooted & I'm up now. I didn't get any errors about my swap space. I was also able to clone my hard drive. My program that I use for cloning my hard drive (Acronis) doesn't work the way it used to for some reason, but I was able to 'manually' copy the slices. Since my hard drives a not exactly the same size my cloned disc has a little smaller swap space than my original drive. The original drive has a 2.31GB swap & the cloned drive has 1.6GB swap. 

I guess I'm good to go now. I really appreciate your help on this. Thank you!!
(How do I mark this as "solved"?)

---

### Post by BoneKracker on 2010-05-29
> **bamim2 said:**
> I did modify the /etc/fstab file & rebooted & I'm up now. I didn't get any errors about my swap space. I was also able to clone my hard drive. My program that I use for cloning my hard drive (Acronis) doesn't work the way it used to for some reason, but I was able to 'manually' copy the slices. Since my hard drives a not exactly the same size my cloned disc has a little smaller swap space than my original drive. The original drive has a 2.31GB swap & the cloned drive has 1.6GB swap. 

I guess I'm good to go now. I really appreciate your help on this. Thank you!!
(How do I mark this as "solved"?)

Glad it's working.  I think you just edit the original post, and add "[SOLVED]" to the title (I haven't used these forums in a long time).

---

