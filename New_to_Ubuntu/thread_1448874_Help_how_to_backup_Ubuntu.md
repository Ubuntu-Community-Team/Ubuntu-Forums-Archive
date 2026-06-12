---
title: "Help how to backup Ubuntu"
date: 2010-04-07
forum: New to Ubuntu
---

### Post by rixaga on 2010-04-07
Excuse me Im newbie here...
I want to ask how do I backup the OS we are already in the ubuntu install on a computer complete with all the packages, drivers, etc. into a CD / DVD so that later can be installed again to another computer,,
because I want make backups my ubuntu and install to the other computer, and because there are already so many package2 installed,,
how to do that, or there are other solutions??,,:confused:
Please help me..:)
thanks before ..

---

### Post by lisati on 2010-04-07
You might want to check out remastersys

[http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)

---

### Post by petrus_yuri on 2010-04-07
You can do back up by doing this step
1.Type sudo su
2.Go to root folder by type cd/
3.type tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt -
-exclude=/sys /

The 'tar' part is, obviously, the program we're going to use.
 
'cvpfz' are the options we give to tar, like 'create archive'  (obviously), 
'preserve permissions'(to keep the same permissions on everything the  same), and 'gzip' to keep the size down.

Next, the name the archive is going to get. backup.tgz in our example.

Next comes the root of the directory we want to backup. Since we want to  backup everything; /

Now come the directories we want to exclude. We don't want to backup  everything since some dirs aren't very useful to include. Also make sure  you don't include the file itself, or else you'll get weird results. 
You might also not want to include the /mnt folder if you have other  partitions mounted there or you'll end up backing those up too. Also  make sure you don't have anything mounted in /media (i.e. don't have any  cd's or removable media mounted). Either that or exclude /media.

2.Restore
Type tar xvpfz backup.tgz -C /

3.If your grub corrupted
Go to this link:[http://www.ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore)

---

### Post by HermanAB on 2010-04-07
The best way to replicate systems is with Red Hat Kickstart for Debian - it is available somewhere - Google should find it. (This is one of the main reasons why large data centres and corporations use Red Hat).

Another simple but slow method is with Clonezilla.

---

### Post by tom.swartz07 on 2010-04-07
My all time favorite backup method is using rsync.

rsync is a terminal program that, once you make the initial backup, will only update the bytes that were changed since last run. 

The one liner that I use goes as follows
```
sudo rsync -av --progress --delete --log-file=/media/backup/$(date +%Y%m%d)_rsync.log --exclude "$HOME/.gvfs" --exclude "$HOME/.maple13" /home /media/backup

```

the -av flag: 'a' means archive, or copy everything recursively preserving almost everything like permissions, ownership and time stamps. The 'v' is verbose, so it tells you what its doing, either in the terminal, in in this case, in the log file. 

--progress gives you more specific info about progress.

--delete checks for changes between source and destination, and deletes any files at the destination that you've deleted at the source. 

--log-file saves a copy of the rsync result to a date-stamped file on my backup location.

--exclude leaves out any files or directories you don't want copied. Some folders, like Maple were too big, and are easier just to re-install should something catastrophic happen.

/home is the directory I want copied. /home copies the directory and its contents, /home/ would just copy the contents

/media/backup is the separate drive. Change this to whatever your backup location is. I prefer to have it synced to a 4GB USB drive for convenience, but you could go to another drive, another partition, or even somewhere far away over SSH!

**In order to restore**, you just reverse the last 2 locations, in my example /media/backup and /home. Boom. Done.

---

### Post by ibuclaw on 2010-04-07
> **lisati said:**
> You might want to check out remastersys

[http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)

Remastersys is handy, I prefer to create one from scratch though (not for light hearted users, mind you).

[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

Some extra tips and tricks that aren't mentioned in the guide.
To get a complete list of installed applications on your system.
```
dpkg --get-selections > packages.list
```
Then copy the list generated into the chroot, and once inside run:
```

dpkg --clear-selections
dpkg --set-selections < packages.list
apt-get dselect-upgrade

```
And that will install all applications that are present on your system inside the chroot, ready for packaging into a CD/DVD.
(see the rest of the guide linked to find out how to do that) :)

Regards
Iain

---

### Post by IndyGunFreak on 2010-04-07
Why not just do a clean install on the other machine, and just set it up?  It's not that difficult, thats how I've always done it.

---

### Post by J V on 2010-04-07
Yes I wrote a bash script to do that, but with a large amount of data it takes longer to do it that way than to image the computer.

+1 for clonezilla

---

### Post by theozzlives on 2010-04-07
+1 for indygunfreak
otherwise clonezilla

---

### Post by nick_goodfate on 2010-04-07
> [http://ubuntuforums.org/showthread.php?t=1406928](http://ubuntuforums.org/showthread.php?t=1406928)
i think thats what you want ...?
ibuclaw already said that, sorry .

---

### Post by Objekt on 2010-04-07
> **HermanAB said:**
> The best way to replicate systems is with Red Hat Kickstart for Debian - it is available somewhere - Google should find it. (This is one of the main reasons why large data centres and corporations use Red Hat).

Another simple but slow method is with Clonezilla.

Why is Clonezilla slower?  I don't really know because Clonezilla is the only imaging solution I've used.  I hadn't heard of Kickstart until reading your post.

Does it have to do with the compression used?  I generally pick the middle option in Clonezilla (can't remember what it's called).

I have definitely noticed that Clonezilla does not run hardware at its fastest possible speed.  For example, when I use Clonezilla to save a system image to a drive connected via eSATA, I don't get anywhere near the 60-70 MB/s that I see in normal Ubuntu operation.  Always wondered why.

---

### Post by J V on 2010-04-07
Clonezilla is probably the fastest cloner there (Except boot time)

You can also rig the thing with scripts to autorun when booted, that way you just stick in the disc and voila, a new file is on the server...

The reason you don't get that speed is because it either has to repeatedly crash (Testing values which may or may not work) or come bundled with a hundred meg or so list of harddrives compatible with this that or the other...

---

### Post by Objekt on 2010-04-07
I wasn't referring to startup time.  I meant that once Clonezilla is actually writing or reading a disk image, it seems that the sustained transfer rate is not as fast as it could be.  I'm about due to refresh my system image anyway, so I guess I'll run it tonight & write down the numbers I see.

---

