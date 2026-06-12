---
title: "How to search for files"
date: 2010-08-28
forum: New to Ubuntu
---

### Post by donescamillo on 2010-08-28
Hi,

I am very confused as to how to use the "Search for files" tool. 
If I set "Look in folders"=File system I find files with certain name in places A, B and C.
If I set "Look in folder"=MyHomeFolder I find files with the same name in places D and E.
Why does not the first search show the files found in D and E?
I thought that setting "Look in folders"=File system will look everywhere INCLUDING my home directory.

How can I search everywhere in the file system and be sure I ve found everything there is?

regards

---

### Post by realzippy on 2010-08-28
...have you opened the dropbox and enabled "hidden files.." ?

---

### Post by donescamillo on 2010-08-28
Yes, I have. And the files are not hidden. 
I read somewhere that this GUI tool is an interface for **locate**.
Now if I run  **sudo find -name name_of_file **I find all the instances of this file
If I run **sudo locate name_of_file** I find only some.
But if I do** sudo updatedb** and after that** sudo locate name_of_file** I find them all.
Does that mean I have to run **updatedb** any time I want to search for files?

---

### Post by beew on 2010-08-28
Go to System Tools > Configuration Editor, then from the menu choose apps > gnome-search-tool and check the box "disable_quick_search". Next time when you search for files you can look anywhere you will find all the specified files within the searched directory.

Don't ask me why. It doesn't seem to be very logical but it works. :)

---

### Post by donescamillo on 2010-08-28
From what I gather, locate (and the "Search for files" tool) rely on some sort of database to do search. Probably this option tell GUI to update the database prior to search. Well probably that is better than searching in a database that is old, as it happened to me. 
This is very bad when doing development since files get created all the time during builds and if the database is old it is unreliable and therefore useless.
Well I least now I know :confused:

---

