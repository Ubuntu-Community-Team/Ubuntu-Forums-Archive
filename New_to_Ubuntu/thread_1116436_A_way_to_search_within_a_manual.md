---
title: "A way to search within a manual?"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by Rumtscho on 2009-04-04
Due to a problem with my screen resolution I have to change my xorg.conf file manually. I open the manual easy enough by typing man xorg.conf, but scrolling through thousands of lines when only 20 are visible at a time (640x480 screen resolution *grrrrr*) is quite trying. Is there a way to open the manual as a searchable file, maybe with gedit? 

By the way, if you think you can help with the other problem, it would be nice if you'd give it a look here: [http://ubuntuforums.org/showthread.php?t=1116341](http://ubuntuforums.org/showthread.php?t=1116341)

---

### Post by ad_267 on 2009-04-04
You can search through man pages using /. 

Type / then your phrase to search for, then use n and N to scroll through the matches.

---

### Post by llamabr on 2009-04-04
Also, besides /, which is a nice tip, you can find any man page by asking google sor it.  html is also nicely searchable.

---

### Post by kansasnoob on 2009-04-05
The man pages will drive you crazy!

What version of Ubuntu are you using?

You can find out by entering in terminal:

```
cat /etc/issue
```

And it would be helpful to know what your graphics card is:

```
lspci | grep VGA 
```

---

### Post by hyper_ch on 2009-04-05
you can of course
```

man COMMAND > ~/Desktop/COMMAND.txt

```

Then you have it as text file that you could open in a different editor.

---

