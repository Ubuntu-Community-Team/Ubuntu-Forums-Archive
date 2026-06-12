---
title: "Inconsistent drive/partition ID"
date: 2009-10-01
forum: New to Ubuntu
---

### Post by dgub on 2009-10-01
I am having problems with the way Ubuntu identifies the drives on my machine. I am using 8.04

I have 4 drives on this machine - 1 PATA and 3 SATA. XP is on the first SATA and Ubuntu on the last.

Doing an fdisk command the first SATA is listed as sda1 to 9.

I am also using Crossover on trial and for that to work I have to enter the drives into fstab. I then enter those drives into fstab and Crossover can see them ok.

Now after a reboot the first SATA has changed to sdb1 to 9 and of course Crossover can no longer see the drives.

How can I overcome this please or is it a bug? I did notice that when I was installing Ubuntu that the drive id's were not consistent



Thanks

---

### Post by cariboo on 2009-10-01
If you mount the drives by uuid in /etc/fstab, you shouldn't have a problem with drive labels changing. To find the uuid of a drive, open an Applications-->Accessories-->Terminal and type:

```
blkid
```

you should get an output that looks something like this:

```
blkid
/dev/sda1: UUID="1ea5424f-337d-4100-94dc-9afe7054c638" TYPE="ext4" 
/dev/sda3: UUID="62516864-235b-4b04-9b36-a7a3f05209c3" TYPE="ext4" 
/dev/sda5: UUID="a9578b07-df7d-4772-a5af-c18434499a1e" TYPE="swap" 
```

then instead of using /dev/sda1 as your drive, use something  like this to mount the drives:

```
# /home was on /dev/sda3 during installation
UUID=62516864-235b-4b04-9b36-a7a3f05209c3 /home           ext4    relatime        0       2
```

---

### Post by dgub on 2009-10-01
> **cariboo907 said:**
> If you mount the drives by uuid in /etc/fstab, you shouldn't have a problem with drive labels changing. To find the uuid of a drive, open an Applications-->Accessories-->Terminal and type:

```
blkid
```

you should get an output that looks something like this:

```
blkid
/dev/sda1: UUID="1ea5424f-337d-4100-94dc-9afe7054c638" TYPE="ext4" 
/dev/sda3: UUID="62516864-235b-4b04-9b36-a7a3f05209c3" TYPE="ext4" 
/dev/sda5: UUID="a9578b07-df7d-4772-a5af-c18434499a1e" TYPE="swap" 
```

then instead of using /dev/sda1 as your drive, use something  like this to mount the drives:

```
# /home was on /dev/sda3 during installation
UUID=62516864-235b-4b04-9b36-a7a3f05209c3 /home           ext4    relatime        0       2
```

Thanks

I will give that a try

---

### Post by dgub on 2009-10-02
I still cannot get this to work correctly. Probably a syntax error but not sure what.

I put in sudo blkid and the relative bit for the drive in question is

> /dev/sda5: UUID="7B8C348A22312740" LABEL="Photos" TYPE="ntfs" 
/dev/sda6: UUID="16F50C0F4BB5A37A" LABEL="Temp" TYPE="ntfs" 
/dev/sda7: UUID="0454C837000FA6ED" LABEL="Programs" TYPE="ntfs" 
/dev/sda8: UUID="32F14BE275A21C66" LABEL="Data" TYPE="ntfs" 
/dev/sda9: UUID="2FDD267671BD39A5" LABEL="Download" TYPE="ntfs" 

I edited fstab and removed by entries for sdb1 to 9 and inserted the following.

> UUID=7B8C348A22312740 /Photos 	ntfs 	realtime	0	2
UUID=16F50C0F4BB5A37A /Temp 	ntfs 	realtime	0	2
UUID=0454C837000FA6ED /Programs 	ntfs 	realtime	0	2
UUID=32F14BE275A21C66 /Data 	ntfs 	realtime	0	2
UUID=2FDD267671BD39A5 /Download 	ntfs 	realtime	0	2

Looking in /media the drives are listed they are listed but cannot access the folders.

Could someone put me right on this please.

