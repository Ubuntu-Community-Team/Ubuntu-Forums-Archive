---
title: "rm -f *~"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by flylehe on 2009-09-03
HI,
I wonder what *~ mean in this example
```

rm -f *~ debug/bin/svm.o

```
Thanks and regards!

---

### Post by SlugSlug on 2009-09-03
> **flylehe said:**
> HI,
I wonder what *~ mean in this example
```

rm -f *~ debug/bin/svm.o

```Thanks and regards!


~ is normally used to goto /home/[username]/

---

### Post by kansasnoob on 2009-09-03
> **flylehe said:**
> HI,
I wonder what *~ mean in this example
```

rm -f *~ debug/bin/svm.o

```
Thanks and regards!

I'm not sure but I'm very, very cautious with any "rm" command!

Paranoid would be a great description.

---

### Post by mcduck on 2009-09-03
The tilde character is also often used to mark backup files by adding it to the end of the filename. In this command it's used together with the wildcard ("*") to automatically remove such backup files.

"*~" would point to any files in the current directory that have "~" as the last character in the name.

Still, that command is clearly taken out of context (based on use of a relative path in the command) so I'm not going to say anything about the usefulness or safety of the command. However removing backup files is usually perfectly safe thing to do.Also I'd recommend leaving the "-f" option out unless you can't get the command to complete succesfully without it. Using unnecessary force automatically is rarely a good way to do things. It's better to try normal "rm" first and then add the force option if needed.

---

### Post by Gen2ly on 2009-09-03
It means don't do.  rm should require super-super user privileges.

---

### Post by perce on 2009-09-03
> **Gen2ly said:**
> It means don't do.  rm should require super-super user privileges.

Absolutely not. rm requires superuser privileges if one wants to remove files belonging to root or to another user, but obviously any user can remove his own files.

---

### Post by Gen2ly on 2009-09-03
lol, perce, think you missed a word there.

---

### Post by lykwydchykyn on 2009-09-03
> **Gen2ly said:**
> It means don't do.  rm should require super-super user privileges.

Oh for pete's sake.  It just deletes files.  You have a key on your keyboard that does the same thing.

Besides, if we always had to use it with root privileges, there'd be a higher chance of me destroying my system while cleaning my home directory.

---

### Post by Simian Man on 2009-09-03
It is often used in the clean target of a makefile to remove backup files that gedit or emacs create.  The -f option is used because otherwise rm will balk at you if there are no such file to remove.  It is a perfectly safe and perfectly sane thing to do.

---

### Post by Penguin Guy on 2009-09-03
> **flylehe said:**
> HI,
I wonder what *~ mean in this example
```

rm -f *~ debug/bin/svm.o

```
Thanks and regards!
**Probably** harmless. Looks as if the person who wrote it didn't have a clue what they were talking about. What it will do is forcefully remove all backup files in the working directory and delete a file at [COLOR="Green"]./debug/bin/svm.o[/COLOR]. In answer to your question, the *~ means 'backup files'.

I'd be very interested to know where you found it. Also, do you have a file called 'svm.o' on your system? To find out run [COLOR="Green"]find / -iname "svm.o" 2>/dev/null[/COLOR].

---

### Post by bacardiandwatermelon on 2009-09-03
To put your mind at ease...
[http://ubuntuforums.org/announcement.php?a=54](http://ubuntuforums.org/announcement.php?a=54)

---

### Post by lisati on 2009-09-03
Extreme care is advised: it looks suspiciously similar to a potentially dangerous command. One slip of the fingers, and ouch!

---

### Post by bodhi.zazen on 2009-09-03
> **flylehe said:**
> HI,
I wonder what *~ mean in this example
```

rm -f *~ debug/bin/svm.o

```Thanks and regards!

As has been stated in this thread :

1. This command will remove files with the "~" character at the end of the file name.

These files are typically automatic backups made with gedit or nano -B and removing them will not do any damage.

2. The rm command does not, by default, ask for confirmation, so if you make a typo you can easily remove more then you barganed for.

I advise you set ```
alias rm="rm -i"
``` in .bashrc (same with cp and mv) and IMO this should be default.

So long as you are careful with your typing and use the -i flag there is nothing inherently malicious about the rm command.

With that, I am going to close this thread as it is getting a bit off topic and I believe the question is asked and answered.

---

