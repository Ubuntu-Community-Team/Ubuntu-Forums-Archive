---
title: "Duplicate files"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by Lemuel111 on 2010-03-09
Can anyone suggest a good & safe programme which will find duplicate files & show which one was the newest so you delete the oldest ones? I tried Fslint but it doesn't show which is the newest file. I also tried KleenSweep but it didn't find my duplicate files in Documents. Its my own Documents folders I mainly want to sort as I haven't a clue about all the other duplicate files which show up & don't want to delete things I shouldn't. 
Thanks.

---

### Post by ubudog on 2010-03-10
The file manager in Ubuntu should be able to handle that.  Just search for the filename and it will find all the files with that name.

---

### Post by sports fan Matt on 2010-03-10
I tried KleanSweep before..it was a very bad idea..deleted alot of good system & config files

---

### Post by 2hot6ft2 on 2010-03-10
I use Kleansweep with no problems at all. You have to pay attention to where you're telling it to look, what to include and what you exclude from the search. If you take your time and use it right it does a fine job. I haven't found a better duplicate file finder in ubuntu yet.

If you just want to compare 2 folders then give krusader a try it's a dual pane file browser which you can find in Synaptic or install with
```
sudo apt-get install krusader
```
in a terminal.
> Krusader is a simple, easy, powerful, twin-panel (commander-style) file
manager, similar to Midnight Commander (C) or Total Commander (C).

It provides all the file management features you could possibly want.

Plus: extensive archive handling, mounted filesystem support, FTP,
advanced search module, viewer/editor, directory synchronisation,
file content comparisons, powerful batch renaming and much more.

If you want to compare the contents of 2 files try meld. Same deal Synaptic or the terminal
```
sudo apt-get install meld
```
> Meld is a tool which allows the user to see the changes in, and merge between,
either two files, two directories, or two files with a common ancestor.

---

### Post by moody_mark on 2013-04-06
You could simple use "diff" on the command line to show which files are different. Or you could use "rsync" again on the command line to provide a means of backing up only newer files.

It depends on what you are trying to do. For example you might want to just report files that have differences, for this "diff" should be adequate. If you want to run a backup program and only backup new/changed files then you should look at rsync.

---

### Post by Elfy on 2013-04-06
Closed - spam necro

---

