---
title: "Terminal/Command line question"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by mattbutsko on 2009-01-07
I'm pretty new to linux/ubuntu still and I got one quick question, how often do I have to use the *terminal/command line*? For example, I'm following Java's instructions on extracting the jdk-6u11-linux-i586.bin file using chmod +x in the terminal, and it continually says "No such file or directory". 

Now, I'm about 99% sure that this is the correct directory, and yet nothing's getting done. I've had linux for about two days now and almost every time I have to use the terminal, I get an error. 

Now, I understand it'll take time and experience, but are there a lot of graphical equivalents to the command line? Cause this is really challenging and slightly annoying.

---

### Post by 2hot6ft2 on 2009-01-07
> **mattbutsko said:**
> I'm pretty new to linux/ubuntu still and I got one quick question, how often do I have to use the *terminal/command line*? For example, I'm following Java's instructions on extracting the jdk-6u11-linux-i586.bin file using chmod +x in the terminal, and it continually says "No such file or directory". 

Now, I'm about 99% sure that this is the correct directory, and yet nothing's getting done. I've had linux for about two days now and almost every time I have to use the terminal, I get an error. 

Now, I understand it'll take time and experience, but are there a lot of graphical equivalents to the command line? Cause this is really challenging and slightly annoying.
Not very often for normal use once you have it set up the way you want. The chmod command would require sudo before it. And if you're just trying to get Java here's how real easy.

You need to put this in a terminal and hit Enter
Applications>Accessories>Terminal

```
sudo apt-get install ubuntu-restricted-extras
```

Then your password and Enter (your password will not be displayed)

It will fix that as well as other missing multimedia you haven't found out about yet.

When it gets to the agreement hit Tab then Enter to accept the Java agreement.

All done

---

### Post by Paqman on 2009-01-07
> **mattbutsko said:**
> how often do I have to use the *terminal/command line*? 

Not often.

Most things that the command line can do also have a GUI. You might have to install it first though. Terminal commands are common in HOWTO guides because they're (mostly) the same for all the different distros.

Unless you've got b0rkage happening in your box, you don't ever have to use the command line if you don't want to.

Easiest way to extract files, btw? Right-click and "extract here". Doing it in the terminal is (IMO) masochism.

---

### Post by Drubie on 2009-01-07
> **mattbutsko said:**
> how often do I have to use the *terminal/command line*?

there are graphical alternatives to many of the things done in the terminal; for example, programs/applications can be installed using the Add/Remove..., the Synaptic Package Manager, or the command ```
sudo apt-get install [package_name]
``` in the terminal are all ways to get or remove apps.

> **mattbutsko said:**
> 
Now, I understand it'll take time and experience

Amen there.  just pay attention to where you are and you should be fine.  there are plenty of command line guides in the forums, just hunt around a bit.  A good place to start would be [here](http://ubuntuforums.org/showthread.php?t=1024219&highlight=terminal+tutorial) I guess.  Dont be scared by doomsayers, just be careful and nothing bad will happen.  

good luck and have patience  (not patients I hope)...

---

### Post by bodhi.zazen on 2009-01-07
Although intimidating at first , the terminal is quite useful.

With that said, some users almost never or even never use the terminal.

My wife for example has used linux for years, never uses a terminal (and I mean NEVER), although I sys admin (much easier with ssh :lolflag: )

At any rate, it is jsut a matter of learning new tricks.

[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

### Post by earthpigg on 2009-01-07
> **mattbutsko said:**
> I'm following Java's instructions on extracting the jdk-6u11-linux-i586.bin file using chmod +x in the terminal, and it continually says "No such file or directory". 


always _always_ ***_always_*** find and follow _*ubuntu specific*_ instructions - i've never had a reason to play around with chmod or compiling or any of that stuff. its all mumbo-jumbo to me.

---

### Post by snova on 2009-01-07
Most of the time, not at all.

But when it comes to support, being a forum, it's a lot easier to give instructions in the form of commands than in graphical instructions. And much shorter.

> For example, I'm following Java's instructions on extracting the jdk-6u11-linux-i586.bin file using chmod +x in the terminal, and it continually says "No such file or directory".

You can be as sure as you want, but if that's what it says, it ain't there. ;)

First of all, what directory did you save it in? Your desktop? Documents folder? Home directory?

Secondly, which directory is the shell in? Run "pwd" to check. (Like I said...)

It is, however, preferable to install things from the package manager... And Sun Java 6 is in the repos.

---

### Post by mattbutsko on 2009-01-08
Thanks for all of the replies, good news is it was just a stupid error. Like almost every other folder/directory in linux, I thought /Desktop was lowercase, after I noticed that, everything's been great and I even wrote my first java app (Hello World!) so I'm pretty excited.

I'm also getting used to the terminal, but I still have a question, is there a guide for ubuntu's graphical equivalent for the terminal? Cause aside from New Folder or Extract File for example, I can't really find any.

---

