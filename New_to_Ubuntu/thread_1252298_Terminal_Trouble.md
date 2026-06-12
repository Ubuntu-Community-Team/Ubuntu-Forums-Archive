---
title: "Terminal Trouble"
date: 2009-08-28
forum: New to Ubuntu
---

### Post by Steve guy on 2009-08-28
HI I am fairly new to ubuntu I have the 9.04 version downloaded on my lap top.

I am trying to copy a file from my desktop to /usr/bin

The file name in desktop is isky and it is a shell script.

I tried:

**sudo cp /steve/desktop/isky /usr/bin**

Although then it tells me the the file /steve/desktop/isky does not exist.

Help please!!!

---

### Post by Tclarkie on 2009-08-28
its /home/steve/Desktop/isky

---

### Post by vttay03 on 2009-08-28
try /home/steve/Desktop/isky 

keep in mind that Linux is case sensitive and your user directory should also be under /home instead of the root directory

---

### Post by Martin Marshalek on 2009-08-28
Try:

```
/home/steve/Desktop/ipsky.sh
```

You need to specify the extension usually as well.

---

### Post by denver on 2009-08-28
You have to read a bit about relative and absolute paths. Linux has a hierarchical file system. What that means is that the filesystem is layed out like the branches of a tree.

In absolute paths everything starts from the root folder "/" and moves onwards to the file you are interested in.

In relative paths you consider the current folder as the starting point, and not the root folder.

So, for you to be able to copy a file from your desktop to somewere else, you should type something allong the lines of:

```
sudo cp /home/steve/Desktop/isky /usr/bin
```
(absolute paths starting from the root folder)

OR if you are currently in /home/steve:

```
sudo cp Desktop/isky /usr/bin
```

Also, be verry carefull you use the corect case when typing. "desktop" is verry different from "Desktop" (note the capital D).

---

### Post by credobyte on 2009-08-28
Shell scripts have an extension: .sh
To ensure that you are not trying to copy something that doesn't exist, cd to $HOME/Desktop and execute ls - copy/paste would be just fine :)

---

### Post by denver on 2009-08-28
Extensions have no relevance in linux. You may rename any shell script with any extension you want...as long as it has the executable flag ON, and the corect header it should run without any problems.

---

### Post by Steve guy on 2009-08-28
Thanks I really appreciate the help although I tried all of these options and i got this exact error
 
cp: cannot stat /home/steve/Desktop/isky.sh' : no such file or directory
 
Any other ideas??

---

### Post by oldos2er on 2009-08-28
Can you post the output of **ls ~/Desktop** ?

---

### Post by CatKiller on 2009-08-28
> **Steve guy said:**
>  Any other ideas??

Always use Tab-completion. Then you'll know that you're dealing with a file that actually exists rather than some random string of characters that you happen to have typed in.

EDIT: Sorry. That came out far more snarky than I intended.

---

### Post by Brian Vaughan on 2009-08-28
Perhaps you could post the output of

```
whoami
pwd
ls -l ~/Desktop
```

Also, if you're not experienced with Unix and Linux, it may not be a good idea to copy a script file to /usr/bin. It would be a bit safer to create /home/steve/bin, and place it there. If /home/[username]/bin exists, it's in your path, but only in your path, whereas files in /usr/bin would normally be in the path of any user, and that could be a security risk if you're not certain of the contents of the script file.

---

### Post by Steve guy on 2009-08-28
Ok I figured that much out but now I cant get the file to run like it was suppose to.

I downloaded isky which is a program that apparently will let me get itunes on linux for synchronising my i pod.

It stated where this file is a shell script just copy it to /usr/bin and make it executable and it will take the appropriate steps from there but it is not doing that.

If someone could look at this post I am about to paste below and follow his steps to the download and let me know what I am doing wrong. Thank you.

