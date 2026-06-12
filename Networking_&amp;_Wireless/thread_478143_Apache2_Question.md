---
title: "Apache2 Question"
date: 2007-06-19
forum: Networking &amp; Wireless
---

### Post by ItsJweed on 2007-06-19
After several hours of goofing around and searching google (and these forums) I've managed to learn a bit about apache2 and enable it on both of my Ubuntu computers. One is running Ubuntu server edition and I've managed to get that one to do what I want. 

Here is what I'm trying to do that isn't working:

On my standard Ubuntu machine, apache2 is enable and working but I can't access an external hard drive - even when apache's starting directory is /dev/media. Is there something I need to do in apache to get this to work or is there something I am doing wrong as far as mounting - the drive is unnaccessable even when mounted. 

Thanks, I appreciate any help.

---

### Post by Mr. C. on 2007-06-19
Apache knows nothing about hard drives.

All access to files is via the *nix file system.  This requires that the file system is mounted somewhere.  If you can list the files with the command line ls, then apache has access as well (I'm ignoring permission here)

Have you checked the output of the mount command to see if the file system in question on the external drive is mounted ?

MrC

---

### Post by ItsJweed on 2007-06-19
I just mounted (a second time) the drive from the command line rather then letting Ubuntu take care of it - to no avail. Mount returns (among others):

/dev/sdc1 on /media/externalhd type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)

and

;this is where I mounted it from the command line
/dev/sdc1 on /media/externalhdview type vfat (rw) 

Which leads me to believe the device is mounted fine... Yet when I navigate to the /media/ folder apache doesn't show the 'externalhdview' folder I know exists...

---

### Post by SkyNet2029 on 2007-06-19
> **ItsJweed said:**
> 
and

;this is where I mounted it from the command line
/dev/sdc1 on /media/externalhdview type vfat (rw) 

Which leads me to believe the device is mounted fine... Yet when I navigate to the /media/ folder apache doesn't show the 'externalhdview' folder I know exists...

Am I being dumb or did you mount that manually in a different directory than that specified by fstab?

'/dev/sdc1 on /media/externalhdVIEW'  ?

---

### Post by Mr. C. on 2007-06-19
What do you mean "when I navigate to the /media/ folder apache doesn't "?

How does *your navigating* affect apache?  Apache will "see" whatever you've configured it to see.  You'll have to be more clear in describing the precise problem.

If the permissions on the directory and files preclude apache from accessing, you'll need to change the permissions.

MrC

---

### Post by ItsJweed on 2007-06-19
> **SkyNet2029 said:**
> Am I being dumb or did you mount that manually in a different directory than that specified by fstab?

'/dev/sdc1 on /media/externalhdVIEW'  ?

