---
title: "Azureus"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by hfox04 on 2009-01-26
I have completly no idea what im doing luckily ive been copying and pasting my way to sucess but now im stuck.

Tried to update azureus because of that problem, kept wanting to restart and couldnt see any browser information, 
Then removed vuze with symantic and tried reinstalling it but i dont even know how to reinstall a program, i downloaded it and cant get any further please help.
I have ubuntu latest version maybe?? sorry im a complete newb idiot whatever words you would like, just please help before i throw my laptop out the window. oh its a dell inspiron b120 by the way if that helps.

---

### Post by LostMagix on 2009-01-26
> **hfox04 said:**
> I have completly no idea what im doing luckily ive been copying and pasting my way to sucess but now im stuck.

Tried to update azureus because of that problem, kept wanting to restart and couldnt see any browser information, 
Then removed vuze with symantic and tried reinstalling it but i dont even know how to reinstall a program, i downloaded it and cant get any further please help.
I have ubuntu latest version maybe?? sorry im a complete newb idiot whatever words you would like, just please help before i throw my laptop out the window. oh its a dell inspiron b120 by the way if that helps.

I am having this same problem, I have just been ignoring it...

---

### Post by sandyd on 2009-01-26
ok, a few things first. 
ive learned one thing while using vuze. 
NEVER click the update button when it says theirs an update. Ive fried my vuze installation at least 10 times by doing this absentmindedly. 

Now lets get vuze installed....