[http://www.linuxquestions.org/questions/ubuntu-63/isky-installs-itunes-internet-explorer-and-skype-on-ubuntu-9.04-749830/](http://www.linuxquestions.org/questions/ubuntu-63/isky-installs-itunes-internet-explorer-and-skype-on-ubuntu-9.04-749830/)

---

### Post by Steve guy on 2009-08-28
Ok I figured that much out but now I cant get the file to run like it was suppose to.

I downloaded isky which is a program that apparently will let me get itunes on linux for synchronising my i pod.

It stated where this file is a shell script just copy it to /usr/bin and make it executable and it will take the appropriate steps from there but it is not doing that.

If someone could look at this post I am about to paste below and follow his steps to the download and let me know what I am doing wrong. Thank you.

[http://www.linuxquestions.org/questi...u-9.04-749830/]("http://www.linuxquestions.org/questions/ubuntu-63/isky-installs-itunes-internet-explorer-and-skype-on-ubuntu-9.04-749830/")

---

### Post by Brian Vaughan on 2009-08-28
After reading that description, iSky sounds like a bad idea.

Wine is already in the Ubuntu repositories, albeit not the latest version of Wine. To install the Wine repository for the latest version of Wine, follow the instructions here:
[Wine for Ubuntu and Ubuntu derivatives]("http://www.winehq.org/download/deb").

However, Wine cannot handle USB connections, and as I understand it, iPods require USB connections, so I don't think this would work for what you have in mind.

I don't see why iSky should have to be installed in /usr/bin, instead of some other arbitrary path. That sounds a bit dodgy.

Also, it's very important to remember that Wine should never be executed by root. It's intrinsically insecure.

As for the question of why isky isn't working, I couldn't say. It could be file permissions -- that was one of the reasons I was asking for the output of ls ~/Desktop, or whichever folder has the file now.

---

### Post by vttay03 on 2009-08-28
if you want to run the script, then you must do the following after copying it into your /usr/bin directory (keep in mind this assumes you are actually in that directory when you're performing these commands) 

```

chmod u+x isky
./isky

```

the first command modifies the shell script and makes it an executable for the user and the second actually runs the script

---

### Post by vttay03 on 2009-08-28
and just as a side note, i agree with Brian - isky doesn't look like a very good idea so I'd disregard what I posted above to actually go through with the install

---

### Post by Tclarkie on 2009-08-28
y not just copy paste

---

### Post by natravis on 2009-08-28
Since it appears that the installation method that this script would give you will not accomplish what you want, perhaps you should take a look at [https://help.ubuntu.com/community/PortableDevices/iPod](https://help.ubuntu.com/community/PortableDevices/iPod)

It gives several solutions for managing an Ipod on Ubuntu, providing that you are not using an Ipod Touch or Iphone. I personally liked Banshee the most out of those, but alas I have an Ipod touch so I manage that with my windozer machine.

---

### Post by CatKiller on 2009-08-29
> **vttay03 said:**
> if you want to run the script, then you must do the following after copying it into your /usr/bin directory (keep in mind this assumes you are actually in that directory when you're performing these commands) 

```

chmod u+x isky
./isky

```

If you're going to run it from the current directory (./isky) you don't have to copy it to /usr/bin. At all.

---

### Post by LewRockwell on 2009-08-29
> **Brian Vaughan said:**
> After reading that description, iSky sounds like a bad idea.

Wine is already in the Ubuntu repositories, albeit not the latest version of Wine. To install the Wine repository for the latest version of Wine, follow the instructions here:
[Wine for Ubuntu and Ubuntu derivatives]("http://www.winehq.org/download/deb").

However, Wine cannot handle USB connections, and as I understand it, iPods require USB connections, so I don't think this would work for what you have in mind.

I don't see why iSky should have to be installed in /usr/bin, instead of some other arbitrary path. That sounds a bit dodgy.

Also, it's very important to remember that Wine should never be executed by root. It's intrinsically insecure.

As for the question of why isky isn't working, I couldn't say. It could be file permissions -- that was one of the reasons I was asking for the output of ls ~/Desktop, or whichever folder has the file now.

+1


isky sounds alot like risky...to us...lol!

.

---

### Post by Random Squires on 2009-09-01
BEFORE WE BEGIN: I was the one who wrote "riSky" as LewRockwell so kindly christened it...

The comments about the directorlocation of the script, permissions etc. are right.....I was being my usual absent-minded self, and you should only copy things into /usr/bin A) if you are sure of their contents and B) if you wish to access the script simply by running the command 'iSky'.

The comments about Wine already being in the ubuntu repos are NOT ENTIRELY correct. They contain an older version of WINE, (yes I know all the reasons for this, packages undergo a lot of testing before they reach the Ubuntu repos etc etc) but anyway this older version of WINE will not run iTunes.

Perhaps I should also repeat something I am fairly sure was in my original post: I do not own an ipod. If you have useful information for me about the state of usb support in WINE and what this means for users of my script, then I'd be glad to hear them, this means I can then inform users of what my script can and cannot do.

Thanks
Eddie

---

### Post by CatKiller on 2009-09-01
> **Random Squires said:**
> They contain an older version of WINE, (yes I know all the reasons for this, packages undergo a lot of testing before they reach the Ubuntu repos etc etc) 

Actually, it's more than that. 1.01 is the current stable version of Wine. Anything else is a development version. It may have been out a year already, but it's still going to be the version that's provided by the *wine* package in Karmic. And it will probably stay that way until Wine pick another future release as a stable milestone.

---

### Post by LewRockwell on 2009-09-01
> **Random Squires said:**
> BEFORE WE BEGIN: I was the one who wrote "riSky" as LewRockwell so kindly christened it...

The comments about the directorlocation of the script, permissions etc. are right.....I was being my usual absent-minded self, and you should only copy things into /usr/bin A) if you are sure of their contents and B) if you wish to access the script simply by running the command 'iSky'.

The comments about Wine already being in the ubuntu repos are NOT ENTIRELY correct. They contain an older version of WINE, (yes I know all the reasons for this, packages undergo a lot of testing before they reach the Ubuntu repos etc etc) but anyway this older version of WINE will not run iTunes.

Perhaps I should also repeat something I am fairly sure was in my original post: I do not own an ipod. If you have useful information for me about the state of usb support in WINE and what this means for users of my script, then I'd be glad to hear them, this means I can then inform users of what my script can and cannot do.

Thanks
Eddie

and you'd be more than happy to accept a donated ipod for testing and research purposes...of course

thanks for your commentary!

.

---

