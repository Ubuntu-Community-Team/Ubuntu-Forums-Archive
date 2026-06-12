---
title: "I tried to add extra repositories as decribed  from another site and now have errors"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by arce on 2009-03-22
I currently have ubuntu 8.10 on my laptop. I'm 3 days into using this OS. I wanted to see my other selections for projects that I could install. 

I followed this sites tutorial

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Now I get an error when I try to open Synaptic package manager or add/remove. I try to close the error window(habit from windows) but as soon as I close both errors in them the whole application closes. 

Heres my Synaptic package manager error

E:malformed line in 54 in source list/etc/apt/sources.list(absolute dist)
E:the list of sources can not be read.
go to the repository dialog to correct the problem
E:_cache->open()failed,please report

Add/Remove Applications Error

This is a major failure of your software management system.
please check broken packages with synaptic. check the file permissions and correctness of the file'/etc/apt/sources.list'
and reload the software information with:'sudo apt-get update'
and sudo apt-get install-f'

---

### Post by James_Lochhead on 2009-03-22
Run the software sources line part in reverse, removing all the lines you have added. There is obviously something wrong with them.

---

### Post by ByteJuggler on 2009-03-22
OK, as per the message, you've broken your sources.list file somehow.  So, open the file in a text editor and review what's up on line 54.  Something must be broken on that line.  You may want to post the few lines surrounding line 54 for us to review.  

To be precise, press alt-f2, then enter or copy:

```
gksudo gedit /etc/apt/sources.list
```

In the editor, click "Edit"->"Preferences" and tick "Display Line Numbers" to help you find the offending line.

---

### Post by James_Lochhead on 2009-03-22
The default repositories are very large and have lots of stuff in. I suggest you just stick to those unless you are after something specific.

---

### Post by drs305 on 2009-03-22
Another trick to get to the malformed line (54):
```
gksudo gedit +54 /etc/apt/sources.list
```
Gedit will open with the cursor on line 54.

---

### Post by arce on 2009-03-22
Thanks everyone... 

I'm Very new but your solutions took care of it. 

Talk about support!

Thanks

---

### Post by hyper_ch on 2009-03-23
you can use the tool in my signature to add new repos. I have not everypossible repo added yet but there are a few.

---

### Post by earthpigg on 2009-03-23
> **hyper_ch said:**
> you can use the tool in my signature to add new repos. I have not everypossible repo added yet but there are a few.

i use that exact tool on every fresh install :P

---

