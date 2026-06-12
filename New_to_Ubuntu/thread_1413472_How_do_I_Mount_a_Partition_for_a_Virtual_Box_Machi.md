---
title: "How do I Mount a Partition for a Virtual Box Machine?"
date: 2010-02-22
forum: New to Ubuntu
---

### Post by mikodo on 2010-02-22
Hello everyone,

I have Virtualbox PURL installed and want to place a vm in a separate partition for Windows 7.

The partition I want to use; as seen in sudo blkid is:

/dev/sda9: UUID="c6280b6d-91cc-4158-a454-a102990948e0" TYPE="ext4

And seen in sudo ls -l /dev/disk/by-uuid as:

lrwxrwxrwx 1 root root 10 2010-02-22 11:20 c6280b6d-91cc-4158-a454-a102990948e0 -> ../../sda9


So, to make the mount point; Can I use:

sudo mkdir /media/virtualmachines

Then give full access to it:

sudo chmod 777 /media/virtualmachines

Then use /media/virtualmachines for my vdi files.

Would that be all I have to do?

If, I have it wrong, can you give me the proper commands?

EDIT   I have forgotten how to put the Code boxes in..sorry,

Thank you.

---

### Post by GrammatonCleric on 2010-02-22
So you want to move a single VirtualBox vdi into a new partition.   Do you want this new partition mount when you boot?  Your permissions (777) for are little on open...are you the only person requiring access to partition?

-GC

---

### Post by mikodo on 2010-02-22
I am the only person on my machine. Would the 755 be a safer way? I thought about it booting when I start my machine, but cannot decide if I should or not. I would be quite happy to just go into Virtual box and open the vm. I intend to use the same commands to have other distro's on other partitions too, so probably I will want to just choose which I want to go into after booting into Karmic and going into Virtualbox.

I am just trying to set up the path (mount point), for a new vm. Not move an existing vm. If that makes it clearer.

---

### Post by mikodo on 2010-02-22
I guess somewhere, somehow, I need to enter the UUID in the path. Can you help me out?

Mike

---

### Post by GrammatonCleric on 2010-02-22
Ok, if you are the only person that is access the new partition I would take ownership...  

```


sudo chown -R yourusername:groupname  /media/virtualmachines

i.e. 

sudo chown -R gcleric:gcleric /media/virtualmachines



```

Then set you file and directory permissions.  If you want to be the only person that has access then set the permissions to... 

```


sudo chmod -R 700 /media/virtualmachines  


```

The above says that only your account has access to read write and execute.  Everyone else has nothing. 

Making sense?

So you have the /dev/sda9 partition mounting when you reboot (i.e. added it to your /etc/fstab)?  

-GC

---

### Post by mikodo on 2010-02-22
Yes it makes sense. Thank you. I have NOT edited my etc/fstab yet though. I have run no commands yet, just have been reading and trying to figure how to set this up, instead of VirtualBox running in my /home as it is initially done on install.

---

### Post by GrammatonCleric on 2010-02-22
Just to be clear... you've mounted the new partition /dev/sda9 to /media/virtualmachines

```


i.e. 

sudo mount /dev/sda9 /media/virtualmachines


```


And also added the mount  statement to your /etc/fstab?  

```


 /dev/sda9  /media/virtualmachines           ext4    defaults 0       0


```


-GC

---

### Post by mikodo on 2010-02-22
> **GrammatonCleric said:**
> Just to be clear... you've mounted the new partition /dev/sda9 to /media/virtualmachines

```


i.e. 

sudo mount /dev/sda9 /media/virtualmachines


```


And also added the mount  statement to your /etc/fstab?  

```


 /dev/sda9  /media/virtualmachines           ext4    defaults 0       0


```


-GC

Sorry for the confusion. I have run nothing yet, I am just trying to figure out what I need to do to have a mount point for the new partition.

---

### Post by GrammatonCleric on 2010-02-22
No worries.    So in summary and in order... 

Mount the new partition...

```


sudo mount /dev/sda9 /media/virtualmachines


```Run a df -h in a terminal and make sure that the new partiton is mounted.

If it is...set ownership. 

```


sudo chown -R username:group  /media/virtualmachines


```Followed by permissions.

```


sudo chmod -R 700   /media/virtualmachines


```
Now[COLOR=Red]** test everything**[/COLOR] to make sure that it works as expected.  Once you are satisfied then added the new mount to your /etc/fstab

```


sudo nano /etc/fstab 

or

sudo gedit /etc/fstab 

for GUI.


```Now add the mount at the bottom of the fstab.

