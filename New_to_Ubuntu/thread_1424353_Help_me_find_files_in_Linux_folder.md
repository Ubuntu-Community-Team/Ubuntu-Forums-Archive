---
title: "Help me find files in Linux folder"
date: 2010-03-07
forum: New to Ubuntu
---

### Post by gcmartin on 2010-03-07
I apologize for appealing for something that is so easy for most of you, but it has been eluding me for weeks in my use of Linux

How do I find a file in a folder when I know a single set of characters (like  the word "anything", that can occur anywhere in the filename?

It is eluding me how to use any Linux command to do this? I have found example for the end of a filename....or the beginning of a filename...BUT NOTHING FOR A SET OF CONSECUTIVE CHARACTERS THAT EXIST IN THE FILENAME OF FILES IN THE FOLDER. (I've been a Microsoft user and this is so easy and apparent..."forgive me for that last comment, but I think you understand the frustration I feel")

Thanks in advance...

---

### Post by patchwork on 2010-03-07
grep -ilr "string" "folder"

---

### Post by egalvan on 2010-03-07
When you open Nautilus to view the folder (directory),
you can use 'ctrl-f' to open the "search' bar,
which will use the current directory...

or use the menus

Go -> Search for Files

---

### Post by gcmartin on 2010-03-07
@patchwork

I tried your offer, but it does work.

Let me give an example and would you be more precise.

Let's say I have a list of files as follows
userid: /mnt/test/documents# ls 
W9.pdf
WebSites I Like
WebSites to visit
What is Active Desktop.rtf
What is MySpace and Facebook.rtf
What is On-Demand-Computing.rtf
Why go to SATA.rtf
WiKi
Win2K
WinProxy Software vs SOHO Hardware.rtf
Wolfenden
wolfenden router setup.rtf
wolfenden router setup.txt
Wonders of the World.rtf
X10 is a Video camera broadcasting on Channel3 or 4.rtf
XCOPY  command setup.rtf
Yahoo
yahoo.rtf

and I want to list all files which have the word "is" in its filename, how would you do that?

---

### Post by gcmartin on 2010-03-07
@egalvan

I'm not seeing how it finds the files with the work "is" and gives me a list

Anyone's help here is allowed...Thakns

---

### Post by patchwork on 2010-03-07
I suppose I gave you a bum line....I can't get it working myself without using the --include option, and even then may not be ideal.

EDIT----None of this was right------

---

### Post by William Shotts on 2010-03-07
What about:

[FONT=Courier New]ls *folder*/**string**[/FONT]

where *folder* is the name of the folder you want to search and *string* is the text you are trying to match.

---

### Post by mechro on 2010-03-07
> **gcmartin said:**
> @egalvan

I'm not seeing how it finds the files with the work "is" and gives me a list

Anyone's help here is allowed...Thakns

Type "is" in the Search bar. Does that not work?

---

### Post by patchwork on 2010-03-07
OK, here's what I have

Contents of "/home/kevin/test/File Contains string" is the search string


```
kevin@crystalpepsi:~/test$ ls
File Contains string  What is Active Desktop.rtf
W9.pdf                What is Myspace and Facebook.rtf
WebSites              Wiki
WebSites I Like       Yahoo
WebSites to Visit
kevin@crystalpepsi:~/test$ **grep -ilr is ~/test && find *is***
/home/kevin/test/File Contains string
WebSites to Visit
What is Active Desktop.rtf
What is Myspace and Facebook.rtf

```Again, sorry for the confusion, I'm not the sharpest tool in the shed.


EDIT:  All this time and I have been completely missing your point:
> CONSECUTIVE CHARACTERS THAT EXIST IN THE FILENAME OF FILES IN THE FOLDER.

If you only need to search in the filename, the find command by itself is sufficient:

```
find *string*
```

I think it's going to be a rough day...

---

### Post by gcmartin on 2010-03-07
I'm not getting any results. I typed 
[COLOR="Black"]**grep -ilr is /mnt/test/documents && find *is***[/COLOR]

I am not getting anything except the prompt

did I mistype something? (and was linux design purposely to NOT allow search from the command line for a filename that contains some specific characters?

---

### Post by patchwork on 2010-03-07
> and was linux design purposely to NOT allow search from the command line for a filename that contains some specific characters?I can't believe that is the case...I just haven't been able to put my finger on it.

All you need is a search within filenames, and not the content, right?   Try:

```
find -L  /mnt/test/documents/*is*
```EDIT: path goes before search string.

---

### Post by William Shotts on 2010-03-07
> **gcmartin said:**
> I'm not getting any results. I typed 
[COLOR=Black]**grep -ilr is /mnt/test/documents && find *is***[/COLOR]

I am not getting anything except the prompt

did I mistype something? (and was linux design purposely to NOT allow search from the command line for a filename that contains some specific characters?

Do either:

[FONT=Courier New]ls *folder*/**string**[/FONT]

or:

[FONT=Courier New]find *folder* -type f -name "**string**"[/FONT]

[FONT=Courier New]find[/FONT] will search recursively.

---

### Post by gcmartin on 2010-03-08
I will generate a report on this threads topic, soon.

My initial tests of offers on this thread is 
[LIST=1]
[*]**cd** to folder I want to search
[*]to issue a **find** *search0word*
[/LIST]
***I was not able to find any example or document which shows this as a form of the _[I][B]find***_ command[/B][/I], BUT THIS DOES WORK!...T**[COLOR="SeaGreen"]hanks goes to @patchwork [/COLOR]**!!!

In my upcoming (final) post on this thread, I will report others offerings (some of which were untested or inaccurately reported/applied), as well.

---

### Post by boxcorner on 2010-03-08
Join Date: Aug 2005
> **gcmartin said:**
> ...it has been eluding me for weeks in my use of Linux ... I've been a Microsoft user ...

Not much hope for the rest of us then.

---

### Post by patchwork on 2010-03-08
> *** was not able to find any example or document which shows this as a form of the _[I][B]find***_ command[/B][/I], BUT THIS DOES WORK!.

```
man find
```

---

