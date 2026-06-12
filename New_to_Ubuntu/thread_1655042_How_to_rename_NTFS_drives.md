---
title: "How to rename NTFS drives?"
date: 2010-12-29
forum: New to Ubuntu
---

### Post by karthick87 on 2010-12-29
How to rename NTFS drives?
[IMG]http://i.imgur.com/uSXGK.png[/IMG]

---

### Post by mcduck on 2010-12-29
If you still have Windows on the computer, the easiest way is to set the disk labels in Windows.

Of course just creating a new directory inside /media, with the name you wish to use, and then configuring /etc/fstab file to mount your drive into that directory will do the trick as well.

(label, if one exists, are used for all drives that are automatically mounted. And the name of the mount point defines the name for drives that are configured in fstab)

---

### Post by Verbeck on 2010-12-29
in disk utility and gparted, there's a 'label' option
after you unmount the partition

---

### Post by theozzlives on 2010-12-29
From the Windows command prompt:
```
label c:(or other letter) <name>
```

---

### Post by vanadium on 2010-12-29
I guess you also could use Disk Utility, under System - Administration, to set labels.

From the terminal, you can do it using ntfslabel, part from ntfsprogs which you need to install first.

---

### Post by karthick87 on 2010-12-29
I have already checked Disk Utility..But those drives are named there,however it is not shown in nautilus i guess..
[IMG]http://i.imgur.com/Mo0v7.png[/IMG]

---

### Post by karthick87 on 2010-12-29
Bump....!

---

### Post by brookie on 2010-12-29
+1 for this:
> **Verbeck said:**
> in disk utility and gparted, there's a 'label' option
after you unmount the partition

gparted can do all this and it should be installed by default in 10.04. if not, install gparted
start gparted (system>administration>gparted, or applications>system tools>gparted

select the drive you want to work with in the upper right hand drop down menu

unmount the drive that you want to rename by right clicking it and select unmount.

right click the unmounted drive and select label

rename the label and click apply

you can do it all in gparted! :)

---

### Post by karthick87 on 2010-12-29
GPARTED shows labels for my NTFS drives..But it is shown in nautilus as **sda5** and [B]sda6   
[/B][IMG]http://i.imgur.com/7TLac.png[/IMG]

---

### Post by Morbius1 on 2010-12-29
I'm confused. Do you have entries in your fstab for these partitions?

Post the output of:
```
cat /etc/fstab
```
It looks like all you need to do is change the mountpoint.

---

### Post by nothingspecial on 2010-12-29
```
 sudo apt-get install ntfsprogs
```
```

sudo umount /dev/sda5
sudo umount /dev/sda6
```


```
sudo ntfslabel /dev/sda5 new_name
sudo ntfslabel /dev/sda6 new_name
```

---

### Post by karthick87 on 2010-12-29
> **Morbius1 said:**
> I'm confused. Do you have entries in your fstab for these partitions?

Post the output of:
```
cat /etc/fstab
```It looks like all you need to do is change the mountpoint.

```
karthick@Ubuntu-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc                                       /proc        proc      nodev,noexec,nosuid           0  0  
#Entry for /dev/sda7 :
UUID=ea6bb1fd-65fd-42f8-aa64-4a591993fe3b  /            ext4,acl  errors=remount-ro             0  1  
#Entry for /dev/sda2 :
UUID=16b8e005-ba37-4212-986f-0ecd20243003  /media/sda2  ext3      defaults                      0  0  
#Entry for /dev/sda5 :
UUID=B630D52430D4EC7D                      /media/sda5  ntfs-3g   defaults,locale=en_IN         0  0  
#Entry for /dev/sda6 :
UUID=D6E8DAE8E8DAC5C1                      /media/sda6  ntfs-3g   defaults,locale=en_IN         0  0  
#Entry for /dev/sda8 :
UUID=94f3a305-5cd8-4f4d-ba07-91c2a63d7498  none         swap      sw  
```

---

### Post by karthick87 on 2010-12-29
> **nothingspecial said:**
> ```
 sudo apt-get install ntfsprogs
``````

sudo umount /dev/sda5
sudo umount /dev/sda6
```
```
sudo ntfslabel /dev/sda5 new_name
sudo ntfslabel /dev/sda6 new_name
```

Tried it,but it din help me..

---

### Post by brookie on 2010-12-29
> **karthick87 said:**
> GPARTED shows labels for my NTFS drives..But it is shown in nautilus as **sda5** and [B]sda6   
[/B][IMG]http://i.imgur.com/7TLac.png[/IMG]

Okay, I see. Thought you meant actual ntfs hard drives, like usb drives. I have changed labels on external usb drives and such. 
So, sda5 and sda6 are ntfs partitions (not actual drives) and nautilus displays them as sda5/sda6.

Because I don't have any ntfs partitions, I don't know if you can change the label of a partition so that they are more user friendly in nautilus. Anybody?

---

### Post by nothingspecial on 2010-12-29
> **brookie said:**
> Okay, I see. Thought you meant actual ntfs hard drives, like usb drives. I have changed labels on external usb drives and such. 
So, sda5 and sda6 are ntfs partitions (not actual drives) and nautilus displays them as sda5/sda6.

Because I don't have any ntfs partitions, I don't know if you can change the label of a partition so that they are more user friendly in nautilus. Anybody?

Until you just said that, I was pretty sure you could......

......now.........

......Anbody??

---

### Post by Morbius1 on 2010-12-29
> #Entry for /dev/sda5 :
UUID=B630D52430D4EC7D  /media/sda5  ntfs-3g   defaults,locale=en_IN         0  0  
#Entry for /dev/sda6 :
UUID=D6E8DAE8E8DAC5C1  /media/sda6  ntfs-3g   defaults,locale=en_IN         0  0  OK, I would just create new mountpoints: 
```
sudo mkdir /media/Datas
sudo mkdir /media/Stuffs
```Then modify fstab to look like this:
> #Entry for /dev/sda5 :
UUID=B630D52430D4EC7D  [COLOR=Blue]/media/Datas [/COLOR] ntfs-3g   defaults,locale=en_IN         0  0  
#Entry for /dev/sda6 :
UUID=D6E8DAE8E8DAC5C1  [COLOR=Blue]/media/Stuffs[/COLOR]  ntfs-3g   defaults,locale=en_IN         0  0Now unmount your old partitions:
```
sudo umount /media/sda5
sudo umount /media/sda6
```And mount the new ones:
```
sudo mount -a
```You'll know instantly if it works.

---

### Post by karthick87 on 2010-12-29
> **Morbius1 said:**
> OK, I would just create new mountpoints: 
```
sudo mkdir /media/Datas
sudo mkdir /media/Stuffs
```Then modify fstab to look like this:
Now unmount your old partitions:
```
sudo umount /media/sda5
sudo umount /media/sda6
```And mount the new ones:
```
sudo mount -a
```You'll know instantly if it works.

It works..Thank you :)

---

