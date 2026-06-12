---
title: "How do I mount / unmount a 2nd internal harddrive at will?"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by cat2005 on 2009-09-20
How do I mount / unmount a 2nd internal harddrive at will?  

I know how to "auto" mount it, but that is not what I want.  Automounting makes the mount permanent.  I do not want it permanently mounted.  I want any of my users to be able to issue a "mount" or "umount" command have have the proper action happen.

I assume I would need to edit fstab to do so, but what language would I use?  Or would I use something other than fstab?

---

### Post by drs305 on 2009-09-20
If the partitions are listed in fstab and you add "users" to the fstab options it should allow anyone to mount/unmount a partition.  ( ... defaults,users 0 2 )

From the *mount* man page:
> 
**users**  Allow  every  user  to  mount and unmount the file system.  This option implies the options noexec, nosuid, and nodev (unless overridden by subsequent options, as in the option line users,exec,dev,suid).


---

### Post by theozzlives on 2009-09-20
> **cat2005 said:**
> How do I mount / unmount a 2nd internal harddrive at will?  

I know how to "auto" mount it, but that is not what I want.  Automounting makes the mount permanent.  I do not want it permanently mounted.  I want any of my users to be able to issue a "mount" or "umount" command have have the proper action happen.

I assume I would need to edit fstab to do so, but what language would I use?  Or would I use something other than fstab?

Take the command out of the fstab and when you plug it in it'll mount, to unmount... right click and go to Unmount Volume.

---

### Post by cat2005 on 2009-09-20
drs305,

No, it currently does not appear in my fstab.  If I mount it, then it might.  However, now I can only mount it if I sudo / give my admin password.

Yes, I read that but didn't fully understand it.  What exactly is "nosuid"?

---

### Post by scrooge_74 on 2009-09-20
You need to declare it in fstab and use the options user and the option noauto 

That way any user can mount it or unmount it and the noauto will avoid it from getting mounted at boot time

---

### Post by cat2005 on 2009-09-20
I did more research and might have discovered a basic syntax (finding a place to learn this stuff in simple English is tough).

**FYI:**  It is a 2nd internal harddrive, all in ext3.  Currently, only root can mount it.  I want all users to mount it.  I labeled it:  2nd

Gparted reported it as:  sdb1

_Here is something I was thinking_:

**Device:**  sdb1
**Mount Point:**  /media/2nd  (I assume I would have to mk dir, since "2nd" does not yet exist)
**File System:**  ext3
**Options:**  This is confusing me.  I have a good idea of the options I need, but does it matter the order in which I write them?  _Here they ar_e:  noauto, user, noexec, rw, sync
**Dump: ** I do not understand this.  All I know is "0" means "ignore" and "1" means "backup".  Which should I select?
**Fsck:**  I do not understand this:  All I know is "0" means "ignore".  Surely options exist.  What should I do?

My main "hang-ups" are with "options" "dump" and "fsck".  As you can see, I have some lingering questions.  Could anyone help?

---

### Post by scrooge_74 on 2009-09-20
Here is a line from laptop fstab for one of my nfs mounts

192.168.2.2:/mnt/musica /mnt/musica nfs rsize=8192,wsize=8192,timeo=14,noauto,user,rw


This is from my server /etc/exports

/mnt/musica/ 192.168.2.0/255.255.255.0(rw,sync,no_subtree_check)

---

### Post by blackened on 2009-09-20
> **scrooge_74 said:**
> You need to declare it in fstab and use the options user and the option noauto 

That way any user can mount it or unmount it and the noauto will avoid it from getting mounted at boot time

+1. Declare it in fstab with noauto,user,rw and you should be good.

---

### Post by cat2005 on 2009-09-21
So, what do you folks think of this potential syntax:
 
/dev/sdb1  /media/2nd  noauto,user,noexec,rw,sync  0 2
 
Must I use a specific editor for the fstab, or would "sudo gedit" work well?
 
Thanks.

---

### Post by blur xc on 2009-09-21
> **cat2005 said:**
> So, what do you folks think of this potential syntax:
 
/dev/sdb1  /media/2nd  noauto,user,noexec,rw,sync  0 2
 
Must I use a specific editor for the fstab, or would "sudo gedit" work well?
 
Thanks.

sudo gedit cuts the mustard

I've done it plenty of times.

There is a program that can do it for you, but I don't recall what it's called...

BM

---

### Post by scrooge_74 on 2009-09-21
> **cat2005 said:**
> So, what do you folks think of this potential syntax:
 
/dev/sdb1  /media/2nd  noauto,user,noexec,rw,sync  0 2
 
Must I use a specific editor for the fstab, or would "sudo gedit" work well?
 
Thanks.


Sounds about right

On the editor everything is good, I just open a terminal and so

sudo nano /etc/fstab

---

### Post by blackened on 2009-09-21
> **scrooge_74 said:**
> Sounds about right

On the editor everything is good, I just open a terminal and so

sudo nano /etc/fstab

If you've never used nano before, then you might be more comfortable using gedit. T

hat said, nano is my preferred editor as well. After you make your changes, press ctrl+x (exit), y (yes confirmation for saving the document), then enter (or change the filename you want to save the document buffer to) to confirm the filename.

---

### Post by drs305 on 2009-09-21
> **cat2005 said:**
> So, what do you folks think of this potential syntax:
 
/dev/sdb1  /media/2nd  noauto,user,noexec,rw,sync  0 2
 
Must I use a specific editor for the fstab, or would "sudo gedit" work well?
 
Thanks.


Gedit will work fine, but please use "gksu gedit" or "gksudo gedit" rather than "sudo gedit". "gksudo" is used with graphical apps such as nautilus and gedit, while "sudo" is used with terminal-based apps such as apt-get.

Here is a link that explains it:
[http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

