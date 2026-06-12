---
title: "Help needed with UBuntu as troubleshooter"
date: 2010-08-22
forum: New to Ubuntu
---

### Post by Janis_2 on 2010-08-22
I haven't gotten any usable replies in the general forum so am thinking I was in the wrong place.  Can the latest download of Ubuntu be used with suggested tutorials (psychocats.net)?   The pc I am working on WILL NOT change directories using the command in the tutorial.   The Windows hard drive is mounted; but all I can end up with is no file found or Ubuntu@ubungtu:~$.     Is there a better link for newbies or how do I correct this?

---

### Post by earthpigg on 2010-08-22
have you tried navigating around using the graphical file manager?

alternatively, the hard drive may not have been mounted in the same place as mentioned in the tutorial.

running this command, and looking on the right, will show you where various hard drives are mounted:

> df -Th

so, to use my thumb drive as an example:

```
[chris: ~]$ df -Th
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sdb1     ext4     59G  4.9G   51G   9% /
none      devtmpfs    3.0G  344K  3.0G   1% /dev
none         tmpfs    3.0G  9.8M  3.0G   1% /dev/shm
none         tmpfs    3.0G   92K  3.0G   1% /var/run
none         tmpfs    3.0G     0  3.0G   0% /var/lock
none         tmpfs    3.0G     0  3.0G   0% /lib/init/rw
/dev/sda1     ext4    917G  235G  636G  27% /home
/dev/sdd1     vfat    3.8G   25M  3.8G   1% /media/Keychain

```

i would navigate to it like this:

```
[chris: ~]$ cd /media/Keychain
[chris: /media/Keychain]$ 
```

note the capital letter K. things are case sensitive in Linux-ville.

---

### Post by Janis_2 on 2010-08-22
I noticed  the command preceded by a name.  Do I need a "login" to use terminal?  I assumed the drive was mounted as it showed up in the left panel.

---

### Post by Thryn on 2010-08-22
> **Janis_2 said:**
> I noticed  the command preceded by a name.  Do I need a "login" to use terminal?  I assumed the drive was mounted as it showed up in the left panel.
Normally when you open the terminal, it shows your username, or yourname@nameofcomputer: ~$

You do have to login to Ubuntu, but not anywhere special.

---

### Post by Janis_2 on 2010-08-23
I don't see a login choice; my apologies for being so green.   Would this show up if I am only using the LiveCD (not the installed version)?  Could it be that the ubuntu@ubuntu:~$ is being set as my login?

---

### Post by QLee on 2010-08-23
[QUOTE=Janis_2]...   Would this show up if I am only using the LiveCD (not the installed version)?  Could it be that the ubuntu@ubuntu:~$ is being set as my login?[/QUOTE]
Yes.

What is the command you are trying that doesn't work?

---

### Post by Janis_2 on 2010-08-23
I had downloaded the tutorial from psychocats  "How to  reset a Windows password with Ubuntu".   My main office pc quit responding to my password.  I am afraid that one of my student gremlins does know Linux or other software!   Now I need to change the password.    I installed chntpw as instructed.  I mounted the correct drive and can see all the folders.   The tutorial instructions are to cd /media/493D9CB55373C3DD/WINDOWS/System32/config.    I get a file not found.   In another tutorial,  it says I should use Nautilus to verify the case sensitive Windows but I don't know how to access that.   I need to get into the pc without any excess expense to accounts.  Hope you can help.

---

### Post by lkraemer on 2010-08-23
If you have mounted the Windows Drive, it most likely is mounted at /mnt
or /media unless you changed the typical mount points.

If you open a Terminal Window and do the following commands you should
be able to drill down to the proper subdirectory.
```

cd /
pwd
ls -alt

cd /mnt
pwd
ls -alt

cd /
pwd
ls -alt

cd /media
pwd
ls -alt

```
When you find the Windows subdirectory, just keep moving down to where
you need to be to get to /Windows/System32/ by using the information from
the "pwd" and "ls -alt" commands.  You should see the files you are looking for.

An easier method would be to download the ISO of Trinity Rescue Kit ver 3.4
[http://trinityhome.org/Home/index.php?content=TRINITY_RESCUE_KIT____CPR_FOR_YOUR_COMPUTER&front_id=12&lang=en&locale=en](http://trinityhome.org/Home/index.php?content=TRINITY_RESCUE_KIT____CPR_FOR_YOUR_COMPUTER&front_id=12&lang=en&locale=en)
and use it to reset your password.

Just be sure to burn the ISO as Disk At Once (DAO) and at 4x, or the slowest speed available.
You might want to use a CDRW and keep it updated for the future.....

Also more info at [www.distrowatch.com](www.distrowatch.com) about Trinity Rescue Kit

lk

---

### Post by QLee on 2010-08-24
[QUOTE=Janis_2]...The tutorial instructions are to cd /media/493D9CB55373C3DD/WINDOWS/System32/config.    I get a file not found....[/QUOTE]

The UUID (descriptor for the partition, those numbers and letters) they used in the example is just for example purposes, you'll have to use the correct UUID for the Windows partition on your system. Read over the example again and try to follow through to locate your Windows installation.

---

### Post by Janis_2 on 2010-08-25
Big thank you to all posters.  With the suggested software,  it was easy and now I am back in business which is good as students return next week.

---

