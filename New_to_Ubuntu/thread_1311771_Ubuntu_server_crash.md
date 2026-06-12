---
title: "Ubuntu server crash"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by jhrach on 2009-11-02
I have been successfully running Ubuntu server V7.10 kernel 2.6.22-14 and tried to upgrade to Ubuntu server V9.10.  I am now getting the kernel panic error and unable to boot.

I have backed up my HD with Knoppix so I don't lose any data.  

I have been trying to repair the boot configuration without success and am convinced the only option is either to re-install Ubuntu server V7.10 or the new V9.10.

**Can I install Ubuntu server V9.10 over V7.10 without partitioning and erasing all the data files on the current OS?**

Thanks,
Joe

---

### Post by jbrown96 on 2009-11-02
It depends on how you have it configured. If you have /home on a separate partition, then you can keep that data, but you will need to choose the mount point for it during installation and DO NOT FORMAT it. 

If it's all one partition, then your options are significantly more limited. You could try to resize the current partition and squeeze ~3GB from it, then install 9.10 on it. In the new system you could mount your old system root parition (I'm going to call this A and the new one B), and delete everything you don't need like /bin, /usr, /lib, etc. and just keep the stuff you need. Then you could just add entries in /etc/fstab to mount those at boot. It will take some time, but will definitely work. I can give you some more specific instructions if that's what you want.

It would be a good idea to get in the habit of using separate partitions for /home and /var (if you run a web server). This could be a good time to set it up if you could get your data off the computer (to an external drive, CDs, etc.). If you decide to go this route, I would recommend reading up on LVMs, which could help depending on your storage needs.

---

### Post by jhrach on 2009-11-03
Thanks JBrown96.

I have 3 partitions sda1, sda2, and sda5.  sda5 is the LVM partition.  I'm pretty sure that /home is on the sda5 partition.  Can I reinstall V9.10 over the exiting sda1 partition without affecting the other partitions?

Thanks,
Joe.

---

### Post by jbrown96 on 2009-11-03
Shouldn't be a problem. choose manual partitioning. Not sure what is on your partitions. If you could mount your old / and post /etc/fstab that would allow me to give concrete recommendations. 
Here's what you would do in the partitioning menu.
I'm going to make some assumptions, so you will need to verify whether this is true. Is sda5 a LVM or an extended/logical partition? I would imagine its an extend partition (sda3 is probably the logical partition). You really need to confirm this before you go any further. 

Assuming that sda1 = old /, sda2 = swap??, and sda5 = /home. Delete sda1 and recreate it as ext4 with mountpoint /, recreate sda2 as swap, and edit sda5 choosing the mountpoint as /home and Do NOT format it.

Post your /etc/fstab and ```
sudo fdisk -l
``` if you still have questions/problems.

---

### Post by jhrach on 2009-11-04
Here's my HD configuration

sda1 start 1 - 31 Linux partition  
sda2 start 32 - 19457 Extended partition  
sda5 start 32 - 19457 Linux LVM partition 

I managed to back up all the folders to an external drive.

Do I continue with your directions to delete sda1, recreate sda2, and edit sda5?

Thanks for your help.
Joe.

---

### Post by jbrown96 on 2009-11-06
If you have backed up your data, then it's not necessary to save your current partition layout. It would probably be easier just to delete them and start over. You will also be able to take advantage of the speed improvements with ext4 if you create new filesystems. 

LVMs are really cool. I did some reading about them, but I've never had a reason to use them. That would probably be my recommendation to create one large lvm for the entire drive, then create two (you may want a 3rd for /var if you host a lot of web content) partitions inside. This will give you a lot more flexibility in the future if you need to change your partition sizes. You can also expand the LVM across disks, so if you ever get another hard drive, it can extend your current one. Again, do some reading on LVMs (I think that linux-mag.com and/or ibm.com had a really good report on LVMs a few years ago). Use ext4 for the partitions.

---

### Post by jhrach on 2009-11-07
Thanks for help in getting my server back up and running.  I followed your directions, installed the V9.10 server, and restored all the files from the crashed server.

Ubuntu rocks!

---

