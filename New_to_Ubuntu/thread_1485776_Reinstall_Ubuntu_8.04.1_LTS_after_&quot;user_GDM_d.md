---
title: "Reinstall Ubuntu 8.04.1 LTS after &quot;user GDM does not exist&quot; - Partition issue"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by Wilf55 on 2010-05-17
I installed Ubuntu 8.04.1 LTS last night on a gifted PC that had a broken Windows XP install (wouldn't boot - but I've fixed that now).

During the install I created a ~40Gb partition on a 160Gb HDD for Ubunutu, I created my personal logon finished the install and was taken to an error message advising Ubuntu was in 'low graphics mode'. I couldn't adequately select my graphics card, so jumped into the desktop and restarted, then graphics were fine.

I went to create separate user accounts, and got a few in there and then went to switch into their accounts to ensure everything was working. The logins wouldn't work, so jumped back into my login and restarted for good measure.

When Ubuntu looks like it's about to load I get a CLI screen advising that "user gdm does not exist". I've done a bit of searching and it seems that I've deleted some fairly important stuff (NFI how, but the system doesn't lie).

I've searched for the fault:

[http://ubuntuforums.org/showthread.php?t=776635&highlight=user+gdm+does+not+exist](http://ubuntuforums.org/showthread.php?t=776635&highlight=user+gdm+does+not+exist)

[http://ubuntuforums.org/showthread.php?t=1253012&highlight=user+gdm+does+not+exist](http://ubuntuforums.org/showthread.php?t=1253012&highlight=user+gdm+does+not+exist)

[http://ubuntuforums.org/showthread.php?t=1191667&highlight=user+gdm+does+not+exist](http://ubuntuforums.org/showthread.php?t=1191667&highlight=user+gdm+does+not+exist)

 and tried some of the troubleshooting mentioned - and nothing seems to work (Note: The PC is not connected to any network at the moment, so downloading anything directly to that PC is out). I'm not emotionally tied to that install and I thought it would just be easier to reinstall the OS rather than bugger around.

When attempting to install again from the CD the install reports the HDD size as 120Gb (It doesn't see the 40Gb partition). I'd like to keep the Windows partition, but if getting rid of it is the only option, then I can reinstall Windows without much issue (I hope).

I'm sure this is a fairly n00b kinda thing, so I'm looking for any help possible, either fixing the GDM issue, or reinstalling to the 40Gb partition.

---

### Post by cariboo on 2010-05-17
Look in /etc/passwd, the gdm user in mine looks like this:

```
gdm:x:114:120:Gnome Display Manager:/var/lib/gdm:/bin/false
```

---

### Post by Wilf55 on 2010-05-17
Should I just be able to enter this via the text editor on the LiveCD ? (Will try after work)

---

### Post by Wilf55 on 2010-05-18
I booted with the LiveCD and then tried to edit etc/passwd with gedit and I'm unable to save, so I went in through terminal and sudo, and saved it.

After a restart the error still occurs.

If fixing the GDM issue isn't possible is it possible to just reinstall Ubuntu to the partition that was created ?

---

### Post by anewguy on 2010-05-18
I don't know if /etc/passwd works like the old password file in Unix (and its' hidden "echo" file), but if so the "x" in the line is actually a password.  That may have something to do with it.

However, I would boot the LiveCD to try Ubuntu without installing it, then when that is up I would run the partition manager (or sudo gparted in a terminal).  It *should* show the disk has a 160gb capacity and show you any partitions that it knows about.  Since it appears you are a new user, do that first but don't make any changes, and report back what it shows.  We'll go from there.

Dave ;)

---

### Post by anewguy on 2010-05-18
You may also want to try this:

- open a terminal window (applications/accessories/terminal)

-cd /etc

sudo gedit passwd

- add the line as suggested by cariboo907

save the file and exit the editor

sudo gedit passwd-

- add the same line to this file 

save the file and exit the editor

- reboot

Did it help any?

I *think* from looking at it that the passwd- (that's a dash) file may be the "echo" file for Ubuntu (I hope I'm not doing a no-no here), and at least in Unix the passwd and the "echo" file must match.

Dave ;)

---

### Post by Wilf55 on 2010-05-18
I've taken a screenshot from gParted and attached to this post.

I've also edited the passwd- file, and it did seem to help a little, now the error message is "The GDM group 'gdm' does not exist. Please correct GDM configuration and restart GDM"

I get that I've just recreated the GDM 'user', does this mean it needs to be in a particular user group as well ?

---

### Post by CharlesA on 2010-05-18
Password info is usually stored in encrypted form in thee /etc/shadow file.

I just checked who was in the gdm group (with cat /etc/group | grep gdm) and all it showed was this: gdm:x:120.

The 120 is the group ID. The "x" means that the password is stored in the /etc/shadow file.

I don't know if that helps at all.

Also: Why did you install 8.04.1? 8.04.4 is already out, if you want to run a LTS that isn't the latest (10.04).

EDIT: Best bet would be to back up your home directory and then do a clean install of 8.04.4 or 10.04 (or whatever release you want to use)

---

### Post by Wilf55 on 2010-05-18
> **CharlesA said:**
> Password info is usually stored in encrypted form in thee /etc/shadow file.

I just checked who was in the gdm group (with cat /etc/group | grep gdm) and all it showed was this: gdm:x:120.

The 120 is the group ID. The "x" means that the password is stored in the /etc/shadow file.

I don't know if that helps at all.

Also: Why did you install 8.04.1? 8.04.4 is already out, if you want to run a LTS that isn't the latest (10.04).

EDIT: Best bet would be to back up your home directory and then do a clean install of 8.04.4 or 10.04 (or whatever release you want to use)

To answer the why question, 8.04.1 is the CD I have with me at the moment - it's really as simple as that :)

As for the suggestion, I'm definitely open to this suggestion, as the install that I broke was a fresh install I'm not even really worried about backing up data. It just seems that when I try to reinstall that the Ubuntu installer doesn't recognise that there is already a partition created, and wants me to repartition the Windows partition.

---

### Post by CharlesA on 2010-05-18
The partition should be found as sda2, you might have to do the advanced partitioning when you reinstall.

What I would suggest doing is downloading 8.04.4 or 10.04 and then installing that.

If you need to do the partitioning manually, set one partition to be mounted as "/" and the other to be swap.

The gparted screenshot looks correct, so I don't know why the installer isn't seeing sda2.

---

### Post by Wilf55 on 2010-05-18
I went back to try the install again, and I've got a copy of the partition screen that doesn't seem to like sda2.

---

