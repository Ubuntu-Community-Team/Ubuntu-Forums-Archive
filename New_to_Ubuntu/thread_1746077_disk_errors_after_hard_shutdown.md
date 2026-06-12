---
title: "disk errors after hard shutdown"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by kyselica.david on 2011-05-01
Hello a I have go t also a problem with dpkg .I was upgrading my ubuntu ,but during upgrading my pc shutted down .When I powered it, there were some errors and  it asked me,if I want to recover it manualy.I think ,if I finish the upgrading ,the errors will be solved.So I decided to finish upgrading. But there was a problem with unlocked dpkg.So I tired dpkg --confugure -a ,but it said : Read only filesystem .I`m just learnig to work with ubuntu ,and I don`t know what to do with it.Is somebody able to help me ? Thanks

---

### Post by yetiman64 on 2011-05-01
> **kyselica.david said:**
> Hello a I have go t also a problem with dpkg .I was upgrading my ubuntu ,but during upgrading my pc shutted down .When I powered it, there were some errors and  it asked me,if I want to recover it manualy.I think ,if I finish the upgrading ,the errors will be solved.So I decided to finish upgrading. But there was a problem with unlocked dpkg.So I tired dpkg --confugure -a ,but it said : **Read only filesystem** .I`m just learnig to work with ubuntu ,and I don`t know what to do with it.Is somebody able to help me ? Thanks

A hard shutdown will cause the root partition to be mounted as read only on occasions, to fix this use in terminal,

```
sudo touch /forcefsck
``` input your password then do a reboot of the machine. All your filesystems will be checked on the next start, so it can take some time to restart, be patient with it even if it appears to hang for a while.

When you get back to the desktop continue with trying to use the dpkg command you listed above. Good luck.

---

### Post by kyselica.david on 2011-05-01
It said the same :Read-only filesystem.

---

### Post by yetiman64 on 2011-05-01
> **kyselica.david said:**
> It said the same :Read-only filesystem.

Ok, there were 2 possibilities, but if you have run the previous process with forcing a filesystem check and the root filesystem is mounted alright, then from the original thread you posted in try, 

```
ls -l /usr/bin/dpkg
```and post back the line it outputs for checking. I suspect the permissions may be wrong on it. 

The first part of the line should be,

> -rwxr-xr-x 1 root root if it differs from this you could try the instructions in post 2 [[COLOR=Blue]--HERE--[/COLOR]]("http://ubuntuforums.org/showpost.php?p=9751557&postcount=2"). 

If you wish to check the whole thread again just click on the title in the top right of the browser window, it will open the whole thread not just the single post I've linked to.

**Edit**: just noted the command you put in your first post needs sudo before it. This could also contribute to your situation, the command to use is,
```
sudo dpkg --configure -a
``` the command needs sudo to run as it is owned by root.

---

### Post by kyselica.david on 2011-05-03
Also any of these comands aren`t working.When I wrote they ,it said again :Read only file system.
For clarification :I`m not logged as root not normally ,but during starting ubuntu it displays some problems with mountig (I didn`t undrstand it exactly )and than it asks me ,If I want to recover it manully .When I accept ,then it asked me for root password.So I`m not logged in normally.

---

