---
title: "HELP ME restore time/date stamps"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by BassKozz on 2008-12-09
I've copied (via Nautilus) a large amount of files (over 200GB, it took a few hours) from one computer [source] to another [destination] (both Ubuntu machines w/ Samba Shares), and now the destination computer has set all the time/date stamps for the files & folders to today (or the time they were copied over), but I need to keep the time & date stamps from the source... how can I restore the file & folders time & date stamps w/out having to copy the files back over again?

In hindsight I prolly should've used rsync for this task, but it's too late now :(
I knew there was a reason I didn't mv the files I cp'ed them ;P
Any idea's?
-BassKozz

---

### Post by jamesrl on 2008-12-10
In the future, you can cp with -p to preserve mode,ownership, and timestamps.  
At this point you could write a (python/bash/csh) script to automate using system tools:
```
touch -r

```

---

### Post by jamesrl on 2008-12-10
A python script would go like this:

```
#!/bin/python
original_dir_name = "/home/username/new"
# dir name with permissions; be sure to not have an extra / at the end
new_dir_name = "/home/username/new2"
# dir name with incorrect permissions; you want set with permissions from original_dir_name

import os
for file_and_dir_tuple in os.walk(original_dir_name):
    orig_prefix = file_and_dir_tuple[0]
    new_prefix = orig_prefix.replace(original_dir_name, new_dir_name)
    dir_list = file_and_dir_tuple[1]
    for my_dir in dir_list:
        os.system("touch --reference=%s/%s %s/%s" % 
                  (orig_prefix, my_dir, new_prefix, my_dir))

    file_list = file_and_dir_tuple[2]
    for my_file in file_list:
        os.system("touch --reference=%s/%s %s/%s" % 
                  (orig_prefix, my_file, new_prefix, my_file))


```

This would be if you can mount the samba share to act like a normal directory somewhere.  [I have only had a very brief experience with samba as I try to avoid it and windows as much as possible.]

EDIT: Actually, the script was slightly flawed originally.  I added in the section about directory names, so the timestamps on directories get updated as well.

---

### Post by BassKozz on 2008-12-10
Thanks for the help James,
But I couldn't get your script to work, it keeps giving me errors like:
```
sh: Syntax error: "(" unexpected
touch: failed to get attributes of `/home/user/blah/blah': No such file or directory
```
I probably should have mentioned that some of the directories have funky characters that are probably throwing your script in a loop like the dreaded colon ":".
But I really do appreciate the effort, I can't say enough about the Ubuntu user community, it never ceases to amaze me how many helpful people there are out there...

Anyways I think I am just going to take one on the chin and re-copy the files over, should I use "cp -p" or should I use "rsync" and if I do use "rsync" what parameters should I use?

> **jamesrl said:**
> [I have only had a very brief experience with samba as I try to avoid it and windows as much as possible.]
If you don't use samba, what do you use to share between two linux boxes ?
<--- still learning
Thanks,
-BassKozz

---

### Post by jamesrl on 2008-12-10
You error seemed to be a sh error.  Cut and paste the script to a file, say copy_timestamps.py
Then type in the terminal
```
python copy_timestamps.py
```

---

### Post by hyper_ch on 2008-12-10
or rather use rsync to copy over...

---

### Post by jamesrl on 2008-12-10
I use primarily ssh / scp / unison (which is basically rsync) for syncing my laptop / desktop / work computer.  My only experience with samba was connecting to windows networks for a project that I only briefly worked on.  My work computer is on my work network (with other linux/unix machines) through nfs (though I know next to nothing about nfs).  I just found out that samba is for more than just for accessing windows smb networks in linux:
[http://en.wikipedia.org/wiki/Samba_(software](http://en.wikipedia.org/wiki/Samba_(software))
I guess we're all just learning.

---

### Post by jamesrl on 2008-12-10
You're right.  Looking at man rsync it seems:
```
rsync -ta orig_dir/* new_dir/

```
would be the easiest way to do this.  Feeling pretty dumb right now ... never bothered to learn rsync syntax (always nice GUI programs) and its pretty straightforward.

---

### Post by hyper_ch on 2008-12-10
you can even "enhance" it more.

If you exchange ssh keys you can even connect to the other computer through ssh automatically and sync ;)

---

### Post by jamesrl on 2008-12-10
Be wary of using passphrase-less ssh keys, it is a security loophole.  Anyone who briefly has read-access to your home directory (another user on the same computer, someone walking into the room before the screensaver locked your machine, etc.), can grab your private key from your .ssh directory.  And then they too can passwordlessly login to any machines you have access to as your username.
That said I use ssh keys all the time, just with a strong passphrase and only keep passphrases on machines where I am the only user with root privileges (this way when i first boot the machine I need to type my passphrase, but only then).

A wrote a how to a while back on this: 
[How to SAFELY use ssh-keygen for frequent remote logins]("http://ubuntuforums.org/showthread.php?t=904796")

---

### Post by philinux on 2008-12-10
> **BassKozz said:**
> I've copied (via Nautilus) a large amount of files (over 200GB, it took a few hours) from one computer [source] to another [destination] (both Ubuntu machines w/ Samba Shares), and now the destination computer has set all the time/date stamps for the files & folders to today (or the time they were copied over), but I need to keep the time & date stamps from the source... how can I restore the file & folders time & date stamps w/out having to copy the files back over again?

In hindsight I prolly should've used rsync for this task, but it's too late now :(
I knew there was a reason I didn't mv the files I cp'ed them ;P
Any idea's?
-BassKozz

They supposedly fixed nautilus regarding this issue. What version of ubuntu are you running.
[https://bugs.launchpad.net/nautilus/+bug/215499](https://bugs.launchpad.net/nautilus/+bug/215499)

---

### Post by BassKozz on 2008-12-10
> **hyper_ch said:**
> or rather use rsync to copy over...
> **jamesrl said:**
> You're right.  Looking at man rsync it seems:
```
rsync -ta orig_dir/* new_dir/

```
would be the easiest way to do this.  Feeling pretty dumb right now ... never bothered to learn rsync syntax (always nice GUI programs) and its pretty straightforward.
Thanks guys "rsync -ta orig_dir/* new_dir/" did the trick :D
> **hyper_ch said:**
> you can even "enhance" it more.

If you exchange ssh keys you can even connect to the other computer through ssh automatically and sync ;)
You mind expanding on this for my own education? What do you mean by "enhance it more" & "connect to the other computer through ssh automatically"?
> **jamesrl said:**
> I use primarily ssh / scp / unison (which is basically rsync) for syncing my laptop / desktop / work computer.  My only experience with samba was connecting to windows networks for a project that I only briefly worked on.  My work computer is on my work network (with other linux/unix machines) through nfs (though I know next to nothing about nfs).  I just found out that samba is for more than just for accessing windows smb networks in linux:
[http://en.wikipedia.org/wiki/Samba_(software](http://en.wikipedia.org/wiki/Samba_(software))
I guess we're all just learning.
So you use command line to transfer files using ssh / scp / unison? But do you have a way of mounting a remote (linux) drive/folder/share using fstab? or how do you use Nautilus to transfer files from a remote machine if not using samba?

-=-
Thanks again for all the help James & hyper_ch ):P

> **philinux said:**
> They supposedly fixed nautilus regarding this issue. What version of ubuntu are you running.
[https://bugs.launchpad.net/nautilus/+bug/215499](https://bugs.launchpad.net/nautilus/+bug/215499)
Ubuntu 8.10 w/ all the latest updates :-k
**_Edit:_** I left a comment on that bug report: [https://bugs.launchpad.net/nautilus/+bug/215499/comments/82](https://bugs.launchpad.net/nautilus/+bug/215499/comments/82)
Hope to hear back.

---

### Post by hyper_ch on 2008-12-10
well, you can setup ssh in a way that you can connect to another account on a remote machine without being required to enter the password... that's key-based ssh login.

As you can also run rsync over a ssh connection this means you can rsync to a remote host without entering a password. This also means you can automate it and do regurarly a sync :)

---

### Post by BassKozz on 2008-12-10
> **hyper_ch said:**
> well, you can setup ssh in a way that you can connect to another account on a remote machine without being required to enter the password... that's key-based ssh login.

As you can also run rsync over a ssh connection this means you can rsync to a remote host without entering a password. This also means you can automate it and do regurarly a sync :)

Gotcha, Thanks for clearing that up, now I understand what you mean ;)

---

### Post by hyper_ch on 2008-12-10
exchanging ssh keys for passwordless login is quite simple :)

---

