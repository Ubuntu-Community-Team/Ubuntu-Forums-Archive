---
title: "Setting Permissions"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by mojo_man on 2009-01-10
Hi,

I used Mount Manager to mount my slave drive in UBUNTU but I cannot seem to delete any info as a regular user. It is mounted as /medoa/sdb1. Any suggestions?

Here is my fstab:

/dev/scd0       /media/sdb1     udf,iso9660     defaults        0       0
UUID=0102db20-0058-4df0-8a42-881a178e1d8c       /       ext3    defaults        0       1
UUID=cfd4b359-44e1-43d0-ac11-c34188930b3f       swap    swap    sw      0       0
UUID=57a5692e-62ea-4bbf-bbdc-660b4884c25b       /media/sdb1     ext3    users

---

### Post by taurus on 2009-01-10
I would edit the last line in /etc/fstab to this.

```
UUID=57a5692e-62ea-4bbf-bbdc-660b4884c25b /media/sdb1 ext3 defaults 0 2
```
Then, you can change the ownership of /media/sdb1 from root to your login name so you can write to it anytime you want.

Assuming your login name is mojo, 

```
sudo chown -R mojo:mojo /media/sdb1
ls -la /media/
```

---

### Post by Toshibawarrior on 2009-01-10
Try this....

Go to a terminal and type:

```
gksudo nautilus
```

That'll open a privileged nautilus window with which you'll access the hard drive you want to set the permissions.

Access the drive and right-click on a clear area. Go to **Properties** and then to the *Permissions* tab. 

Click on the drop-down lists and in *Owner* select your username, and select *Read and Write* on *File Access* and *Create and Delete Files* in *Folder Access*...do the same for *Group*...Then click on *Apply Permissions To Enclosed Files*...Click *Close*, restart and presto!...

If it didn't work or I wasn't clear enough let me know...If it worked, let me know too ;)!

---

### Post by mojo_man on 2009-01-10
> **taurus said:**
> I would edit the last line in /etc/fstab to this.

```
UUID=57a5692e-62ea-4bbf-bbdc-660b4884c25b /media/sdb1 ext3 defaults 0 2
```
Then, you can change the ownership of /media/sdb1 from root to your login name so you can write to it anytime you want.

Assuming your login name is mojo, 

```
sudo chown -R mojo:mojo /media/sdb1
ls -la /media/
```

So what did adding the 2 do?
When I rebooted my machine I noticed I could read/write and did not have to type that code part again. Was that code just so that I could read/write the drive in my existing session and on reboot it read the new fstab which granted me permission to read/write

---

