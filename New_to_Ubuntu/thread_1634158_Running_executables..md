---
title: "Running executables."
date: 2010-11-30
forum: New to Ubuntu
---

### Post by bertv on 2010-11-30
Hi all, my name is Bert and I am running Meerkat on an HP Pavillion, 1.0 GB, 2,8 GHz. I am truely a beginner on a Linux machine, so I may have a ton of questions. What is buggung me now is that, evrytime a want to run an exe.file and I give the 'open' command, I get this message:

 End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/bert/Downloads/wlsetup-web.exe or
          /home/bert/Downloads/wlsetup-web.exe.zip, and cannot find /home/bert/Downloads/wlsetup-web.exe.ZIP, period.

and, of course, the process aborts.

I have already set all permissions to the max and it still comes back with the same result. 

AAAAAAAAAAAAAAAAARRRRRRRRRRRRRGGGGGGGGGGGGGGGHHHHHHHHHHHHHHHH, :D

What can I do?

Thanx,
Bert.

---

### Post by Joker1134 on 2010-11-30
well Bert
im not sure why your getting that error but i do know that you can run .exe files on a linux machine anyways. .exe are windows only files. if its a windows program your tying to install try using wine HQ to install it on linux

---

### Post by surfer on 2010-11-30
you have to install wine if you want to run windows executables on linux. there is no guarantee that the program works though!

try this:
```
sudo apt-get install wine
```
and after that completes:
```
wine wlsetup-web.exe
```

---

### Post by ronnielsen1 on 2010-11-30
It looks like you could probably run windows live messenger in wine but it's a lot better running native linux applications. Try Pidgin. Applications > Internet > Pidgin Internet Messenger

---

### Post by Mark Phelps on 2010-11-30
If you're going to use Wine, you first need to check the WineHQ site for the compatibility rating of the app you want to run.

The site link below is for Windows Live Messenger:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=127]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=127")

As you can see, it's rated Garbage -- meaning, it's NOT going to work, no matter what you do.

---

### Post by ronnielsen1 on 2010-11-30
> As you can see, it's rated Garbage -- meaning, it's NOT going to work, no matter what you do. 	

The newest version, true. Some of the older versions give a little bit better rating. But I still recommend pidgin

---

### Post by bertv on 2010-12-19
To all you guys who have replied. Many thanks, I have installed wine and I found out that you have to set a flag in the file properties so that it will see the .exe as an actual program to run. 

Slowly, 1 step at a time, I a getting better and better at this, :p.

Greetz from a very cold Holland that is covered in snow this weekend,

Bert.

---

### Post by RJ12 on 2010-12-19
> **ronnielsen1 said:**
> It looks like you could probably run windows live messenger in wine but it's a lot better running native linux applications. Try Pidgin. Applications > Internet > Pidgin Internet Messenger

Ubuntu 10.10 includes Empathy by default instead of Pidgin. You can use either of them, but for pidgin, you need to install it using the Ubuntu Software Center or using this code in the terminal
```
sudo apt-get install pidgin
```

When using sudo, it will ask you for your password, when you type it, it will look as if you aren't typing it when you are. Don't worry, continue typing and then press enter. When it asks if your sure you want to install it, type y then press enter.

---

