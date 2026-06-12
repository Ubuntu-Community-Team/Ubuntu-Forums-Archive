---
title: "System restore in Ubuntu 9.10"
date: 2010-03-25
forum: New to Ubuntu
---

### Post by BurKaBU on 2010-03-25
Hi, with a lot of reading and help from this forum I finally
have my Ubuntu 9.10 working... THANKS!

After browsing these forums I have seen some very interesting setups in different desktop enviroments and addons that I'd like to try.

The thing is I'm very scared of messing up my Ubuntu, I've worked long and hard to get it working.
When I visited a friend of mine over a year ago he showed me how simple it it was to backup Ubuntu.
Just plug in the USB and choose "backup" in a meny, and he could alway revert back just by booting into failsafe and choose "revert" no matter how bad he messed up.

And knowing myself I KNOW I'm going to mess something up when I
try out the different setups :)
The thing is that I cant find the backup-button in any of my menus and my friend have stopped using Ubuntu and says he does not remember >:(.

So any help would be much apreciated

ps. Ive read a few treads about backups, but none seem to work they way I want/remember.

---

### Post by undecim on 2010-03-25
I don't know how he set up the backup script. The only backup setup I have a lot of experience with is rsync, which isn't as user-friendly as what you're describing. I have seen many people recommending Clonezilla.

But I can tell you that trying out differenct desktop environments shouldn't hurt your installation. Just make sure that you install them from the Software Center or by using "apt-get" or "aptitude" in the terminal.

---

### Post by BurKaBU on 2010-03-25
> **undecim said:**
> I don't know how he set up the backup script. The only backup setup I have a lot of experience with is rsync, which isn't as user-friendly as what you're describing. I have seen many people recommending Clonezilla.

But I can tell you that trying out differenct desktop environments shouldn't hurt your installation. Just make sure that you install them from the Software Center or by using "apt-get" or "aptitude" in the terminal.

Ok, so as long as I use the software center I can never mess up my pretty Ubuntu? :)

---

### Post by lidex on 2010-03-25
> **BurKaBU said:**
> Hi, with a lot of reading and help from this forum I finally
have my Ubuntu 9.10 working... THANKS!

After browsing these forums I have seen some very interesting setups in different desktop enviroments and addons that I'd like to try.

The thing is I'm very scared of messing up my Ubuntu, I've worked long and hard to get it working.
When I visited a friend of mine over a year ago he showed me how simple it it was to backup Ubuntu.
Just plug in the USB and choose "backup" in a meny, and he could alway revert back just by booting into failsafe and choose "revert" no matter how bad he messed up.

