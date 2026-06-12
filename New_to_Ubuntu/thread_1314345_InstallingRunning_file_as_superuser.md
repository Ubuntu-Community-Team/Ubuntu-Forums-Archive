---
title: "Installing/Running file as superuser"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by UntidyUser on 2009-11-04
Hi,

I'm currently trying to install Mathematica and have downloaded the ISO file. It was not a problem to mount it, however I'm unable to run the shell script (I assume it's an .exe file). 

If I try to open it, using the file browser, it opens in a terminal where I am unable to do anything as I get the continuous message: "You may need to login as root to continue with this installation." 

However if I write su I get told Error: Cannot create directory su.

I don't know how to log in as root and then ask the file to run in a terminal. Various combinations of sudo, su and open filename are not working - what am I missing?

(Googling has turned up little - which is why I hope someone will help out a newb - looks to me like I'm missing something extremely simple!)

---

### Post by celtic426 on 2009-11-04
> **UntidyUser said:**
> Hi,

I'm currently trying to install Mathematica and have downloaded the ISO file. It was not a problem to mount it, however I'm unable to run the shell script (I assume it's an .exe file). 

If I try to open it, using the file browser, it opens in a terminal where I am unable to do anything as I get the continuous message: "You may need to login as root to continue with this installation." 

However if I write su I get told Error: Cannot create directory su.

I don't know how to log in as root and then ask the file to run in a terminal. Various combinations of sudo, su and open filename are not working - what am I missing?

(Googling has turned up little - which is why I hope someone will help out a newb - looks to me like I'm missing something extremely simple!)

Not sure I completely understand, but putting "sudo" before any command will do the job.  Also, you can open up a terminal and type "sudo nautilus", which will open a file browser in super-user mode.  Maybe opening the program that way will work.

---

### Post by stderr on 2009-11-04
You'll want to open a terminal, navigate to the correct directory (cd path/to/my/directory) and use sudo to run the script. 

```
sudo ./myscript
```

or

```
sudo path/to/myscript 
```

Notice the extra "./" when you're in the same directory as the script.

If it hasn't got executable permissions, you'll need to set them first:

```
chmod +x myscript
```

If the script is an .exe, that's a Windows file (not compatible with Linux). You will have to see if it can work under Wine or not (see the [appdb]("http://appdb.winehq.org/")).

edit: If you're getting confused with su, sudo, gksudo etc, read [this]("http://209.85.229.132/search?q=cache:avJKczQuT34J:https://wiki.ubuntu.com/RootSudo+ubuntu+gksudo&cd=6&hl=en&ct=clnk&gl=uk&client=firefox-a") (link is to ubuntu website from Google cache, as for some reason the live copy is blank)

---

### Post by sisco311 on 2009-11-04
type: 
```
sudo sh
```
in a terminal, type a space and drag the installer in the terminal window, press Enter, type your password and press Enter.


[https://help.ubuntu.com/community/Mathematica]("https://help.ubuntu.com/community/Mathematica")

---

### Post by LunaticHiatus on 2009-11-04
your post is kinda confusing.
.iso files are something you burn onto cd as an image then run.
Your also looking for a .deb file or a .tar
If its a .tar file you will have to install it from source. which can be kinda annoying but easy to find guides for. I would provide a link of how to install from source but someone else probably has a better one then I do.

---

### Post by UntidyUser on 2009-11-05
Typing "sudo nautilus" and working from there turned out to be what was needed :) (It was a different approach :) but one that worked!)

Thank you very much!

---

