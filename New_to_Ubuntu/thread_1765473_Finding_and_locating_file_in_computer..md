---
title: "Finding and locating file in computer."
date: 2011-05-23
forum: New to Ubuntu
---

### Post by eb3ha4el on 2011-05-23
I use locate command to find file in my computer
but strangely it seems to fail to work sometimes..
Not sure, but i got a feeling... :confused:

do people generally use locate command to find any file?
is locate command equals to that of searching function in explorer in Windows?

---

### Post by r-senior on 2011-05-23
The locate command is a convenience command that relies on a database which is only refreshed once a day. It won't find files created since the last update.

From the command line, the find command would be your best bet. Or you can also use Nautilus (file manager) to search for files.

If you are running 11.04 and Unity, Zeitgeist tracks your recent file history (in most cases) and lists them in the Files and Folders lens on the launcher.

There's general help on finding files here (but it's a bit out of date):

[https://help.ubuntu.com/community/FindingFiles](https://help.ubuntu.com/community/FindingFiles)

---

### Post by nothingspecial on 2011-05-23
You can update the database manually

```
sudo updatedb
```

Then use locate.

---

### Post by eb3ha4el on 2011-05-23
Fantastic 
thanks.

but would you consider find command better than locate?
what's difference between them?

---

### Post by nothingspecial on 2011-05-23
find is an incredibly powerful command (and potentially destructive if you don't know what you are doing).

There are many many options with find, you can search by modification time, owner, size, etc etc and perform actions on the files you find.

If you just want to know where a file is, use locate.

If you want to find every video file in on our computer, convert them to mp4 and place them in a folder on an external hard drive (for example), use find.

---

### Post by shashanksingh on 2011-05-23
sudo find / -name <filename or %like>

this can give you similar file names, if you want to be thorough with your search

---

### Post by eb3ha4el on 2011-05-23
Right
I think i got that
thanks very much you all

---

### Post by r-senior on 2011-05-23
Locate uses an index in a database to look up files by name, with pattern matching. Because it uses an index, it's fast, but not always up to date.

Find is a more general command line tool that allows you to scan the filesystem (not a pre-built index), execute commands on files, control the search depth and so on. But running find on a large filesystem takes time.

Neither is better. They have different objectives.

---

### Post by andrew.46 on 2011-05-25
Perhaps have a look at this page for more information on 'find':

find - Community Ubuntu Documentation
[https://help.ubuntu.com/community/find](https://help.ubuntu.com/community/find)

Andrew

---

