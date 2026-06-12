---
title: "Book or articles about learning and understanding commands better"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by ukulele_ninja on 2008-12-10
I am still very green to the linux world but I have a huge fascination with it and I want to learn as much as I can. Can anyone suggest some good books or articles to read that will help me learn and better understand how commands work and what ones do what? That way I dont have to come groveling for help everytime I need one simple thing? lol, thanks all!

---

### Post by philinux on 2008-12-10
Just for starters, you'll get more.

[http://www.oreillynet.com/linux/cmd](http://www.oreillynet.com/linux/cmd)
[http://www.linuxcommand.org/index.php](http://www.linuxcommand.org/index.php)
[http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml)

---

### Post by ayoung on 2008-12-10
I'd head over to your nearest bookstore/library and browse the computer shelves for anything published by O'Reilly with the words 'linux' or 'ubuntu' in the title.  O'Reilly books are easy to spot: they have a bold color with a nice b&w wood-cut (often) animal image.  Their quality and conciseness is tops, IMO.  They also have nice little pocket guides which may be what you're after.

---

### Post by Michael.Godawski on 2008-12-10
I personally do not recommend Linux books; I have the feeling they are always outdated. 

I can err, but that is my impression. 

The best way to learn Linux commands is to experiment, read some threads, try out for yourself, search the internet, which is the most up-to-date source, concerning the very quickly changing Linux world.

---

### Post by bodhi.zazen on 2008-12-10
In addition to the links, learn how to use (read) the man pages. They contain most any information you need.

You can add color if you use most

```
sudo apt-get install most
```

Then, edit ~/.bashrc and add a line :

PAGER='most'

then :

```
. .bashrc
```

---

### Post by txwooley on 2008-12-10
> **bodhi.zazen said:**
> 

Then, edit ~/.bashrc and add a line :

PAGER='most'

I searched File System for "bashrc".  I have 4 of them: bash.bashrc  bash.bash.rc(locked file emblem)  dot.bashrc(locked file emblem) occurs twice albeit with different info inside.  The second dot.bashrc says it is "Personal initialisation file for bash"  Which one do I modify?  Do I need to use gedit?

It would be cool to have a little color in terminal!

---

### Post by cmay on 2008-12-10
[http://www.ss64.com/bash/](http://www.ss64.com/bash/)
i think this is a useful quick overlook. not fantastic but good enough to print out .

---

### Post by txwooley on 2008-12-10
> **cmay said:**
> [http://www.ss64.com/bash/](http://www.ss64.com/bash/)
i think this is a useful quick overlook. not fantastic but good enough to print out .

That's just the "pocket manual" I've been looking for!  Many thanks!

---

### Post by bodhi.zazen on 2008-12-10
> **txwooley said:**
> I searched File System for "bashrc".  I have 4 of them: bash.bashrc  bash.bash.rc(locked file emblem)  dot.bashrc(locked file emblem) occurs twice albeit with different info inside.  The second dot.bashrc says it is "Personal initialisation file for bash"  Which one do I modify?  Do I need to use gedit?

It would be cool to have a little color in terminal!

Modify the one in your home directory

/home/user/.bashrc or ~/.bashrc for short

~ is short hand for $HOME

---

### Post by utnubuuser on 2008-12-10
I've found RUTE to be quite useful too.  (Google it)

---

### Post by txwooley on 2008-12-10
> **bodhi.zazen said:**
> Modify the one in your home directory

/home/user/.bashrc or ~/.bashrc for short

~ is short hand for $HOME

None are in my home directory.  I ran "dir ~" just to make shure, but there is no /user/...  Three of these files are in /ete/usr/share  and one is in /etc/bash.bashrc  If this is the correct file, where do I insert PAGER = most ?  Nothing in there looks like that.  Does it matter exactly where?

---

### Post by bodhi.zazen on 2008-12-10
Files that start with a . (dot) are "hiddden".

Either show hidden files in nautilus or 

ls -a ~

the a flag will show hidden files.

---

### Post by txwooley on 2008-12-10
I tacked SHARE = 'most' onto the end of /etc/bash.bashrc and finished the instructions as shown.  Nothing seemed to happen.  I closed terminal.  Re-opened to run ls -a ~ and voila!  Everything's color coded.  Not sure if colors mean anything though.  I'm gonna MAN "most" and see.  Thanks to all for the handy info.

---

### Post by flynnguy on 2008-12-10
When I was starting out, I found the UNIX Powertools book (the one with the Drill on the cover) to be quite useful. Most O'Reilly books I've gotten have been pretty good though.

---

### Post by MattBD on 2008-12-10
Vim has a great tutor mode available - just type vimtutor in the terminal and it'll start up. Vim is well worth learning.
Book-wise, I liked Beginning Ubuntu Linux from Apress.I also recommend [this link]("https://help.ubuntu.com/community/AdvancedCommandlineHowto#Other%20shells").
I hate to blow my own trumpet, but you might want to check out a blog I run called Easierbuntu, which is at [http://easierbuntu.blogspot.com/](http://easierbuntu.blogspot.com/) , which is aimed at teaching people this kind of thing.

---

### Post by andrew.46 on 2008-12-10
Hi,

Can I put my 2 cents worth in with a book that I have by my side constantly:

> [A Practical Guide to Linux(R) Commands, Editors, and Shell Programming]("http://www.amazon.com/Practical-Guide-Commands-Editors-Programming/dp/0131478230/ref=sr_1_1?ie=UTF8&s=books&qid=1228950709&sr=8-1")
by Mark G. Sobell

Perhaps it tries to do a little too much but I have found it immensely helpful in understanding Linux in general. Ubuntu is not covered specifically in this book though.

All the best,

  Andrew

---

