---
title: "How do I allow other users to view my home dir?"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by bsmith1051 on 2010-03-09
This is a two-bird-with-one-stone kinda question!  First off, my wife and I share a single desktop PC and I want us to be able to at least view each other's 'home' directory.  My basic technique has been to add each of us to the other's Group.

Secondly, I'm trying to make a complete backup of each of our's 'home', i.e., with the other person logged-out so that no files are locked or in-use.  But belonging to the other person's Group isn't sufficient.  Sometime the Group doesn't have any access-rights.  So then I tried adding Group-read rights to all our files/folders and that helped a lot, e.g.
 > sudo chmod g+r -R /home/<wife>

But now what I'm running into is that -- even though her FOLDERS permissions are 'List files' -- it doesn't work; from my login I can't see what files are in her folders.  I also discovered that there's another Group permission called 'Access files' -- is that what I need?  If so I don't see any way to specify that from the command-line?

Hopefully I've been clear, both about my ultimate goals (shared access/backups) and the steps I've taken so far!

---

### Post by Barriehie on 2010-03-09
Regarding the backup are you desiring to do this via a crontab file entry?  You could use rsync as root like this and it should do it:
```

rsynv -av /home/<wife> /backup-device/<wife>/     # as long as <wife> exists on /backup-device then root won't create it.

```Alternatively you could use tar:
```

tar -cvpzf /backup-device/<wife>/filename /home/wife
```I suffix my backup file names with the date like this:
```

dateNtime=$(date +%m%d%y)
blah blah blah home-$dateNtime
blah blah blah etc-$dateNtime

```My machine is single user so can't help with the home dir. sharing.

---

### Post by bsmith1051 on 2010-03-09
Thanks for the quick reply!  Actually, I'm not trying to do any of that :-p

In your example, though, you show a command-line:
```
tar -cvpzf /backup-device/<wife>/filename /home/wife
```
Does that command work on your own 'home' directory, i.e., if you're logged-in and running the Gnome desktop?

---

### Post by Barriehie on 2010-03-09
> **bsmith1051 said:**
> Thanks for the quick reply!  Actually, I'm not trying to do any of that :-p

In your example, though, you show a command-line:
```
tar -cvpzf /backup-device/<wife>/filename /home/wife
```Does that command work on your own 'home' directory, i.e., if you're logged-in and running the Gnome desktop?

Yes,
```

tar -<switches> <file.tgz that tar will create> <dir/file(s) to put in file.tgz>
```What I do is use rsync to backup /etc and /home and then use tar to put those 2 dirs as a compressed file each on a USB thumb drive.

Note that if your backup media is part of your home dir you'll have a recursion loop going on and unexpected things could/might/probably will happen!

---

