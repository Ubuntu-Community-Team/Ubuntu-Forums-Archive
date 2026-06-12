---
title: "Folder with files gone somewhere"
date: 2011-04-17
forum: New to Ubuntu
---

### Post by Krise on 2011-04-17
Hi.

Here is the problem.I installed Cryptkeeper to protect my personal folder with my work stuff, music and pictures.I dont know how but after i cliked in startup programs *remember currently running programs* , part of my password protected folder was gone.I mean everything was gone wrom this folder.Only the folder that i was protecting is still in my desktop, bud all the folders inside this folder is gone.I uninstalled cryptkeeper, but no help.
 Missing files must be somewhere in my computer because the free disc space is still the same as before.
 Hope someone can help me to recover my files.

---

### Post by hakermania on 2011-04-17
EDIT: Excuse me, I forgot that you are maybe unexperienced :(
Go to Applications->Accessories->Terminal and type in
```

sudo updatedb

```
it will prompt for your password, type in your login password (nothing will be shown, not even "***") and press [Enter]
Wait for the command to end, and then type in
```

sudo locate name_of_a_missing_file

```
And follow the same procedure as above. The last command will output the directory(ies) of the name_of_a_missing_file  system-widely, where name_of_a_missing_file is a file's filename which you lost.
Prefer the name_of_a_missing_file to be quite weird and special so as to have less results.

---

### Post by ousef on 2011-08-29
Hi I too have the same issue. The thing is that with me I created a folder using cryptkeeper and moved a lot of stuff to it. After moving it I couldn't figure out how to unmount the drive so i logged off and on. The encrypted folder is still there but is empty. Cryptkeeper doesn't recognize the folder or rather think it exists. I know it's there somewhere. Please help US!!!!

---

### Post by HarrisonNapper on 2011-08-29
> **ousef said:**
> Hi I too have the same issue. The thing is that with me I created a folder using cryptkeeper and moved a lot of stuff to it. After moving it I couldn't figure out how to unmount the drive so i logged off and on. The encrypted folder is still there but is empty. Cryptkeeper doesn't recognize the folder or rather think it exists. I know it's there somewhere. Please help US!!!!

Ousef, I would send an email to someone on the Cryptkeeper team since I assume this was an encrypted folder.

[QUOTE=hakermania]sudo locate name_of_a_missing_file [/QUOTE]

Hakermania, does this do approximately the same thing as

```
sudo find / -name <file>
```

Or maybe the search would be similar to *<file>* ?

It certainly seems faster than find; thanks for the tip. I have a tendency to be working on something and stick clutter places when I'm not paying attention and I'm not in /tmp, so this is great (no more waiting for find to finish)

---

### Post by Wim Sturkenboom on 2011-08-29
updatedb creates a database, next locate will use that; the problem is that it's not real time; actually you have to run updatedb everytime if you look for something

find works real time; create a file and find will find it, locate will not

updatedb is usually / often run once a day using a crontab (my slackware servers do that by default)

---

### Post by Rhizoid on 2011-08-29
Locate is faster because it's searching an index not the filesystem.  It's a great tool but if the index doesn't include the file you're looking for you can get a false negative when it reports it can't find something.

Find searches the filesystem, so it's slower but more thorough and will reflect very recent changes.

Use locate first, if you get a neg then use find.  If find gives you a neg then the file or your spelling of it doesn't exist - retry with -iname instead of -name as that ignores casing.

---

### Post by HarrisonNapper on 2011-08-29
Great! Sorry for derailing the thread, OP may have it back. Will add updatedb to crontab :)

Cheers and thanks for the info all.

---

