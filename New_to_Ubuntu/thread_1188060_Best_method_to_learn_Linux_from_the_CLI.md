---
title: "Best method to learn Linux from the CLI?"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by dromichaetes on 2009-06-15
I think the best feature of Linux is that it lets you play with it and has lots of new things to learn. Since I am a new convert to Linux (yap, I erased Windows for good) I already crashed it 4 times. You can figure why...
 
So my question to you is which method is the best (apart from regularly messing everything up and installing Ubuntu afresh as I mentioned before) for learning to work with the system from the CLI? 
 
I have found a few very good tutorials and, of course, the forum here is great, but maybe someone knows a better, more intensive way to learn Linux quicker.

---

### Post by dvdhaar on 2009-06-15
You can setup a virtual machine in Virtualbox and mess with it all you want :)

---

### Post by the8thstar on 2009-06-15
Buy books on Amazon.com. There's plenty to choose from and some of them focus specifically on the CLI (command line interface).

---

### Post by dromichaetes on 2009-06-15
@dvdhaar
I don't really have a problem crushing Ubuntu as long as I use my old laptop for learning CLI, but I will give it a try with Virtualbox as you mentionned.
 
@the8thstar
I could find a couple of books on torrents, but I miss the advice of someone who is well experienced, especially when it gets to --options for commands. Some things are not as easy to understand as one should expect. Do you have some particular titles in mind? 
 
Is there a possibility to find a tutor, which I could bother with questions when I get stuck and who could set for me the first important steps to learn? You know, sometimes is more important to learn how to learn right...

---

### Post by halitech on 2009-06-15
instead of messing around with it, breaking it and then reinstalling, when you break it, learn how to fix it instead of just reinstalling. You'll get good at reinstalling that way but you won't really learn how to use the system.

---

### Post by Bachstelze on 2009-06-15
> **dromichaetes said:**
> Is there a possibility to find a tutor, which I could bother with questions when I get stuck and who could set for me the first important steps to learn?

That's what the forums are for. ;)

---

### Post by iponeverything on 2009-06-15
Here is a very good lecture with exercises:

[http://www.doc.ic.ac.uk/~wjk/UnixIntro/](http://www.doc.ic.ac.uk/~wjk/UnixIntro/)

---

### Post by jvc26 on 2009-06-15
Obvious starting point is the man and info pages for a given command:

```
man <command>
```

```
info <command>
```

Which will give you loads of information on a given command. Sometimes a little cryptic or inaccessible, but they are really helpful for the budding command line user.

Il

---

### Post by theozzlives on 2009-06-15
The Ubuntu Linux Bible is good and Amazon has the 8.10 version.

---

### Post by dromichaetes on 2009-06-15
Thank you guys, you really rock! First of all, I have already started to make backups (just in case), but it happens sometimes that bad commands cannot be undone. It happened to me while playing with symbolic links. Only after I was in trouble I searched the forums only to find out that once you make a symbolic link by naming it with a different file, the content of respective file is actually erased and replaced...

I hope I will be able to fix my mistakes without having to reinstall everytime. 

Btw, I have found a version (I think is 2007) of Ubuntu Bible on torrents. Is great stuff, but does not compare with tutorials like this one: [http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php) . I have also found another book: Linux for Dummies. Which explains the basics plain and simple, but I think I can go now to the next level. 

I already play around with CLI customizations (I learned how to use aliases and color-marking), but going into the man pages is pretty cumbersome if you do not know the commands you need to look for...

How did you learn linux? Is it a good idea to try a project like [Linux from Scratch]("http://www.linuxfromscratch.org/")? Has anyone tried it or is not a good idea for a noob?

---

### Post by oldsoundguy on 2009-06-15
or get yourself a used cheapo computer somewhere (Goodwill?) and practice and test on it.  I have one     that is on my net and it is called "Crash Test Dummy"

---

### Post by H2SO_four on 2009-06-15
I would recomend reading and trying the examples given in the book.  Much like school.  

Heres some texts that I use as reference:

ubuntukungfu.org

[http://www.amazon.com/Ubuntu-Linux-Bible-William-Hagen/dp/0470038993/gizmodo-20](http://www.amazon.com/Ubuntu-Linux-Bible-William-Hagen/dp/0470038993/gizmodo-20)

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

there are many more out there.  I like to learn by reading and doing.  Some people prefer doing only, just my suggestion.  

Best of luck!!

---

### Post by donkyhotay on 2009-06-15
I personally haven't had much luck with books for learning about computers. I've found the best way is lots of experimentation and tutorials/how-to's online. Obviously you don't want to do this with your 'regular' computer that you use all the time. Either have a crash box designed to be broken & repaired or use virtualbox (as has been mentioned before). Also, after breaking something definitely try to fix it without reinstalling however sometimes there are no easy solutions besides reinstalling. Play around with it, don't be shy. Remember there is nothing you can do to the computer that reinstalling the OS won't fix (well... short of physical damage or firmware updates that is). So long as it's either a crash box that you expect to be down more often then not or a virtual machine where it doesn't matter then don't worry about messing up.

---

### Post by dromichaetes on 2009-06-15
> **iponeverything said:**
> Here is a very good lecture with exercises:

[http://www.doc.ic.ac.uk/~wjk/UnixIntro/]("http://www.doc.ic.ac.uk/%7Ewjk/UnixIntro/")
@iponeverything,
thanks for the great link. This is good for practice. I will try to make a collection of such links with exercises. Maybe other noobs like me will find it useful. There are lots of examples (short scripts) spread around this forum.

---

### Post by Azrael3000 on 2009-06-15
I'm learning myself but if you have not yet stumbled across the
```
apropos
``` command, I can recommend it a lot :)
Enjoy fidling around.

---

### Post by dromichaetes on 2009-06-15
@donkyhotay
what you say is my preferred way of learning. I have to experiment to see exactly what changes. This is why usually when learning from "man" I test in the terminal all the attributes and options...

---

### Post by dromichaetes on 2009-06-15
> **Azrael3000 said:**
> I'm learning myself but if you have not yet stumbled across the
```
apropos
``` command, I can recommend it a lot :)
Enjoy fidling around.
When running it in the terminal I get this:
```
~$ apropos
apropos what?

```

Ok, now I get it :) Thanks a lot, this might be very helpful when searching for a command.

