---
title: "gedit - comparing two files similtaneously by eye"
date: 2009-06-10
forum: New to Ubuntu
---

### Post by F W Adams on 2009-06-10
This seems such an obvious problem that perhaps I've missed something simple. Couldn't find a solution elsewhere on bb.

Suppose I want display and compare two files side by side for differences by eye. This seems only possible by running two versions of gedit at the same time. With only one version I can only see any one file at a time?

Having messed about quite a lot I am unable to get two files on the screen at the same time to compare them.

Of course I can use a different program but that seems to be ducking the issue. Surely there is a better solution.

---

### Post by PmDematagoda on 2009-06-10
> **F W Adams said:**
> This seems such an obvious problem that perhaps I've missed something simple. Couldn't find a solution elsewhere on bb.

Suppose I want display and compare two files side by side for differences by eye. This seems only possible by running two versions of gedit at the same time. With only one version I can only see any one file at a time?

Having messed about quite a lot I am unable to get two files on the screen at the same time to compare them.

Of course I can use a different program but that seems to be ducking the issue. Surely there is a better solution.

If you want to know the differences between two files you can use diff as such in a terminal, this may be more easier than to try and find the differences manually:-
```
diff -u name-of-first-file name-of-second-file
```

---

### Post by sonicb00m on 2009-06-10
Diffuse merge tool is a very good graphical file compare utility as well. I use it a lot.

---

### Post by Celauran on 2009-06-10
> **F W Adams said:**
> Of course I can use a different program but that seems to be ducking the issue. Surely there is a better solution.

I don't think it's ducking the issue at all. I think it's using the right tool for the job. That said, I've been happy with Meld for years.

---

### Post by glennric on 2009-06-10
You could also use gvim.  If you type 
```
gvim -d file1 file2
```
from a terminal then gvim will show a split window with the differences between the two files highlighted.  Of course vim can be a bit confusing to those who are not familiar with it, but is one of the most powerful text editors in existence.

---

### Post by Mornedhel on 2009-06-10
> **glennric said:**
> You could also use gvim.  If you type 
```
gvim -d file1 file2
```from a terminal then gvim will show a split window with the differences between the two files highlighted.  Of course vim can be a bit confusing to those who are not familiar with it, but is one of the most powerful text editors in existence.

In the interest of continuing the standard vim vs emacs troll, I hereby assert that 1. emacs has a diff mode as well and 2. emacs > vim.

In the interest of answering the OP's question, as previously stated, meld works fine and has a not too confusing interface.

---

### Post by handydan918 on 2009-06-10
In the interest of not making it sound like gedit can't do this...

Use the "File" menu in gedit. This will allow you to open a file, resize the windows, and open another file in another window.


See? How hard is that?

---

### Post by F W Adams on 2009-06-10
handydan918
It didn't sound hard at all but is your set up the same? I felt sure it was possible but how to open another window?

Once you're got one file in one window, if you open a second file, whether by using File->open or by double-clicking a second file from elsewhere all you get ( or rather all I get ) is a second tab in the original window. And no possible way of viewing both files at once. I suspect I'm being thick over this. I use gedit all the time for multiple files and have never seen it open a second window. I use it as my usual editor but with this one problem. Could it be somethig to do with setting up?

ps
other people:
I'd rather solve the problem I want to solve, I already use diff but it is no good for this.

---

### Post by Kevbert on 2009-06-10
Once you have two files in gedit, that is two tabs, right-click on the second tab and select 'move to new window'.

---

### Post by F W Adams on 2009-06-10
Thanks Kevbert, that's been bugging me for ages, I knew it surely must be possible.

---

### Post by Celauran on 2009-06-10
So this leaves you with two instances of gedit running, each of which you can resize? Is that the idea? Or did I miss something and you can actually resize tabs within one instance of gedit?

---

### Post by llamabr on 2009-06-10
I don't use gedit, and I'm sure it can do this.

This would also be a perfect job for screen, which would split the screen in a terminal, allowing you to open two instances of nano.

I'd probably use diff for this, tho.

---

### Post by sonicb00m on 2009-06-11
Comparing files side by side in gedit is not a proper solution, in my opinion.

A tool like Diffuse is exteremely powerful in that it highlights the changes and adds white space in your views so you pretty much are always looking at the identical code parts in syncronisation. Saves a lot of scrolling between two different files.

---

### Post by techie2go on 2009-06-11
try meld

---

### Post by nandemonai on 2009-06-11
If you really want to use gedit then just drag one of the tabs out and it will act as a separate instance of the program.

That said there are better alternatives mentioned in this thread.

---

