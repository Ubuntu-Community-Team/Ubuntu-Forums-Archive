---
title: "My Windows partition is not showing up in the Places menu anymore"
date: 2010-11-30
forum: New to Ubuntu
---

### Post by diablo75 on 2010-11-30
I really don't know what to say about this.  I'm used to seeing some sort of shortcut in the Places menu for my Windows partition, that I can use to access it from Ubuntu.  It's simply missing.  I haven't done anything out of the ordinary except perhaps apply updates several days ago...

sudo fdisk -l shows:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13944   112005148+   7  HPFS/NTFS
/dev/sda2           13945      121601   864754822    5  Extended
/dev/sda3           22455      120951   791177152+  83  Linux
/dev/sda5           13945       22454    68356543+  83  Linux
/dev/sda6          120952      121601     5221093+  82  Linux swap / Solaris


So it SEE's it, as it always has, but something is not adding the shortcut to the Places menu...

---

### Post by wilee-nilee on 2010-11-30
Do I hear the refrain of a chkdsk in the background. Look in gparted and the info in the right click on that partition.

Personally it would be chkdsk /r do you have a disc if needed?

W7 is in my maverick drop down where yours is missing.

Could be another reason I will look around.

---

### Post by diablo75 on 2010-11-30
I'm running XP.  Haven't done a chkdsk on it recently, and it boots just fine so I'm going to make it check itself and see what happens.  Thanks!

---

### Post by wilee-nilee on 2010-11-30
> **diablo75 said:**
> I'm running XP.  Haven't done a chkdsk on it recently, and it boots just fine so I'm going to make it check itself and see what happens.  Thanks!

I looked on the web and didn't see much, I don't know the area of control of that drop down, but gconf-editor comes to mind. I would look through but I'm just to lazy.

---

### Post by diablo75 on 2010-11-30
Well I did a chkdsk on Windows, rebooted into it, then rebooted into Ubuntu which had it's own fsck pending, and I let it run.  None of it helped.  There is still no listing for the NTFS partition Windows sits on...

:confused:

---

### Post by psycho5 on 2010-11-30
You can use your fdisk -l and use the information to automatically put the entry for your windows partition in fstab. 

/dev/sda1 /mnt/Win7 ntfs-3g (mount options) dump pass

Not sure about the details but you can look up fstab in the community documentation, I think it's called "how to fstab"

If gparted can see the partition, try right click and mount it from there. See if the icon shows up.

---

### Post by philinux on 2010-11-30
> **diablo75 said:**
> Well I did a chkdsk on Windows, rebooted into it, then rebooted into Ubuntu which had it's own fsck pending, and I let it run.  None of it helped.  There is still no listing for the NTFS partition Windows sits on...

:confused:

What is listed under Places>Computer?

Check out gconf-editor Apps>Nautilus>Prefs

---

### Post by karthick87 on 2010-11-30
Well add your entry in fstab,Type blkid in terminal to get the UUID of your drive,

```
sudo blkid
```And then type df in terminal to see the mount point
```
df
```From the blkid result get the UUID of your windows partition and then edit fstab file
```
sudo gedit /etc/fstab
```For example:
**BLKID**
> karthick@Ubuntu-desktop:~$ sudo blkid
/dev/sda1: LABEL="Windows" UUID="EA04026F04023F57" TYPE="ntfs" 
/dev/sda2: LABEL="Disk" UUID="16b8e005-ba37-4212-986f-0ecd20243003" TYPE="ext3" 
/dev/sda5: LABEL="Datas" UUID="B630D52430D4EC7D" TYPE="ntfs" 
/dev/sda6: LABEL="Stuffs" UUID="D6E8DAE8E8DAC5C1" TYPE="ntfs" 
/dev/sda7: LABEL="Linux" UUID="ea6bb1fd-65fd-42f8-aa64-4a591993fe3b" TYPE="ext4" 
/dev/sda8: UUID="94f3a305-5cd8-4f4d-ba07-91c2a63d7498" TYPE="swap" 
/dev/ramzswap0: TYPE="swap" 
**DF**
> karthick@Ubuntu-desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda7             36326000  12738592  21742112  37% /
none                   1017880       292   1017588   1% /dev
none                   1024836       100   1024736   1% /dev/shm
none                   1024836       308   1024528   1% /var/run
none                   1024836         0   1024836   0% /var/lock
none                   1024836         0   1024836   0% /lib/init/rw
/dev/sda2             10072488   7335364   2225456  77% /media/sda2
/dev/sda5             40957684  33191684   7766000  82% /media/sda5
/dev/sda6             40957684  14602308  26355376  36% /media/sda6
Now if you want to add the SDA6 (NTFS) to FSTAB you should add the following in fstab

> UUID=D6E8DAE8E8DAC5C1 /media/sda6 ntfs    defaults,nls=utf8,umask=0222    0    0

---

### Post by diablo75 on 2010-11-30
> **philinux said:**
> What is listed under Places>Computer?

Check out gconf-editor Apps>Nautilus>Prefs

I've attached two screenshots to answer your questions.  One of them I used two screenshots to create one long image so you could see everything within the Preferences folder in gconf-editor.

---

### Post by diablo75 on 2010-11-30
> **karthick87 said:**
> Well add your entry in fstab,Type blkid in terminal to get the UUID of your drive,

```
sudo blkid
```And then type df in terminal to see the mount point
```
df
```From the blkid result get the UUID of your windows partition and then edit fstab file
```
sudo gedit /etc/fstab
```For example:
**BLKID**

**DF**

Now if you want to add the SDA6 (NTFS) to FSTAB you should add the following in fstab

I'm running into a slight problem.  df doesn't appear to show the ntfs partition like blkid does.  Here's the output:

```
/dev/sda1: UUID="2A10D03810D00D27" TYPE="ntfs" 
/dev/sda3: UUID="92916a37-406f-4a43-b6d2-0200d0275a16" TYPE="ext4" 
/dev/sda5: UUID="9408c45f-970c-408f-a313-9bd019ba963d" TYPE="ext4" 
/dev/sda6: UUID="4a9b3714-c90f-4a58-96f0-621aa84d26a8" TYPE="swap" 
user@user-desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5             67282996  25100568  38764604  40% /
none                   1024752       284   1024468   1% /dev
none                   1030348       164   1030184   1% /dev/shm
none                   1030348       208   1030140   1% /var/run
none                   1030348         0   1030348   0% /var/lock
/dev/sda3            778761552 185768868 553433832  26% /home

```

---

