---
title: "Hd warning... then can't boot into Ubuntu"
date: 2011-07-01
forum: New to Ubuntu
---

### Post by Bupkus on 2011-07-01
Using 11.04 from recent install in 100GB partition dual boot w/ Windows 7.

All was good but suddenly after installing VLC (VideoLAN [http://www.videolan.org/vlc/#download)I](http://www.videolan.org/vlc/#download)I) began to receive system reports about problems with my hard drive. My hdd is a new SAMSUNG Spinpoint F3 HD103SJ 1TB. 

I tried to get more information about a so called "SMART" capability. I found nothing even on Samsung's website. (I used the link from Newegg.) Not knowing what else to do I opened Disk Management in Win7. 

My C: partition has the following status:
Healty(Boot, Page File, Crash Dump. Primary Partition)

My Ubuntu partition has this as status:
Healthy (Primary Partition) 100% Free. 
Now either Win7's Disk Management doesn't read usage because of the file system Ubuntu uses or the partition got hosed.

When trying to reboot into Ubuntu I'm offered a self repair option but it still can't boot. After posting this I'm going to try another reboot.

What really hurts is I'm using a password manager in both of my dual boot OSs and I may have a couple passwords in the Ubuntu OS file that's not in the Win7 file.

Is there a way I safely retrieve any files from my /home folder.
I don't think I have a separate /home partition as I used a default install config. DM however reports 4 partitions but I'm guessing the 4GB is a swap. I won't do that again.

Where should I go from here?

---

### Post by pawhtiobo on 2011-07-01
Hi,

Does Ubuntu start in recovery mode? If so, maybe you can use the **fsck** utility to see if you can correct the errors, other options are third party softwares to check HDD integrity... i prefer **spinrite** to do this job.

See ya...

---

### Post by Bupkus on 2011-07-01
I'm now replying to this thread using my Ubuntu boot.

How? I tried recovery mode and got:

Errors were found while checking the disk drive for /
Press F, I, S, M... etc [for brevity]
mountall: fsck / [362] terminated with status 4
mountall: Filesystem has errors: /

Then I noticed I had a 2GB USB drive plugged into a port.
I unplugged, restarted and ubuntu let me in.

It still takes a while to boot, does a harddisk check for errors, this last time gave me the above Fix, Ignore, S(?), M options and restarted. 

I don't feel safe with this so I did a backup of any files in my documents folder of which there were only 5. (New install).

Maybe it will recover, maybe it will die. I don't know.
It may still be looking for the removeable storage I pulled.
At least it loads. We'll see.

Thanks for the reply.

---

