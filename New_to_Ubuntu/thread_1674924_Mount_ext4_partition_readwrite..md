---
title: "Mount ext4 partition read/write."
date: 2011-01-24
forum: New to Ubuntu
---

### Post by victorhugo289 on 2011-01-24
Hi, I want to mount an ext4 partition but it keeps mounting as read-only, it appears on my desktop and I can see the files but the 'Create new Folder' and other options are grayed-out, so I can't do much with it.

I use the usual command:
----"sudo mount /dev/sda6 /media/EXT4part"

I've tried using this:
----"sudo mount -t ext4 -o defaults,uid=1000,noatime /dev/sda6 /media/EXT4part"
but it gives me the following error:
"mount: wrong fs type, bad option, bad superblock on /dev/sda6,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so"

I've used 'chown' on the mountpoint directory before mounting:
---"sudo chown 777 /media/EXT4part"
and the directory appears with my name, but as soon as I mount the Ext4 partition it becomes 'root'. :(

I've managed to mount NTFS and VFAT already without using the 'chown' command and I thought Ext4 was supposed to be easier.

Any help? thanks.

---

### Post by sikander3786 on 2011-01-24
Please see here if it is of any help to you.

[http://ubuntu4beginners.blogspot.com/2011/01/permanently-mount-ext3ext4-drives-with.html](http://ubuntu4beginners.blogspot.com/2011/01/permanently-mount-ext3ext4-drives-with.html)

---

### Post by victorhugo289 on 2011-01-24
> **sikander3786 said:**
> Please see here if it is of any help to you.

[http://ubuntu4beginners.blogspot.com/2011/01/permanently-mount-ext3ext4-drives-with.html](http://ubuntu4beginners.blogspot.com/2011/01/permanently-mount-ext3ext4-drives-with.html)

I did what it said, except that I don't want to automount it on startup, so I just did it on the terminal, I chowned the mount-point directory and it said "Victor Victor", right, but as soon as I mounted the Ext4 partition it became root, it no longer said "Victor victor". ](*,)

---

### Post by sikander3786 on 2011-01-24
Try the recursive switch.

```
sudo chown -R username:username /place-to-mount
```

Or, I am not sure if those permissions would last for a single session only :-k

---

### Post by victorhugo289 on 2011-01-24
> **sikander3786 said:**
> Try the recursive switch.

```
sudo chown -R username:username /place-to-mount
```Or, I am not sure if those permissions would last for a single session only :-k

Same stuff, "Create Folder" and other options is grayed-out.

Now, something tells me that this is not a read-only mount problem but that I have to 'chown' all the files in that partition, Is that so?
But I thought I could just mount it as "read-write" all together, :/

---

### Post by lucius.antonius on 2012-12-31
look here: 
[http://askubuntu.com/questions/159992/how-to-mount-ext4-partition](http://askubuntu.com/questions/159992/how-to-mount-ext4-partition)

---

### Post by oldfred on 2012-12-31
Closed, necromancy. Old thread closed.

From the Ubuntu Forums Code of Conduct.
[http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

"If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful."

---

