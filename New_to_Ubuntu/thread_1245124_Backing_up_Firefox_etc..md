---
title: "Backing up Firefox etc."
date: 2009-08-20
forum: New to Ubuntu
---

### Post by kenmac2 on 2009-08-20
When using XP, I used Firefox and Thunderbird.( both Mozilla)
It was easy to back up both by copying the Profile folder for both.
Does Firefox have a Profile folder or similar in Ubuntu?
What's the best way to back up Firefox and Evolution in Ubuntu?

kenmac2

SOLVED

---

### Post by Grenage on 2009-08-20
/home/USERNAME/.mozilla/

This folder should hold all that you need.

---

### Post by Copernicus1234 on 2009-08-20
Yep. Use these command to take a copy of the above folder and its subfolders, keeping the timestamp on all the files in it.

```

cd ~
cp -rp .mozilla .mozilla-backup

```

Your copy is named .mozilla-backup and its in your home directory. To list it, you will need to use the -a flag for ls since all files and folders starting with . are hidden otherwise.

```

cd ~
ls -la 

```

---

### Post by philinux on 2009-08-20
Thunderbird profile is:-

/home/user/.mozilla-thunderbird

File with a dot in front are hidden. Press ctrl h to see them in the file browser.

---

### Post by kenmac2 on 2009-08-20
What about the mail program Evolution - does that have a Profile folder somewhere?

kenmac2

---

### Post by Copernicus1234 on 2009-08-20
Yes, its .evolution in your home directory. :)

See how easy it is?

---

### Post by peakshysteria on 2009-08-20
Posted in earlier in the forums: [URL="http://ubuntuforums.org/showthread.php?t=663985"]Howto - backup/restore firefox profile
[/URL]
> Backup video:
[http://www.youtube.com/watch?v=8lEEnsFcUHg](http://www.youtube.com/watch?v=8lEEnsFcUHg)

Restore video:
[http://www.youtube.com/watch?v=OAIKajlslnE](http://www.youtube.com/watch?v=OAIKajlslnE)

**[Mozillazine]("http://forums.mozillazine.org/index.php")** might also be of some small interest for the OP.

**[FEBE 6.2]("https://addons.mozilla.org/en-US/firefox/addon/2109")** also seems very useful.

> FEBE (Firefox Environment Backup Extension) allows you to quickly and easily backup your Firefox extensions. In fact, it goes beyond just backing up -- It will actually rebuild your extensions individually into installable .xpi files. Now you can easily synchronize your office and home browsers.

---

### Post by kenmac2 on 2009-08-20
Thanks guys.

kenmac2

---

