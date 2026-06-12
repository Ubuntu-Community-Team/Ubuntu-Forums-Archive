---
title: "HELP:  All files belong to NOBODY!"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by Kellemora on 2010-06-01
Hi Gang

I moved all of my files from computer A to computer B using a shared folder on computer B appearing on computer A's desktop.

Once I was sure all the files were moved to computer B safely we reformatted the hard drive on computer A, so I can't go back to fix anything there!
(Getting ready to install Lucid on that computer!)

I have the SAME Owner NAME, the SAME Group Name on both computers.

Every single folder and file now says Owner NOBODY, Group NOGROUP!

I cannot seem to change them, "You Do Not Have Permission"

I know RSYNC to my external backups do not cause this MAJOR PROBLEM!

Copying Files should NEVER change ownership permissions!!!!!

In any case, I'm now in a Pickle!
I've studied all of my notes, spent 3 hours on-line, and all I find are complaints about this SERIOUS BUG in Ubuntu.........

Everything is basically READ ONLY can't save changes, etc.

Chown, chgrp, chmod and such do not seem to be working, apparently because ROOT is not the owner either!

I'm talking about thousands of files and folders here, not just a single file or folder.

They ARE backed up via RSYNC but I NEED THEM on this computer!

HELP!

TTUL
Gary

---

### Post by Kellemora on 2010-06-01
Can't even edit the files on the external drive either!

I changed the ownership of individual files that I MUST get done today!
Now I get the message, can't save changes, the drive is READ ONLY......

Yet I can go to other files and make changes on the same drive.......

How can that be if the DRIVE is Read Only as claimed?????

Today is going from BAD to WORSE way to fast!

TTUL
Gary

---

### Post by viralmeme on 2010-06-01
> **Kellemora said:**
> Hi Gang

I moved all of my files from computer A to computer B using a shared folder on computer B appearing on computer A's desktop.
Do you mean the contents of A' s/home directory or the system root  `/'. What mount point did you choose for the shared folder. Why would you use such a method to transfer a system. Why not just clone the partition?

> **Kellemora said:**
>  I have the SAME Owner NAME, the SAME Group Name on both computers.
But not necessarly the same UID and GUID as the original machine ..

[http://www.itwire.com/business-it-news/open-source/14446-uid-and-gid-the-basics-of-linux-user-admin](http://www.itwire.com/business-it-news/open-source/14446-uid-and-gid-the-basics-of-linux-user-admin)

---

### Post by ajgreeny on 2010-06-01
If the file system of the shared folder you copied the files to was not a linux file system, if it was fat32 for example, the files will not have permissions set as that file system type does not support linux permissions.

When you copy the files back to your linux file system, eg back to your home folder or partition, they will take on your user permissions, in the same way that any file copied from a usb flash drive (usually fat32) to your home will magically become yours again.

If I've got this all wrong, my apologies.

---

### Post by Kellemora on 2010-06-01
Hi YM and AJ

I have an Ubuntu Hardy 64 bit I've been using now for years, file system is EXT3........ with /home in it's own partition.  This is computer A above.

I created a Shared Folder on Computer B, also Ubuntu Hardy 64 bit, file system EXT3 as well.  

Using Places Network on Computer A I mounted the shared folder from Computer B onto Computer A to make the transfer of files a little easier.

I've done this many times in the past with no problems, when I needed to exchange files between computers.  
But it seems I did have a problem and found it works better if you FETCH a file from Computer A by using places network on Computer B as an example.
I just forgot is all.

However, as an experiment, I created another folder on another machine, pulled it from this machine, made changes to the docs I placed in it, no problems.  Yet I didn't do anything different than I did before.

I have also discovered that I cannot write to files on other machines now too.  They won't save, saying the drive is read only.  However, if I create a folder, move the document to it, on the other machine, I can then write to it with no problems.

I think my problem was PUTTING the Computer A files onto the Computer B machine RATHER THAN using Computer B to FETCH the files from Computer A.

The other problem is, If I try to change the PERMISSIONS as ROOT, it will only change the permission of the LEAD Folder (directory) even though I tell it to change ALL files, NONE get changed.

Since I do have 3 other backups, one external drive local, one external in another building and one way off-site by 500 miles.  It's not like I have lost the data.  I just can't seem to use it.

I'm in the process right now of having my new computer B FETCH all the files from the External Drive, which is slow since it's over usb.
Those files (the external drive is formatted NTSF because it has mostly WinDOZE files on it.  And often needs to be connected to a Doze machine.

But even as ROOT I can't seem to GLOBALLY correct the permissions of the files residing on this computer.

I THINK after the files download from the external, I may have more luck.
With that in mind, I moved all the current files into their own folder, I named BAD DOG, hi hi.........

We'll see how it goes, I've lost an entire day of work, once again, due to BUGS in UBUNTU that have never been corrected!

It's just a shame I forgot about the bug-fix workaround before we wiped the hard drive on Computer A........

As I said in my other post, Copying a FILE should NEVER change the Permissions of that FILE, OR FOLDER, or ALL THE FOLDERS and Files in that Folder.

As much as I like Ubuntu and the people behind it, I'm seriously considering going back to CentOS with no outside help to turn to.
At least what works on Red Hat would work on CentOS the same way, and nearly every problem in Red Hat has been ironed out and/or documented.

I can go for months with ZERO problems, Ubuntu works right out of the box, so to speak.  But when I do have problems, NOTHING that should work to fix them, ever does.

Which could be Pilot ERROR too by the way, hi hi.......

Hey, thanks for you help guys!
I'll get it figured out somehow.

TTUL
Gary

---

### Post by Calash on 2010-06-01
sudo chown xxx:xxx is not working?  That is odd, it should be from what I know.

Just want to verify you tried sudo with chown and chmod before going farther with the troubleshooting.


Edit: I missed your last post.  It seems like you tried with root permissions and using the -R flag.  Not sure what to suggest next but I do wish you luck.

---

### Post by Kellemora on 2010-06-01
Hi Calash

I was able to upload a new set of files from my file server and get the permissions to work with them.

Where I had gone wrong was I had forgotten about the BUG in Ubuntu that's been there as long as I've been using Ubuntu.

You cannot PUT files onto another computer, only FETCH them from another computer, else it messes up permissions big time.  Unless you use RSYNC to do it.  I do manually copy files to the File Server and found most of those have the same NOBODY NOGROUP problem as well, but chown usually fixes them.

In any case, Even though the BUG has never been fixed, I'm marking this file solved.

TTUL
Gary

---

