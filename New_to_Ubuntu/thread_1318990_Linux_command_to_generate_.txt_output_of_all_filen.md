---
title: "Linux command to generate .txt output of all filenames in a folder?"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by humphreybc on 2009-11-08
[B]EDIT: Don't worry, I figured it out! You just have to cd to your directory, ie, cd /home/benjamin/movies and then ls as usual - this will display the list of files in the terminal.

To redirect the output to a txt file, you can go:

```

ls > movies.txt

```

God I love Linux![/B]

I've read how to do this in a book somewhere but I've forgotten. Basically I have a folder of movies, over 100 of them, and I'd like to generate a .txt file with a list of all the movies in that folder.

What's the command?

Thanks!

---

### Post by squenson on 2009-11-08
The command ls lists the files in a folder, the attribute -1 (dash one) puts one file per line. To send the result to a file called mylist.txt, simply adds the sign > followed by the file name. All this gives:
ls -1 > mylist.txt

---

### Post by CJ Master on 2009-11-08
squenson covered it, and also if you want to see the files in a directory without putting them in a text file just run plain "ls."

---

