---
title: "NFS shares"
date: 2006-12-09
forum: Networking &amp; Wireless
---

### Post by daveyiv on 2006-12-09
I have the following shares setup in my /etc/exports file:

```
/media/data     192.168.0.100(rw)
/media/music    192.168.0.100(rw)
/media/videos   192.168.0.100(rw)

```

However, when I mount them from another client, I am able to add files and stuff, but once it is there I can't delete it or anything. It says I don't have permission. What would cause it to say that I don't have permission, when I am able to copy files to there?

I am able to remove the files through a terminal using sudo rm filename, but can't through nautilus

The mount command i'm using is:

```
sudo mount -t nfs spork:/media/videos /media/shares/spork/videos
```

---

### Post by DaveBorealis on 2006-12-09
> **daveyiv said:**
> I am able to remove the files through a terminal using sudo rm filename, but can't through nautilus

Hello,

I'm not certain I fully understand the behavior.

What happens if you open a terminal on a client, do something like 'touch hi.txt' to creat a file in the mounted directory, and then do  a 'rm hi.txt'?  You get 'permission denied'?  Or is it a Nautilus thing?

Dave

---

### Post by daveyiv on 2006-12-09
It's a nautilus thing, I can move files to a directory in nautilus, but cannot remove them.

However, if I do it in terminal it works fine for moving to and deleting from, it's just a terminal is a pain in the *** for a large number of files that are scattered all over the place.

---

### Post by DaveBorealis on 2006-12-09
> **daveyiv said:**
> It's a nautilus thing

On my Dapper 6.06 I can copy files to a mounted directory via Nautilus, and then delete it.  (However my server is a FreeBSD.)

Have you looked at the properties nautilus gives for a file that you created in the remote directory?  (Right click on the file icon, select 'Properties' and the 'Permissions' tab.)  Do the owner, group, and permissions match with what you get when you use a terminal to list the same file?

---

### Post by daveyiv on 2006-12-09
Nautilus shows permissions as read and write for all 3 and terminal shows -rw-rw-rw- as the permissions.

edit:

For some reason I didn't have access to the .Trash directory

Which leads me to another question, why do all my files default to a permission level that I am unable to write to. How can I make them default to a permission which I can modify?

---

### Post by DaveBorealis on 2006-12-09
> **daveyiv said:**
> 
Which leads me to another question, why do all my files default to a permission level that I am unable to write to. How can I make them default to a permission which I can modify?

Ah, another piece of the puzzle!  Perhaps with Nautilus you're working with a umask.  Use Nautilus to create a file on the remote directory, then right click the icon and click the permissions to read and write for everyone.  Then see if you can delete it.

Also, when you right click the icon, are the owner and group what they should be?

---

### Post by daveyiv on 2006-12-10
When I create a file in nautilus the default permissions are set as owner is the account im using on the client computer and has read and write access, while group and everyone have none as their access privileges. However, I can then change them to read and write for everyone and I am able to delete the file. 

How can I change the default permission level nautilus is apparently giving it as 700?

---

### Post by dmizer on 2006-12-10
as you've realized the problem is permissions.  follow the nfs howto in my sig and you'll have a working nfs client/server with read write capabilities.

---

### Post by DaveBorealis on 2006-12-10
> **daveyiv said:**
> 
How can I change the default permission level nautilus is apparently giving it as 700?

I'm not sure, but on the client machine open up .bash_profile (note the leading period) in the home directory, and see if there's a line with umask in it, something like 'umask = 077'.  If there isn't a '#' in front of it, put one there to comment out the line so it's ignored.  That might be the problem.

The .bash_profile is a "hidden" file, so if you're looking for it with Nautilus, under 'view' click 'Show Hidden Files'.

[edit]The problem could also be in your '/etc/fstab', assuming that you have a the remote directories listed there on the client.  Could you post what you have in it?  There might be a misconfigured umask there!

---

### Post by daveyiv on 2006-12-10
> **DaveBorealis said:**
> I'm not sure, but on the client machine open up .bash_profile (note the leading period) in the home directory, and see if there's a line with umask in it, something like 'umask = 077'.  If there isn't a '#' in front of it, put one there to comment out the line so it's ignored.  That might be the problem.

The .bash_profile is a "hidden" file, so if you're looking for it with Nautilus, under 'view' click 'Show Hidden Files'.

[edit]The problem could also be in your '/etc/fstab', assuming that you have a the remote directories listed there on the client.  Could you post what you have in it?  There might be a misconfigured umask there!

I could post it, but I don't have any NFS shares in there right now. I was just trying to mount them manually the whole time with ```
mount -t spork:/media/videos /media/shares/spork/videos
```


I followed the guide in your signature above, dmizer, but most of my directories on the shares still contain files with the lock emblem on them and permissions are set to 700

---

### Post by DaveBorealis on 2006-12-10
Have you looked in .bash_profile to see if umask was set there?  You can also take a peek at '/etc/profile'.

Dave

---

### Post by daveyiv on 2006-12-10
Yeah, it is commented out.

---

### Post by dmizer on 2006-12-11
okay ... here's your issue.  on the server side, you've placed all your folder mounts in /media which is by default owned by root.  you have to change your /media/data /videos and /music to 700 or 777 ownership.  that or you need to serve shares from your home folder instead of the media folder.

also, in your exports file, don't forget to include the no_root_squash and async options in the brackets like so:
```
/media/data     192.168.0.100(rw,no_root_squash,async)
```

---