first, download it from the site ([http://vuze.com](http://vuze.com)) to your desktop
open up a terminal and type this in
if you don't know how to open up a terminal, perhaps another user could help you

```

sudo apt-get remove vuze
cd Desktop
bzip2 -d vuze*.bz
tar xvf vuze*.tar
mv vuze ../
cd bin
ln vuze ~/vuze/vuze
```
to start vuze, just type this in the terminal
```

vuze
```

have a great time on your new ubuntu system :)

oh yes, and one more thing. to do torrents, youll have to open up ports, just like in windows.

type this in the terminal

```

sudo apt-get install firestarter
sudo firestarter
```
There, you can choose which ports to open (all ports incoming are closed by default.

Theirs also another firewall you can use 
```

sudo apt-get install gufw
sudo gufw
```

Gufw is a little harder than firestarter, but firestarter hasn't received an update in a long time.


P.S. you might want to use other bittorent clients as Vuze is a little slow on linux.

ill give a list here....

Transmission (installed by default, find it in the menu)(this is the fastest ive found so far)
ktorrent (sudo apt-get install ktorrent)
bittornado (sudo apt-get install bittornado)

P.P.S the program you used (in the first post) is called "Synapatic" not "symantic"
although there is symantec antivirus for linux

---

### Post by hughcrowther on 2009-01-28
Sorry struggling with it still 
after the sudo line I get 

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Can you get men out of this and beyond?
thanks

---

### Post by hyper_ch on 2009-01-28
> **carlee said:**
> oh yes, and one more thing. to do torrents, youll have to open up ports, just like in windows.

type this in the terminal

```

sudo apt-get install firestarter
sudo firestarter
```
There, you can choose which ports to open (all ports incoming are closed by default.

By default, you don't ahve to open any ports as none are closed. By installing firestarter you actually do close the ports!

---

### Post by GepettoBR on 2009-01-28
> **hughcrowther said:**
> Sorry struggling with it still 
after the sudo line I get 

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Can you get men out of this and beyond?
thanks

that error appears when there's already a package manager working (if Synaptic is open, for example, or if you're installing/uninstalling/updating anything). Just close the package manager (you'll want to wait until it's done, if it's still doing something) and try again.

---

### Post by hfox04 on 2009-01-29
alright so ive remmmoved vuze completly, with synaptic, and add/remove programs, now i would really like to install vuze because its an all in one search download client. Then i downloaded the up to date 4.1 vuze for linux right off the website to my desktop, and extracted it, also tried without extracting, neither worked. i tried your aboze directions, and this is what happens.
harrison@harrison-laptop:~/Desktop$ sudo apt-get remove vuze
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package vuze is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libsm-dev gappletviewer-4.3 libecj-java libice-dev x11proto-xext-dev
  ttf-wqy-zenhei libgcj-bc x11proto-kb-dev linux-headers-2.6.27-7 antlr junit
  ttf-kannada-fonts libregexp-java libjaxp1.3-java-gcj
  linux-headers-2.6.27-7-generic libxi-dev libantlr-java ecj-gcj libxdmcp-dev
  libxerces2-java-gcj xtrans-dev libbcel-java ant-optional-gcj
  x11proto-core-dev ant gcj-4.3 ecj gjdoc ttf-telugu-fonts libjaxp1.3-java
  libgcj9-dev libxt-dev libxext-dev libswt-gnome-gtk-3.4-jni libxerces2-java
  zlib1g-dev x11proto-input-dev libpthread-stubs0-dev libxau-dev
  libpthread-stubs0 libgcj9-0-awt libgcj9-src fastjar ttf-oriya-fonts
  libx11-dev libxcb-xlib0-dev libcommons-lang-java libecj-java-gcj libxcb1-dev
  ttf-bengali-fonts ant-gcj ant-optional libswt-cairo-gtk-3.4-jni
  libantlr-java-gcj libswt-gtk-3.4-jni libswt-mozilla-gtk-3.4-jni
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
harrison@harrison-laptop:~/Desktop$ cd Desktop
bash: cd: Desktop: No such file or directory
harrison@harrison-laptop:~/Desktop$ bzip2 -d vuze*.bz
bzip2: Can't open input file vuze*.bz: No such file or directory.
harrison@harrison-laptop:~/Desktop$ tar xvf vuze*.tar
tar: vuze*.tar: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
harrison@harrison-laptop:~/Desktop$ mv vuze ../
harrison@harrison-laptop:~/Desktop$ cd bin
bash: cd: bin: No such file or directory
harrison@harrison-laptop:~/Desktop$ ln vuze ~/vuze/vuze
ln: accessing `vuze': No such file or directory


Sorry for being an idiot i really need to figure this out, thanx guys.

---

### Post by GepettoBR on 2009-01-29
> **hfox04 said:**
> alright so ive remmmoved vuze completly, with synaptic, and add/remove programs, now i would really like to install vuze because its an all in one search download client. Then i downloaded the up to date 4.1 vuze for linux right off the website to my desktop, and extracted it, also tried without extracting, neither worked. i tried your aboze directions, and this is what happens.
harrison@harrison-laptop:~/Desktop$ sudo apt-get remove vuze
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package vuze is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libsm-dev gappletviewer-4.3 libecj-java libice-dev x11proto-xext-dev
  ttf-wqy-zenhei libgcj-bc x11proto-kb-dev linux-headers-2.6.27-7 antlr junit
  ttf-kannada-fonts libregexp-java libjaxp1.3-java-gcj
  linux-headers-2.6.27-7-generic libxi-dev libantlr-java ecj-gcj libxdmcp-dev
  libxerces2-java-gcj xtrans-dev libbcel-java ant-optional-gcj
  x11proto-core-dev ant gcj-4.3 ecj gjdoc ttf-telugu-fonts libjaxp1.3-java
  libgcj9-dev libxt-dev libxext-dev libswt-gnome-gtk-3.4-jni libxerces2-java
  zlib1g-dev x11proto-input-dev libpthread-stubs0-dev libxau-dev
  libpthread-stubs0 libgcj9-0-awt libgcj9-src fastjar ttf-oriya-fonts
  libx11-dev libxcb-xlib0-dev libcommons-lang-java libecj-java-gcj libxcb1-dev
  ttf-bengali-fonts ant-gcj ant-optional libswt-cairo-gtk-3.4-jni
  libantlr-java-gcj libswt-gtk-3.4-jni libswt-mozilla-gtk-3.4-jni
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[b]harrison@harrison-laptop:~/Desktop$ cd Desktop
bash: cd: Desktop: No such file or directory[/b]
harrison@harrison-laptop:~/Desktop$ bzip2 -d vuze*.bz
bzip2: Can't open input file vuze*.bz: No such file or directory.
harrison@harrison-laptop:~/Desktop$ tar xvf vuze*.tar
tar: vuze*.tar: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
harrison@harrison-laptop:~/Desktop$ mv vuze ../
**[color=red]harrison@harrison-laptop:~/Desktop$ cd bin**[/color]
bash: cd: bin: No such file or directory
harrison@harrison-laptop:~/Desktop$ ln vuze ~/vuze/vuze
ln: accessing `vuze': No such file or directory


Sorry for being an idiot i really need to figure this out, thanx guys.

The process failed on the lines I bolded out. Instead of "cd Desktop", type ```
cd ~/Desktop
```

The line in red is also wrong. The correct command is not "cd bin", it is ```
cd /bin
```
It should work if you try again with these changes.

Sorry it took so long to reply, and good luck. Remember to doublecheck each line for typing errors before hitting "Enter"!

---

### Post by hfox04 on 2009-01-29
cant get pass the third line in...
harrison@harrison-laptop:~$ cd ~/Desktop
harrison@harrison-laptop:~/Desktop$ bzip2 -d vuze*.bz
bzip2: Can't open input file vuze*.bz: No such file or directory.
harrison@harrison-laptop:~/Desktop$ zip2 -d vuze*.bz
bash: zip2: command not found
harrison@harrison-laptop:~/Desktop$ zip -d vuze*.bz
	zip warning: vuze*.bz not found or empty

zip error: Nothing to do! (vuze*.bz)
harrison@harrison-laptop:~/Desktop$ tar xvf vuze*.tar
tar: vuze*.tar: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
harrison@harrison-laptop:~/Desktop$ 
 
tryied to skip it , and obviously doesnt work.??? do i need to rename the file just for FYI the file name of the installer of vuze i downloaded is Vuze_Installer.tar.bz2

thanks again for the help.

---

### Post by GepettoBR on 2009-01-30
If that's the case, then just capitalize the V in "vuze*.bz" and "vuze*.tar".

---

### Post by hfox04 on 2009-01-30
still no dice. ive tried everything, if i new how to install the package i downloaded id be good, everything you tell me to do man isnt working no offense to you, im sure its the way i downloaded it or something. i even extraced the Vuze_Installer.tar.bz2 to the desktop and then tried your script and still didnt work. please someone give me the magic fix,

---

### Post by GepettoBR on 2009-01-30
you can always just ```
sudo apt-get install vuze
```or download and double-click the Vuze .deb package from [http://www.getdeb.net/](http://www.getdeb.net/)

This won't get you the absolute latest version, though. GetDeb has the latest _stable_ version, and the repositories tend to get outdated.

---

