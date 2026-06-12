---
title: "Path variable help"
date: 2010-11-22
forum: New to Ubuntu
---

### Post by CorCor on 2010-11-22
Hi all,  brand spankin new here.  Little info first,  very new to linux,  had Mint dual booted with win2000 for the past year,  rarely ran Mint due to not being able to get my internet working with it.  Installed Ubuntu 10.10 last week and loving it,  only booted back to windows once because I needed to use a tool I only have for windows...

The dilemma,  I have been working on building a theme for the motorola droid.  One tool I found useful for in the process is called apkmanager ([http://forum.xda-developers.com/showthread.php?t=695701](http://forum.xda-developers.com/showthread.php?t=695701))  In windows I had it working fine,  downloaded the linux version and im a bit lost.

Directions for linux read:

> - Open terminal and change-directory to apkmanager (Easiest way is to type "cd ")
- Chmod 755 Script.sh
- Chmod 755 all files apps inside other folder (thanks for the tip bkmo  )
- Run script by typing ./Script.sh 

Got the directory changed,  no idea what the chmod is all about,  tried typing it into terminal and nothing seemed to happen...  When I run the script I get the following...

> The program optipng is missing or is not in your PATH,
please install it or fix your PATH variable
The program 7za is missing or is not in your PATH,
please install it or fix your PATH variable
The program adb is missing or is not in your PATH,
please install it or fix your PATH variable
The program aapt is missing or is not in your PATH,
please install it or fix your PATH variable
The program sox is missing or is not in your PATH,
please install it or fix your PATH variable


Found this page ([http://everyjoe.com/technology/howto-add-a-directory-to-my-path-statementvariable/](http://everyjoe.com/technology/howto-add-a-directory-to-my-path-statementvariable/)) But I want to make sure I dont screw up trying this because directions were a bit confusing to me...

Says to type this to terminal
```
PATH=$PATH:/new/path (where /new/path is the directory you want to add)
export PATH
```
The programs it says Im missing are in the directory /home/corey/Android/apkmanager/other
so from what im understanding I just need to open terminal and type ```
PATH=$PATH:/home/corey/Android/apkmanager/other
export PATH
```

Is this correct or am I missing something?


OH also read at the very bottom  
> To add that PATH to every user but root, add the line(s) to /etc/profile
To add that PATH to root, add those line(s) to /root/.bash_profile
Do I type this after "export PATH"?

---

### Post by cwa on 2010-11-22
That is how you export the path, that looks correct. You can also try, export PATH=$PATH:/new/path

echo the path variable and make note of that. If something goes wrong, then you can always set it back I believe. use echo $PATH to see the current path, you can use echo $PATH 1> path.bk  to back it up. NOTE: if something does go wrong, then you would probably have to use absolute paths to use the programs you want to use to set the path back. 

Also, personally, I wouldn't follow the advice about /etc/profile or  /root/.bash_profile if you are going to keep the program in your home directory. I would move it some place else. might move/install it to /opt

here is a website about this directory [http://www.pathname.com/fhs/pub/fhs-2.3.html#OPTADDONAPPLICATIONSOFTWAREPACKAGES](http://www.pathname.com/fhs/pub/fhs-2.3.html#OPTADDONAPPLICATIONSOFTWAREPACKAGES)

hope that helps.
cwa

---

### Post by karlwbloedorn on 2010-11-22
Hopefully some of this helps you understand it better:

The command "chmod" changes the permissions of a folder or files that you specify. It usually doesn't print anything out unless there is a problem.

PATH is an environment variable. What does this mean? It means that shell scripts and programs can access the information. Its helpful so that you don't have to type "/usr/bin/ssh". Instead you can type ssh, thus saving work.

Running the command "PATH=$PATH:/home/corey/Android/apkmanager/other" will add the specified directory to the PATH environment variable. In order to make this change persist beyond a reboot you need to "export PATH". So, to me, it looks like you are doing it right.

Tip: If you want to see what your current PATH is, you can type "echo $PATH" into a terminal. Then, try it after you run those two commands and see what changed.

---

### Post by CorCor on 2010-11-23
\\:D/ Awesome,  thanks for the help to both of you.  I took the advice and moved it to /opt along with the android sdk...much easier to type out that path.  Also found out part of my problem was I hadn't run chmod 755 on all the files in the other folder    ](*,)  And there was 1 little program I didnt have... sox something to do with sounds.  But I just got it running I'm going to export the path since its working

---

### Post by karlwbloedorn on 2010-11-23
Glad to hear you got it working

---

### Post by CorCor on 2010-11-23
dont want to start a new thread for this,  but the path isnt sticking.  ive set it up and done "export PATH" at least twice now and every time I reboot or even close the terminal it resets... is there more to it than just typing "export PATH"?

Heres terminal
```
corey@corey-desktop:/opt/apkmanager$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
corey@corey-desktop:/opt/apkmanager$ PATH=$PATH:/opt/apkmanager/other:/opt/ASDK/tools
corey@corey-desktop:/opt/apkmanager$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/opt/apkmanager/other:/opt/ASDK/tools
corey@corey-desktop:/opt/apkmanager$ export PATH
```

Close out then open term again and...
```
corey@corey-desktop:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```

---

### Post by bschrib on 2011-06-15
> **CorCor said:**
> dont want to start a new thread for this,  but the path isnt sticking.  ive set it up and done "export PATH" at least twice now and every time I reboot or even close the terminal it resets... is there more to it than just typing "export PATH"?

Heres terminal
```
corey@corey-desktop:/opt/apkmanager$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
corey@corey-desktop:/opt/apkmanager$ PATH=$PATH:/opt/apkmanager/other:/opt/ASDK/tools
corey@corey-desktop:/opt/apkmanager$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/opt/apkmanager/other:/opt/ASDK/tools
corey@corey-desktop:/opt/apkmanager$ export PATH
```

Close out then open term again and...
```
corey@corey-desktop:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```

Great news! I was having this problem too.. The guide I was following had me input the path(s) into my .bashrc file (located at ~), but had a space between : and ~.. Anyways, just append this to your .bashrc file and you should be in business.

```
export PATH=$PATH:/opt/apkmanager/other:/opt/ASDK/tools
```

---

### Post by h3llsdr0id on 2013-01-14
> **CorCor said:**
> Hi all,  brand spankin new here.  Little info first,  very new to linux,  had Mint dual booted with win2000 for the past year,  rarely ran Mint due to not being able to get my internet working with it.  Installed Ubuntu 10.10 last week and loving it,  only booted back to windows once because I needed to use a tool I only have for windows...

The dilemma,  I have been working on building a theme for the motorola droid.  One tool I found useful for in the process is called apkmanager ([http://forum.xda-developers.com/showthread.php?t=695701](http://forum.xda-developers.com/showthread.php?t=695701))  In windows I had it working fine,  downloaded the linux version and im a bit lost.

Directions for linux read:



Got the directory changed,  no idea what the chmod is all about,  tried typing it into terminal and nothing seemed to happen...  When I run the script I get the following...



Found this page ([http://everyjoe.com/technology/howto-add-a-directory-to-my-path-statementvariable/](http://everyjoe.com/technology/howto-add-a-directory-to-my-path-statementvariable/)) But I want to make sure I dont screw up trying this because directions were a bit confusing to me...

Says to type this to terminal
```
PATH=$PATH:/new/path (where /new/path is the directory you want to add)
export PATH
```
The programs it says Im missing are in the directory /home/corey/Android/apkmanager/other
so from what im understanding I just need to open terminal and type ```
PATH=$PATH:/home/corey/Android/apkmanager/other
export PATH
```

Is this correct or am I missing something?


OH also read at the very bottom  

Do I type this after "export PATH"?

20130114 UPDATE For:

The program sox is missing or is not in your PATH,
please install it or fix your PATH variable

The program adb is missing or is not in your PATH,
please install it or fix your PATH variable


**Well the new APK Manager is 5.0.**

And the only things missing when trying to run the "./Script.sh" is:

- adb
- sox

So, if you don't already have the Android SDK installed,
and/or your PATH is not setup correctly,
then run these two commands:

**## to install sox**

sudo apt-get install sox

**## to install adb**

sudo add-apt-repository ppa:nilarimogard/webupd8

sudo apt-get update

sudo apt-get install android-tools-adb android-tools-fastboot

Now you can use the APK Manager.

---

### Post by howefield on 2013-01-14
Old thread closed.

---

