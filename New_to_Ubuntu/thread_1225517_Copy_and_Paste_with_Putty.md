---
title: "Copy and Paste with Putty"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by lexluth0r on 2009-07-28
I am on a WinXP using Putty and connecting to my Ubuntu via SSH, what command would I use if say I want to copy the directory C:\Example to Linux Desktop
 
Thanks
 
Lex (Linux Newbie)

---

### Post by nhasian on 2009-07-28
it sure would be a lot easier to do with filezilla.  you could connect to your ubuntu pc via sftp.  or i guess you could do it by hand with the put command.

---

### Post by ericab on 2009-07-28
> **lexluth0r said:**
> I am on a WinXP using Putty and connecting to my Ubuntu via SSH, what command would I use if say I want to copy the directory C:\Example to Linux Desktop
 
Thanks
 
Lex (Linux Newbie)

there is a modified PuTTY available which i've been using for years.
it has a bunch of options the default putty should have...

its called 'KiTTY' avaliabe here: [http://kitty.9bis.com/](http://kitty.9bis.com/)

anyway, one of the features is drag and drop from XP to the putty window.

just 'cd' into the directory you want the files copied, and drag and drop :)

forget ftp

---

### Post by bodhi.zazen on 2009-07-28
You can copy and paste with putty with great ease.

to copy to putty 

Select text -> copy text -> move mouse to putty terminal -> hit right mouse button.

to copy from putty -> Highlight text with mouse. Highlighted text is automatically copied to clip board. Paste it where you will.

---

### Post by ericab on 2009-07-28
you havent read his post correctly.

he wants to copy files.

"I want to copy the directory C:\Example to Linux Desktop"

---

### Post by bodhi.zazen on 2009-07-28
Ah, I did too :redface: to copy files use winscp

winscp uses ssh and putty keys.

[http://winscp.net/eng/docs/introduction](http://winscp.net/eng/docs/introduction)

[IMG]http://winscp.net/eng/docs/ui_commander[/IMG][IMG]http://winscp.net/eng/docs/ui_commander[/IMG][IMG]http://winscp.net/eng/data/media/screenshots/commander.png[/IMG]

[http://winscp.net/eng/docs/screenshots](http://winscp.net/eng/docs/screenshots)

---

### Post by lexluth0r on 2009-07-28
Thanks for all the quick replies, I have installed winscp and works fine, so easy to use in fact!!!!

Cheers


Lex

---

### Post by llamabr on 2009-07-28
There's winscp, and other ftp programs for windows, like cuteftp.  Putty also has an ftp program of their own:

```
http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html
```

---

