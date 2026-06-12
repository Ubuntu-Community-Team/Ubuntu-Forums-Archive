---
title: "Cant Move Files To Trash"
date: 2010-06-30
forum: New to Ubuntu
---

### Post by opticyclic on 2010-06-30
I just moved my data in my home directory to a different ext4 partition.
[http://ubuntuforums.org/showthread.php?p=9532464](http://ubuntuforums.org/showthread.php?p=9532464)

Now when I try to delete any files from those directories I get the message:
"Cannot move file to trash, do you want to delete it immediately"

Why is that and how do I fix it?

---

### Post by ubunterooster on 2010-06-30
When you delete a file on an ext file system besides /home, it can not  send it to trash because there is no trash cam for it. So it asks if you  want to permanently delete it.

---

### Post by opticyclic on 2010-07-01
OK. Great.
So how do I create a trash can?

When I mount my NTFS drive I don't get this message.
When I show hidden files the NTFS drive has a .Trash-1000 folder, which I guess is the trash can.

Do I have to modify something in fstab to enable this feature?

---

### Post by nishant.singh28 on 2010-07-01
> **ubunterooster said:**
> When you delete a file on an ext file system besides /home, it can not  send it to trash because there is no trash cam for it. So it asks if you  want to permanently delete it.
Not true...I have 2 ext4 partitions besides home and / and I have Trash in all of them.

---

### Post by arrange on 2010-07-01
Can you try removing a file from the command line? Please provide the output too.```
touch ~/temp.file
gvfs-trash ~/temp.file
```(will create a temporary file in your home directory and then try to move it to trash)

---

### Post by opticyclic on 2010-07-02
If I run those commands in my home directory the file gets sent to the Trash.

However, if I try in the sub-directories (the ones that are symlinked to another ext4 partition) I get the following error:
```
Error trashing file: Unable to find or create trash directory
```

It seems like I need to create a Trash directory in that other partition, but I don't know how to do that.

---

### Post by opticyclic on 2010-07-02
A bit of searching found the answer :)

I changed my fstab entry
```

sudo cp /etc/fstab /etc/fstab.20100701
gksudo gedit /etc/fstab

```
```

# /home was on /dev/sda8 during installation. moved it back to sda8 and put in a data partition
UUID=9893d323-5290-4aba-aa72-7c79ebd4e14a /media/data           ext4    defaults**,uid=1000**        0       2
```

I then remounted it
```

sudo umount /dev/sda8
sudo mount -a

```
Then created the magic folder for the trash and chown'd it
```

cd /media/data/
sudo mkdir .Trash-1000
sudo chown -R myUser:myUser .Trash-1000

```
Magic :)

---

### Post by Rodu on 2010-07-10
> **opticyclic said:**
> A bit of searching found the answer :)

I changed my fstab entry
```

sudo cp /etc/fstab /etc/fstab.20100701
gksudo gedit /etc/fstab

``````

# /home was on /dev/sda8 during installation. moved it back to sda8 and put in a data partition
UUID=9893d323-5290-4aba-aa72-7c79ebd4e14a /media/data           ext4    defaults**,uid=1000**        0       2
```I then remounted it
```

sudo umount /dev/sda8
sudo mount -a

```Then created the magic folder for the trash and chown'd it
```

cd /media/data/
sudo mkdir .Trash-1000
sudo chown -R myUser:myUser .Trash-1000

```Magic :)


On a fresh install of 10.04, this worked for me as well but, I had to put ',user' instead of ',uid=1000' to mount the volume.
By putting ,uid=1000 it did not let me mount it complaining for bad options...

Putting ,user and creating the .Trash-1000 on the volume it went ok.

Now just to understand, as I am the only user on this machine that solution is fine. What if on the machine there would be more users? A .Trash-... for each user should be created?

thanks

---

