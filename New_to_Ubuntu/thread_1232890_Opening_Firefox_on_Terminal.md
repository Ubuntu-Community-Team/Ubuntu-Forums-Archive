---
title: "Opening Firefox on Terminal"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by r3cht3r on 2009-08-06
I open up firefox on a terminal and while I was surfing the internet once in awhile I try to look up at the terminal and then I saw this: ```
:~$ firefox
[SmartNamer] updateEntry()
[FDLProc] canHandle()
[FDLProc] canHandle()
[FDLProc] requireDownload()
[FDLProc] handle()
[SmartNamer] updateEntry()
!!! [SmartNamer] updateEntry(): TypeError: /^https?:\/\/([^\/]+)/.exec(pageUrl) is null
[FDLProc] canHandle()
[SmartNamer] updateEntry()
!!! [SmartNamer] updateEntry(): TypeError: /^https?:\/\/([^\/]+)/.exec(pageUrl) is null
[FDLProc] canHandle()
[SmartNamer] updateEntry()
!!! [SmartNamer] updateEntry(): TypeError: /^https?:\/\/([^\/]+)/.exec(pageUrl) is null
[FDLProc] canHandle()
[SmartNamer] updateEntry()
!!! [SmartNamer] updateEntry(): TypeError: /^https?:\/\/([^\/]+)/.exec(pageUrl) is null
[FDLProc] canHandle()
[SmartNamer] updateEntry()
[FDLProc] canHandle()
[FDLProc] canHandle()
[FDLProc] canHandle()
[SmartNamer] updateEntry()
[FDLProc] canHandle()
[SmartNamer] updateEntry()
[FDLProc] canHandle()
[FDLProc] canHandle()
[FDLProc] canHandle()
[FDLProc] canHandle()
``` Can somebody please tell me what this means? Or, maybe the thought of it. It doesn't look too good to me, although I don't want to think there is something bad going on but I guess being a little paranoid is good. Thanks.

---

### Post by rudihawk on 2009-08-08
I think its just some messages that FF is returning while its running - nothing to be worried about I don't think.

---

### Post by Liolikas on 2009-08-08
Yes just some info. If FF runs fine it is not important if FF do not work you (or at least FF developers) can find in those lines what is wrong.

---

### Post by Sidewinder1 on 2009-08-08
You probably already know this but, as a side note, if you decide to open FF in terminal with root privileges, make *sure *that you use gksudo and **not** sudo as that will screw up your FF permissions, make "root" the owner of your bookmarks or some such... I've seen several posts lately of folks who have used sudo and regretted it...
Side

---

### Post by Liolikas on 2009-08-08
> 
if you decide to open FF in terminal with root privileges

It is IT security suicide in windows style.

---

### Post by Sidewinder1 on 2009-08-08
In "windows style", unless you've set up specific and separate user permissions, *everything* is opened with root privileges, lovely operating system that it is...

---

