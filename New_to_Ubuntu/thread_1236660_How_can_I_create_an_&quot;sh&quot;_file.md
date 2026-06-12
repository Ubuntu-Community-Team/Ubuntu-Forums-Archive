---
title: "How can I create an &quot;sh&quot; file?"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by Cotopaxi on 2009-08-10
Hi,

I am trying to create an &#8220;sh&#8221; file that starts up a java application.

In the terminal I have to type:

> java -jar Zettelkasten.jar

being &#8220;Zettelkasten&#8221; the application.

In the command line it looks like this:

> xxl@xxl-desktop:~/Software/Zettelkasten/Zettelkasten3$ java -jar Zettelkasten.jar

Can anyone give me a helping hand please?

Thanks!:popcorn:

---

### Post by Tibuda on 2009-08-10
Application > Accessories > Text Editor (aka Gedit). Type:
```
#!/bin/sh
cd ~/Software/Zettelkasten/Zettelkasten3
java -jar Zettelkasten.jar
```
Save it somewhere, and right-click the file and click Properties. On the Permissions tab, allow the file to be executable. Done.

---

### Post by Cotopaxi on 2009-08-10
Danielrmt

Thanks very much indeed, it works!! :popcorn:

One funy thing:

I did not mention that I am working with Kubuntu, because I thought all &#8220;terminal commands&#8221; are the same in all linux distros! They eventually are, but with SMALL AND SUBTLE differences! But in Kubuntu, I have to type:

> cd '/home/Software/Zettelkasten/Zettelkasten3'

How to find out, which is the correct way in your linux distro?

In your file manager open the menu &#8220;view&#8221; and select &#8220;show terminal&#8221;.

In the &#8220;Dolphin&#8221; file manager a terminal-sub-window opens op in the lower end of the file manager.

Click yourself through the different directories and observe the text in the terminal.
This text is the text that has to go into the *.sh file!

Again, thanks very much indeed!

---

### Post by Cotopaxi on 2009-08-10
Sorry, how do I mark this thread as solved?

---

### Post by Tibuda on 2009-08-10
I think both would work. There are three ways to go to a home subfolder as I know:
```
cd ~/subfolder
cd $HOME/subfolder
cd /home/$USER/subfolder
```

> **Cotopaxi said:**
> Sorry, how do I mark this thread as solved?

The 'solved' feature was disabled in the forums, but you can add a 'solved' tag to the thread, if you click on "Edit tags" in the thread footer. You can also rename your thread title to include [SOLVED]

---

