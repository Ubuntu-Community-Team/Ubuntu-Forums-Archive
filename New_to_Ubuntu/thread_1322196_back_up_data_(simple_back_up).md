---
title: "back up data (simple back up)"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by Konbuntu on 2009-11-10
i would like to know if it's possible to use "simple back up" in order to do a fresh installation of ubuntu?

or do i have to save my data in a cd or dvd?

---

### Post by laidback on 2009-11-10
I copy /home to a USB HDD but I guess a DVD would do the same job. After the fresh install you can copy back what you need/want.
In fact I don't get rid of the previous install as I use a caddy system which allows me to swap HDDs easily, so I can always go back to the old installation and recover anything I need. After a time I get happy with the new installation and find the old version has not been used for awhile, it's at this point that I recycle the HDD.

---

### Post by Konbuntu on 2009-11-10
thanks!

---

### Post by aPaSv5 on 2009-11-10
I use a simple shell script to periodically back up my files to a flash drive.

```

dest=/media/backup

# Find all normal files in the list of directories, exluding .git repos.

find ~/Projects ~/bin ~/.vim ~/.fvwm -type f -print0 |
	grep -vz "\.git\/" |
	xargs -0 tar cvzf "${dest}/$(date "+backup_%Y_%m_%d.tar.gz")"

```

 Note that just copying and pasting this into your shell probably won't result in anything -- your flash drive would have to be mounted at /media/backup and, even if it was, the script only backs up the directories listed after "find" -- in this case, ~/Projects, ~/bin, ~/.vim, and ~/.fvwm.

Also note that (to save space) this script doesn't back up git repository stuff.

If, for example, you wanted to back up your whole home folder, you would use this instead:


```

dest=/media/backup

# Find all normal files in the list of directories, exluding .git repos.

find ~ -type f -print0 | xargs -0 tar cvzf "${dest}/$(date "+backup_%Y_%m_%d.tar.gz")"

```

The other nifty part about this script is that it appends the current date to the filename.

---

### Post by Sir Jasper on 2009-11-10
Hi,

Simple Backup will NOT backup everything.

However, it has advantages as well as disadvantages.

My regards

---

