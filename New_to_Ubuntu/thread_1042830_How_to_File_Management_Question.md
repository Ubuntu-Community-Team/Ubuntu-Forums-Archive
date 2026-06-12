---
title: "How to: File Management Question"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by LeakyInkPen on 2009-01-17
First of all, thanks to everybody here that contributes.  I rid my system of the M$ virus as my new years resolution (after toying around with a dual boot system for a few years) and that was only made possible by the community here... And lots of coffee.

I think I finally have an issue that I can't locate a solution to by searching.  So if it is solved already, I am sorry but I did try.

I am running Kubuntu 8.10 with 3 separate hard drives, 2 "clean" ones that have only been used for linux, and the third one that I have all my files from XP on.  When I say all, I mean all.  It is formatted as ext3, but I basically cut and pasted the file directory from XP onto it.  Now the Wife's photos/music is kind of moved all over the drive.  So now I am looking for a way to automagically move all photos and whatnot to a new location.  I am hoping that I can just rip all the files with the extensions I want to keep into a new folder so I can the feel relatively safe in deleting the rest of them to free up a bunch of room on that drive.

Again, thanks to everybody as everything is working amazingly.

---

### Post by neerajvm on 2009-01-18
I'm no expert and I'm sure there is a neater/compact way of doing this through the command line, but you can search for files of a specific type by going to places >> search and then using wildcards(.jpg .jpeg .mp3 etc). Then you can just copy paste the required files. Only drawback is it might take a while for searching through the whole disk/partition depending on its size.

---

### Post by LeakyInkPen on 2009-01-18
AAAAAAAAAAGGGGGGGGGHHHHHHHH!  Holy crap, can't believe I didn't think about that.  I am doing it right now, thanks to you.  I would like to keep this thread open as I would like to know what the more elegent(read: terminal) method would be.  Thanks again for the quick reply!

---

### Post by neerajvm on 2009-01-18
This is interesting. You can use the find command from the terminal. Have a look at the man page or try googling. In your particular case, say you want to search and then copy all jpeg files from a folder into another folder, say your home folder.


```
find /media/disk -name '*.jpg' -exec cp '{}' /home/ \;

```

-name option searches for files with a particular name as mentioned inside the quotes
-exec option executes the command immediately following it(here copy)
the {} means use the files obtained from find

Have a look at this [HTML]http://www.codecoffee.com/tipsforlinux/articles/21.html[/HTML]

---

