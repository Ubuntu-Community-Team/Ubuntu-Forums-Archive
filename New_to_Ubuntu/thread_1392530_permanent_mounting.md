---
title: "permanent mounting"
date: 2010-01-28
forum: New to Ubuntu
---

### Post by 1991sudarshan on 2010-01-28
how to permanently mount the disk? i find it hard to give authentication to mount it every time!!!

---

### Post by warfacegod on 2010-01-28
You'll need to modify you /etc/fstab file.

---

### Post by konqueror7 on 2010-01-28
and just you will know how to do it, here's a [guide]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")...;)

---

### Post by muffinboy on 2010-01-28
I found a thread before on auto mounting NTFS disks with a program that edits fstab for you. 

Here's the link: [http://ubuntuforums.org/showthread.php?t=785263&highlight=ntfs+configuration+tool](http://ubuntuforums.org/showthread.php?t=785263&highlight=ntfs+configuration+tool)


:)

---

### Post by phillw on 2010-01-28
Hi,

can you state which disk / partition it is that you wish to automount and provide the contents of you /etc/fstab  file.

/edit - actually, there's an easier way !!

System --> Administration --> Synaptic Package Manager
install pysdm

You will then see Storage Device Manager in System --> Administration.  Select the disk / partition you want to auto-mount, click on "?Assistant" and put a tick in the box "The file system is mounted at boot time"  Click OK, then Click Apply, then Close.

No editing of /etc/fstab required :D

Regards,

Phill.

---

### Post by skymera on 2010-01-28
I prefer to edit fstab manually, it doesn't take much and the default file has some guidance already.

Mine is:

```
#WINDOWS
/dev/sdc1  /media/windows  ntfs-3g defaults  0  0 
```

That mounts SDC1 to /media/windows on every boot :) 

Try the GUI above. Foolproof ^^

---

### Post by 1991sudarshan on 2010-01-28
> **phillw said:**
> Hi,

can you state which disk / partition it is that you wish to automount and provide the contents of you /etc/fstab  file.

/edit - actually, there's an easier way !!

System --> Administration --> Synaptic Package Manager
install pysdm

You will then see Storage Device Manager in System --> Administration.  Select the disk / partition you want to auto-mount, click on "?Assistant" and put a tick in the box "The file system is mounted at boot time"  Click OK, then Click Apply, then Close.



No editing of /etc/fstab required :D

Regards,

Phill.

i am using ubuntu 9.10 there is no storage devive manger in system-->administration

---

### Post by muffinboy on 2010-01-28
> **Joeb454 said:**
> Ok, I decided to write this - because over the last week or 2 I've been seeing **a lot** of threads asking how to AutoMount drives in Ubuntu. Most of the time these also happen to be NTFS drives ;)

I know what it's like - I still dual boot too :) So anyway - here's how to do it the nice easy way :D



-------------------------------------------------------------------------

Fire up a terminal, to do this click **Applications > Accessories > Terminal**
Then type (or copy/paste) the following - **_1 line at a time_**```
sudo aptitude update
sudo aptitude install ntfs-config
```Ok so when that returns you to **user@pcname**, that should be it installed :)

Next, make sure you have **NO** drives mounted (they'll usually appear on your desktop). And then run the program from **Applications > System Tools**

**Note:** In Ubuntu 9.04 (Jaunty) it appears that the configuration tool has moved to **System > Administration**.

Enter your password when prompted - and then choose the drives that you want to be automounted. Click Apply.

Now simply make sure that "Enable Write Support for Internal Drives" and click OK.

Enjoy your automounted NTFS Drives :D

**Note:** If you want to undo this for whatever reason, StolenPie posted a walkthrough [later in the thread]("http://ubuntuforums.org/showpost.php?p=8221939&postcount=139") :) So kudos for that!

Try this.

---

### Post by 1991sudarshan on 2010-01-28
> **muffinboy said:**
> Try this.


but no such options available in System tools or system--> Administration

---

### Post by sisco311 on 2010-01-28
Click [here]("apt://ntfs-config") to make sure that it's installed.

Once it's installed you should find it under:
System -> Administration -> NTFS Configuration Tool


If it's not there, then press Alt+F2 and run:```
/usr/sbin/ntfs-config-root
```

---

### Post by DGortze380 on 2010-01-28
> **skymera said:**
> I prefer to edit fstab manually, it doesn't take much and the default file has some guidance already.

Mine is:

```
#WINDOWS
/dev/sdc1  /media/windows  ntfs-3g defaults  0  0 
```

That mounts SDC1 to /media/windows on every boot :) 

Try the GUI above. Foolproof ^^

I suggest using UUIDs when ever possible to avoid future issues.

---

### Post by phillw on 2010-01-28
> **1991sudarshan said:**
> i am using ubuntu 9.10 there is no storage devive manger in system-->administration


You need to install it ..

System --> Administration --> Synaptic Package Manager
install pysdm


Regards,

Phill.

---

