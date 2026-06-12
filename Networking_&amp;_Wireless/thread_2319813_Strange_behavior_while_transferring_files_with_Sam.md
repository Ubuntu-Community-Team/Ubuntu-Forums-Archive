---
title: "Strange behavior while transferring files with Samba"
date: 2016-04-07
forum: Networking &amp; Wireless
---

### Post by lakeshore2985 on 2016-04-07
So this is really really weird stuff. I'll try and explain a little more in detail for you.

I have a home network comprised of multiple computers for testing, most of which have Linux distributions along with Samba and Samba client. The thing is whenever I perform file transfers between two Linux distros using samba, I can verify a considerable dip in file transfer speeds IF for example I'm transferring files that are NOT in the home folder or pertaining directory structure. For example if I'm transferring from a device that is in /media/ folder, it will slow down (on a 100mbit LAN, I am losing about 2mbps/sec average).

 These numbers are consistent and regardless of which Linux distro I'm running or computers I'm testing with. I wonder if it has anything to do with file systems and samba or something. It's pretty annoying.

Thanks!

---

### Post by papibe on 2016-04-07
Hi lakeshore2985.

A few thoughts.

While transferring file over the network, you have to consider if you are limited by HD read and write speeds. 

Are any of the file systems full, or close to full?

Is there any external USB disk mounted below /media ?

Are you using the discovery/automount features of Nautilus (file manager), or are you mounting the shares on a mountpoint?

What tool, or command are you using to measure the transfer?

Regards.

---

### Post by lakeshore2985 on 2016-04-07
Hi papibe!

No, it's not an HDD issue as I have been testing with several different hardware, all clearly bottlenecked by the 10/100mbit ports on my router.

No full/close-to-full file systems. They are testing machines.

No external USB devices attached.

Yes, using discovery/automount in Nautilus and Nemo.

