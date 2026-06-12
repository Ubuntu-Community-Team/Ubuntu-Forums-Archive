---
title: "New partition and Home folder"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by jnmjr on 2010-03-11
Hi Guys, I just created a new partition so I could move my Home folder to it. I need your help on how to copy it to the new partition and to make sure that it works after the deed. Please understand that I'm not too swift with the command line so I need specific line by line help, THX in advance for your participation.8-[

---

### Post by jnmjr on 2010-03-11
bump

---

### Post by sandyd on 2010-03-11
whats the name of the partition?

I mean, like "/dev/sdaxx"
And the partition filesystem type? ext3? ext4?
you can find this by running```
sudo fdisk -l
```

The below example assumes your partition is /dev/sdaxx (replace it with your own partition), and it also assumes the filesystem is ext3 (change it to ext4 if needed)
```

sudo mount -t ext3 /dev/sdaxx /mnt
sudo cp -r ~/* /mnt
sudo chown -r [username] /mnt/*
mv /home/[username] /home/[username].bak
sudo umount /mnt
sudo mount -t ext3 /dev/sdaxx /home/[username]

```

---

### Post by audiomick on 2010-03-11
Hi.
There is this
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
and this
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Between the two of those, you should be right.

---

### Post by jnmjr on 2010-03-11
> **carlee said:**
> whats the name of the partition?

I mean, like "/dev/sdaxx"
And the partition filesystem type? ext3? ext4?
you can find this by running```
sudo fdisk -l
```The below example assumes your partition is /dev/sdaxx (replace it with your own partition), and it also assumes the filesystem is ext3 (change it to ext4 if needed)
```

sudo mount -t ext3 /dev/sdaxx /mnt
sudo cp -r ~/* /mnt
sudo chown -r [username] /mnt/*
mv /home/[username] /home/[username].bak
sudo umount /mnt
sudo mount -t ext3 /dev/sdaxx /home/[username]

```

The new partition is /dev /sdb3.... file system ext4, I  assume that by replacing the values in your example it would copy Home to the new partition or move it? Can you explain if after this it will always look for Home in the new partition or "mount it" whichever is the correct terminology, excuse my ignorance on this subject I appreciate your patience, THX.

---

### Post by audiomick on 2010-03-11
> **jnmjr said:**
> The new partition is /dev /sdb3.... file system ext4, I  assume that by replacing the values in your example it would copy Home to the new partition or move it? Can you explain if after this it will always look for Home in the new partition or "mount it" whichever is the correct terminology, excuse my ignorance on this subject I appreciate your patience, THX.
This is correct.
For the permanent mount, I think you have to edit your fstab. There is some info here
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

As it says there, you can use
```
sudo blkid
```to find the UUIDs of your partitions.

I get this
```
mick@ubuntu-desktop:~$ sudo blkid
/dev/sda1: LABEL="main_system" UUID="97201036-c514-47b5-aeb1-7ce98a8711ff" TYPE="ext4" 
/dev/sda3: LABEL="test-system" UUID="a8b6c85c-65da-4ffa-9d2e-8356e5c26bd2" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="e7d97bbe-adf2-4ad8-8d3e-c9f56adeed60" TYPE="swap" 
/dev/sda6: LABEL="test-home" UUID="aafe7a68-6945-48cf-b28a-f22b963d5fa6" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: LABEL="basement" UUID="4772ec87-6f08-40b9-a274-64e930e7c336" SEC_TYPE="ext2" TYPE="ext3" 
[COLOR=Red]/dev/sdb1: UUID="aa6c721e-d06e-4756-bac9-b3849e1a9195" TYPE="ext3" [/COLOR]
/dev/sdb2: UUID="96004184-5efc-490d-9280-0e1ab845a142" TYPE="swap" 

```The red is my /home.

This is my fstab
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=97201036-c514-47b5-aeb1-7ce98a8711ff /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb1 during installation
[COLOR=Red]UUID=aa6c721e-d06e-4756-bac9-b3849e1a9195 /home           ext3    defaults        0       2[/COLOR]
# swap was on /dev/sda5 during installation
UUID=e7d97bbe-adf2-4ad8-8d3e-c9f56adeed60 none            swap    sw              0       0
# swap was on /dev/sdb2 during installation
UUID=96004184-5efc-490d-9280-0e1ab845a142 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```the red is the entry for the mount point of my home.

Do
```
gksu gedit /etc/fstab
```to open your fstab in the editor gedit with root privileges and create an entry like that for the new home partition if it isn't already there after following carlee's instructions.
edit: I don't think it will be there. I can't see anything in carlee's post that would edit fstab.

another edit: just found this.
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by jnmjr on 2010-03-11
> **carlee said:**
> whats the name of the partition?

I mean, like "/dev/sdaxx"
And the partition filesystem type? ext3? ext4?
you can find this by running```
sudo fdisk -l
```The below example assumes your partition is /dev/sdaxx (replace it with your own partition), and it also assumes the filesystem is ext3 (change it to ext4 if needed)
```

