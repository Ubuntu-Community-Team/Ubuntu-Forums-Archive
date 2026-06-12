---
title: "Terminal question"
date: 2009-12-01
forum: New to Ubuntu
---

### Post by holadebob on 2009-12-01
Hello,
I've never been happier since switching from XP as with Jaunty, but I am still learning and have probably the proverbial stupid question, but I think I may have done something wrong when I set Jaunty up.
On the Terminal, my prompt is: maryybob@maryybob-desktop:~$ 
Now the maryybob part I understand, but the "desktop" part I don't. Initially I thought that meant that I was in the desktop subdirectory.
When I tried to use md5sum yesterday, it said to start the md5sum in the directory of the .iso file. Well, the iso file was in my Desktop dir, and it appeared as if by the prompt that I was already in the Desktop directory. But I wasn't, I found out by trial and error that I was in the maryybob directory, even though it appeared in the prompt as if I was in the Desktop directory and that the Desktop is a subdirectory of maryybob. Why is the word Desktop in the prompt or did I put it there when I installed Jaunty? Can I correct it? 
Or maybe there is no problem and I am just confused.
Thank you for reading all this,
Bob

---

### Post by NoaHall on 2009-12-01
It's the name of your computer and the user logged in on your computer :)

---

### Post by corncob on 2009-12-01
> **holadebob said:**
> Hello,
I've never been happier since switching from XP as with Jaunty, but I am still learning and have probably the proverbial stupid question, but I think I may have done something wrong when I set Jaunty up.
On the Terminal, my prompt is: maryybob@maryybob-desktop:~$ 
Now the maryybob part I understand, but the "desktop" part I don't. Initially I thought that meant that I was in the desktop subdirectory.
When I tried to use md5sum yesterday, it said to start the md5sum in the directory of the .iso file. Well, the iso file was in my Desktop dir, and it appeared as if by the prompt that I was already in the Desktop directory. But I wasn't, I found out by trial and error that I was in the maryybob directory, even though it appeared in the prompt as if I was in the Desktop directory and that the Desktop is a subdirectory of maryybob. Why is the word Desktop in the prompt or did I put it there when I installed Jaunty? Can I correct it? 
Or maybe there is no problem and I am just confused.
Thank you for reading all this,
Bob

"marybob-desktop" is the name of your computer that you gave it when you installed Ubuntu.  It might have defaulted to that using your username marybob.  ~ is the symbol for your home folder "marybob".  $ is the prompt.  If you want to go to your desktop subfolder type:
```
cd Desktop
```
in the terminal.  Its case sensitive.
If you get lost and want to know what folder you're in type
```
PWD
```
(Print Working Directory).
Somebody that can type faster than me has probably answered your question already but hopefully I helped too.

---

### Post by holadebob on 2009-12-01
a ha! So it was my error when I installed Jaunty...can I edit that entry somehow and just put maryybob and eliminate the desktop part of it?

---

### Post by rudy.b on 2009-12-01
Yes, but you gotta change it in two places:
```

$ sudo nano /etc/hosts
$ sudo nano /etc/hostname

```
You may have to log out/in for the change to take effect.

---

### Post by corncob on 2009-12-02
> **holadebob said:**
> a ha! So it was my error when I installed Jaunty...can I edit that entry somehow and just put maryybob and eliminate the desktop part of it?

Good info from Rudy.B!  Some people prefer to use a graphical interface though, in which case you'd want to type
```
gksudo gedit /etc/hosts
gksudo gedit /etc/hostname
```
One more thought for what its worth as I haven't tried it lately -- sometime, somewhere, on some operating system it wouldn't allow me to have a computer name and a username that were identical.

---

