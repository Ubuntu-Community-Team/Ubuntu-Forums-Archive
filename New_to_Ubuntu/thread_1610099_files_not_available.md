---
title: "files not available"
date: 2010-10-31
forum: New to Ubuntu
---

### Post by janettheblog on 2010-10-31
Something is wrong with my computer dealing with files. I was out of the room and returned to find a blank screen but the power light on on the computer. I turned off the computer and restarted. There was an error message during booting which I cannot remember. It was about a problem with mounts and said I could press esc to bypass the problem. I did this. Booting finished but my desktop was empty and the 'Places' would not find any of its places. I restarted the computer a number of times but the error message did not re-appear and the file problem did not go away.
 All the programs seem to work. I can get to my mail; the recent files are available in Open Office; the mount command in the terminal lists all the partitions except swap. On one of the restarts there was a file check (looked a bit different from the usual) and it did not register any problem. But the problem persists.
 The details of the machine are: Ubuntu 9.10, kernal 2.6.31-22-generic, Acer, 2x AMD Athlon Dual core 4450e, 2.7 G memory, 320 G disk
 In summary: it boots normally with no error message, all programs tried have worked, files in recent list are available – but – nothing is available through 'places' which is how I find files.
 Can anyone help? Please.

---

### Post by Hippytaff on 2010-10-31
If you have a seperate home partition you might need to mount it?

---

### Post by janettheblog on 2010-10-31
home has a separate partition. When I type mount in the terminal I get a list and /home is recorded as /dev/sda8 on /home type ext (rw). Doesn't that mean it is mounted already? How do I mount it if it isn't already? How do other programs find the files if home is not mounted?

---

### Post by Mark Phelps on 2010-10-31
You don't by any chance have a dual-boot setup with MS Windows, do you?

If so, which of the partitions are you having trouble with -- MS Windows? Ubuntu?

---

### Post by Hippytaff on 2010-10-31
Whats the output of

```

df -h

```

Unless you rebooted other progammes might have the data in a cache or something. This should tell you if it is mounted anyway

---

### Post by janettheblog on 2010-10-31
not dual boot - no trace of Windows

---

### Post by janettheblog on 2010-10-31
result of df -h

janet@janet-acer:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             2.8G  297M  2.4G  12% /
udev                  1.4G  292K  1.4G   1% /dev
none                  1.4G  200K  1.4G   1% /dev/shm
none                  1.4G   88K  1.4G   1% /var/run
none                  1.4G     0  1.4G   0% /var/lock
none                  1.4G     0  1.4G   0% /lib/init/rw
/dev/sda2             183M   35M  139M  21% /boot
/dev/sda5             1.9G  447M  1.4G  26% /var
/dev/sda6              19G  2.3G   16G  14% /usr
/dev/sda7             942M   18M  877M   2% /tmp
/dev/sda8             264G   24G  227G  10% /home
janet@janet-acer:~$

---

