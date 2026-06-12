---
title: "Share Drive Samba Permission Problems"
date: 2008-07-01
forum: Networking &amp; Wireless
---

### Post by NoSkill on 2008-07-01
Hi,


      I have been trying to share a vfat internal harddrive over the network for a while with no success. I have the harddrive mounted in /mnt/Volume750 and my share in smb.conf is setup as such:

> [Volume750]
path = /mnt/Volume750
guest ok = yes
available = yes
browsable = yes
public = yes
writable = yes
create mask = 777
directory mask = 777

The problem is that i cannot write to the harddrive, I can see it fine using df -h :

> 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             290G  123G  153G  45% /
varrun               1014M  240K 1013M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   36K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
**/dev/sdb1             699G   16K  699G   1% /mnt/Volume750**
but cannot write to it, when i try I get the following error message from the windows box:

> Cannot copy test.txt: Access is Denied.

Any ideas would be appreciated.
Thank you

---

### Post by Iowan on 2008-07-01
You may need to set up the guest account.  Also, you might check the directory (mount)permissions.

---

### Post by NoSkill on 2008-07-01
The fstab line for my drive is :

> /dev/sdb1    /mnt/Volume750   vfat rw,user,auto,sync 0 2

and the guest account is setup, yet I have the same problem

---

### Post by Iowan on 2008-07-01
> **NoSkill said:**
> ... the guest account is setup, yet I have the same problemDo you have a "guest account= " line in **/etc/samba/smb.conf**?

---

### Post by NoSkill on 2008-07-01
> **Iowan said:**
> Do you have a "guest account= " line in **/etc/samba/smb.conf**?

yep :


>    guest account = nobody

---

### Post by dardack on 2008-07-01
is the /mnt/Volume750 writable by the usergroup?  IIRC samba can override the "local" file system permissions.  I had the same problems until i chmod u+w /mntdirectory. actually i may have made it writtable by all, just not executable by any.  Can't remember, anyways could try that.

---

### Post by NoSkill on 2008-07-02
> **dardack said:**
> is the /mnt/Volume750 writable by the usergroup?  IIRC samba can override the "local" file system permissions.  I had the same problems until i chmod u+w /mntdirectory. actually i may have made it writtable by all, just not executable by any.  Can't remember, anyways could try that.

I just tried that and still no dice, this is really starting to be very frustrating, any other ideas?

Thank you


EDIT: When i do a ls -l on /mnt i get the following 

> drwxrwxrwx 2 root root  4096 2008-06-15 10:51 External
drwxr-xr-x 2 root root 16384 1969-12-31 19:00 Volume750

should i be changing anything there?

---

### Post by dardack on 2008-07-03
> **NoSkill said:**
> I just tried that and still no dice, this is really starting to be very frustrating, any other ideas?

Thank you


EDIT: When i do a ls -l on /mnt i get the following 

> drwxrwxrwx 2 root root 4096 2008-06-15 10:51 External
drwxr-xr-x 2 root root 16384 1969-12-31 19:00 Volume750 

should i be changing anything there?

Oh root is the owner so chmod u+w won't work i believe.  Looks like to me anyone other than root isn't able to write to the directory.  Do: sudo chmod a+w /Volume750
and not trying to imply anything but am posting following incase you don't know: The first 3 characters are the permissions for
the owner of the file or directory. The next 3 are permissions for the group that the file is owned by and the final 3 characters define the access permissions for everyone not part of the group.  Afther that info you see who owns the directory/file in this case: Root owns the directory, so you need to make others be able to write to the directory not part of root (rwx = read/write/execute), than the next is the group the user belongs to (which root belongs to root).
(if you want all to be able to write, i may take executable off from non root though, that's just me)

---

### Post by Iowan on 2008-07-03
One option might be to "change owner" (**chown**) of Volume750 to the guest account (nobody).  Might need "force user=nobody".

---

### Post by remitaylor on 2008-07-16
bump - did this ever get figured out?

i've never had issues with Samba before but i recently put a fresh install of Hardy on a machine and I CANNOT for the life of me make the samba shares writable to guests.

i've tried dozens of tutorials.  i've tried things that've always worked before.  i've tried security = share types of setups and security = user types of setups.

i SIMPLY CANNOT get Samba shares to be writable to guests on Hardy.

it's making me crazy.

does anyone know a setup that works?  tia.

[ instead of continuing this thread, i thought my problem was deserving of its own thread: [http://ubuntuforums.org/showthread.php?p=5399670](http://ubuntuforums.org/showthread.php?p=5399670) ... i didn't mean to cross-post!  just decided to make a new thread, instead. ]

---

