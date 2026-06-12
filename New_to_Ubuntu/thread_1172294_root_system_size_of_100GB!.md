---
title: "root system size of 100GB?!?"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by kramer65 on 2009-05-28
Hello,

When I want to download something it says I have no space left in /tmp

When I view the filesystems in the system monitor it says that my root (/) is a total of 94GB of which 86.6 is free, **but 0 bytes are available**.

What the hell is the difference between free and available? And how is this possible..?

PLease help!

---

### Post by drs305 on 2009-05-28
Perhaps the easiest reason to correct: The system monitor results include Trash in the used space. So if you have trash in either your trash bin or root's trash bin it must be emptied before this space becomes available and can be used. There are specific commands in the link below to investigate, but you can check your root trash bin with: 
```

gksudo nautilus /root/.local/share/Trash/files

```
Use SHIFT-DELETE to remove any files found here but be careful as you can't restore them once deleted. If you just use DEL, the files remain in the trash bin.

There are a variety of things that could have eaten up your free space. This wiki is fairly comprehensive in finding and correcting this type of problem.
[https://help.ubuntu.com/community/RecoverLostDiskSpace]("https://help.ubuntu.com/community/RecoverLostDiskSpace")

If you have questions about it, post them here.

---

### Post by taurus on 2009-05-28
Open a terminal and post the output of this command.

Applications -> Accessories -> Terminal
```
df -h
```

---

### Post by LowSky on 2009-05-28
sudo apt-get autoremove

sudo apt-get clean

---

### Post by kramer65 on 2009-05-28
Hi Excuse me, I forgot to include some more details about my system. I am running Ubuntu 8.04 and I've got a separate /home partition. I *think* the trash is in the home folder so that should not be the issue. Nonetheless I double checked my trashbin and emptied it several times.

@taurus

The results of your command:

```
Bestandssysteem            Grtte Gebr Besch Geb% Aangekoppeld op
/dev/sda1              93G   93G     0 100% /
varrun                1,7G  120K  1,7G   1% /var/run
varlock               1,7G     0  1,7G   0% /var/lock
udev                  1,7G   88K  1,7G   1% /dev
devshm                1,7G   12K  1,7G   1% /dev/shm
lrm                   1,7G   40M  1,6G   3% /lib/modules/2.6.24-24-generic/volatile
/dev/sda2             185G  133G   44G  76% /home
/dev/sdb1             925G   92G  787G  11% /media/sdb1
overflow              1,0M   40K  984K   4% /tmp
gvfs-fuse-daemon       93G   93G     0 100% /home/hiekra/.gvfs
/dev/sda4             646G  405G  209G  67% /media/Opslag
```

Does that help.. ?

---

### Post by drs305 on 2009-05-28
Your / system partition shows 100% full. The two main reasons (if the partition is of normal size) is trash in root's trash bin and a backup which has been improperly saved to the system partition instead of to a backup partition. Many users of *sbackup* experience this. If you look at the wiki linked in the previous thread, there are commands for finding large files, which would probably be the case if a backup was improperly stored on the system partition.

Just to be clear, the trash bin that may be full is root's, not the user's. So the place you would have to look is in /root/.local/share/Trash/files and not in /home or some other partition. Emptying your user trash bin won't solve a root trash problem.

Also, as covered in the wiki, it is best to unmount all *non*-system related partitions when trying to find the problem. Other partitions mounted on /media or /mnt may be hiding files installed on the / partition that won't be seen if another partition is mounted on top of it. You can do this with "sudo umount -a". You will get a few messages when running this but at the end only your system partitions would normally still be mounted.

---

### Post by philinux on 2009-05-28
> **kramer65 said:**
> Hello,

When I want to download something it says I have no space left in /tmp

When I view the filesystems in the system monitor it says that my root (/) is a total of 94GB of which 86.6 is free, **but 0 bytes are available**.

What the hell is the difference between free and available? And how is this possible..?

PLease help!

Sounds like you've been deleting some large files using say gksudo nautilus or something like that. They would end up in roots trash not the users.

---

### Post by kramer65 on 2009-05-28
I could indeed well be the sbackup since I enabled that about a week ago.

I am readin through [this stuff]("https://help.ubuntu.com/community/RecoverLostDiskSpace") now and it is quite complicating. Could you guys help me out a little bit here?

I first need to "unmount all but your system folders using the sudo umount -a command". Can I simply paste that onto the command line safely?

---

### Post by drs305 on 2009-05-28
> **kramer65 said:**
> I first need to "unmount all but your system folders using the sudo umount -a command". Can I simply paste that onto the command line safely?

Yes. First close out all your open apps, then run the command.

It will attempt to unmount everything that is mounted. Of course, it won't unmount necessary system partitions. It will give you messages about a partition being busy - those are the system partitions still in use. If you prefer, you can run the "mount" command to see everything that is mounted and manually umount the extras with "sudo umount /dev/sd[COLOR="DarkRed"]XX[/COLOR].

From the wiki, if it's an *sbackup* problem, you will probably find a large file or more with one of these commands:
```

sudo find / -name '*' -size +1G
or
sudo find / -name '*' -size +500M

```

Once you find the large backup files, move them somewhere else - off the system partition. Since these files are on the system partition, they will probably be owned by root so do the moving with "gksudo nautilus".

You also have to determine why *sbackup* made the backup on the system partition in the first place (if that was the cause). Usually it is because sbackup was supposed to save the backup to a folder mounted in /media or /mnt, but for some reason the backup device (another partition or external drive) wasn't mounted at the time. So instead of being written to the backup device, it remained written on the system partition instead.  

Put more simply, sbackup is going to write the backup file to the designated location - let's say /media/backup. Hopefully, there is an external drive mounted there, so the file written to /media/backup is actually written to the backup device. If the backup device isn't mounted when sbackup writes the file, it still gets written to /media/backup. Only in this case it is written directly to the system partition, thus eating up your free space.

---

### Post by kramer65 on 2009-05-29
Hello there. I had not much time but I'm back again. I hope you guys can still help me out.

I ran the sudo umount -a command and then the sudo find / -name '*' -size +1G command.

It found some files in my home folder larger then 1GB (some movie files etc) and also this file:
/media/Backup/2009-05-18_09.02.54.335770.hiekra-desktop.ful/files.tgz

But isn't that one mounted on my external drive?


If I simply (shift) delete that one, will it then be alright?

---

### Post by halitech on 2009-05-29
sounds like the external was the intended location but it may not have been mounted so it created the file locally. Yes, a shift + delete will get rid of it but it won't be on your external unless you have a copy of it there as well. Before you delete it, make sure the external isn't connected and see if the file still exists.

---

### Post by kramer65 on 2009-05-29
Alright. I deleted it, restarted, and everything seems fine now.

Surprisingly, many other issues have been resolved as well: youtube video's play again, my printer works again and random freezes of my firefox don't seem to appear anymore either.

How can sbackup mess up a system so badly? Isn't that a simple programming error? I mean, how can noobs (like me) fix this. Because to be honest, I was about to fully erase Ubuntu from my system since I can't go about fixing things every other month because some kind of program messes things up. I need my pc to work for me and not the other way around.

Well, anyway, I'll stick with Ubuntu, but I just think that sbackup really needs some work.

Thanks a lot anyway!

---

### Post by halitech on 2009-05-29
glad to hear things are working properly again. I don't think I would completely blame it on sbackup. It was just doing what it was told to do but for some reason the intended location wasn't mounted so it created it as best it could. Best thing to do before doing a backup is to make sure the intended location is mounted properly.

Glad to hear you will be sticking with it :)

