---
title: "Permission problem with external hard drive"
date: 2011-05-28
forum: New to Ubuntu
---

### Post by Deedlit on 2011-05-28
I formatted a hard drive using gparted and ext3. It formatted just fine, I can access the drive, it mounts just fine. However, when I try to write to it, the drive says it is read only. Now, I could solve this simply by becoming root and working with it that way. I would like a more elegant and non repetitive solution. So, my research has shown me that I should use sudo chown, but when I try it tells me I have a "missing operand"

Any ideas?

---

### Post by yeats on 2011-05-30
Sounds like you've mounted it read-only.  You can verify this by doing:

```
mount
```

(feel free to paste the output here and people can help you troubleshoot).

> So, my research has shown me that I should use sudo chown, but when I try it tells me I have a "missing operand"

Can you paste the exact command you're trying?

---

### Post by Deedlit on 2011-05-31
Okay, here is the command I used

sudo chown /dev/sdg


and got this back: chown: missing operand after `/dev/sdg'

---

### Post by Deedlit on 2011-05-31
So, when I input the command "mount" this is what I got

>  mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/deedlit/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=deedlit)
/dev/sdg1 on /media/Piglet type ext3 (rw,nosuid,nodev,uhelper=udisks)
/dev/sdf1 on /media/37a7275f-68fb-4dfa-91b5-14d380515700 type ext3 (rw,nosuid,nodev,uhelper=udisks)


---

### Post by Deedlit on 2011-05-31
The drive in question is "Piglet"

---

### Post by yeats on 2011-06-02
> sudo chown /dev/sdg

Missing an operand indeed.  What you probably want is:

```
chown *<username>*:*<usergroup>* **/media/Piglet**
```

Where "*<username>*" is the user's name you want to give permissions for and "*<usergroup>*" is that user's group (no brackets in either case).  (In my case, it would be "yeats:yeats", for example).  You also want to add the permissions to the mounted device "/media/Piglet" rather than the raw device "/dev/sdg" (which wouldn't work anyway because it would need to be "/dev/sdg**1**").  

> /dev/sdg1 on /media/Piglet type ext3 (rw,nosuid,nodev,uhelper=udisks)

The "rw" means "read/write" so my original thought was wrong.  :-)

---

### Post by doas777 on 2011-06-02
but hold off on the Chowning for now.

It looks like your drive is EXT3,  so thats good.

what is the output of 
```
sudo ls -al /media/Piglet/
```?

always good to lookat your ownership/permissions before modifying them.

will this drive be used on other systems, or just this one?

---

### Post by Deedlit on 2011-06-02
> **doas777 said:**
> but hold off on the Chowning for now.

It looks like your drive is EXT3,  so thats good.

what is the output of 
```
sudo ls -al /media/Piglet/
```?

always good to lookat your ownership/permissions before modifying them.

will this drive be used on other systems, or just this one?

This is what came back when I put in your command.
> ls: cannot access /media/Piglet/: No such file or directory

Now, please note, it shows up in Place>Home Folder, so I don't know why it's not showing up.

Also this drive will be accessed by our entire home network which includes a Mac. (Which means I'm probably going to have problems when I get to that part, but one problem at a time)

---

### Post by doas777 on 2011-06-02
> **Deedlit said:**
> This is what came back when I put in your command.


Now, please note, it shows up in Place>Home Folder, so I don't know why it's not showing up.

Also this drive will be accessed by our entire home network which includes a Mac. (Which means I'm probably going to have problems when I get to that part, but one problem at a time)
ok, try mounting the drive and run the command again. its worrysome that the command failed though (it should have printed nothing if the folder already exists.) that kind of implies that it has never mounted correctly. 

as for whom else in the house uses it, your network sharing service (samba) will act as an intermedia and allow everyone access remotely. I was more asking if the ext HDD will get moved from PC to PC occasionally. if not, and since it is ext3, chowning it is probably not a big deal. just don't do it everytime you hook up to a new PC. that would be a sign that another approach is in order.

---

