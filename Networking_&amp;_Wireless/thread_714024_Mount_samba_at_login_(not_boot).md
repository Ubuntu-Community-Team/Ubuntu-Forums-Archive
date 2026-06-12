---
title: "Mount samba at login (not boot)"
date: 2008-03-03
forum: Networking &amp; Wireless
---

### Post by aweller on 2008-03-03
Dear all,

I have several networked drives that I would like to mount with samba at user login, not during boot (i.e. not using fstab), because different users have different network shares.

The idea is that I can put the code in "System > Preferences > Sessions" as start-up programs and voila, my networked drives appear as folders in Nautilus (for easy backup purposes, etc).

I have tried:
```
smbmnt //SHARE /mnt/share
```
and
```
smbmnt //SHARE /mnt/share -o username=XYZ,password=123
```
to no avail.

I also know that:
```
sudo mount -t cifs -o 'username=XYZ,uid=XYZ,gid=XYZ,domain=DOMAIN' '//SHARE' /mnt/share
```
works, but I cannot "sudo" from "System > Preferences > Sessions".

I am using Gutsy.

Many thanks, Andy

---

### Post by fazavon on 2008-03-03
This should help

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

Thanks

//j

---

### Post by aweller on 2008-03-04
Thanks for your reply.  Not having tested the link yet, it looks like it involves a fstab edit, which means all users will have access to the *same* samba mounts.

I'm really not after this.

I would like to put commands in "System > Preferences > Sessions" to start-up for each user so that their respective samba shares are mounted at login.

So, for example, there are two shares:

//SHARE/Andy
//SHARE/Claire

when user "Andy" logs in, I would like his share to be accessible to him.  Alternatively, when user "Claire" logs in, I want her share to be accessible to her.

I don't want to create "//SHARE" for all in fstab.  The reason being: I know this works (in a shell):

```
sudo mount -t cifs -o 'username=XYZ,uid=XYZ,gid=XYZ,domain=DOMAIN' '//SHARE' /mnt/share
```

but not all users can "sudo".

I hope that makes sense?!

Thanks!

---

### Post by fazavon on 2008-03-04
Yes you do have to, but it is still relent on if they have access to the said share.

---

### Post by aweller on 2008-03-05
Bump!

I guess the simple question is why does the command:

```
sudo mount -t cifs -o 'username=XYZ,uid=XYZ,gid=XYZ,domain=DOMAIN' '//SHARE' /mnt/share
```

not work as a start-up program/command from within "System > Preferences > Sessions"?  (My guess is that it has something to do with sudo?!)

Or, how can I set the command to run in a terminal?

---

### Post by aweller on 2008-03-05
OK, I have figured out a temporary solution, but this still involves sudo-ing:

```
gnome-terminal -x sudo mount -t cifs -o 'username=XYZ,uid=XYZ,gid=XYZ,domain=DOMAIN' '//SHARE' /mnt/share
```

Perhaps I can make mount usable by all?  Is this dangerous?

---

### Post by Eiríkr on 2008-03-05
One option would be to mount the shares *not* in the globally accessible [font=courier]/mnt[/font] directory but rather somewhere in each individual home.  Then the shares could all be mounted at boot and still have access restricted to each individual user.

However, as [post=2470296]this post[/post] notes, there are some problems with boot-time Samba share mounting, apparently due to Ubuntu-specific boot order issues, that require adding a couple lines to your [font=courier]/etc/rc.local[/font] file (also included in that post :)).  

And yes, any command involving [font=courier]sudo[/font] will *not* work properly as an automated solution.  [font=courier]sudo[/font] by its very definition requires the user to input the proper password, and this cannot happen in any automated no-input setup.  If you really want to use a script that runs on login, you could use one owned by root but executable by members of a certain group, and with the setuid bit set (so anyone running it runs it as root).  The script would then make use of the $USER variable to figure out who ran it, and likely use that to figure out the name of the share to mount.  

HTH,

Eiríkr

---

