---
title: "partitions/directories/file system"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by capnthommo on 2009-01-15
Hi everyody, my question is about the way my directories are organised.  i performed a complete reinstall and what i have is as follows.  looking in the 'Places' menu on the top panel of the desktop i have as follows (i shall just list them, rather than put them in a column as they actually are):
[Home Folder.  Desktop.  Documents.  Music.  Pictures.  Videos.  (section divider)  Computer.  CD/DVD Creator.  CD-RW/DVD+-RW Drive.  (section divider)  Network.  Connect to Server.  (section divider)  Search for Files.  Recent Documents.]

Looking in GParted shows the following:
```
                                                     flags
/dev/sda2          ext3         /data
/dev/sda1          ext3         /backup               boot
/dev/sda4          extended     
/dev/sda5          ext3         /
/dev/sda6          linux-swap          
```

(Edit:  i'm sorry, the formatting didn't transfer,  boot is a flag on sda1)
sda1, 2 and  5 are all unmountable according to a right click on the mouse.
'Home Folder' on Places leads into file browser displaying the same entries as first two sections of Places with the addition of 
[File System] which i presume is /dev/sda5.  Am i correct to assume that /dev/sda1 and /dev/sda2 and /dev/sda5 are all part of [File System] and if so then since any files i copy or create seem to save to /Home/Nigel on sda5 how can i make them got to sda2  /data instead.
At present i am save asing files and sending music etc to /home/nigel as the save as option suggests and then going into nautilus with [gksudo] and copying the files into the appropriate folders in /Data (sda2) then deleting the copy on sda5 /home/nigel.
This seems a needlessly laborious process so can someone help me to set up some kind of system where i save as either to the right place to start with or so that the files are automatically copied to /data and the original deleted.

there must be a way, surely?  trhanks for any suggestions.
cheers
nigel

---

### Post by hyper_ch on 2009-01-15
what's teh output of:

```

ls -al /data

``` ?

Btw, to properly "format" output embrace the output in [noparse]```

```[/noparse] brackets.

---

### Post by capnthommo on 2009-01-15
Hi and thanks hyper_ch.  here is the output you requested
```

nigel@nigel-laptop:~$ ls -al /data
total 52
drwxr-xr-x 10 root root  4096 2009-01-14 19:13 .
drwxr-xr-x 22 root root  4096 2009-01-15 13:44 ..
drwxr-xr-x  4 root root  4096 2009-01-15 13:41 Documents
drwx------  2 root root 16384 2009-01-12 20:39 lost+found
drwxrwxrwx 19 root root  4096 2009-01-13 17:18 Music
drwxr-xr-x  3 root root  4096 2009-01-14 19:17 Pictures
drwxr-xr-x  2 root root  4096 2009-01-13 10:57 Public
drwxr-xr-x  2 root root  4096 2009-01-13 10:56 Templates
drwx------  4 root root  4096 2009-01-13 10:58 .Trash-0
drwxr-xr-x  2 root root  4096 2009-01-13 10:55 Videos
nigel@nigel-laptop:~$ 

```
i knew about the brackets, i should have thought!
thanks
nigel

---

### Post by cariboo on 2009-01-15
If you run:

```
sudo fdisk -l
```

and paste the output in your next post, we would have a better idea of what you partition setup looks like.

Jim

---

### Post by capnthommo on 2009-01-15
hi cariboo907, thanks and here it is:
```

nigel@nigel-laptop:~$ sudo fdisk -l
[sudo] password for nigel: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x939aab47

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        6238       12525    50508360   83  Linux
/dev/sda2               1        6237    50098671   83  Linux
/dev/sda4           12526       19457    55681290    5  Extended
/dev/sda5           12526       19168    53359866   83  Linux
/dev/sda6           19169       19457     2321361   82  Linux swap / Solaris

Partition table entries are not in disk order
nigel@nigel-laptop:~$ 


```
hope that helps.
just to clarify, i might not actually have a major problem - you guys will know far better than me, obviously.  but i am not sure so would just like to check it all out and if possible rationalise the way things work/appear.  it just doesn't seem logical the way things look to be organised.
thanks again everybody
nigel
):P

---

### Post by capnthommo on 2009-01-16
bump

---

### Post by Elfy on 2009-01-16
I've read your first post twice and still can't quite understand what the problem is :)

Can you sya exactly what you are trying to do, I sort of am thinking that you have the drives at boot but things aren't saving to the right place.

If that is what you're saying - what things aren't saving to where you want, which apps are they?

---