---

### Post by dgub on 2009-10-02
> **dgub said:**
> I still cannot get this to work correctly. Probably a syntax error but not sure what.

I put in sudo blkid and the relative bit for the drive in question is



I edited fstab and removed by entries for sdb1 to 9 and inserted the following.



Looking in /media the drives are listed they are listed but cannot access the folders.

Could someone put me right on this please.

I am still not getting anywhere with this.

I realise that "realtime" should be "relatime" but from reading I think this only applies to Linux partitions so have removed it. Instead I have tried 

> 
UUID=7B8C348A22312740 /Photos 	ntfs defaults 0 0
UUID=16F50C0F4BB5A37A /Temp 	ntfs defaults 0 0
UUID=0454C837000FA6ED /Programs ntfs defaults 0 0
UUID=32F14BE275A21C66 /Data 	ntfs defaults 0 2
UUID=2FDD267671BD39A5 /Download ntfs defaults 0 0


That doesn't work either and it removes the partitions from Nautilus.

I would appreciate some direction on this please.

---

### Post by louieb on 2009-10-02
do you have directories made for the partitions to mount to? ie. /photos /temp...

Suggest you make your mount points inside the /media directory. Don't have to, but its the normal place. and by putting them there icons will show up on the desktop. 

i.e  make directory if not there. 
```
sudo mkdir /media/photos
```
then in fstab 
```
UUID=7B8C348A22312740 media/photos 	ntfs defaults 0 0
```

BTW: Liunx is case sensitive - if you capitalize  - do it the same in both places. - /media/[COLOR=Red]p[/COLOR]hotos is not the same as /media/[COLOR=Red]P[/COLOR]hotos

---

### Post by dgub on 2009-10-03
> **louieb said:**
> do you have directories made for the partitions to mount to? ie. /photos /temp...

Suggest you make your mount points inside the /media directory. Don't have to, but its the normal place. and by putting them there icons will show up on the desktop. 

i.e  make directory if not there. 
```
sudo mkdir /media/photos
```
then in fstab 
```
UUID=7B8C348A22312740 media/photos 	ntfs defaults 0 0
```

BTW: Liunx is case sensitive - if you capitalize  - do it the same in both places. - /media/[COLOR=Red]p[/COLOR]hotos is not the same as /media/[COLOR=Red]P[/COLOR]hotos

Thank you for that. Unfortunately it does not work. It creates another directory (/media/photos) but does not allow access to the existing /media/photos.

As it stands I can access all ntfs folders but relying on referring to them as sdb etc is not consistent. As soon as I start changing them to UUID I lose them.

---

### Post by louieb on 2009-10-03
> **dgub said:**
> As it stands I can access all ntfs folders but relying on referring to them as sdb etc is not consistent.

Its for that very reason Ubuntu changed from using /dev/sd@# to using the partitions UUID. (changed with v6.10) A partitions /dev/sd@# can change if boot order changes. But its UUID stays the same. 

>  As soon as I start changing them to UUID I lose them.

blkid will sometimes report a partitions UUID incorrectly. use 

```
sudo blkid -c /dev/null
```

to make it ingore its cache and report the correct UUID.

---

### Post by dgub on 2009-10-03
> **louieb said:**
> Its for that very reason Ubuntu changed from using /dev/sd@# to using the partitions UUID. (changed with v6.10) A partitions /dev/sd@# can change if boot order changes. But its UUID stays the same. 



blkid will sometimes report a partitions UUID incorrectly. use 

```
sudo blkid -c /dev/null
```

to make it ingore its cache and report the correct UUID.

Thanks 

Checked that and they are all correct.

I have been trying the NTFS configuration tool and although it worked by adding them to fstab I couldn't get it to work correctly. I think my fault. In the end in messing around with fstab I managed to corrupt the system and could not get it to boot even using the repair option. I had an earlier image I made with Acronis and restored that, then used the NTFS tool again. When that was in I edited fstab and replaced the /dev/sda6 with the UUID in the line that had been created. Now it seems to work correctly.

Thanks to everyone for the help and nudging me in the correct direction.

---

