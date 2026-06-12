---
title: "Samba Share Mount Point Corruption - SMBFS"
date: 2007-06-01
forum: Networking &amp; Wireless
---

### Post by drybittermelon on 2007-06-01
Around three weeks ago, I set up a backup server (with rdiff-backup if anyone is interested) using Ubuntu 7.04. The machine wakes up every morning at 3am, mounts two samba shares on the network, backs them up onto its harddrive and shuts down itself at 6am. I tried running the backup script manually once, the backup takes around 1 hour. The machine only does backup and nothing else.

I check the logs of the machine during the night every now and then. I found that every so often the backup would suddenly stops working. On preliminary investigation, the samba mount points have been somehow corrupted, which causes the backup to fail. So I renamed the /mnt (where the samba shares are mounted) to /mnt1 or similar, and recreate the mount points (i.e. /mnt/a, /mnt/b), everything start working for a couple of days, before the problem repeats again. 

As I am mounting to a Windows98 machine, I have to use smbfs; so using cifs, however great it is, will not work. (Tried and Tested)

Instead of renaming these corrupted mount points, I tried once to remove them, but its a pain; rm does not work, so I had to use root maintenance startup to fsck the drive, then delete the /mnt directory after fsck had fixed it.

Something else I have noticed, although may not be related, is that ever since this happens, when it shuts down, it switches to text mode and displays this error message :
smb_retry : no connection process

the message stays on the screen for around a minute before finally switching itself off.

Any ideas? 

I have search the forum, there are a few users experiencing the same problem, but not getting the answer we need (listed below). So I started this new thread, hoping this problem will get the attention it deserves. 

Also If you have similar experience, please post it here.

[COLOR="DeepSkyBlue"][LIST]
[SMBFS - FS corruption??]("http://ubuntuforums.org/showthread.php?t=344589&highlight=mount+point+corrupt")
[/LIST]
[LIST][Mount point corrupt]("http://ubuntuforums.org/showthread.php?t=304602&highlight=samba+corrupt+mount")
[/LIST]
[LIST][corrupt directory listing after smbmount]("http://ubuntuforums.org/showthread.php?t=300382&highlight=samba+corrupt+mount")
[/LIST]
[LIST][How to fix corrupt directory]("http://ubuntuforums.org/showthread.php?t=326533&highlight=samba+corrupt+mount")
[/LIST]
[LIST][samba mounts broken after update]("http://ubuntuforums.org/showthread.php?t=452359")[/LIST][/COLOR]

---

### Post by dmizer on 2007-06-02
i've tried to nail down this issue a few times before, but since i've never actually experienced it myself it's difficult.

anyway ... it seems silly, but try this:
```
sudo aptitude install smbfs
```
even if you're sure you've already done it.

also, you might be more successful by mounting with cifs instead of smbfs.  howto is located in the second link in my sig.

---

### Post by ruy_lopez on 2007-06-02
If all you are doing is a backup, you'd be better off using something like rsync. You'll only have to do a full backup once. After that, rsync will just update the changes. It won't take as long to do, either.

---

### Post by drybittermelon on 2007-07-12
SOLVED BY A WORKAROUND

Solved my problem this week :-
1) named my mount directory /mnta instead of the usual /mnt
2) Just before backup, rename the /mnta to /mnt, then mount drives and do the copying (be it rsync or rdiff-backup, whatever)
3) Right after backup, rename /mnt back to /mnta (this is to prevent whatever is corrupting the umounted samba mount points)

Just tired of trying to find out what is wrong with smbfs, so worked out a quick fix

Hope this helps others.

---

