---
title: "Installing using WINE in 10.04"
date: 2010-05-18
forum: New to Ubuntu
---

### Post by flyfishingphil on 2010-05-18
Here's a very basic question for somebody that is experienced at using WINE.

I went to the WINE assist page here in Ubuntu, installed it from the Synaptics, got everything running there, copied a the PCSuite.exe file from the cd (for my cell) to the desktop and was ready to install until I ran into that famous "everybody but you knows how to do that!" wall.

Here is what it says in the manual for installing using WINE:
[I]
# Download the Windows application from any source (e.g. download.com). Download the .EXE (executable).
# Place it in a convenient directory (e.g. the desktop, or home folder).
#

Open the terminal, and cd into the directory where the .EXE is located.
#

Type wine the-name-of-the-application.extension (e.g. wine realplayer.exe).[/I] 

What/how do I do the cd into the directory where the .exe is located?

It's on Desktop so do I need to add a folder there and drag it into the folder or something?

(I hate directions that assume you already know how to do it, you just need to fine tune it!)

Thanks for any assists.

---

### Post by ubunterooster on 2010-05-18
right-click the .exe and select "open with">"wine"

Why do they think it is easier to tell others to use commandline all the time?

---

### Post by KdotJ on 2010-05-18
if the PCSuite.exe is on your desktop, this is how you "cd" to it...
open a terminal and type:

```
cd Desktop
```

then you can use the command as you found:

```
wine PCSuite.exe
```

However, if you have wine installed, you should be able to right-click on the PCSuite.exe file and there should be an option to install it via wine

---

### Post by pizza-is-good on 2010-05-18
> **flyfishingphil said:**
> Here's a very basic question for somebody that is experienced at using WINE.

I went to the WINE assist page here in Ubuntu, installed it from the Synaptics, got everything running there, copied a the PCSuite.exe file from the cd (for my cell) to the desktop and was ready to install until I ran into that famous "everybody but you knows how to do that!" wall.

Here is what it says in the manual for installing using WINE:
[I]
# Download the Windows application from any source (e.g. download.com). Download the .EXE (executable).
# Place it in a convenient directory (e.g. the desktop, or home folder).
#

Open the terminal, and cd into the directory where the .EXE is located.
#

Type wine the-name-of-the-application.extension (e.g. wine realplayer.exe).[/I] 

What/how do I do the cd into the directory where the .exe is located?

It's on Desktop so do I need to add a folder there and drag it into the folder or something?

(I hate directions that assume you already know how to do it, you just need to fine tune it!)

Thanks for any assists.

They tried to get you to do it through the terminal. They should have been more clear. You came to the right place however.


> **ubunterooster said:**
> right-click the .exe and select "open with">"wine"

Why do they think it is easier to tell others to use commandline all the time?

I agree. They should explain things.

The second quote is right. For me just double-clicking on the .exe(s) opens up wine.
TIP: Sometimes the .exe will not run because it is not set as a trusted executable(Usually if you just downloaded the .exe from the web). If that happens, you need to right click it, go to properties, permissions tab, and check "Allow executing file as program" box. That will fix it.

---

### Post by ubunterooster on 2010-05-18
I have default as "virus scanner" for security so I need to right-click for the wine option; see if double click works for you

---

### Post by flyfishingphil on 2010-05-18
> **ubunterooster said:**
> right-click the .exe and select "open with">"wine"

Why do they think it is easier to tell others to use commandline all the time?
Experimented while waiting, and taking care of a problem with a counterfit version of XP I purchased to use in VBox, and a nice little box popped up that says:

*The file'/home/flyfishingphil/desktop/PCSuite.exe' is not marked as executable. If this was downloaded or copied from an untrusted source, it may be dangerous to run. For more details, read about the _**executable bit**_.*

When I clicked on the "executable bit" here's what I got:

   [I] * Security/ExecutableBit

Software in Ubuntu needs to be "executable" (sometimes called "trusted"), both in the sense that the software is a program, and that it is marked as an "executable file" via file permissions. Normal software is available for installation via the Software Center; this is the primary source of software in Ubuntu.

Files downloaded from other locations are not marked as "executable" since they did not get installed via a trusted software repository. Because of this, attempting to open downloaded files that are software will fail. The primary reason for blocking this software is to help unsuspecting users avoid malware (i.e. malicious software like trojan horses, worms, and viruses).

Ubuntu Policy requires that software not marked as executable not be runnable. One of the most common ways this happens is by having a package ship a .desktop file for a MimeType which executes the target file (.EXE, .JAR, etc). This is not allowed unless the target file is already executable (or installed by a trusted software repository). [/I]

This is starting to sound a little like the problem with Windough$. "If we don't write it you can't use it."

Guess you can only use in Wine what it offers. Any suggestions on how I might get around this?

BTW, thanks for the fast and helpful replies.

---

### Post by afmGM on 2010-05-18
Right click the file, Properties.  In the permission tabs, check allow file to execute as program, and there ya go :)

---

### Post by flyfishingphil on 2010-05-18
> **afmGM said:**
> Right click the file, Properties.  In the permission tabs, check allow file to execute as program, and there ya go :)
Thanks afmGm. Followed your directions. Went into Wine, clicked on the SE PCSuite, the little wheel spun 'round 'n' 'round and got nothing. Received a little box that flashed something about "unable to load", but I was typing and that's all I saw. 

