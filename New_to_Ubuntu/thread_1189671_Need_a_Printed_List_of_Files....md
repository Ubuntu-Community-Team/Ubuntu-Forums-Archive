---
title: "Need a Printed List of Files..."
date: 2009-06-17
forum: New to Ubuntu
---

### Post by Mattaus on 2009-06-17
Hi all,

Quick question here. I have a folder that contains a lot of movies in it. I would like to obtain a printed list of these files so I can cross check them against another checklist I have.

Basically I want to just spit the list out to a text file so I can email it to myself at work.

What would the best way to go about doing that be?

Could I grep the output of an ls command and redirect it to another file or something?

Any help would be appreciated.

Cheers.

EDIT: Sorry, opened my mouth before using my head.

I guess this would work fine:
> 
ls -1 | sort > temp.txt

- Matt.

---

### Post by Mark Phelps on 2009-06-17
There may be ways to do that with various file managers, but using the "ls" command as you have indicated is certainly the way I would do it.

---

### Post by raptor2552 on 2009-06-17
or you could send the output to the printer:

> ls -1 | sort  |lpr

---

### Post by achase79 on 2009-06-17
you can set the output of ls to a text file
```
ls > sample.txt
```

---

### Post by Polaris96 on 2009-06-17
ls > movielist.txt

You can open the textfile with any app from a terminal text editor (nano or vim) to a word processor.  it will save to whatever directory you're in when you type the command.  I would print it from openoffice, so you can snazz it up if you feel like it.

---

### Post by Mattaus on 2009-06-17
I'm just really using it as a check list so I can tell what XBMC has and has not picked up on. From what I can tell so far it has not found much :-(

---

