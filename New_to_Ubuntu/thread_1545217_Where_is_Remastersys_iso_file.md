---
title: "Where is Remastersys iso file??"
date: 2010-08-03
forum: New to Ubuntu
---

### Post by Inisfad on 2010-08-03
OK, a really stupid question.  I have downloaded Remastersys to make a dist copy for myself ( would like to do whole backup, but too many videos, etc, for the DVD).  Remastersys runs, all seems ok.  It advises that the iso is in /home/remastersys.  I look in my home folder, but see nothing (wrong place??)  So, stupid question, where do I find the iso file Remastersys created?  Thanks.  Eck, never mind.  Seek and ye shall find.  Although I STILL cannot find a 'remastersys' folder in my home folder, I did a search for 'custom.iso' and was able to find it that way.

---

### Post by cosine352 on 2010-08-03
> **Inisfad said:**
> OK, a really stupid question.  I have downloaded Remastersys to make a dist copy for myself ( would like to do whole backup, but too many videos, etc, for the DVD).  Remastersys runs, all seems ok.  It advises that the iso is in /home/remastersys.  I look in my home folder, but see nothing (wrong place??)  So, stupid question, where do I find the iso file Remastersys created?  Thanks.

At 
> /home

---

### Post by ankspo71 on 2010-08-03
> **Inisfad said:**
>  Although I STILL cannot find a 'remastersys' folder in my home folder, I did a search for 'custom.iso' and was able to find it that way.

Hi,
The custom.iso was never in your home folder (/home/inisfad). The custom.iso was located in remastersys's own personal home folder (/home/remastersys). To get to that folder, you have to go to your home folder, then go up one directory so you are in /home and can see two folders - inisfad and remastersys. You can see the remastersys folder if you use the command:
```
ls /home
```
which will list the contents of the home directory.
I hope this explains it well :D

---

### Post by philinux on 2010-08-03
Don't forget there is an ISO file size limit of 4gig.

---

### Post by Inisfad on 2010-08-04
Thanks!!  Although I was able to find it in a kind of backwards way, I appreciate the proper instructions.  I got my remastersys DVD done, checked it, all working now, so all ok. Just one more (newbie) question......How do you all know this stuff?  Is there one place that shows/teaches the terminal codes for the various things you want to do, or do newbies (like myself) just continually nag all you experienced users for each code that is needed?  (In other words, should I start taking notes of all these instructions????)  Thanks!!

---

### Post by ankspo71 on 2010-08-04
> **Inisfad said:**
> Thanks!!  Although I was able to find it in a kind of backwards way, I appreciate the proper instructions.  I got my remastersys DVD done, checked it, all working now, so all ok. Just one more (newbie) question......How do you all know this stuff?  Is there one place that shows/teaches the terminal codes for the various things you want to do, or do newbies (like myself) just continually nag all you experienced users for each code that is needed?  (In other words, should I start taking notes of all these instructions????)  Thanks!!

Hi,
Taking notes is exactly what I do. If I see an interesting command, and if it works when I try it out, I will copy the command to the single text file where I keep all of my copied commands and include a brief explanation for each of them. That file eventually gets bigger and bigger and better and better.

My advice to anybody is to start out small by looking for basic commands to do everyday/useful things in the terminal, stick with that for a while, then move onto the next basic everyday/useful thing to do in the terminal.

I started out looking for commands for file management, and navigating my way around the system. Then I went into searching for ways to edit text files. Then I went into package management. 
Then I went into learning searching for files.

Whenever anyone needs help with a specific command, there is help for those commands located right inside ubuntu via the terminal.

man the-command-i-need-help-with
info the-command-i-need-help-with
the-command-i-need-help-with --help

Google is a powerful tool to find commands too. Some keywords might be:
copy command ubuntu
copy command linux
and so on.

Here are some commands I found very useful to begin with:
cp, mv, rename, rm (file management)
mkdir, rmdir (folder management)
ls (list contents of a directory)
find, locate (to search for files)
cat, nano, touch (to edit or view text files)
dpkg, apt-get, apt-cache (package management)

Some fun ones include,
w3m, wget, rtorrent, :-)

---

### Post by Inisfad on 2010-08-04
Wow.  Thanks for the really great response.  I have begun my new text file with your answer.  Thanks very much for all.

---

