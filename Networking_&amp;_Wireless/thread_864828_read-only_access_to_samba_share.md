---
title: "read-only access to samba share"
date: 2008-07-20
forum: Networking &amp; Wireless
---

### Post by snowguy on 2008-07-20
Hi, I'm having the following problem. When I go under places>connect to newtork and then connect to a share drive on samba it works great. I get read-write access to the share. However, when I use the same samba share drive using this in my fstab

//192.168.1.103/matthew  /media/samba_share  cifs  rw,users,auto,credentials=/etc/samba/user,noexec 0 0

Unfortunately though this works, I am not getting the ability to write to the drive unless I open it using sudo. Any suggestion on how I can get read-write access to this drive?

---

### Post by cdtech on 2008-07-20
I believe it's ::.
```
//192.168.1.103/matthew	/media/samba_share smbfs dmask=777,username=,password=	 0 0
```

**Update::.**
```
//192.168.1.103/matthew	/media/samba_share cifs username=,password=	 0 0
```

This is what works for me....

---

### Post by snowguy on 2008-07-22
sorry that didn't help. But I did finally figure it out based on a comment in: [http://ubuntuforums.org/showthread.php?t=280473](http://ubuntuforums.org/showthread.php?t=280473)

it turns out that I had to have the same ids for the user on both boxes. Here's the details as best I understand them.

On the samba server I have a username matthew. The id = 1001
on the client I also have a user matthew but the id there = 1000. On that same client box I have another user with id = 1001. I could tell by looking at the properties of the mount point /media/samba_share (once it was mounted) that the user with id = 1001 was listed as the owner. As noted in the post this read-only problem did not occur when using the gui connect to server. Also, interestingly if I used umount to unmount the share then it would show the owner of /media/samba_share as root. So I could tell that somehow it was picking up the wrong owner in the process of mounting. Anyway, it seemed like I should have been able to solve this issue by changing some setting in my fstab--but nothing seemed to work. 

What I finally did is changed the uid on both boxes for the matthew account to 1010. (Following a hint in the above link.) I did this with the command:

sudo usermod --uid 1010 matthew

on both boxes.

That worked though I hope it doesn't break something else. IF it has broken something else, so far I haven't noticed that. But what a pain! It certainly doesn't seem like people should have to try and coordinate uid's across boxes. Does anyone else have a simpler solution? There's got to be a better one than this.

---