The tools I'm using to measure network speeds are the default applications that come with the OSes. Nautilus, Nemo and Gnome's System Monitor (as well as router's dd-wrt).

PS: a little correction, the difference in transfer speeds on a 100mbit connection is of about 2MByte/second, and not 2mbps/sec as described in my original post, so pretty significant dip in transfer speed.

---

### Post by papibe on 2016-04-07
I see.

2MB/sec is closer to a wireless G connection. If one of the machines is a laptop, make sure the WiFI is off.

I'd start testing basic network transfers. First ping, back and forth, iperf both ways, and maybe even the combo dd/netcat ([here]("http://askubuntu.com/questions/7976/how-do-you-test-the-network-speed-betwen-two-boxes")'s how to use those tools. Use an actual file, maybe even the same you're transferring instead of /dev/zero).

Please post back the results of those tests.
Regards.

---

### Post by lakeshore2985 on 2016-04-07
Of course I'm not transferring over WiFi. Do you think I'd be asking if it were on a wireless connection?

As I said before, the speed "issue" only happens when transferring files that are NOT in the home folder, which is pretty indicative of something related to the operating system itself (or Samba), not the TCP protocol.

Besides, I've never said file transfer speeds are in the 2MB/s range... I said it is 2MB/s less, not the total throughput (if the total throughput is 11MB/s, then how would a wireless B/G/N connection handle 9MB/s?). It's just not feasible for wireless in any case.

---

### Post by Morbius1 on 2016-04-07
Just passing through but I don't know of anything personally that would explain your symptom but there really isn't enough information presented to know for sure.

Different partitions between /home/$USER and /media?
Different filesystems?
Different type of disk?

In your first post you mentioned:
>   if I'm transferring from a device that is in /media/ folder, it will slow down (on a 100mbit LAN, I am losing about 2mbps/sec average

And what "device" would that be?

Too many unknowns.

---

### Post by lakeshore2985 on 2016-04-07
> **Morbius1 said:**
> Just passing through but I don't know of  anything personally that would explain your symptom but there really  isn't enough information presented to know for sure.

Different partitions between /home/$USER and /media?
Different filesystems?
Different type of disk?

In your first post you mentioned:


And what "device" would that be?

Too many unknowns.

Exactly. Yes, I know it sounds crazy  lol, like really really strange but it does happen and it is consistent.  I was just hoping to see whether someone has a theoretical explanation  for this since it's not really a "problem" per se.

This strange  network performance behavior only happens with files outside the /home  folder and can be of various filesystems or disk types. In fact, I  noticed a more pronounced difference in speed when handling two distinct  filesystems (PC1 in NTFS and PC2 in EXT4). I wonder if this is because  the Samba server has to do some conversion or something? I don't know  much about how samba works yet, but I do know my Windows machines can  see my EXT4 partitions when shared over the network so there is that.

The  more consistent results I got so far happen when the /home folder is  not on a different partition from the root partition (where the OS is  installed). For example, I can do 10-11MB/s file transfers if the files  are in the /home/user/Downloads folder, but if that same file is  somewhere else outside /home (especially if in /media), or the /home  folder is in a separate partition then I can only do about 7-8MB/s or  sometimes even less.

Just a strange odd rather curious fact I'd  like to report here. I'll get gigabit capable equipment soon so the  performance difference should be even more pronounced.

---

### Post by Morbius1 on 2016-04-08
Still didn't provide enough information for anyone to comment. Especially what is under /media? How is it mounting?

The one exception is this comment:
>  I  noticed a more pronounced difference in speed when handling two distinct  filesystems (PC1 in NTFS and PC2 in EXT4)
R/W in NTFS is going to be slower than R/W in EXT4 - in Linux. 

To be more precise about that: An NTFS partition mounted in Linux will be slower than the exact same partition mounted in Windows. Linux mounts an NTFS partition using fuse which creates a "view" of the partition that makes it appear as though it has Linux ownership and permissions bits when in fact it has none. This is why you can't do a chown or chmod on an NTFS partiition. There are no Linux bits to change. This abstraction - if you want to think about it that way - comes at a cost.

---

### Post by lakeshore2985 on 2016-04-08
> **Morbius1 said:**
> Still didn't provide enough information for anyone to comment. Especially what is under /media? How is it mounting?

I don't know... what else would you like to know? Are there any commands you'd like me to copy/paste here? Like "*fdisk -l*", "*df -h*", "*lsblk*", dunno tell me something. As you can see I'm not exactly a "Linux expert".

All I can tell is that the /media partitions are not mounted in /mnt (cause I still don't see the point in mounting using /mnt), are not USB external devices and are not automatically mounted at boot (using fstab). They are EXT4 partitions I created for storage and sometimes to use as a separate /home partition. But they are not the same /root partition where the operating system is.

---

### Post by Morbius1 on 2016-04-08
Ah, so these are separate partitions ( maybe separate physical disks ? ) mounted using the file manager ( i.e., udisks2 ) under /media/$USER/Something.

Never noticed a speed degradation under those conditions but I don't know if it ever mattered to me. Why not create a test folder at say /media/Test:
```
sudo mkdir /media/Test
```
Change permissions to be available to everyone for this exercise:
```
sudo chmod 777 /media/Test
```
Share that folder however you are sharing things.

And see if you experience the same speed degradation. If you don' then it's not a home folder vs /media thing. It's a normal mount vs a udisks2 mount.

---

### Post by lakeshore2985 on 2016-04-09
> **Morbius1 said:**
> Ah, so these are separate partitions ( maybe  separate physical disks ? ) mounted using the file manager ( i.e.,  udisks2 ) under /media/$USER/Something.

I been saying that since post #7, but anyway no it's not a separate physical disk.

The type of "exercise" you suggested is exactly what I did the first time and getting the same odd results everywhere.

Anyway though there is one other variable I may have overlooked, which  is router overload; only very rarely do I bother to reboot my home  router (24/7 heavy duty), which may have a slight influence on its  hub-switch capabilities. Could also be my crappy 10-year-old machine  acting up on me again lol, dang! They drive me nuts!

> And see if you experience the same speed degradation. If you don'  then  it's not a home folder vs /media thing. It's a normal mount vs a  udisks2  mount.

Wait a minute... what is a "normal mount" and a "udisks2 mount" ? And why would that influence samba performance? 

Since there are so many different ways to mount partitions in Linux, things may get confusing sometimes.

---

### Post by Morbius1 on 2016-04-10
I can't reproduce your symptoms but what you might want to do is to post the output of the following commands so the folks here can see how you are set up:
```
sudo blkid -c /dev/null -o list
```
```
cat /etc/fstab
```
```
testparm -s
```
```
net usershare info --long
```

---

### Post by lakeshore2985 on 2016-04-10
Ok, but could you please explain what you mean by "normal mount" and "udisks2 mount"? I'm curious.

---

### Post by Morbius1 on 2016-04-10
There's two ways to mount a partition. One is the the traditional way through fstab or manually by invoking the mount directive like "sudo mount .......". The other way is the on-demand mechanism that Nautilus uses for all those partitions that are not declared in fstab. When Nautilus does that it essentially issues a udisksctl operative to mount them to /media/$USER/LABEL or /media/$USER/UUID. 

Shouldn't be any difference in the end except for the odd mount point and it should have no bearing on your symptom but it's the only thing different so far in your description of the problem.

---

