---
title: "Samba sharing problem between two Ubuntu Servers"
date: 2014-02-24
forum: Networking &amp; Wireless
---

### Post by bd314159 on 2014-02-24
I am running into an odd situation where I have three Ubuntu Server machines running Ubuntu Server 10.4.3 LTS.  One has a shared directory that the other two will read to get testing information.  This setup has been working correctly for quite some time, but twice now, I have seen the situation where I read the shared file from one computer that accesses it and get one value and reading it from the other computer gives me a different (older) value.  The only thing I can think of is that the older value is buffered somewhere in Samba, but I do not know where or even if this is the true problem.  Fixing the problem is trivial, rebooting the system will clear it up. I would like to know why this happens in the first place so that I can prevent it from happening again.  Thank you for your help.

---

### Post by TheFu on 2014-02-25
I don't know.
Are the clocks synchronized via NTP on all the systems?  They should be within 0.001 seconds easily.

But why not use NFS between UNIX systems? Native file permissions rock for networked file systems.

---

### Post by bd314159 on 2014-02-25
I do have ntp running on all the linux systems.  Samba got used because there are also Windows boxes involved in the configuration.  I could switch over to NFS for that particular share, Windows is not involved with that one.

---

### Post by tgalati4 on 2014-02-25
SAMBA is generally a slow protocol (as I duck) and perhaps the files that you are comparing are large?  If that is the case, then file-locking could force an older copy (in cache) to be used instead.  You can drop the cache on a machine to investigate.

```
echo 1 | sudo tee /proc/sys/vm/drop_caches
```

If the behavior does not change after dropping the cache, then there must be some other issue.  Do you have *rsync* running in a cronjob between the two servers?

---

### Post by TheFu on 2014-02-25
I think he has 1 copy of the file and the other 2 machines access it live, when needed.  1 sees recent changes and the other doesn't. Most normal UNIX file editors would not apply a file-lock until write ... not while sitting in the editor overnight ... just when :w happens.  A newer mtime should force any network file system to get a newer version of the file/directory, right?

Or I could be wrong.

I've done lots and lots of this sort of stuff. The only time I've seen issues was using virtualbox to access files on a host-Win7 system. The built-in file sharing didn't handle locking correctly and caused corruption.

---

### Post by bd314159 on 2014-02-25
The file contains one word as a parameter for different test conditions.  Not large at all.

---

### Post by bd314159 on 2014-02-25
TheFu, you are basically correct.  The file is created with echo "baseline" > /mnt/share/filename.dat not with an editor. The odd thing was that looking at the details of the file on both machines showed the same modification date/time while one of those machines still returned the earlier value if more'd.

---

### Post by bd314159 on 2014-02-25
*rsync* is not running as a cronjob

---

