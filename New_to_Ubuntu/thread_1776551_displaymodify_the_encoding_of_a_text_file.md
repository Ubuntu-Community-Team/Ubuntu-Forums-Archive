---
title: "display/modify the encoding of a text file"
date: 2011-06-06
forum: New to Ubuntu
---

### Post by mkornig on 2011-06-06
Hi there,

I know how to display and modify the encoding of a text file with KWrite. For instance modify from "iso-8859-15" to "utf-8". Here are two questions:

[LIST=1]
[*]Can gedit modify the encoding as well? How?
[*]Can I display/modify the encoding without a text editor? Is there a simple way? Maybe some Linux command?
[/LIST]

---

### Post by wolfen69 on 2011-06-06
[http://ubuntuforums.org/showpost.php?p=1199976&postcount=4](http://ubuntuforums.org/showpost.php?p=1199976&postcount=4)

---

### Post by mkornig on 2011-06-06
> **wolfen69 said:**
> [http://ubuntuforums.org/showpost.php?p=1199976&postcount=4](http://ubuntuforums.org/showpost.php?p=1199976&postcount=4)

Thanks wolfen,

I can't find the "Add button" which I'm supposed to click on. The thread you mention is from 2006: Ubuntu may have changed since then?

---

### Post by wolfen69 on 2011-06-06
I have the add button, but it is greyed out. I need to investigate this. Will post back if I find anything.

---

### Post by mkornig on 2011-06-06
Found the following work around solution:

[LIST]
[*]I open the text file with KWrite first. I check the encoding. If necessary I set the encoding I want, i.e. utf-8. Then I leave KWrite.
[*]Later on I use gedit to edit the file as usual. The application accepts utf-8 and doesn't change it.
[/LIST]

---

### Post by dargaud on 2011-06-06
Something very powerful (make copies of your files first):
> $ man convmv
convmv - converts filenames from one encoding to another

---

### Post by mkornig on 2011-06-07
> **dargaud said:**
> Something very powerful (make copies of your files first):

Thanks dargaud.

In a terminal I get the reply: *No manual entry for convmv*

And for a blank```
 convmv
``` this is confirmed:* convmv not installed*. 

I had it installed and studied the man pages: this command is specifically for filenames. I'm looking for a similar tool converting file content (my filenames are okay since only use ascii for filenames).

---

### Post by mkornig on 2011-06-07
Since I won't use the command* convmv* do you think I should uninstall it?

---

### Post by mkornig on 2011-06-07
I think I've found an interesting command:* iconv*. It converts file content from one encoding to another.

How do I find out what encoding a file is in in the first place?

---

### Post by dargaud on 2011-06-07
Yes, sorry I read too fast, the command you are looking for is iconv. To find out the correct encoding... you have to try. Easiest is to open it in an editor that has selective encoding (like kate), or to try:
```
$ iconv -f UTF-8 file
$ iconv -f WINDOWS-1250 file
$ ...
```
Until everything seems fine (no double or weird chars). If you know the origin of your files, there aren't that many possibilities, don't get scared by 'iconv -l' ! To find out the encoding of your console (used as default output by iconv):
```
$ echo $LANG
en_US.UTF-8

```

---

### Post by mkornig on 2011-06-08
Cool, I didn't know about the parameter $LANG.

---

