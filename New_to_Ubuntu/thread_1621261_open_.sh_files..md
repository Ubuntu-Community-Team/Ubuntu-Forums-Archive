---
title: "open *.sh files."
date: 2010-11-14
forum: New to Ubuntu
---

### Post by drordh on 2010-11-14
hey,
i am trying to open files in *.sh, that opened in windows , saving at fastq format, but i didnt succeed of open it in ubuntu?
ideas?
thanks...

---

### Post by Wtower on 2010-11-14
It depends on how you're trying to open it really. Perhaps there is something wrong with the file association in gnome or a permissions problem. I don't know what is fastq, the sh files are shell script files in linux.

Regards

---

### Post by c2tarun on 2010-11-14
> **drordh said:**
> hey,
i am trying to open files in *.sh, that opened in windows , saving at fastq format, but i didnt succeed of open it in ubuntu?
ideas?
thanks...

try changing that file to executable mode by writing following to the terminal

```

sudo chmod u=+x <filename>

```then type 
```

./<filename>

```

---

### Post by c00lwaterz on 2010-11-14
> **drordh said:**
> hey,
i am trying to open files in *.sh, that opened in windows , saving at fastq format, but i didnt succeed of open it in ubuntu?
ideas?
thanks...

you can do shortcut then execute in there. use -window in command line

---

### Post by tajiknomi on 2010-11-14
[I][SIZE=2]You should try **App-Runner**, its easy tool to open/run .sh,.run and many more by just right-clicking it...

moreover,follow this,, [/SIZE][/I][http://hacktolive.org/wiki/App_Runner](http://hacktolive.org/wiki/App_Runner)

---