It didn't work when it was mounted automatically or when I specified through properties the mount point. (view the attached picture for clarification) Since that didn't work, I also mounted it through the command line to externalhdview. (which also didn't work)

Mr. C -

When I am in a web browser opened to my apache2 server (with no index file) it shows its current directory and lets me browse subdirectories and files. It is here that I can navigate to /media/ and see the cdrom device etc. but the hard drive doesn't show up, even though I know it is mounted under /media/externalhd. (And was also mounted under /media/externalhdview until I rebooted.)

---

### Post by ItsJweed on 2007-06-19
I just attached another two screenshots for clarification. The first shows the problem I'm having with apache2 not displaying all the folders in /media. The second shows there are folders in /media/ apache2 isn't displaying.

---

### Post by Mr. C. on 2007-06-19
Try to avoid the "it doesn't work" statement. It provides no useful data.

Have you examined your apache error logs ?
Have you examine the permissions of the mount point?

MrC

---

### Post by ItsJweed on 2007-06-19
The mount point is set to grant my user full access and no access to any other users. (It won't let my change it through the permissions window - perhaps sudo chmod would) When I checked the error log I got this (repeated several times and also for my other internal HD which I'm not as concerned about sharing but the message is the same except the different file path)-

[Tue Jun 19 20:13:32 2007] [error] [client 192.168.1.1] (13)Permission denied: access to /media/externalhd/index.html denied, referer: [http://**.**.***.***/](http://**.**.***.***/)
[Tue Jun 19 20:13:32 2007] [error] [client 192.168.1.1] (13)Permission denied: access to /media/externalhd/index.cgi denied, referer: [http://**.**.***.***/](http://**.**.***.***/)
[Tue Jun 19 20:13:32 2007] [error] [client 192.168.1.1] (13)Permission denied: access to /media/externalhd/index.pl denied, referer: [http://**.**.***.***/](http://**.**.***.***/)
[Tue Jun 19 20:13:32 2007] [error] [client 192.168.1.1] (13)Permission denied: access to /media/externalhd/index.php denied, referer: [http://**.**.***.***/](http://**.**.***.***/)
[Tue Jun 19 20:13:32 2007] [error] [client 192.168.1.1] (13)Permission denied: access to /media/externalhd/index.xhtml de

(EDIT)Just checked and apparently even 'sudo chmod 777 /media/externalhd' didn't change the permissions on the drive.

---

### Post by Mr. C. on 2007-06-19
Well, you certainly want to grant rights to www-data to see the files.

Your files need to be mode 644 and directories 755 if you want apache to be able to read them.

You will need root privs to change them if you do not own them.

MrC

---

### Post by ItsJweed on 2007-06-20
Hmm. Running 'sudo chmod -R 755 /media/externalhd' did not allow apache to "see" the files. I had to change the permissions back to 777 to copy some files onto my other computer using rsync and then sure enough the new folder was not visible. (The other computer has apache running) I chmoded the new folder on the other computer to 755 and sure enough it is now visible and all is well - for that computer. Yet for some reason even when I changed the permissions on the entire external drive on this computer I'm still having the same problem. Is it possible that because the external drive was originally written to on Windows the file permissions are somehow unchangeable/corrupt? 

Also, could you please explain to me how to set the folder permissions to 755 and the file permissions to 644? I've only been able to find how to set everything the same.

It appears I can't change anything but my own user's permissions. Here is the output of 'ls -ls' after setting permissions back to 777:

total 224
32 drwx------  6 me root 32768 2007-01-22 16:26 Backup Folder
32 drwx------  4 me root 32768 2007-01-22 16:18 BitTorrent Downloads
32 -rwx------  1 me root   104 2007-06-18 19:58 index1.html
32 drwx------  8 me root 32768 2007-05-30 17:39 Local Disk
32 drwx------  2 me root 32768 2007-03-16 19:26 Recycled
32 drwx------ 12 me root 32768 2007-01-19 10:00 Southpark
32 drwx------  4 me root 32768 2006-12-24 21:04 System Volume Information
 

(I just started with Linux about two weeks ago and through trial and error coupled with google I've learned to do a few things. Yet there is still way more I need to learn...)

---

### Post by Mr. C. on 2007-06-20
In my last post, I failed to re-read how your file system was mounted, and what type it was.  I see now that it is vfat.

Windows file system and Unix/Linux file system have different concepts of permissions. They do not map one-to-one.  There is no "Group" or "Other" permissions in vfat.

Your uid (1000) owns the files, and they show up as read/write for only you.  Try unmounting, and re-mounting with umask=000 in your mount command, as well as gid=APACHEGIDHERE.   Umask generally affects only the creation of new files and directories.  It may be that umask here will also mask how the permissions appear as well, given that would be the only way to make files accessible by group/others.

Sorry for the bad advice earlier.

MrC

---

### Post by ItsJweed on 2007-06-20
No problem, thanks for the advice at all. I checked my groups file '/etc/group' and I don't see apache listed. How do I go about determining apache's group id? Sorry if these are stupid questions, I couldn't find the answer to this one on google.

(EDIT) - Nevermind, I found it. It's the group www-data, right?

---

### Post by Mr. C. on 2007-06-20
Right, www-data.

MrC

---

### Post by ItsJweed on 2007-06-20
It gives me an "invalid mount option" error when I try 'gid=33'  (33 is www-data's group number) Nevertheless, just adding 'umask=000' fixed the problem I've been having all along, and now I can navigate to my external HD through apache. Thank you so much for the help; I've spent so much time screwing around trying to get this to work.

J

---

### Post by Mr. C. on 2007-06-20
Great to hear.

Can't comment on the illegal mount option without seeing the actual command line and error.  But you're up and running now, so that's probably good enough.

And thanks for the follow-up; you've confirmed be belief about how umask would have to operate to make sense.

Cheers,
MrC

---

