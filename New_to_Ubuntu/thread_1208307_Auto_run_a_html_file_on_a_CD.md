---
title: "Auto run a html file on a CD"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by avanrens on 2009-07-09
I have a HTML file on a CD which I would like to run as the CD is inserted similar to the go.bat and Autorun.inf in Windows.

---

### Post by nhasian on 2009-07-09
create a file called autorun.inf and place it in your root cdrom folder.  in the file put:

```
[autorun] 
open=firefox linktohtmlfile 
icon=Filename.ico 

```

---

### Post by avanrens on 2009-07-16
Thanks for your reply what I meant was an auto run a.html file from Ubuntu. I no how to get it to run in Windows, but I want the CD to auto run in both Ubuntu and Windows its a demo CD.

---

### Post by Mark Phelps on 2009-07-16
> **avanrens said:**
> Thanks for your reply what I meant was an auto run a.html file from Ubuntu. I no how to get it to run in Windows, but I want the CD to auto run in both Ubuntu and Windows its a demo CD.

If what you asking is to autorun a .bat file, you can't do that because Linux doesn't use .bat files.  To get a similar function, you'd have to write a Bash script and have Linux run that.

---