### Post by capnthommo on 2009-01-16
Hi forestpixie.  i find it hard to actually get a handle on waht my problem is (or if there even is one) - but i will have another shot.  What i am puzzled by is that when i save a new file it goes to the appropriate place - such as the /Home/Documents folder.  if i leave it there this is surely going to fill up my sda5 / partition so i move it to the /data partition by going (gksudo nautilus).  now this just seems to need automating so it doesn't rely on repeated operations by me - i am going to mess it up sooner or later!  what i want to do is be able to simply 'save as' a file and have it go to the appropriate place in /data and leave nothing in /home.
i think my worry over the Places menu is unimportant.  i was concerned that in order to look in 'file system i had to select Home Folder and then move to File System which then gave me access to /Data.  Perhaps what i mean is that i feel that /Data should mount at boot up (maybe /Backup too?).  it just seems clumsy to have to follow the path i do to get to my data files.
to try and put it briefly:  can the process of saving files etc be automated so that they ends up on the /data partition instead of /home and that i dont have to take such a roundabout rout to access the data files (i know that unutbu (and you) helped me a few weeks ago when i had some problems and on that thread we did things like creating symlinks and so on, but i'm not sure if i can just use those same commands as the system is now different/reinstalled due to crisis).  also is it possible that the /data partition can show a shortcut/link on the Places menu?
sorry, as usual i have used far too many words, but i hope i have made things a bit clearer
cheers
nigel

---

### Post by Elfy on 2009-01-16
So you don't have the partitions in fstab so they mount at boot - is that right - that's easy enough to deal with.

Basically - add a folder to mount to then edit fstab so there is a line for each partition/fodler you wish to have available at boot.

That would go some way towards not having to run nautilus again - you can drag form the right to left pane - creates a shortcut to drives/partitions if you so wish - I do just that.

What I wouldn't be wanting to do is move files with root rights from my home to a data partition.

> sorry, as usual i have used far too many words, but i hope i have made things a bit clearerdon't apologise for verbose mode - but it might help those who don't have english as a first tongue if you used a bit more white space :)

---

### Post by capnthommo on 2009-01-16
Hi forestpixie
To start with, a good point about the white space, i shall bear it in mind.

> 
So you don't have the partitions in fstab so they mount at boot - is that right - that's easy enough to deal with.


Firstly, im not sure if i have - if i look in partition editor it shows them as mounted (or at least there is an option to unmount them so i assume they are).  And system monitor also shows them and i have noticed it only sees mounted partitions/devices but other than that? 

Secondly, i don't know how to add the folders as you advise.  I have folders in /File System named Data and Backup and that is where i have been moving the data files to. These show up as containing the correct numbers of Gigabytes are they the ones you mean?

 I agree with you, I dont want to be messing around with root privileges in nautilus to do things that i believe should be do-able in a safer way - that's why i raised this thread.
I feel that what needs to happen is that when i save or download a file it should go to data straight away otherwise I know what will happen - I will begin to fret about the amount of used space in the Home folder and do something stupid.
cheers, hope this helps
nigel

---

### Post by vanadium on 2009-01-16
This thread has gone too long and is confusing.

capnthommo, I think al you need is some knowledge about symbolic links and about permissions.

1) Symbolic links

Symbolic links allow you to organise directories the way YOU want. You can easily create a symbolic link with the file browser nautilus: Press Ctrl+Shift then drag the directory to some other directory to create a link there.

In your example, let us create a symbolic link to /dev/sda2 (mounted in /data) in your home directory.

* Open a nautilus window. Navigate to "file system". It shows your system directories, and you will also find an icon for /data.

* Open a second nautilus window in your home directory. By default, nautilus opens in your home directory. At any time, you can hit Alt+Home to quickly go there.

* Hit Ctrl+Shift, then drag the icon of "data" in the first nautilus window to a white space in the other nautilus window. Release the mouse button: a symbolic link "Link to data" has been created in your home directory. You can rename it to "Data" or "data" or whatever you like.

The beauty is that this link acts and behaves like a real directory. You can now access the other partition directly from within your home directory.

Note you do not need to be administrator (root) to achieve what you did!

2) Permissions

Another aspect is that you need to acquire the required permissions to read/write/execute in the location on the other partition. For this, you need to change the permissions of the directory, referred to by your link. In our example, it is /data.

To change permissions, you must be root. An easy way to change permissions is with nautilus. You need, however, to start it with root permissions.

* Hit Alt+F2
* type "gksu nautilus" then enter

A nautilus window opens. Navigate to "File system" and right-click "data", then "Properties. Change the owner from "root" to your own user name.

---

### Post by capnthommo on 2009-01-16
Hin there, and thanks you helped sort out in my own mind what i am looking for.

okay, so i have created a symlink as you suggested from home to /data and that looks ok.
but in order to change all the permissions it looks as if i am going to have t0 change things for every individual folder in /data.  
it only gives permisssions to delete etc those files i have actually changed individually - 
is there no command that will change the permission/ownership of all files in /data and/or /backup or even eg the documents folder in data - 
i would have thought "Apply permissions to enclosed files" button would have done that at the folder lvel but it seems not - unless i'm doing something wrong.  -  okay its no biggie but its a  bit tedious when you have a large music collection.

And will these permissions/ownerships hold true for any other files created/saved to /data  or will they need to be djusted like this too?
okay, we're gradually getting there - when you consider that 5 days ago i completely blew the whole system it's not so bad.

cheers all
nigel

---

### Post by vanadium on 2009-01-16
The standard permissions of new files are determined by the umask value. By default, this is 0022, meaning that for new files - the owner has all permissions - groups and others can read and execute. Pay attention: you must apply the permissions to the original directory (/data), not the link.

Either with "gksudo nautilus" or the command line, you can apply permissions to all files in an entire directory tree.

---

### Post by capnthommo on 2009-01-16
okay thanks vanadium. 
i did apply it to the original /data.  in fact i applied it before i even made the link, first time.  
but now it seems to be working ok - i just copied the /data into /backup and it all worked anyway.
i shall call this one solved - now i dont have to mess around in "root privileged nautilus" which has to cut down the chances of lash ups.
thamks for the help
cheers
nigel

---

