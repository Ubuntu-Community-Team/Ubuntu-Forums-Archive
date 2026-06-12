---
title: "no cd burner found"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by eddski on 2009-09-02
I would like to burn some cd/dvds for backups so I installed K3b. When I launch the program it says "there is no cd burner recognized". I have a sony cd/dvd burner installed and would like to know how to proceed. Is there any online comprehensive manual as the pocket guide wasn't much help.
thanks

---

### Post by nhasian on 2009-09-02
if you insert a CD into the drive, is the media recognized?  does Brasero see your cd burner?

---

### Post by mikechant on 2009-09-02
k3b should see your drive even if there's no media in it.
You could try running the k3b command in a terminal and see if you get any useful error messages.

---

### Post by eddski on 2009-09-02
This is what I get when I run k3b at the command:

DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
Error: "/tmp/kde-john" is owned by uid 0 instead of uid 1000.
Error: "/tmp/kde-john" is owned by uid 0 instead of uid 1000.
Error: "/tmp/ksocket-john" is owned by uid 0 instead of uid 1000.
Error: "/tmp/ksocket-john" is owned by uid 0 instead of uid 1000.
kdeinit: Aborting. No write access to '/home/john/.ICEauthority'.
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket

I know I don't know what this means...

Brasero does not see the drive because when I start a project and put a cd in nothing happens.

---

### Post by zeroseven0183 on 2009-09-02
How did you install Ubuntu? via CD? Is Live CD working on your drive?

---

### Post by mikechant on 2009-09-02
Your error messages look like a permissions problem.

Try running k3b as root, I suppose with

```
gksu k3b
```
if you use gnome
or
```
kdesu k3b 
```
if you use kde (I think this is right - I don't use kde myself)

If this works then we can look at your permissions problem, if not post the new errors (should be different).

---

### Post by eddski on 2009-09-02
For zeroseven0183, I installed via cd to a hard drive, I am not using a live cd.

---

### Post by eddski on 2009-09-02
Thanks, mikechant, I got it to recognize my drive. But I received a warning as follows:

Running K3b as root user
It is not recommended to run K3b under the root user account. This introduces unnecessary security risks.
Solution: Run K3b from a proper user account and setup the device and external tool permissions appropriately.

It shows in the background my dvd recorder, but I guess I need to rtfm, if it has one. I not sure what external tool permissions are...

---

### Post by mikechant on 2009-09-03
> I got it to recognize my drive. 

Good, so we know there's no problem with the hardware, drivers or application - it looks pretty certain it's a problem relating to your home directory.

Based on the 'ICEauthority' error, take a look at the fifth post down in this thread:
[http://ubuntuforums.org/archive/index.php/t-957905.html](http://ubuntuforums.org/archive/index.php/t-957905.html)

and there are three possible fixes for your problem.

Check the disc space issue first and if that's OK, try the other two solutions. They won't do any harm if they're not applicable.
Lets us know how you get on.

---

### Post by eddski on 2009-09-04
Below is the result of df -h :

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             4.6G  627M  3.8G  15% /
tmpfs                 868M     0  868M   0% /lib/init/rw
varrun                868M  108K  868M   1% /var/run
varlock               868M     0  868M   0% /var/lock
udev                  868M  172K  868M   1% /dev
tmpfs                 868M  484K  868M   1% /dev/shm
lrm                   868M  2.5M  866M   1% /lib/modules/2.6.28-13-generic/volatile
/dev/sda3             183M   60M  114M  35% /boot
/dev/sda8              14G  349M   13G   3% /home
/dev/sda9             2.3G   68M  2.2G   4% /tmp
/dev/sda7             9.2G  2.6G  6.2G  29% /usr
/dev/sda10            2.3G  453M  1.8G  21% /var
/dev/sda11             58G  160K   58G   1% /windows


I don't think I have any probs with no partition with over 35% usage, but below is the result of running  sudo chown -R john /home/john

chown: cannot access `/home/john/.gvfs': Permission denied

I know I am in the admin group so this does not make sense to me, hope you can help.

---

### Post by mikechant on 2009-09-04
.gvfs is weird; I had to exclude it from my rsync backup of /home - I think you just need to ignore this error and carry on - do the chown and chmod and logoff and on again and if that doesn't fix it, try the ICEauthority delete.

---

