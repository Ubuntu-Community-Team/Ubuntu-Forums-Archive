---
title: "How to make Luxor Amun Rising as an executable file"
date: 2011-03-20
forum: New to Ubuntu
---

### Post by sashag on 2011-03-20
Hi!

I keep trying to download Luxor Amun Rising, but keep getting the same 'error' message over and over again. After looking online for help, I've discovered that I needed to make the game file 'executable' in the Ubuntu Linux OS.

Right now, I have the game showing up
on my desktop, and I need 'exact' wording in the terminal window on what to put down to see if the game will run. I've also read that I need to install the game onto the computer first, but don't know how to do that either. Please help! Thanks!

---

### Post by Clever_Username on 2011-03-20
Assuming your username owns the file,
```
chmod +x filename
```

---

### Post by sashag on 2011-03-22
Hi!

Thanks for the reply. However, since I'm totally new to Ubuntu Linux, I don't know what your reply means. When I put in my Luxor Amun Rising CD, I saw it appear on the desktop. When I clicked on the .exe file, I got the following 'error' message.

The file '/media/Luxor-AR_Bundle/Luxor_AR_Setup.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

How do I 'fix' this problem in order to make
the Luxor Amun Rising game run? I have already installed the 'Wine 1.2' program. Is the Wine program enough? I'm getting so frustrated with the Ubuntu Linux program right now, I'm seriously thinking of uninstalling it permanently. As much as I like some of the games that came with Ubuntu Linux, I still can't play the Luxor game, nor can I find out how to make it run. Hope you can help me out again. If you can, please let me know what else I need to do to make the Luxor game run if it can't run on the Wine program what other program do I need, and if so, how to make the Luxor game work with the other program. Thanks!

---

### Post by gandaran on 2011-03-22
> **sashag said:**
> Hi!

Thanks for the reply. However, since I'm totally new to Ubuntu Linux, I don't know what your reply means. When I put in my Luxor Amun Rising CD, I saw it appear on the desktop. When I clicked on the .exe file, I got the following 'error' message.

The file '/media/Luxor-AR_Bundle/Luxor_AR_Setup.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

How do I 'fix' this problem in order to make
the Luxor Amun Rising game run? I have already installed the 'Wine 1.2' program. Is the Wine program enough? I'm getting so frustrated with the Ubuntu Linux program right now, I'm seriously thinking of uninstalling it permanently. As much as I like some of the games that came with Ubuntu Linux, I still can't play the Luxor game, nor can I find out how to make it run. Hope you can help me out again. If you can, please let me know what else I need to do to make the Luxor game run if it can't run on the Wine program what other program do I need, and if so, how to make the Luxor game work with the other program. Thanks!
you wont be able to install from the cd, there is no way to mark it executable on the cd so copy the game to desktop then right click the .exe file go to properties » permissions tab and mark the little box allow executing file, now a double click on the .exe installs the game with wine.
also you should check if the Luxor Amun Rising game will work in wine, very few windows games actually work.

---

### Post by sashag on 2011-03-24
Hi!

Thanks for the help. This is the message that I got when I double clicked on the .exe
file for the game after I did all that you mentioned:

Archive:  /home/sasha/Desktop/Luxor/Luxor_AR_Setup.exe
[/home/sasha/Desktop/Luxor/Luxor_AR_Setup.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /home/sasha/Desktop/Luxor/Luxor_AR_Setup.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /home/sasha/Desktop/Luxor/Luxor_AR_Setup.exe or
          /home/sasha/Desktop/Luxor/Luxor_AR_Setup.exe.zip, and cannot find /home/sasha/Desktop/Luxor/Luxor_AR_Setup.exe.ZIP, period.

I don't know what all of the above mean, but I'm guessing that the Luxor Amun Rising
game still won't run, even though I do have Wine 1.2 already installed on the computer. Unless you can suggest something else, I guess I will just have to give up on the game. I even tried making the game run using Crossover Games program, and I did get as far as seeing the startup screen in Luxor Amun Rising, but when I tried to play the game, it went into 'super-slomo', and took forever to go from one screen to the next, so the game was impossible to play. Anyway, thanks for all of your help so far!

---

