---
title: "No permission to create folder"
date: 2010-06-02
forum: New to Ubuntu
---

### Post by webwiller on 2010-06-02
Hi there!
I did a fresh install of ubuntu lucid 10.04. I partitioned my hdd with 2 primary partition, a "root" partition (/) a /home partition and an extended partition with a logichal /swap and a logichal /data partition.

Now I am trying to make folders in my /data partition for my docs, videos, music and stuff but I'm not able to make folders unless I'm superuser. How is this? How do I workaround it?

---

### Post by yetiman64 on 2010-06-02
For permanent write access for yourself to the /data partition one way would be to change its ownership from root:root to root:<your-username> (where your-username is actually the group with your-username as its name). To do this in terminal
```
sudo chown root:<your-username> /data
``` (don't include the < and >) this will give anyone you assign to your group the ability to write to the partition /data. But to be able to write here in terminal do 
```
sudo chmod 775 /data
``` as by default its permissions are 755.

Any folders or files created in the partition will be owned by their creator.

---

### Post by oldos2er on 2010-06-02
```
sudo chown -R user:user /data
``` where "user" is your username.

---

### Post by webwiller on 2010-06-02
```
christian@christian-laptop:~$ sudo chown root:christian /data
chown: impossibile accedere a `/data': Nessun file o directory
christian@christian-laptop:~$ 

```

which translated means: No file or directory

Why? Am I wrong?

---

### Post by webwiller on 2010-06-02
```
christian@christian-laptop:~$ sudo chown root:christian /data
chown: impossibile accedere a `/data': Nessun file o directory
christian@christian-laptop:~$ sudo chown -R christian:christian /data
chown: impossibile accedere a `/data': Nessun file o directory
christian@christian-laptop:~$ 

```

same answer. Could that be cause the folder is empty?

---

### Post by yetiman64 on 2010-06-02
> **webwiller said:**
> ```
christian@christian-laptop:~$ sudo chown root:christian /data
chown: impossibile accedere a `/data': Nessun file o directory
christian@christian-laptop:~$ 

```which translated means: No file or directory

Why? Am I wrong?

Seems as though its not mounted post output of 
```
cat /etc/fstab
```here to check.

---

### Post by webwiller on 2010-06-02
```
christian@christian-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=011e38d2-46e1-4edd-89aa-e23ed01bf8f6 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=60ed827f-4ae4-4fc1-970a-4ba15de8b66e /home           ext4    defaults        0       2
# /mnt/data was on /dev/sda6 during installation
UUID=a4167b19-0e1b-479d-bed3-2850001e104e /mnt/data       ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=261d069a-0904-460f-a1e5-2a47a1ddabf5 none            swap    sw              0       0
christian@christian-laptop:~$ 

```

---

### Post by yetiman64 on 2010-06-02
its on /mnt/data so change all references to /data to /mnt/data

---

### Post by webwiller on 2010-06-02
Is it /mnt/data I have to put in?

---

### Post by yetiman64 on 2010-06-02
No, in the previous instructions at the top, change the /data to /mnt/data as that is where /etc/fstab is telling me its already mounted.

---

### Post by RiceMonster on 2010-06-02
It's mounted at /mnt/data, not /data. If you want it in /data, change the entry in /etc/fstab to say /data

---

### Post by webwiller on 2010-06-02
Thx a lot Yetiman, sorted-out! ;)

---

### Post by yetiman64 on 2010-06-02
Goood to hear, :)

---