And knowing myself I KNOW I'm going to mess something up when I
try out the different setups :)
The thing is that I cant find the backup-button in any of my menus and my friend have stopped using Ubuntu and says he does not remember >:(.

So any help would be much apreciated

ps. Ive read a few treads about backups, but none seem to work they way I want/remember.

Go to your Software Center, click the "System" icon and search "backup". You will find various utilities for backing up/restoring your files. Simple Backup, Lucky Backup, Back in Time, etc. Those are all relatively user friendly and I know Simple Backup adds an entry to your Administration menu and allows to backup to an external drive. I would also recommend a separate /home partition:
[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by Paddy Landau on 2010-03-25
> **BurKaBU said:**
> Ok, so as long as I use the software center I can never mess up my pretty Ubuntu?
Well, nothing is certain in this life. But, I can tell you that I've installed (and uninstalled) lots of programs, both through Synaptic Package Manager and through downloading .deb files from trusted sites. None of them has ever messed up my Ubuntu.

The good thing about the way that Linux works is that programs install in their own locations, and run by themselves. They don't have that "spaghetti" involvement that Windows seems to have with its registry.

*EDIT* And I wholeheartedly agree that [CloneZilla]("http://clonezilla.org/") is the best way I've found to back up and restore a partition -- even Windows, which has been of great help when my kids have got a virus.

---

### Post by BurKaBU on 2010-03-25
> **lidex said:**
> Go to your Software Center, click the "System" icon and search "backup". You will find various utilities for backing up/restoring your files. Simple Backup, Lucky Backup, Back in Time, etc. Those are all relatively user friendly and I know Simple Backup adds an entry to your Administration menu and allows to backup to an external drive. I would also recommend a separate /home partition:
[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

I do have a separate /home partition (not sure how it will help me if my system crashes though :P) and I'll look into Simple backup, tnx.

> Well, nothing is certain in this life. But, I can tell you that I've installed (and uninstalled) lots of programs, both through Synaptic Package Manager and through downloading .deb files trusted sites. None of them has ever messed up my Ubuntu.


Sounds great :)

---

### Post by Doctor Mike on 2010-03-25
> **BurKaBU said:**
> I do have a separate /home partition (not sure how it will help me if my system crashes though :P) and I'll look into Simple backup, tnx.



Sounds great :)Another option is to create images of your Ubuntu partitions. I have dual boot with xp and run macrium reflect (free version) from within windows to create and restore images. Good thing too because I killed a lot of installs, but I was trying to push the limit. I keep one happy, dust free copy available for quick recovery at any time. There are open source versions, but what I've seen looks more complicated. Still looking though.

---

### Post by BurKaBU on 2010-03-25
> **Doctor Mike said:**
> Another option is to create images of your Ubuntu partitions. I have dual boot with xp and run macrium reflect (free version) from within windows to create and restore images. Good thing too because I killed a lot of installs, but I was trying to push the limit. I keep one happy, dust free copy available for quick recovery at any time. There are open source versions, but what I've seen looks more complicated. Still looking though.

This sounds very promising as well since I dual boot with XP, tnx :D

---

### Post by Doctor Mike on 2010-03-25
> **BurKaBU said:**
> This sounds very promising as well since I dual boot with XP, tnx :Dcool it only takes me 12 minutes to back up and about twenty to restore (with verification) have fun breaking you install cause now you can break it as many times as you want. Oh, one hint though... get everything setup the way you want it first... email etc. so you don't have to plug it all back in later.

---

### Post by jromer on 2010-03-26
I dual boot xp and Ubuntu and use Clonzilla to backup. It creates images of all partitions and the MBR. You can restore the whole HD or one or more of the partitions. I've restored many times without a problem. It's my recommendation.

---

### Post by amsterdamharu on 2010-03-26
Ubuntu can be backed up by simply copying the files. No system files that need special place on harddisk.
The boot partition can be backed up with a tool called dd.
You want to back up your system so no need to copy your home partition, the home partition has files you worked on yourself like documents and pictures you took. They are much more importaint than your system and should be backed up to CD or something.

Here is how to back up your system:

Make a bootable usb stick, I use tiny core linux.

To back up your mbr and partition tables:
```

dd if=/dev/sda of=/myusb/mbr.bin bs=512 count=1
dd if=/dev/sda1 of=/myusb/sda1.bin bs=512 count=1
# ... any other partitions and or mbr like sda2,sda3 or sdb, sdb1,sdb2 

```To restore mbr and partition tables
```

dd if=/myusb/mbr.bin of=/dev/sda bs=512 count=1
dd if/myusb/sda1.bin of=/dev/sda1 bs=512 count=1

```dd is dangerous command as it can wipe out your harddrive, it will not break it but destroy all data on it if used wrongly. I read somewhere that you cannot put of= before if= but never tried it as it can wipe out your harddrive.
The reason why your mbr and partition table goes on a usb stick is pretty obvious. If these things get corrupt you cannot read the files on your harddisk and or cannot boot so there is no point in putting them on the harddisk.
Another thing I hear somewhere is that partition table and boot sector of ext4 is not stored in the first block of the partition so the dd command would be pretty useless there.

Now to backup the system:
boot with usb and run the following command (assuming your system is on sda5):

```

cd /sda5
mkdir backup
tar -cvpzf backup/backup.tar.gz -&#8211;exclude=backup --exclude=lost+found --exclude=sys --exclude=mnt --exclude=media --exclude=home . 

```To restore:
```

# delete the directories that you backed up (all but backup, lost+found, sys, mnt, media and home)
cd /sda5
tar -xvpzf backup/backup.tar.gz -C .

```It is not as simple as choosing or clicking backup and restore but it could be scripted. The point is that you can look at the commands and try to understand it so you can tweak them to your specific needs.

---