---

### Post by Anzan on 2009-06-15
Try Inx (Inx==Inx is Not X), a disto based on Ubuntu LTS.

[http://inx.maincontent.net/]("http://inx.maincontent.net/")


> INX is a "Live CD" distribution of GNU/Linux, derived from Ubuntu 8.04.1 LTS, but using "ubuntu-minimal" and "ubuntu-standard" as a base. It is console only, without any graphical "X" programs.

INX is intended as a "tutorial" and introduction to the Bash command line, but is a fully capable, portable GNU/Linux system in its own right. It has a collection of easy-to-use menus, colour themes, easy configuration tools, music (and video on the frame buffer), some games, and several surprises for those who are not aware of what can be done in a console/tty.

INX is fun, and not intimidating for console beginners.


---

### Post by guyminuslife on 2009-06-15
I think reading some books on Bash and about Unix in general is a good idea. Tutorials are nice for "I want to do this, here's how," books are good for, "Hey, here's some tools, and how they work, happy hunting."

Of course messing around is imperative. But I've found I'm more efficient at learning when I have some general knowledge to back it up. And you're not going to find every useful command from Google or the manpages.

I'm at the point, at least, where if I break something, I can fix it without reinstalling.

---

### Post by MrWES on 2009-06-15
> **dromichaetes said:**
> I think the best feature of Linux is that it lets you play with it and has lots of new things to learn. Since I am a new convert to Linux (yap, I erased Windows for good) I already crashed it 4 times. You can figure why...
 
So my question to you is which method is the best (apart from regularly messing everything up and installing Ubuntu afresh as I mentioned before) for learning to work with the system from the CLI? 
 
I have found a few very good tutorials and, of course, the forum here is great, but maybe someone knows a better, more intensive way to learn Linux quicker.

Try installing and reading the Advanced Bash Scripting guide;
```
sudo apt-get install abs-guide
```
Then you can view the guide by pointing your web browser to:
[file:///usr/share/doc/abs-guide/html/index.html]("file:///usr/share/doc/abs-guide/html/index.html")

---

### Post by DarkDancer on 2009-06-15
> **halitech said:**
> instead of messing around with it, breaking it and then reinstalling, when you break it, learn how to fix it instead of just reinstalling. You'll get good at reinstalling that way but you won't really learn how to use the system.

+1

---

### Post by lkraemer on 2009-06-15
Here is a wallpaper that can help.
[http://tuxtraining.com/2008/10/02/handy-wallpaper-for-basic-linux-commands](http://tuxtraining.com/2008/10/02/handy-wallpaper-for-basic-linux-commands)

lkraemer

---

### Post by the8thstar on 2009-06-16
> **HymnToLife said:**
> That's what the forums are for. ;)

Ditto.

---

### Post by dromichaetes on 2009-06-16
@Ikraemer, 
getting that wallpaper is one of the first things I have done when switching to Linux. I have it in negative (black on white) on my desktop.

---

### Post by Mornedhel on 2009-06-16
> **dromichaetes said:**
> @Ikraemer, 
getting that wallpaper is one of the first things I have done when switching to Linux. I have it in negative (black on white) on my desktop.

As someone who does all of his work on his computer, and then mostly in a terminal (emacs) or reading text (in PDFs), I should point out that white-on-black is much less tiring for the eyes than black-on-white and, in the long term, less likely to cause vision problems. My terminal is white on black, and I read PDFs with the Compiz plugin to render a window in negative.

---

### Post by dromichaetes on 2009-06-16
> **guyminuslife said:**
> I'm at the point, at least, where if I break something, I can fix it without reinstalling.
 
After crashing and trashing my system 4 times I know now a lot more what NOT to do. And - based on what I could find on the forums - I can perform simple tasks from the CLI and without using the GUI. I think is a lot more rewarding to perform a task with a simple command line than to click and click the hell out of the graphical interface. 
 
One more thing: I am that kind of person who uses the trackpoint instead of a touchpad or mouse - because I don't need to move my fingers from the keyboard.

---

### Post by dromichaetes on 2009-06-18
Maybe someone knows how to do this: I have a relatively large collection of mp3 [mostly jazz and rock]. Some of my files are ordered in albums, so that e.g. for Louis Armstrong I have under Album 1: track01.mp3, track02.mp3, track03.mp3 etc. 
 
When I copy my music to a portable [a samsung] I cannot copy just the mp3s [without directories] because in each Album there is a track01.mp3, track02.mp3 etc. I know that it should be possible that, instead of manually renaming each mp3 file, one changes the names of mp3 files in directory Album 1 for example with a command from the CLI using wildcards [???]. I need to rename the files so that track01.mp3 under Album 1 becomes 1.track01.mp3, and track05.mp3 under Album 3 becomes 3.track05.mp3. 
 
What command should I use?
 
_Update_: I have found the command. It is easily done with "rename", although using wildcards is still pretty confusing for me.

---

### Post by marshag63 on 2009-06-23
+1 for INX - it has tutorials and a lot of great CLI apps ready to run.

[http://inx.maincontent.net/](http://inx.maincontent.net/)

MarshaG.

---

### Post by wizard10000 on 2009-06-23
> **oldsoundguy said:**
> or get yourself a used cheapo computer somewhere (Goodwill?) and practice and test on it.  I have one that is on my net and it is called "Crash Test Dummy"

I do the same.

---

### Post by dromichaetes on 2009-06-23
> **wizard10000 said:**
> I do the same.
ok, guys, could you be more specific than that? What do you mean by an old cheap comp? Something with Intel Pentium III (like my old Thinkpad T23) will do? Or do you mean older still? And how many RAM should be enough fr a "crash test dummy"?

---

### Post by halitech on 2009-06-23
anything above a P3 500 with 512 meg of ram should be enough to play with. I play around on older systems (P 300 with 128meg of ram) but I'm patient and I like learning the limitations of the systems.

---

### Post by m9ke on 2009-06-23
Over the last couple of years I've been an Ubuntu user, I have wanted to make the OS do stuff, and sometimes had to fix problems. 

I figured most of these out, with the help of this forum.  

But unless I used what I learned frequently, I forgot it.  So, I got into the habit of informally documenting how I did stuff in the terminal including commands and results.  

I routinely go back and refer to these notes when I need to do something I haven't done for a while.  It saved me from having to re-learn many solutions.

---

