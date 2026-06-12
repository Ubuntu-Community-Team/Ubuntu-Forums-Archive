---
title: "File Paths in Unix-like OS'es"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by Wataru8675 on 2009-07-21
Before I ask my question, I just want to say I'm sorry if my language or word-choice is goofy...I've been scouring the web reading Java and Linux how-to's and tutorials all day, so I'm about toast by now. @____@

I'm a little lost as to how to define a pathway in the terminal.  Upon finding a source code for a Java application, I put it into Geany, compiled it, and got 3-4 .class files.  Now, putting these .class files together in the same folder and making them work together is a completely different topic that I'll save for the Sun forums, but from the tutorials I've read, I need to define my classpath by showing the computer where my .class files are.

I made a folder for my class files on the Desktop called Java.  To direct my path here, would I type to the terminal:

```
home/Desktop/Java
```?  Because the terminal doesn't seem to like the destination Desktop.

I really hope that this is coherent and followable...a mix of weariness and not having a good grip on the lingo makes for a bad question, I know, so if I've said something that sounds weird...it's probably wrong...let me know so I can clarify.

Thank you a million times over. @_@

---

### Post by nmaster on 2009-07-21
try using '~/Desktop/Java' instead of 'home/Desktop/Java' .  the directory '/home' doesn't contain Desktop.  look into nautilus to get a visual of the filesystem.  use 'cd directory_name' to move to a directory and 'ls' to list the files/directories that are in it.

---

### Post by Wataru8675 on 2009-07-21
But...but...the visual says that Desktop is in my home folder (aka kyle)....right?

---

### Post by lisati on 2009-07-21
> **Wataru8675 said:**
> But...but...the visual says that Desktop is in my home folder (aka kyle)....right?

You're absolutely right. The "~" in "~/Desktop/Java" refers to the currently logged on user's home folder. Each user on your machine has there own home folder.

---

### Post by nmaster on 2009-07-21
kyle != home.  the directory 'kyle' is in the 'home' folder. type 'cd /home' into the terminal.  then type 'ls'  you'll see that 'kyle' is in the 'home' directory

---

### Post by Wataru8675 on 2009-07-21
> **lisati said:**
> You're absolutely right. The "~" in "~/Desktop/Java" refers to the currently logged on user's home folder. Each user on your machine has there own home folder.

Oooooooooooooooooooooooooooooh, okay...you're so smart, thank you. o-o

---

### Post by nmaster on 2009-07-21
> **Wataru8675 said:**
> But...but...the visual says that Desktop is in my home folder (aka kyle)....right?


careful! 'kyle' is not the same as 'home'!!!! they have different names and you need to remember that. it'll be easier if you refer to the directories by their names.  this will make it easier to ask for help.  the info from lisati is totally correct though, i prob should have said that in the first place.

---

### Post by lisati on 2009-07-21
> **neal.m.master said:**
> kyle != home.  the directory 'kyle' is in the 'home' folder. type 'cd /home' into the terminal.  then type 'ls'  you'll see that 'kyle' is in the 'home' directory

> **neal.m.master said:**
> careful! 'kyle' is not the same as 'home'!!!! they have different names and you need to remember that. it'll be easier if you refer to the directories by their names.  this will make it easier to ask for help.  the info from lisati is totally correct though, i prob should have said that in the first place.

Good catches. Perhaps I should have said that each user has their own folder within home.....

---