### Post by Hippytaff on 2010-10-31
maybe try unmounting and remounting
[http://manpages.ubuntu.com/manpages/karmic/en/man2/unmount.2freebsd.html](http://manpages.ubuntu.com/manpages/karmic/en/man2/unmount.2freebsd.html)

home looks mounted /dev/sda8

---

### Post by janettheblog on 2010-10-31
Is this what I do?
sudo unmount /home

and then
sudo mount /home /dev/sda8

---

### Post by balloooza on 2010-10-31
Try this:

*(when somone puts a $ before a line it means run in terminal. Also, less comonly used, a # at the beginning means to run it as an admin)*
```
$ nautilus
```
Do you see the browser now?

Then in nautilus try this:

**CTRL + L** and type **/home/janet/** then **enter**

---

### Post by janettheblog on 2010-10-31
Here is what happened

janet@janet-acer:~$ nautilus

(nautilus:3068): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Segmentation fault
janet@janet-acer:~$ 

Does this tell you anything? Hoping.

---

### Post by janettheblog on 2010-10-31
The happy face was a end bracket followed by a colon but the editor did its own translation.

---

### Post by balloooza on 2010-10-31
Eeek!

That is not good, I will try to find a bug report for that one.

This is looking serious :(

---

### Post by balloooza on 2010-10-31
It looks like it was a bug, have you updated lately (not distribution upgrade, just there are yada yada updates to install popup thing)

---

### Post by janettheblog on 2010-10-31
Hi, yes I did update recently.
Before the computer stopped on me there was a update message (the sort I get every few days) and I was very busy so I ignored it. When the computer stopped working properly I thought in may need the updates that had been waiting and so I when into update manager and accepted the installs it recommended but it made no difference to the problem (not better or worst).

---

### Post by balloooza on 2010-10-31
Try creating a new user (sorry for the delay, I forgot to subscribe)

This seems to fix it for a great deal of people, if this works, just migrate to the new user.

---

### Post by JKyleOKC on 2010-10-31
If you do migrate to a new user, be aware that "sudo" won't work for that new user until you join the "adm" group. The first user created at install time is automatically added to that group, but later ones are not.

---

### Post by janettheblog on 2010-10-31
Well, I made a new user. Now 'place' works for that user! You have been a great help.:P However this is all new folders and my files (made as the old user) are not available. I assume that I will have to get sudo status and then use the terminal to copy my files into the new folders. Is that correct or is there something easier. What about the programs - will they be able to find the moved files? I don't even know what the name and path is for my gramps database.

---

### Post by balloooza on 2010-10-31
Here is how you will do it: (for more information on any of the steps, ask, I will be away for a while)

1: run```
su janet -
sudo su (This will make you root, so be careful, it is like sudo on all commands you type)
cd /home/janet (if that is not your user name, just replace it, but it should be, by judging what you posted)
cp -r ./Music /home/NEWUSERNAME/
cp -r ./Documents /home/NEWUSERNAME
(the reason you are doing it like this is for safety, just copy the folders you want)
cd /home/NEWUSER
chown -R NEWUSER:NEWUSER ./

```

2: Add yourselfe to the sudoers file (google it)

3: More later, have to go.

Good Luck!

---

### Post by janettheblog on 2010-10-31
OK I have followed the commands you gave and copied the files (or most of them - rest later). I still will have to configure programs and move bookmarks etc. I put the new user in the adm group. If you have any more wisdom I would welcome it. Thanks for your help.

---

### Post by balloooza on 2010-10-31
I am back.

1: I was not clear on the last step, all folders should get the same treatment as Music and Documents, eg. Pictures, Downloads, et cetera.

2: Test out your sudo ability.

3: Copy all . (hidden) folders you want in the same way you copied the other folders like Music.
To list all files, including hidden ones, in the current directory, Run:
```
ls -lrta
```[SIZE="1"][INDENT]ls for list
-l for long, shows time, permissions, owners, name, size
-r for reverse order
-t for time ordered (reverse time if you have been following)
-a for hidden directory[/INDENT][/SIZE]

And also look in the .config directory

4: Gconf is a mess to copy over, since it can bring back the same problem you were having before, so you will have to reset your preferences on your apps, unluess you want to try copying over gconf.

---

### Post by janettheblog on 2010-11-01
Well damn. I did tranfer .gconf although I didn't intend to and yes the problem appeared in the new user like you suspected it would. 
Would it be a good idea to destroy .gconf in the new user? and see if it works then.

also there was a message about .gvfs saying there permission was denied (all its information is ? except the first d in the permissions. I assume this is normal. OK?

I'll wait for help before I do anything further.

---

### Post by balloooza on 2010-11-01
gconf: Hmm, how about this, make yet annother new user, and copy (and chown) *that new users* .gconf to *your* new users home, and see if that works.

gvfs: This is just a wierd place that gnome mounts network volumes, so it should not be copyed, that being said, I do not think copying it would do anything, if you have any problems mounting network file systems (other than the ones that you get when there is nothing seemingly wrong) Then umount all things in nautilus, and see if any directorys in .gvfs still remain, and remove them, but I think gvfs is robust when it comes to directorys getting in its way.

---

### Post by janettheblog on 2010-11-01
Sounds like a good idea so I'll make a new user shortly.

About .gvfs - there is nothing that can be done about it anyway because reading its permissions even blocks root.

Thanks so much for your help so far.

---

### Post by janettheblog on 2010-11-01
I made a user 'again' but it does not seem to have a .gconf.

janet@janet-acer:~$ sudo su
[sudo] password for janet: 
root@janet-acer:/home/janet# cd /home/again
root@janet-acer:/home/again# cp -r .gconf /home/alice
cp: cannot stat `.gconf': No such file or directory
root@janet-acer:/home/again# ls -lrta
total 24
-rw-r--r-- 1 again again  675 2010-11-01 14:21 .profile
-rw-r--r-- 1 again again  167 2010-11-01 14:21 examples.desktop
-rw-r--r-- 1 again again 3180 2010-11-01 14:21 .bashrc
-rw-r--r-- 1 again again  220 2010-11-01 14:21 .bash_logout
drwxr-xr-x 6 root  root  4096 2010-11-01 14:21 ..
drwxr-xr-x 2 again again 4096 2010-11-01 14:21 .
root@janet-acer:/home/again#

---

### Post by JKyleOKC on 2010-11-01
Try going back to your original user, delete the .gconf file, reboot, and see if that takes care of the problem. The fact that your new new user doesn't have such a file indicates that it's not totally necessary, and your first new user provides confidence that all your files and data are safely backed up.

I've seen recommendations to delete .gconf as solutions for other problems, so it may well work in this case also!

---

### Post by janettheblog on 2010-11-01
Well I have spent a few hours erasing all of the .gconf directory. It didn't cure the problem. 
I did see the error message again when I first entered the third user but it is not visible for long enough to read and I saw it again when I booted the first user after removing .gconf 
As far as I could read it before it disappeared was 'one or more mounts listed in /etc/s.....(maybe stat)' . There was at least another line maybe more. 
It is getting very late here so I'm off to bad. 
Maybe I should just bite the bullet tomorrow and reinstall ubuntu.

---

### Post by janettheblog on 2010-11-02
I have given up, reinstalled ubuntu and I am now getting the apps to work and have their data. Thanks for trying to help.

---

