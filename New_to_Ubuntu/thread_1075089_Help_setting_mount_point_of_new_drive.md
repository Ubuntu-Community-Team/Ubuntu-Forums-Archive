---
title: "Help setting mount point of new drive"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by eljikobie on 2009-02-19
Hey,

I got a new hard drive, installed it, and formated it ext2. Now I want to move the contents of my /home directory to the new drive and set it to mount itself as /home at boot. Can anybody please help me with this?

---

### Post by bodhi.zazen on 2009-02-19
First I would advise you use an journaled file system , such as ext3

Try this : [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Second, I advise you make it a data partition rather then a /home partition.

Mount is at say /mnt/data

Then use links : ln -s /mnt/data/music ~/music

and on ...

---

### Post by taurus on 2009-02-19
[http://www.psychocats.net/ubuntu/separatehome#usingnew](http://www.psychocats.net/ubuntu/separatehome#usingnew)

---

### Post by eljikobie on 2009-02-19
Thanks for the fast advice.

---

### Post by mttman on 2009-02-19
EDIT : Don't mind me, to slow i guess

I highly suggest you do backups of your stuff before you do this.

to do this you will need to mount in a neutral position first. So ```
> sudo mkdir /mnt/hdd2
> sudo mount /dev/hdb1 /mnt/hdd2
```
now we need to copy your home folder over so ```
cp /home /mnt/hdd2
```now we need to edit your fstab so that it will automatically mount your hdd to /home to do this we need to get your UUID for the drive so we ```
sudo vol_id /dev/hdb1 > /home/username/volid.txt
``` we now use the volume id to create a new fstab entry so ```
sudo nano /etc/fstab
```in the fstab make a new entry that looks like this ```
#/dev/hdb1
UUID=<contents of /home/username/volid.txt> /home    ext2    relatime   0   2
``` then save the changes (ctrl^X y [return] [return]) and restart

---

### Post by bodhi.zazen on 2009-02-20
@ [mttman]("http://ubuntuforums.org/member.php?u=336021")

Probably not the best to use the cp command, see the links we gave above for a discussion.

---