I'll go to the Sony Ericsson site and see if I can download it from there. Don't know if that will be a different file, or not, but hey, gives m something else to get frustrated about.

---

### Post by oldgeekster on 2010-05-18
> **flyfishingphil said:**
> Experimented while waiting, and taking care of a problem with a counterfit version of XP I purchased to use in VBox, and a nice little box popped up that says:

*The file'/home/flyfishingphil/desktop/PCSuite.exe' is not marked as executable. If this was downloaded or copied from an untrusted source, it may be dangerous to run. For more details, read about the _**executable bit**_.*

When I clicked on the "executable bit" here's what I got:

   [I] * Security/ExecutableBit

Software in Ubuntu needs to be "executable" (sometimes called "trusted"), both in the sense that the software is a program, and that it is marked as an "executable file" via file permissions. Normal software is available for installation via the Software Center; this is the primary source of software in Ubuntu.

Files downloaded from other locations are not marked as "executable" since they did not get installed via a trusted software repository. Because of this, attempting to open downloaded files that are software will fail. The primary reason for blocking this software is to help unsuspecting users avoid malware (i.e. malicious software like trojan horses, worms, and viruses).

Ubuntu Policy requires that software not marked as executable not be runnable. One of the most common ways this happens is by having a package ship a .desktop file for a MimeType which executes the target file (.EXE, .JAR, etc). This is not allowed unless the target file is already executable (or installed by a trusted software repository). [/I]

This is starting to sound a little like the problem with Windough$. "If we don't write it you can't use it."

Guess you can only use in Wine what it offers. Any suggestions on how I might get around this?

BTW, thanks for the fast and helpful replies.Gee, don't rebel because it is trying to help protect ya. ;)

If you feel the file is from a reliable source, just right click on it - select properties | permissions - mark it as executable - then proceed as before. (This also can be done from the command line but I don't think you really want to mess with that - using the nautilus file browser is SO much easier these days).  Good luck!

---

### Post by flyfishingphil on 2010-05-18
OK. Went to SE and downloaded it. It appeared to be a different file. gave it permission, did the Wine thing, and a window pops up (that I had to use the arrows and enter on) that said I needed MTP (Media Transfer Protocol) and did I want it installed. Entered yes and it plodded along for a while. Got into the setup process for connecting the phone then it stops and up pops a box that reads:

[I]The program ISAdmin.exe has encountered a serious problem and needs to close. We are sorry for the inconvenience.

This can be caused by a problem in the program or a deficiency in Wine. You may want to check [http://appdb.winehq.or](http://appdb.winehq.or) for tips about running this application.

If this problem is not present under Windows and has not been reported yet, you can report it at [http://bugs.winehq.org](http://bugs.winehq.org)[/I]

Tried to do the Wine bug but got so turned around there I gave up.

Here are a couple more questions: Does anybody know if there is a Media Transfer in Ubuntu that may replace the other one? **_Disregard, I checked in Symantic and it shows that libmtp8 has been installed. Guess Wine didn;t see that.)_** Do I need to get rid of the one above and, if so, how? Also, how do I delete the program from Wine so, if everything works, I don't have 2 PCSuites listed there?

---

### Post by flyfishingphil on 2010-05-19
> **flyfishingphil said:**
> OK. Went to SE and downloaded it. It appeared to be a different file. gave it permission, did the Wine thing, and a window pops up (that I had to use the arrows and enter on) that said I needed MTP (Media Transfer Protocol) and did I want it installed. Entered yes and it plodded along for a while. Got into the setup process for connecting the phone then it stops and up pops a box that reads:

[I]The program ISAdmin.exe has encountered a serious problem and needs to close. We are sorry for the inconvenience.

This can be caused by a problem in the program or a deficiency in Wine. You may want to check [http://appdb.winehq.or](http://appdb.winehq.or) for tips about running this application.

If this problem is not present under Windows and has not been reported yet, you can report it at [http://bugs.winehq.org](http://bugs.winehq.org)[/I]

Tried to do the Wine bug but got so turned around there I gave up.

Here are a couple more questions: Does anybody know if there is a Media Transfer in Ubuntu that may replace the other one? **_Disregard, I checked in Symantic and it shows that libmtp8 has been installed. Guess Wine didn;t see that.)_** Do I need to get rid of the one above and, if so, how? Also, how do I delete the program from Wine so, if everything works, I don't have 2 PCSuites listed there?
Just thought I'd throw another question in here and see if it gets answered and helps to diagnose the problem.

I have VBox installed, with all of the infor regarding the SE W760 PCSuite, etc, in there and I tried to install that in Wine to see if it would work better there. Could there be a conflict between those two? Also, in VBox, keep getting the "Unable to mount the W760, error 60" box but, at the same time, it shows the phone mounted in the upper left side of the main screen. Any thoughts on that?

**_EDIT Add On_** Curiouser and Curiouser! I just went in to Synaptics and did a full search using "mobile phones" and it came up with a long list of add-ins related to that. Among them were GMobileMedia, Gnokii, Cobex, Gammu and a slug of others. Is anybody versed in those regarding how to choose, do they actually work, would they do any good in my trying to communicate with my Sony Ericsson W760? 

This could drive a guy crazy after a while.

---