```

 /dev/sda9  /media/virtualmachines           ext4    defaults 0       0

```**[COLOR=Red]Only add it to the fstab once you tested things mounted. [/COLOR]**

-GC

---

### Post by mikodo on 2010-02-22
Thank you for the replies.

When I ran the first command I get the following:

mikodo@mikodo-desktop:~$ sudo mount /dev/sda9 /media/virtualmachines
[sudo] password for mikodo: 
mount: mount point /media/virtualmachines does not exist
mikodo@mikodo-desktop:~$

Should I run this first?

sudo mkdir /media/virtualmachines

---

### Post by GrammatonCleric on 2010-02-22
No problem... looks like you need to create the virtualmachines directory to  mount the partition to.. 


```


sudo mkdir /media/virtualmachines


```

Now run the mount command again. 

```


sudo mount /dev/sda9 /media/virtualmachines


```

You do have a partition called sda9 created already right?

-GC

---

### Post by mikodo on 2010-02-22
> **GrammatonCleric said:**
> No problem... looks like you need to create the virtualmachines directory to  mount the partition to.. 


```


sudo mkdir /media/virtualmachines


```

Now run the mount command again. 

```


sudo mount /dev/sda9 /media/virtualmachines


```

You do have a partition called sda9 created already right?

-GC

Yes, I have the partition. I will start with the command 
 
sudo mkdir /media/virtualmachines

and report back.

Thank you.

---

### Post by mikodo on 2010-02-22
Thank you,

I have the directory and ownership. How do I test now. 

mikodo@mikodo-desktop:~$ sudo mount /dev/sda9 /media/virtualmachines
[sudo] password for mikodo: 
mount: mount point /media/virtualmachines does not exist
mikodo@mikodo-desktop:~$ sudo mkdir /media/virtualmachines
mikodo@mikodo-desktop:~$ sudo mount /dev/sda9 /media/virtualmachines
mikodo@mikodo-desktop:~$ sudo chown -R mikodo:mikodo /media/virtualmachines
mikodo@mikodo-desktop:~$ sudo chmod -R 700   /media/virtualmachines
mikodo@mikodo-desktop:~$

---

### Post by GrammatonCleric on 2010-02-22
Excellent!  To test copy some data out there, make sure that you can read, write and modify and delete  data on the new partition. Create a new virtualbox vdi on it and delete it.. etc... 

Once you are satisfied add the entry to your fstab. =)

-GC

---

### Post by mikodo on 2010-02-22
mikodo@mikodo-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7              14G  5.9G  7.2G  45% /
udev                  2.0G  304K  2.0G   1% /dev
none                  2.0G  1.2M  2.0G   1% /dev/shm
none                  2.0G   88K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
none                  2.0G     0  2.0G   0% /lib/init/rw
/dev/sda8              84G   54G   27G  67% /home
/dev/sda9              60G  180M   57G   1% /media/virtualmachines
mikodo@mikodo-desktop:~$

---

### Post by mikodo on 2010-02-22
> **GrammatonCleric said:**
> Excellent!  To test copy some data out there, make sure that you can read, write and modify and delete  data on the new partition. Create a new virtualbox vdi on it and delete it.. etc... 

Once you are satisfied add the entry to your fstab. =)

-GC


Will do!

Thank you for holding my hand through all of this. I greatly appreciate your patience and expertise. 

Mike

---

### Post by GrammatonCleric on 2010-02-22
One last thing... this is more virtualbox vm base of advice.  When you build a vm using virtualbox make sure that you install the virtualbox guest tools to the vm.  You can download the latest and greatest version from... 

```


http://download.virtualbox.org/virtualbox


```

Find your version of virtualbox and download the "VBoxGuestAdditions" iso for your version.

-GC

---

### Post by GrammatonCleric on 2010-02-22
No worries.. glad to have helped!   =)

-GC

---

### Post by mikodo on 2010-02-22
> **GrammatonCleric said:**
> One last thing... this is more virtualbox vm base of advice.  When you build a vm using virtualbox make sure that you install the virtualbox guest tools to the vm.  You can download the latest and greatest version from... 

```


http://download.virtualbox.org/virtualbox


```

Find your version of virtualbox and download the "VBoxGuestAdditions" iso for your version.

-GC

Thanks for this also.

---

### Post by mikodo on 2010-02-23
Hello everyone,

Just a note to thank again, GrammatonCleric, and to report that everything went swimmingly with the vm on the partition.

Thank you.

EDIT   This was obviously my first effort at mounting a partition. I will configure the partitions differently later to allow for more.

See screenshot of gparted below:

---

### Post by GrammatonCleric on 2010-02-24
Excellent! Glad to help. =)

---