---

### Post by drs305 on 2009-05-29
As I tried to explain in my last post, the sbackup file is written to /media/Backup. If an external device isn't mounted there, it will write to the system partition itself.

I don't use sbackup but I have answered several posts about this problem and is partly why I wrote the wiki guide. I know that at least one person wrote a script so that sbackup checks to make sure an external drive was mounted before running - to prevent the situation you found yourself in. You could search forum threads from the past 6 months in which I had a post to find that script.

Added: This is from the wiki:
> To help prevent this when using sbackup, the user can select the "Abort backup if destination directory does not exist" in the "Destination" tab during setup.

In order for this to work, make sure the mount point of the device you are saving to is the one created when the external device is mounted and that the mount point disappears when the device is unmounted. 

If it always exists, even when that device isn't mounted, the above option wouldn't work. If the mount point always exists, you could perhaps use the script if you can find it, which may use a different approach to seeing if the external device is present.

---

### Post by kramer65 on 2009-05-29
Hi Guys,

Thanks for all the help. I know there must be a solution. I am just saying that if somebody does not know what the words "mounting" "mount point" "partition" etc mean (and the majority of pc users don't know) then sbackup becomes not only unusable, but actually dangerous to the system. This check for mounting should be done by sbackup itself already.

I've gone through all this trouble to get my system working correctly again. Unfortunately I simply don't want to spend the time to fix all this correctly.

Please don't understand me wrong, I don't want to complain since I realise that all this is free software, made by volunteers. And for this I really applaud the effort as well as the result. I am just saying that if sbackup, for whatever reason, CAN have the result that the system becomes unusable, there is something wrong..

---

