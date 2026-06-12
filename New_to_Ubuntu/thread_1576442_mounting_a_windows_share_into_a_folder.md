---
title: "mounting a windows share into a folder"
date: 2010-09-17
forum: New to Ubuntu
---

### Post by digitography on 2010-09-17
I want to mount a windows share into my documents folder on Ubuntu.
Can this be done?

---

### Post by QLee on 2010-09-17
> **digitography said:**
> I want to mount a windows share into my documents folder on Ubuntu.
Can this be done?
Yes.
You will probably want to have a look at these:
Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

Ownership and permissions of vfat / ntfs are set at the time of mounting.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

---

### Post by sikander3786 on 2010-09-17
It surely can.

[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

---

### Post by Elfy on 2010-09-17
If you want it to show in the Documents folder you will need to symlink it I think.

---

### Post by digitography on 2010-09-17
> **forestpiskie said:**
> If you want it to show in the Documents folder you will need to symlink it I think.
What's a symlink?

---

### Post by QLee on 2010-09-17
[QUOTE=digitography]What's a symlink?[/QUOTE]
"A symbolic link is a special type of file whose contents are  a  string
       that  is  the pathname another file, the file to which the link refers.
       In other words, a symbolic link is a pointer to another name,  and  not
       to  an underlying object."
I've copied that from the manual page, which you can read for more information by entering the command, man symlink, in a terminal.

What forestpiskie is suggesting is creating a symlink (symbolic link, similar to Windows shortcut) from the mountpoint you choose to a folder in your documents or links to your files on the mount, depending on your specific needs.

---

### Post by digitography on 2010-09-17
> **QLee said:**
> 

What forestpiskie is suggesting is creating a symlink (symbolic link, similar to Windows shortcut) from the mountpoint you choose to a folder in your documents or links to your files on the mount, depending on your specific needs.
Well that sounds like a fine solution, but how?

---

### Post by digitography on 2010-09-17
scratch that figured it.
However if I try to symlink to a folder in my share I get an error telling me that symlinking is not supported.
So back to square 1

---

### Post by egalvan on 2010-09-17
> **forestpiskie said:**
> If you want it to show in the Documents folder you will need to symlink it I think.

If an NTFS partition can be permanantly mounted to  mount point under 

/media   (icons appear on desktop)

 or

/mnt    (icons do not appear on desktop)


why would it not be possible to create a mount point under the 

/home/*user-name*/Documents


would it not be as simple as 
create empty directory under 
/home/*user-name*/Documents
giving it the name that you want for your mount point...
then mounting via fstab?



Only my main work machine is running at this moment, so I have no 
"play-with-Linux" machine to test it on...
Anyone else?

---

### Post by Elfy on 2010-09-17
> why would it not be possible to create a mount point under the Maybe you can - I've not got access to anything that I can play with either at the moment.

I've not ever tried to 'play' about with any of the default folders in /home - other than symlinking media drives.

---

### Post by egalvan on 2010-09-17
> **forestpiskie said:**
> Maybe you can - I've not got access to anything that I can play with either at the moment.

Man, I have **got** to get those other machines up and running...
I truly miss "playing" with things Linux :)
Way too much on my plate at this time... 

> I've not ever tried to 'play' about with any of the default folders in /home - other than** symlinking media drives**.

I agree there.. I've seen several excellent "how-to" describing this scenario.

It would be very interesting to find a good analysis/comparison of symlinking versus mounting.

Cheers.

---

### Post by Elfy on 2010-09-17
I'd not be able to do any comparison any longer - I finally got a drive big enough to not need to have some from this pc and others mounted with nfs from another PC. 

The other thing I thought about briefly in mounting an ntfs driectly into a /home was the way permissions work here and there, not sure if that would cause an issue or not and I've not got any ntfs partitions anywhere any longer.

---

