---
title: "Move Data To Separate Partition"
date: 2010-06-22
forum: New to Ubuntu
---

### Post by opticyclic on 2010-06-22
After reading several posts, it seemed a good idea to install this time with a /home partition.
I like trying out different distros and a separate /home partition seemed to be the way to do it.

However, I quickly found that I actually quite like seeing the look and feel of the different distros as much as any other feature.
This led my shared /home partition to actually be an issue as (not surprisingly) when I installed 2 distros alongside each other all the GNOME settings etc conflicted.

I have decided that probably what I want is, folders like Documents/Music/Videos etc on a separate partition, but the home directory to be contained with the system partition of each distro.

How would I best go about doing this?

I think I need to do something like this:
[LIST=1]
[*]Copy my /home dir back to the system partition.
[*]Delete the settings (hidden folders) from the original /home
[*]Delete the Documents/Music/Videos etc from the copied /home
[*]Create Symlinks in the copied /home to the Documents/Music/Videos etc 
[/LIST]

Does that seem reasonable?
What do I have to do to make sure that the correct /home is picked up at boot/login?

---

### Post by Rubi1200 on 2010-06-22
This might help you regarding the process involved in creating a separate home partition "after the fact."

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by jerome1232 on 2010-06-22
You seem to have the right idea, it's what I do.

With that setup you don't even need seperate home partitions, just a seperate data partition and keep /home for your individual OS's on their respective root partitions.


I use the symlink method, works great. You might need to mount that data partition with a specific umask to keep permissions from becoming messed up. (maybe one of your os's doesn't use the same uuid for the first user, this will cause problems).

---

### Post by bodhi.zazen on 2010-06-22
If you use a separate /home partition , use a unique user name for each distro.

In general a /home partition is , IMO, less then ideal due to either conflicts in the config or . (dot) files or in uid. For example, the first user in Ubuntu is uid=1000 , while in Fedora the first user is 500 ...

As others have commented, I suggest you use a data partition and then sym link back to home.

Personally I use and old computer to share data via nfs , works great on a LAN.

---

### Post by oldfred on 2010-06-23
I just copied all my folders to a /data partition and then linked them.

How to Multi-boot (Maintain more then 2 OS) old grub
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)
Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

I have a bash file I use to create mount points, edit fstab, etc rename or remove default folders and auto link from my mount point /usr/local/fred/data into /home

I include this

mv Music oldMusic
etc 

first time I did each 
ln -s /usr/local/fred/data/Music
etc

Then I found I can do all in one line:
# All folders to be linked in /home are in /data as folders
for i in `echo /usr/local/fred/data/*`;do ln -s $i; done

---

### Post by opticyclic on 2010-06-30
Great! 
I now have achieved my goal.
I was a bit nervous at first but it all worked out fine.

I started off using the quoted guide, but found that the guide on the wiki that it links to was more successful
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

First I booted to a LiveUSB.
Then I mounted my current home to /old (remember my current home is in its own partition in this case) and my current / to /new
```
sudo mkdir /old
sudo mount -t ext4 /dev/sda8 /old
sudo mkdir /new
sudo mount -t ext4 /dev/sda7 /new

```

I then created my username in the home dir
```

cd /new/home
sudo mkdir myUser

```

I then copied the contents to this directory and renamed the old home dir to make sure it wasn't accidentally picked up when I logged back in .
```

sudo rsync -axS /old/myUser/. /new/home/myUser/.
sudo mv myUser/ myUser_b

```

For the next bit I needed to know the UUIDs
```

sudo blkid

```
I then modified my fstab to make sure that /home was no longer mounted on the separate partition and that the separate partition was now a data partition.
```

sudo mkdir /new/media/data
sudo cp /new/etc/fstab /new/etc/fstab.20100630
gksu gedit /new/etc/fstab

```
It used to say
```

# /home was on /dev/sda8 during installation.
UUID=9893d323-5290-4aba-aa72-7c79ebd4e14a /home           ext4    defaults        0       2

```
So I changed it to
```

# /home was on /dev/sda8 during installation. moved it back to sda8 and put in a data partition
UUID=9893d323-5290-4aba-aa72-7c79ebd4e14a /media/data           ext4    defaults        0       2

```
I then logged out of the LiveUSB and rebooted back in to my usual account.

I didn't like the way it was labelling the partition though so I modified it.
```

sudo umount /media/data
sudo e2label /dev/sda8 data
sudo mount /media/data

```

Since everything was working I renamed my folder back on the old home (now data) partition.
```

mv /media/data/myUser_b /media/data/myUser

```

Then I created the symlinks.
```

rm -rf Documents/
rm -rf Downloads/
rm -rf Music/
rm -rf Pictures/
rm -rf Videos/

ln -s /media/data/myUser/Documents/ Documents
ln -s /media/data/myUser/Downloads/ Downloads
ln -s /media/data/myUser/Music/ Music
ln -s /media/data/myUser/Pictures/ Pictures
ln -s /media/data/myUser/Videos/ Videos

```

Top Stuff!

---

### Post by opticyclic on 2010-07-02
I had to make a slight modification to enable the files be sent to the Trash and not be permanently deleted.

fstab:
```

# /home was on /dev/sda8 during installation. moved it back to sda8 and put in a data partition
UUID=9893d323-5290-4aba-aa72-7c79ebd4e14a /media/data           ext4    defaults**,uid=1000**        0       2
```

Create the trash folder and chown it
```

cd /media/data/
sudo mkdir .Trash-1000
sudo chown -R myUser:myUser .Trash-1000

```

---