sudo mount -t ext3 /dev/sdaxx /mnt
sudo cp -r ~/* /mnt
sudo chown -r [username] /mnt/*
mv /home/[username] /home/[username].bak
sudo umount /mnt
sudo mount -t ext3 /dev/sdaxx /home/[username]

```

All was going well until the third command, this is what I got.......

jnmjr@My-Desktop:~$ sudo chown -r jnmjr /mnt/*
[sudo] password for jnmjr: 
chown: invalid option -- 'r'

Did I make a mistake? Are the third and fourth lines in the example one command or separate? please advice, THX

---

### Post by audiomick on 2010-03-11
At a guess, I think it should be a capital R.
The purpose of the option would be to make the change of ownership ( chown) recursive, i.e. to apply it to all folders and files contained in the folder it is being applied to.
According to the "chown" man pages
```
man chown
```
the option for recursive is -R

---

### Post by jnmjr on 2010-03-11
> **audiomick said:**
> At a guess, I think it should be a capital R.
The purpose of the option would be to make the change of ownership ( chown) recursive, i.e. to apply it to all folders and files contained in the folder it is being applied to.
According to the "chown" man pages
```
man chown
```the option for recursive is -R

Yes, -R worked but the next line produced this result......

jnmjr@My-Desktop:~$ mv /home/jnmjr /home/jnmjr.bak
mv: cannot move `/home/jnmjr' to `/home/jnmjr.bak': Permission denied
jnmjr@My-Desktop:~$ 

I'm at a loss, please advise, THX

---

### Post by audiomick on 2010-03-12
Yes, I have encountered similar problems to that myself, and not yet found a good way around it. The problem is likely to be that, although your home folder belongs to you, there are one or two hidden files in there that belong to root.

I would suggest going through the links I posted in post #4 again. The first one doesn't seem all that good, actually, but read it anyway. The second one, from psychocats, seems better. If you also go and look at the link in that in the first sentence of the "important disclaimers", you will see that the author of that page refers to similar difficulties. 

You will see that at this "mv" step, the authors use "sudo" to perform the move with root privileges. That should solve the problem you are having at this point.

---

### Post by jnmjr on 2010-03-12
> **audiomick said:**
> Yes, I have encountered similar problems to that myself, and not yet found a good way around it. The problem is likely to be that, although your home folder belongs to you, there are one or two hidden files in there that belong to root.

I would suggest going through the links I posted in post #4 again. The first one doesn't seem all that good, actually, but read it anyway. The second one, from psychocats, seems better. If you also go and look at the link in that in the first sentence of the "important disclaimers", you will see that the author of that page refers to similar difficulties. 

You will see that at this "mv" step, the authors use "sudo" to perform the move with root privileges. That should solve the problem you are having at this point.

First I'd like to thank you and Carly for your suggestions..... I followed the Psychocats post to the letter and it has worked but only partially....

On booting I get this message... Could not update ICEauthorityfile /home/jnmjr/.ICEauthority

Then it continues to boot into Karmic but somewhat delayed..."THERE IS NO SOUND"
Once it is on the desktop it takes time to search for network connection and other stuff in the background... When I try to open any file in Home or Evolution etc. I get the following warning...

GConf error: Can't overwrite existing read-only value: Can't overwrite existing read-only value: Value for [COLOR=DarkGreen]`/apps/nautilus/preferences/navigation_window_saved_maximized'[/COLOR] set in a read-only source at the front of your configuration path
All further errors shown only on terminal

Would this be the file that's causing the errors? What would be the fix? 
How would I find further erros in terminal?

Seems the whole thing is almost working, it just needs some fine tuning... THX for your patience.

---

### Post by srs5694 on 2010-03-12
> **audiomick said:**
> Yes, I have encountered similar problems to that myself, and not yet found a good way around it. The problem is likely to be that, although your home folder belongs to you, there are one or two hidden files in there that belong to root.

No, the problem is that you don't have write privileges to the /home directory, although you do own and have write privileges /home/{user} (where {user} is your home directory name). Your solution of using "sudo" will work, but the reason you've provided is incorrect. Unix permissions rules for directories require you to have write access to the directory in which a file or subdirectory exists in order to change that file or subdirectory. You can test this yourself (comments after hash marks (#):

```

$ mkdir foo                 # create a subdirectory
$ sudo chown root foo       # give ownership of the subdirectory to root
Password:
$ touch foo/bar             # try to create a file in the subdirectory
touch: cannot touch `foo/bar': Permission denied  # failed; you're not root
$ sudo touch foo/bar        # create a file as root
$ mv foo/bar foo/bar2       # try to move the file as an ordinary user
mv: cannot move `foo/bar' to `foo/bar2': Permission denied
$ sudo mv foo/bar foo/bar2  # it works only when you're root
$ sudo chown {username}.users foo/bar2  # give yourself ownership of the file
$ mv foo/bar2 foo/bar       # try to move it again, and it still won't work
mv: cannot move `foo/bar2' to `foo/bar': Permission denied
$ sudo mv foo/bar2 foo/bar  # must be root to move file in root's directory

```

Of course, change "{username}" to your own username in the preceding.

I'll also comment that it's usually better to move the entire /home directory to a new partition rather than just /home/{username}. Moving the whole /home directory will enable you to create new user accounts and have their contents stored on that partition. Even if you're the only user of the computer, you might want to create a new account in order to test software without risking your main account's files or for some other reason.

---

### Post by audiomick on 2010-03-12
> **jnmjr said:**
> 
On booting I get this message... Could not update ICEauthorityfile /home/jnmjr/.ICEauthority
Check the permissions on that file. Mine has -rw------
 >  When I try to open any file in Home or Evolution etc. I get the following warning...

GConf error: Can't overwrite existing read-only value: Can't overwrite existing read-only value: Value for [COLOR=DarkGreen]`/apps/nautilus/preferences/navigation_window_saved_maximized'[/COLOR] set in a read-only source at the front of your configuration path
All further errors shown only on terminal
That doesn't really mean anything to me. You could try starting nautilus from a terminal to see if it shows you any useful error messages. Just type
```
nautilus
```in terminal and enter.
When I do that, I get this
```
mick@ubuntu-desktop:~$ nautilus

(nautilus:7923): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
```but from what I have seen here on the forum the "Eel-CRITICAL" thing is "normal", i.e. happens all the time.

> Would this be the file that's causing the errors? What would be the fix? 
How would I find further erros in terminal?

Seems the whole thing is almost working, it just needs some fine tuning... THX for your patience.
I am afraid I am at a bit of a loss there. I would at least try and check the permissions on the hidden files in /home. I think that is most likely where things are getting hung up, but I am guessing at this point.
Did I understand you right that nautilus starts despite the warning? If so, if you don't have it already, set nautilus to "list view", and in the "view" menu entry "columns" or something like that, you can make it show you a column for "owner", "group" and "permissions". Select "show hidden files" in the "view" menu, and you can easily see who the files belong to and what their permissions are.

I have a couple of things in there that belong to root:
.dbus : owner root group root drwx------
.ure : root root drwxr-xr-x
.nvidia-settings-rc root root -rw-r--r--

Most of what is in there should be owned by you and in the user group with the name of your user.

---

### Post by jnmjr on 2010-03-12
> **audiomick said:**
> Check the permissions on that file. Mine has -rw------
 That doesn't really mean anything to me. You could try starting nautilus from a terminal to see if it shows you any useful error messages. Just type
```
nautilus
```in terminal and enter.
When I do that, I get this
```
mick@ubuntu-desktop:~$ nautilus

(nautilus:7923): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
```but from what I have seen here on the forum the "Eel-CRITICAL" thing is "normal", i.e. happens all the time.

I am afraid I am at a bit of a loss there. I would at least try and check the permissions on the hidden files in /home. I think that is most likely where things are getting hung up, but I am guessing at this point.
Did I understand you right that nautilus starts despite the warning? If so, if you don't have it already, set nautilus to "list view", and in the "view" menu entry "columns" or something like that, you can make it show you a column for "owner", "group" and "permissions". Select "show hidden files" in the "view" menu, and you can easily see who the files belong to and what their permissions are.

I have a couple of things in there that belong to root:
.dbus : owner root group root drwx------
.ure : root root drwxr-xr-x
.nvidia-settings-rc root root -rw-r--r--

Most of what is in there should be owned by you and in the user group with the name of your user.

THX Audiomick for all your effort on my behalf, I have reverted to my original configuration and given up on a separate partition for /home at this time, I found it to be tooo!! complicated for now to continue messing around without really knowing what I was doing. The previous post about Unix etc. really turned me off since it is basically Chinese to me, pardon the pun, it must be obvious that Unix is not my forte and since Linux is based on it I'm like a bat in a dark cave. I also want to extend my thanks to all who tried to help me.

---

### Post by AnushaSameer on 2012-01-31
go to your home folder

press cntl + h

then your home folder will display hidden files

check whether any of the folders is locked

right click on the folder then click "properties". In that Click "permissions".

In owner, change folder access to "create and delete files."

And then click "Apply Permissions to Enclosed files"

If you cannot see any locked folders then select all folders and do the above

---

