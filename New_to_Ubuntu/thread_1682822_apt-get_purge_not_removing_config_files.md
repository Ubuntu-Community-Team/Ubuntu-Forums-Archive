---
title: "apt-get purge not removing config files"
date: 2011-02-06
forum: New to Ubuntu
---

### Post by Nico-dk on 2011-02-06
Earlier I had some trouble [getting sysinfo to run](http://ubuntuforums.org/showthread.php?t=1682118), because I triggered a known bug by accident. To get sysinfo to run, I needed a clean config file, so I proceeded to completely remove sysinfo.
First via Synaptic (marked for complete removal), and then via apt-get purge.

**1)** Shouldn't **apt-get purge sysinfo** have removed sysinfo including config files?

At least that's what the trace says, when using the purge switch

```
Removing sysinfo ...
Purging configuration files for sysinfo ...
```

But even after doing ...

```
sudo updatedb
locate sysinfo
```

I could still find config files for sysinfo in my Home dir. Since I'm far from proficient in Linux, I didn't want manually remove said config files, as I had no idea what system dependencies, I could potentially screw up.

**2)** How can I safely remove config files after removing an application?


**3)** If purge should've removed all files (incl. configs), could this have been botched because I've setup my /Home on a different partition?

[IMG]http://i62.photobucket.com/albums/h112/nico-dk/Linux/20110206_001.png[/IMG]

Thanks for all and any response :)

---

### Post by mcduck on 2011-02-06
Apt-get will never remove any config files from user's home directories, purge or not.

Every user's config files belong to that user only, and no regular admin task on the system should touch them. So they are only ever removed if the user himself, or root, specifically chooses to do so.

This is the only way things can be, when you consider that those user config files can contain very personal things, like your e-mails, web browser bookmarks & saved passwords, IM contacts and other such things. It would be pretty disastrous if some admin task would delete such data.

For example think of a multi-user system, with troubles updating to new Evolution version. In such situation it might be necessary for the admin to remove the current Evolution package completely before installing a new one, and if duing that would cause every single user of the system to loose their calendars, address books, notes and everything there would soon be a bunch of *very* angry users around the admin's office... ;)

---

### Post by Nico-dk on 2011-02-06
Thanks, very good explanation :)

Now, even with my short time in Linux, I've learned one thing; there's always a way to get the job done.

On that note, isn't there a way for the current user, to delete his own config files on a one user system?

I know there are effectively 2 users; me and root, but you probably catch my drift

---

### Post by mcduck on 2011-02-06
Well, if it's your config file and in your home directory you can delete it just like any other file you own. Drop it to trash. ;)

edit: if you are not sure what removing a certain config file would do, the safe way is to rename it or move it somewhere first. But most of the user config files will just be automatically created again if they are missing, so you can't really break anything by removing them, it's just a question of keeping your own program settings and personal data.

---

### Post by Nico-dk on 2011-02-06
Heh, well my own fix was to edit it, since I didn'twant to screw anything up (still getting used to the filesystem).

Again, thanks for the input :)

---

### Post by asmoore82 on 2011-02-06
> **Nico-dk said:**
> I could still find config files for sysinfo in my Home dir. Since I'm far from proficient in Linux, I didn't want manually remove said config files, as I had no idea what system dependencies, I could potentially screw up.

As already said, the administrative tools wont meddle in user home folders.

On the flip-side of this, a great rule of thumb is that those same
user files are always expendable from the system's point of view :D.

---

