---
title: "Mounting ext3 partition, no R-W permission"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by Ordes on 2009-04-28
Dual Boot XP Ubu;

System:
sdb1 : Linux
sdb2 : Home
sdb3 : Public storage (was preformatted in ext3, and i intended it to be a drive where all users can put on files)

During install i didnt touch the the sdb3.

Now:
I can mount sdb3 from nautilus, but have no r-w permission. i can r-w with sudo.

i tried fstab:

/dev/sdb3 /media/Public ext3 rw,auto,user,exec 0 0

it gets mounted, but still no r-w permission.

but when i mount to /media/disk (this is where my Win ntfs is mounted) than i get r-w permission. but only with /media/disk, how can i change that? because i cant keep it like this, because in this way it will always interfer with my ntfs drive.

or any other way to mount sdb3 on /media/Public with r-w permissions?

thanks

---

### Post by Peter09 on 2009-04-28
What are the permissions on the mount point - /media/Public

---

### Post by Ordes on 2009-04-28
mhm, u mean on the folder in -Public- in /media/ ?

they are root.

Are you thinking to give the folder user permissions? Can i do this for multiple users, or do i than have to use user-goups?

---

### Post by northern lights on 2009-04-28
> **Ordes said:**
> Are you thinking to give the folder user permissions? Can i do this for multiple users, or do i than have to use user-goups?
You can do either.

At any rate, user(s) have to have read/write permissions in the folder you mount to.

Sidenote: Take care not to mix up ownership and permissions. The folder can be owned by root and still be given varying permissions for regular users.

[man chmod]("http://linux.die.net/man/1/chmod")

---

### Post by Ordes on 2009-04-28
thanks so far. but could you be so nice the tell me the command for chmod. i looked at the link, but didnt quite get it.

Lets say, User1 "He"  User2 "She"

How would the comand look like to give both users permission to R-W on the drive?

thanks

---

### Post by northern lights on 2009-04-28
```
sudo chmod -R 766 /media/Public
```

The initial *sudo* is only necessary if the file is owned by root. Alternatively, you could give ownership to the user "He":

```
sudo chown HE:GROUP_OF_HIM /media/Public
```where *HE* and *GROUP_OF_HIM* obviously need to be replaced by the respective user- and groupname (most likely identical) of your setup.

If you've done this (given ownership to the user "HE"), you can run the *chmod* command without *sudo*. Further, if "HE" and "SHE" are in the same group, you can use octal code *760* or *764* instead of *766*, which would be safer.

Octal codes:

XYZ:
X - owner's permissions
Y - group member's permissions (other users who are in the owner's group)
Z - permissions for other users

4 - read permissions
2 - write permissions
1 - execute permissions

---

### Post by Ordes on 2009-04-28
"he initial sudo is only necessary if the file is owned by root. Alternatively, you could give ownership to the user "He":
"

You say alternatively give the ownership to "He", so 
--sudo chmod -R 766 /media/Public-- would this give rights to all? or do i need all the other commands? What exaclty does the command 766 do? Further He and She are in one group.

Sorry to ask so much, but i really like to understand what i am doing.

Why is it, that when i mount ntfs partitions everyone can read and write, and when i mount ext3, no one has permissions? is there something i did wrong first, or is it supposed to be so?

And is than there no command like "give permissions to everyone"?

---

### Post by northern lights on 2009-04-28
> **Ordes said:**
> sudo chmod -R 766 /media/Public -- would this give rights to all?Read (further denoted by "r"), Write (further denoted by "w") and Execution (further denoted by "x") rights to the owner (i.e. rwx), whoever he is, rw rights to both group member and everyone else.

> **Ordes said:**
> What exaclty does the command 766 do?It's an *octal code* and part of the *chmod command*. I tried explaining that in my earlier post.

First value: owner's permissions
Second value: group member's permissions
Third value: Everyone else's permissions

r = 4
w = 2
x = 1

Any combination is just the sum:

rw = 6
rwx = 7
and so on

If the owner is "He" and "She" is in the group, you need not give permissions to anyone outside the group, so you can make the third value 0.

> **Ordes said:**
> 
Why is it, that when i mount ntfs partitions everyone can read and write, and when i mount ext3, no one has permissions? is there something i did wrong first, or is it supposed to be so?
Nothing you did wrong. Defaults.

> **Ordes said:**
> And is than there no command like "give permissions to everyone"?```
chmod 777 /path/to/file
```
would do that, but giving execution rights to everyone is something I wouldn't recommend.

---

### Post by timcredible on 2009-04-28
> **Ordes said:**
> 
Why is it, that when i mount ntfs partitions everyone can read and write, and when i mount ext3, no one has permissions? is there something i did wrong first, or is it supposed to be so?
ext3 has file permissions, you aren't supposed to be able to just overwrite other people's files, so what you're seeing is intentional.  keep in mind that it's not usernames that are important in linux/unix, it's the UID - if the UID on the system matches any UIDs on the ext3 system you're using, then those people can write their own files.  ntfs has file permissions, but i don't think the linux driver for it pays attention to them.  if you want everyone to be able to access all files all the time, just use fat32.

---

### Post by Ordes on 2009-04-28
Thanks northern lights, helped me out a lot.

But when you use fat32, you would have fragmentation, which ext3 can prevent. Furthermore you would have a limit to 4gb file size. Right?

---

### Post by northern lights on 2009-04-29
> **Ordes said:**
> But when you use fat32, [...] you would have a limit to 4gb file size. Right?True.

---

