---
title: "question on 'ls' command"
date: 2010-08-15
forum: New to Ubuntu
---

### Post by gaurish108 on 2010-08-15
I had a question about the 'ls' command.

My Desktop currently has only two files source.c and Makefile. 

However when I type 'ls' in the terminal I see many file names in the  list which are followed by a tilde. I remember some of them being old files I had created a couple of weeks back while being introduced to C . *(See below)


gtelang@Ubuntu-B-148-6:~/Desktop$ ls 
attempts.c~    b.txt~    file2.c~  LWS.txt~   mango.c~   source.c~  tiger.txt~
attempts.txt~  column~   file3.c~  Makefile   marathon~  test1d~    tree.txt~
a.txt~         file1.c~  hello.c~  Makefile~  source.c   test.c~
gtelang@Ubuntu-B-148-6:~/Desktop$ 

What is the significance of this tilde sign? Do these deleted files still exist on some part of my computer? My trash can is empty by the way. 


And more importantly how do I stop the 'ghost' filenames with ~ after them to stop showing themselves in the terminal

---

### Post by Finalfantasykid on 2010-08-15
Yes that would usually mean that they are temporary files, most likely created by gedit or any other text editor.  You can disable this in the properties of gedit.

---

### Post by gaurish108 on 2010-08-15
ooh thanks....but how do I disable the feature? My default text-editor is emacs.  

And will disabling this feature be of any possible disadvantage in the future?

---

### Post by Finalfantasykid on 2010-08-15
I found this [http://blogs.sun.com/terrygardner/entry/disable_emacs_backup_files](http://blogs.sun.com/terrygardner/entry/disable_emacs_backup_files)

And I don't think it will affect it really.  If there is a crash, you might just lose a backup

---

### Post by amac777 on 2010-08-15
```
ls -B
```

will ignore those backup files. If you want that to be the default, you can modify your bash_rc to alias that ls command.

```
gedit .bashrc
```

Find the ls alias and change it to this:

```
alias ls='ls --color=auto -B'
```

---

### Post by gaurish108 on 2010-08-15
thanks, I guess that settles it.

---

