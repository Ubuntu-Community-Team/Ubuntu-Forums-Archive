---
title: "too many problems/new to linux"
date: 2010-11-21
forum: New to Ubuntu
---

### Post by ByteOneZero on 2010-11-21
started out trying to play blu ray discs.searched forums found enough to get in trouble trying m player trying xmbc trying to find plugins.now im completely screwed.i cant get into software sources nor synaptic pkg mgr.my terminal supposedly has corrupt lines 48 and 54 so far.i dont know how to even change or remove anything in terminal.this os is not intuitive like mac or windows.i feel so frustrated i think soon its back to dump everything and start over.am i alone in this?thanks to anyone wholl even talk to me

---

### Post by dFlyer on 2010-11-21
Not sure what your asking but an OS is a personal choice. If you need help fixing something please give us the errors messages and program it's associated with.

---

### Post by ivanovnegro on 2010-11-21
> **ByteOneZero said:**
> started out trying to play blu ray discs.searched forums found enough to get in trouble trying m player trying xmbc trying to find plugins.now im completely screwed.i cant get into software sources nor synaptic pkg mgr.my terminal supposedly has corrupt lines 48 and 54 so far.i dont know how to even change or remove anything in terminal.this os is not intuitive like mac or windows.i feel so frustrated i think soon its back to dump everything and start over.am i alone in this?thanks to anyone wholl even talk to me

Please, calm down and tell step by step what the problem is and then you will find help here for all of your issues if possible.
I know, the first time could be frustrating if you dont know how its expected to work on Ubuntu/Linux, but everything is very intuitive, no worries.

Regards

---

### Post by magnatron on 2010-11-21
Start from scratch, re-install Ubuntu, open synaptic and install VLC instead of MPlayer. It sounds like you've been applying all kinds of stuff in an effort to get your Blue Ray disc player to play, what you should have probably done was search on Google for a solution first or asked another Ubuntu Geek before adding and editing loads of stuff that you probably didn't need in the first place.  It can be frustrating, believe me you think getting Blue Ray going is hard, wait till you run into a wireless card that doesn't want to play nicely and you have a load of proprietary drivers that are not supported on Linux.   :D

Then it becomes real nail bitting hair pulling and exasperating stuff followed with lots of punctuated sighing staring into space, re-reading guides and PDF's and reading other peoples posts, looking over the manufacturers drivers and source etc.

---

### Post by uRock on 2010-11-21
It is hard to help you without knowing what is not working right.

Have you installed the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") package for decrypting DVDs? If not, then following the directions in this ink will get you the software needed for watching DVDs. [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

What do you mean when you say you have corrupt lines in the terminal?

---

### Post by matt_symes on 2010-11-21
Hi

Can i make a suggestion as well?

Ask for help _before_ trying something you are not sure how to do. There are many people here who can help you. Don't give up yet.

Post more information about your problem.

Kind regards

---

### Post by ByteOneZero on 2010-11-21
wow thanks for caring.my synaptic pkg mgr wont open.software center wont show any software.cant play blu ray discs.soooooo i guess ill show an error message.E:malformed line 54 in source list/etc/apt/sources.list (disparse)E:The list of sources could not be read

---

### Post by matt_symes on 2010-11-21
Hi

Open a terminal and type

cat /etc/apt/sources.list

This will display the contents of the file. Copy and paste the result and post it back on this thread in between code tags. I.e press the # button on the toolbar above where you post.

I have no idea about blue ray though so someone else will have to help with that.

Kind regards

---

### Post by ByteOneZero on 2010-11-21
what i mean by corrupt lines in terminal is that i got a message to remove 2 lines or uncommit 2 lines because of improper info.

---

### Post by magnatron on 2010-11-21
sudo gedit /etc/apt/sources.list

It sounds like you added a malformed URL to the apt-get sources, once its removed it'll fix synaptic. Do you remember what repository you tried to add to it?

If not follow matt's advice and use the command cat /etc/apt/sources.list and paste the output on here (in code tags) from the terminal window.

Lines 48 and 54 are the cause of your Woe.

---

### Post by ByteOneZero on 2010-11-21
sorry i typed in terminal cat/etc/apt/sources.list and got .No such file or directory

---

### Post by oldsoundguy on 2010-11-21
Blu-Ray is DRM .. which makes it very difficult to set up in Linux/Ubuntu

Here is a recent read:
[https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD](https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD)

---

### Post by ivanovnegro on 2010-11-21
> **ByteOneZero said:**
> wow thanks for caring.my synaptic pkg mgr wont open.software center wont show any software.cant play blu ray discs.soooooo i guess ill show an error message.E:malformed line 54 in source list/etc/apt/sources.list (disparse)E:The list of sources could not be read

Maybe its really not bad to start from scratch, installing Ubuntu again and then to try to do all the things you want. It seems you messed up some things.

---

### Post by matt_symes on 2010-11-21
Hi

> **ByteOneZero said:**
> sorry i typed in terminal cat/etc/apt/sources.list and got .No such file or directory

Add a space between the cat and /etc/...

cat <space> /etc/apt/sources.list

Kind regards

---

### Post by ByteOneZero on 2010-11-21
tenza@tenza-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://ppa.launchpad.net/team-xbmc/ppa/juanty](http://ppa.launchpad.net/team-xbmc/ppa/juanty) main
deb-src [http://ppa.launchpad.net/team-xbmc/ppa](http://ppa.launchpad.net/team-xbmc/ppa) jaunty main
tenza@tenza-desktop:~$

---

### Post by matt_symes on 2010-11-21
Hi

Open at terminal and type

sudo nano /etc/apt/sources.list

Enter your password you use to log on. You will not see anything as you type it. This normal.

Using the down arrow button, scroll down to the last two lines. They are ...

deb [http://ppa.launchpad.net/team-xbmc/ppa/juanty](http://ppa.launchpad.net/team-xbmc/ppa/juanty) main
deb-src [http://ppa.launchpad.net/team-xbmc/ppa](http://ppa.launchpad.net/team-xbmc/ppa) jaunty main

Put a # and <space> in in front of them so they become...

# deb [http://ppa.launchpad.net/team-xbmc/ppa/juanty](http://ppa.launchpad.net/team-xbmc/ppa/juanty) main
 # deb-src [http://ppa.launchpad.net/team-xbmc/ppa](http://ppa.launchpad.net/team-xbmc/ppa) jaunty main

Press 

Ctrl + o

to save the file.

Press

ctrl + x

to exit nano.

Retry the software centre. Be very careful while exiting this file. Don't make any mistakes. I believe these two entries are causing you problem.

Kind regards

---

### Post by alphacrucis2 on 2010-11-21
> **ByteOneZero said:**
> tenza@tenza-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://ppa.launchpad.net/team-xbmc/ppa/juanty](http://ppa.launchpad.net/team-xbmc/ppa/juanty) main
deb-src [http://ppa.launchpad.net/team-xbmc/ppa](http://ppa.launchpad.net/team-xbmc/ppa) jaunty main
tenza@tenza-desktop:~$

Appears that jaunty is spelled wrong. In any case it isn't usually a good idea to be using a jaunty ppa when you are running lucid

---

### Post by matt_symes on 2010-11-21
Hi

>                                  Appears that jaunty is spelled wrong. In any case it isn't usually  a good idea to be using a jaunty ppa when you are running lucidYes.

deb [http://ppa.launchpad.net/team-xbmc/ppa/juanty](http://ppa.launchpad.net/team-xbmc/ppa/juanty) main

This is the main line to remove and is what is causing the problem. Get back to a working system first though, was my thinking.

EDIT: Anybody know anything about blueray for the OP?

Kind regards

---

### Post by magnatron on 2010-11-21
[https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD](https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD)

That link has some helpful info.. ;)

Looks like it is MPlayer & FFMPEG (not VLC) surprising... This one looks promising [http://themediaviking.com/software/bluray-linux/](http://themediaviking.com/software/bluray-linux/) (and yeap VLC!!)

---

### Post by ByteOneZero on 2010-11-21
thank you Matt for your time and effort.i did as you suggested but when i pressed ctrl+x nothing happened except a dull thudding sound.i tried again and a terminal message said y or n ,i forget the true instruction but i clicked n and terminal went blank except for the original message sudo nano ....etc.i told you i was a dummy when geekspeak is involved.i hate to do it but i think ill wipe my hd and install a copy of win 7 so i can use my pc.can you tell me if a wipe is e z to do? thanks for the effort.

---

### Post by ivanovnegro on 2010-11-21
> **ByteOneZero said:**
> thank you Matt for your time and effort.i did as you suggested but when i pressed ctrl+x nothing happened except a dull thudding sound.i tried again and a terminal message said y or n ,i forget the true instruction but i clicked n and terminal went blank except for the original message sudo nano ....etc.i told you i was a dummy when geekspeak is involved.i hate to do it but i think ill wipe my hd and install a copy of win 7 so i can use my pc.can you tell me if a wipe is e z to do? thanks for the effort.

Its a pity, really. I dont know what you messed up in your sources list but if the first way did not work, why you dont try it with a new install.
With a new install you will have everything on default and then you begin with your custamization or whatever you want to do. Dont give up so fast! I know this feeling.

Edit: I forgot to say, you had to type Y and not N to save the changes.

---

### Post by uRock on 2010-11-21
I don't understand why there are Jaunty repos listed there.

Put a # sign in front of the Jaunty entries and everything should be good to go.

---

### Post by ivanovnegro on 2010-11-21
> **uRock said:**
> I don't understand why there are Jaunty repos listed there.

Put a # sign in front of the Jaunty entries and everything should be good to go.

Thats also right. And I think this was the big problem. But I thought maybe it was too hard to edit with Nano, its not but it seems for him.

---

### Post by uRock on 2010-11-21
> **ivanovnegro said:**
> Thats also right. And I think this was the big problem. But I thought maybe it was too hard to edit with Nano, its not but it seems for him.
That is why I prefer gedit. Vi is even harder to figure out the first few tries.

---

### Post by apollothethird on 2010-11-21
> **ivanovnegro said:**
> Maybe its really not bad to start from scratch, installing Ubuntu again and then to try to do all the things you want. It seems you messed up some things.

I believe starting over is a bad first suggestion to a new user.  I believe it's best to become familiar with trouble shooting an issue.

If after a couple of days of following suggestions from the gurus of this forum it becomes evident that the system is corrupted beyond repair the start-over should become a strong consideration.

I haven't read the whole thread, but from what I see so far the user is ranting and might not have the bleak situation that you're suspecting.

There's a good chance that starting over will bring us back to where we are now, but with the user having a taste that Ubuntu is a fragile application that needs to be constantly reinstalled to make it work.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by ivanovnegro on 2010-11-22
> **apollothethird said:**
> I believe starting over is a bad first suggestion to a new user.  I believe it's best to become familiar with trouble shooting an issue.

If after a couple of days of following suggestions from the gurus of this forum it becomes evident that the system is corrupted beyond repair the start-over should become a strong consideration.

I haven't read the whole thread, but from what I see so far the user is ranting and might not have the bleak situation that you're suspecting.

There's a good chance that starting over will bring us back to where we are now, but with the user having a taste that Ubuntu is a fragile application that needs to be constantly reinstalled to make it work.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

I understand you and I agree. But it seems that he will already go back to Win7 because he could not edit his sources list with Nano.
I admit it was a little bit too fast to advice a new install but with the help of this forum I expected it would not be a great deal.

---

### Post by apollothethird on 2010-11-22
> **ByteOneZero said:**
> thank you Matt for your time and effort.i did as you suggested but when i pressed ctrl+x nothing happened except a dull thudding sound.i tried again and a terminal message said y or n ,i forget the true instruction but i clicked n and terminal went blank except for the original message sudo nano ....etc.i told you i was a dummy when geekspeak is involved.i hate to do it but i think ill wipe my hd and install a copy of win 7 so i can use my pc.can you tell me if a wipe is e z to do? thanks for the effort.

If you have an extremely pressing deadline for looking at your BluRay disk, you might consider spending a couple of hours installing Windows 7 which might have the drivers for your application.

But if you can wait, I would think your best bet would be to spend a couple of hours allowing the users here to help you to cleanup your problem and get you on your way with Ubuntu.

Of course the decision is up to you.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by beew on 2010-11-22
> **ByteOneZero said:**
> thank you Matt for your time and effort.i did as you suggested but when i pressed ctrl+x nothing happened except a dull thudding sound.i tried again and a terminal message said y or n ,i forget the true instruction but i clicked n and terminal went blank except for the original message sudo nano ....etc.i told you i was a dummy when geekspeak is involved.i hate to do it but i think ill wipe my hd and install a copy of win 7 so i can use my pc.can you tell me if a wipe is e z to do? thanks for the effort.

Instead of using nano to edit your sources list just use gedit instead, much more intuitive.

in the terminal type 

```
sudo gedit /etc/apt/sources.list 
```When the sources list appears just delete the offending lines and  click save then close it. It is very easy, no obscure key combinations to do simple things like nano or worse, vi(i don't see the point of commenting them out, as they are the wrong repositories for Lucid anyway)

---

### Post by apollothethird on 2010-11-22
> **ivanovnegro said:**
> I understand you and I agree. But it seems that he will already go back to Win7 because [color=green]**he could not edit his sources list with Nano.**[/color]
I admit it was a little bit too fast to advice a new install but with the help of this forum I expected it would not be a great deal.

Kind of my point exactly.  He's having problems with very simple commands and steps.  I believe he'd still have the same problems if he started over.  There will be occasions to describe steps or make some changes.  He probably might as well become familiar with them from where he happens to be.

I'm glad to see we are on a similar page.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by uRock on 2010-11-22
> **ByteOneZero said:**
> thank you Matt for your time and effort.i did as you suggested but when i pressed ctrl+x nothing happened except a dull thudding sound.i tried again and a terminal message said y or n ,i forget the true instruction but i clicked n and terminal went blank except for the original message sudo nano ....etc.i told you i was a dummy when geekspeak is involved.i hate to do it but i think ill wipe my hd and install a copy of win 7 so i can use my pc.can you tell me if a wipe is e z to do? thanks for the effort.
I have Windows 7 Professional on 2 of my machines. The install process is super easy. Windows is also has very good drivers that will work decent enough while you download the drivers for W7 from you hardware manufacturers, which is the most time consuming part of the process.

I do encourage you to figure out the problems with ubuntu on your machine. Ubuntu is a great tool for many people and I'd like to see it work well for you.

To add the # signs to the lines with Jaunty on them and find out if it is the culprit ausing problems, then open you sources list with gedit, which is a lot like Windows Notepad. Here is the command to open your sources list in gedit. ```
sudo gedit /etc/apt/sources.list
``` Just put a # sign in front of those two lines, then click on the save button in the top panel of the window.

There is another way to turn off those two repos. You can go in your menus to System> Administration> Software Sources and in Other Software tab you should see the two Jaunty entries. Uncheck them and let it reload. [SIZE=1][COLOR=Gray](I would throw in a screenshot of the Software Sources window, but I am using W7 at the moment.[/COLOR][/SIZE][COLOR=Gray])[/COLOR] We'll see what happens from there.

---

### Post by ivanovnegro on 2010-11-22
> **uRock said:**
> 

There is another way to turn off those two repos. You can go in your menus to System> Administration> Software Sources and in Other Software tab you should see the two Jaunty entries. Uncheck them and let it reload. [SIZE=1][COLOR=Gray](I would throw in a screenshot of the Software Sources window, but I am using W7 at the moment.[/COLOR][/SIZE][COLOR=Gray])[/COLOR] We'll see what happens from there.

That was really the best suggestion, the graphical way, its so easy.
Sometimes we forget these things.

---

### Post by apollothethird on 2010-11-22
> **ivanovnegro said:**
> That was really the best suggestion, the graphical way, its so easy.
Sometimes we forget these things.

I didn't think of that because, while I've seen it as a suggestion a few times, I have yet to have it available in any of my Ubuntu 10.10 installations.  It appears to be a great feature that was dropped, or maybe there is a different way to get to it that I don't know of.

The only menus under System -> Administration -> on my system that start with an "S" are:

[INDENT]Startup Disk creator
Synaptic Package Manager
System testing
[/INDENT]

Most likely this Software Source was replaced by the Synaptic Package Manager, I tried to use it to add a sour> ce in the past but couldn't figure out how to do it.  If this is the place for adding sources to the list, can someone tell me how to add a source.  I have had to use a text editor in the past.  If would like to be able to share the convenience of the graphics option when helping others if it's possible.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by ivanovnegro on 2010-11-22
> **apollothethird said:**
> I didn't think of that because, while I've seen it as a suggestion a few times, I have yet to have it available in any of my Ubuntu 10.10 installations.  It appears to be a great feature that was dropped, or maybe there is a different way to get to it that I don't know of.

The only menus under System -> Administration -> on my system that start with an "S" are:[INDENT]Startup Disk creator
Synaptic Package Manager
System testing
[/INDENT]Most likely this Software Source was replaced by the Synaptic Package Manager, I tried to use it to add a source in the past but couldn't figure out how to do it.  If this is the place for adding sources to the list, can someone tell me how to add a source.  I have had to use a text editor in the past.  If would like to be able to share the convenience of the graphics option when helping others if it's possible.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

You are right, it seems there was a change, for now on 10.10. you have to go to System->Administration->"System Update" (dont know how it is in English)->Preferences->Other Software. Thats it.

Edit: I could make also a screenshot but it would appear in German as Im working in Germany and using the German layout.

---

### Post by apollothethird on 2010-11-22
> **ivanovnegro said:**
> You are right, it seems there was a change, for now on 10.10. you have to go to System->Administration->"System Update" (dont know how it is in English)->Preferences->Other Software. Thats it.

Edit: I could make also a screenshot but it would appear in German as Im working in Germany and using the German layout.

Thanks, Ivanovnegro.  I found it.  This might be useful for this user.  I don't see a reference to his Ubuntu version, but it's likely that it's 10.10.

This option to add/edit the sources is (Ubuntu 10.10):

System -> Administration -> Update Manager -> Settings -> Other Software.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by ivanovnegro on 2010-11-22
> **apollothethird said:**
> Thanks, Ivanovnegro.  I found it.  This might be useful for this user.  I don't see a reference to his Ubuntu version, but it's likely that it's 10.10.

This option to add/edit the sources is (Ubuntu 10.10):

System -> Administration -> Update Manager -> Settings -> Other Software.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

He is running Lucid I think because I saw his sources list, it appeared Lucid there.

---

### Post by magnatron on 2010-11-22
> **apollothethird said:**
> I didn't think of that because, while I've seen it as a suggestion a few times, I have yet to have it available in any of my Ubuntu 10.10 installations.  It appears to be a great feature that was dropped, or maybe there is a different way to get to it that I don't know of.

The only menus under System -> Administration -> on my system that start with an &quot;S&quot; are:[INDENT]Startup Disk creator
Synaptic Package Manager
System testing
[/INDENT]Most likely this Software Source was replaced by the Synaptic Package Manager, I tried to use it to add a source in the past but couldn't figure out how to do it.  If this is the place for adding sources to the list, can someone tell me how to add a source.  I have had to use a text editor in the past.  If would like to be able to share the convenience of the graphics option when helping others if it's possible.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

On synaptic it's settings, repositories then other software, but I think your far better doing it with APT as it makes it far easy to enroll the PPA or Repo GPG keys with apt-get add key etc

Even if he did manage to install the Jaunty repo for that build which is covered on the help page I think he would have still had synaptic throw up an error about missing GPG keys and it seems the jaunty repo wasnt really the one he wanted in the first place just MakeMKV on the other site, I was interested to notice blue-ray is mostly DRM I didnt know that, first time trying to help someone setup there blue-ray but as he's not familiar with the command line or doing things from the shell, getting it to work must seem like a very difficult task indeed.

What you really need at ByteOneZero is the Book Teach Yourself Unix in 24 Hours, Unix & Linux are very similar and it sounds like your not familiar with navigating your way around comfortably in the shell. Using the command cd for instance will change directories and the command pwd will print the directory your in. Everything branches down from the root directory, think of it as a tree with branches growing from it's roots, so cd / would take you to the root of that tree.

Commands you need to get familiar with are: cd, ls, pwd treat them as baby steps.

Most of the guys trying to help you on here with the exception of myself probably use Ubuntu Server which doesn't even have a GUI - graphical user interface. They probably don't want one as the command line is all you really need.  Once you get used to the command line, then you can start thinking about your GUI, some of the GUI's available are awesome to look at once they've been skinned and themed, fluxbox, xfce, lxde or even just OpenBox which when seen is just a wallpaper with no visible icons on the desktop at all!

@ByteOneZero;

Because Blue-Ray is DRM (digitally rights managed) the problem your getting is because it was never designed to be compatible with linux the MakeMKV is a work around to stream blue-ray into VLC which then allows you to watch your movie, I saw one website advising most Linux users to boycott Blue-Ray because of the way it's been designed from the ground up to lock you into one solution. Microsofts!  From Byte (tenzo's) silence one can only presume thats another victory for the evil mega-corporation "you will use windows seven muhahahah!"

**Note to Mod** Can we change thread title to: 
"I binned & hosed my Ubuntu FOSS installation because my proprietary hardware would not kowtow without MPAA cRaZy EvIL CrAcK!"

---

### Post by ByteOneZero on 2010-11-22
gedit didit.i am at least back to square one,thanks to this helpful community.now i will try to get professional advice to play blu ray for backup on dvd5.happy computing to all

---

### Post by ivanovnegro on 2010-11-22
> **ByteOneZero said:**
> gedit didit.i am at least back to square one,thanks to this helpful community.now i will try to get professional advice to play blu ray for backup on dvd5.happy computing to all

Oh man, thats great!!!
Im glad you are back:D.
Ask whatever you want, you see it works.

---

### Post by apollothethird on 2010-11-22
> **ByteOneZero said:**
> gedit didit.i am at least back to square one,thanks to this helpful community.now i will try to get professional advice to play blu ray for backup on dvd5.happy computing to all

Hi, ByteOneZero.  Glad you got that part resolved.  Did you try some of the suggestions for resolving the Blu-Ray player problems such as the one giving by Magnatron:

[http://ubuntuforums.org/showpost.php?p=10145547&postcount=4](http://ubuntuforums.org/showpost.php?p=10145547&postcount=4)

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by matt_symes on 2010-11-22
Hi

I'm glad to hear its fixed.

For XBMC on 10.04 read this

[http://www.unixmen.com/linux-distributions/4-ubuntu/996-install-xbmc-media-center-on-ubuntu-1004-lucid-lynx](http://www.unixmen.com/linux-distributions/4-ubuntu/996-install-xbmc-media-center-on-ubuntu-1004-lucid-lynx)

So what is the problem with your blue ray?

Kind regards

---

### Post by magnatron on 2010-11-22
@ ByteZero glad to hear you resolved it, linux is way cooler than windows, I can walk you through getting your blue-ray to work.  Open Synaptic and in the search bar look for:  nautilus-open-terminal  install that, then follow the instructions on this page until it comes to the point about extracting the files, move both copies of the downloaded *.tar.gz files into an empty folder, right click them and press extract all to here.  then navigate to those two folders inside the file manager (nautilus) and right click and you can get inside those folders that you've extracted them into with the terminal. 

The linux release includes full source code for MakeMKV GUI, libmakemkv  multiplexer library and libdriveio MMC drive interrogation library. You need to follow the steps outlined below to compile and install the  application and all libraries.
Download binary and source packages:

[U][http://www.makemkv.com/download/makemkv_v1.6.2_bin.tar.gz](http://www.makemkv.com/download/makemkv_v1.6.2_bin.tar.gz)
[http://www.makemkv.com/download/makemkv_v1.6.2_oss.tar.gz](http://www.makemkv.com/download/makemkv_v1.6.2_oss.tar.gz)
[/U]
Make  sure you have all required tools and libraries installed. You'll need  GNU compiler and linker and header and library files for following  libraries: glibc, openssl-0.9.8, zlib, qt4. You may use the following  command to install all prerequisites on debian-based system like ubuntu:
```
[URL="http://www.makemkv.com/forum2/viewtopic.php?f=3&t=224#"]
[/URL]sudo apt-get install build-essential libc6-dev libssl-dev libgl1-mesa-dev libqt4-dev
```Unpack both packages and starting from source package do the following steps for each package:
```
[URL="http://www.makemkv.com/forum2/viewtopic.php?f=3&t=224#"]
[/URL]make -f makefile.linux
sudo make -f makefile.linux install
```The application will be installed as "/usr/bin/makemkv".


[LIST=1]
[*]Run the application /usr/bin/makemkv by typing that at the command line as makemkv & or the full path /usr/bin/makemkv &
[*]Go to File, Open Disc > Select your Blu-Ray drive
[*]Once MakeMKV finishes opening the blu-ray disc, it will list the titles and file information
[*]Go to File menu and choose "Stream"
[*]MakeMKV will  look like "Buffer State" and "File Position" are  stuck, but look in the dialog box at the beginning for something similar  to: "Operation sucessfully completed. Streaming server started.
[/LIST]

[LIST=1]
[*]Open VLC and go to Media, Open Network Stream
[*]Protocol should HTTP, in the address box put [http://localhost:51000/stream/title0.ts](http://localhost:51000/stream/title0.ts)  The port option should be greyed out.
[*]Click Play and enjoy your blu-ray movies within Linux
[/LIST]
Tada! ;)

P.S: the & command on the end of the command will cause it to spool as a Job so it wont close when you shut the terminal window or press Ctrl+C
P.P.S: if you dont have VLC it's in synaptic & if it asks you for a port number its 51000 ;)

N.B: The link on the Ubuntu Official Help page that leads to the MakeMKV files is way out of date, those links are now hosted on the MakeMKV forum.
Sadly I could not locate the MakeMKV changelog so you never know as it's gone from version 1.4 to version 1.6 if it still works the same way or if you just have to click play and regretfully I don't own a blue-ray (yet) to test it out myself.

---

### Post by ByteOneZero on 2010-11-22
thank you magnatron.i have been working this blu ray thing for 3 wks now.i found several people who have played blu ray on lucid.ive watched on you tube ,ive followed the instructions that you posted 2 wks ago but im such a nuts and bolts dope that the lingo is like trying to read greek to me.i dont understand half of the instructions youve pasted in the post starting with :librarys and i had makemkv 1.6.2 but i trashed it.i was hoping to not purchase software if i cant run it.it was so easy to back up dvds and blu rays in windows i just cant understand why this is so difficult to do in ubuntu.i am going to take a break from this to cool down and watch a movie then ill try your instructions one more time.again i think its awesome that you even bother with a dope like me.

---

### Post by magnatron on 2010-11-23
Dude, I was in your shoes once. We all have to start somewhere it took me 6 years until I was comfortable with Linux and I jumped in the deep end and just removed my XP installation and never looked back. I borked and killed my own system many a time with graphics driver updates etc, believe me I've started from scratch more than once! lol

If your like me, you'll find you cant resist the temptation to fiddle with some setting somewhere just to see what it does.

I've even completely cut myself off the internet before by installing a firewall switching it on and then suddenly realized that because I hadn't taken time to configure it, no internet! lol

Ubuntu has not been my first choice, slackware was, later BSD, Ubuntu is actually twice as user friendly than either of those.

A YAST installer can be nasty, because it's all in the terminal window going, would you like to configure your gateway and internet settings now, invariably you click yes and the questions it used to ask, used to drive me around the twist!

Things like: PARTITION SIZES (On BSD thats SLICES), HOSTNAME, GATEWAY, DNS SERVER; if your a novice that stuff is all alien lingo!

The bit that always used to catch me out was *Slackware* provides more than a dozen precompiled *kernels - So your left thinking which one of these is the one I want?*

Having a Major search engine is a big plus, when you get stuck you can find helpful places like this with other people that have been in the same boat. ;)

[IMG]http://www.zisman.ca/ubuntu/Terminal1.jpg[/IMG]

Thats the little fellow you need to learn your way around in, all the magic of installing stuff you cant find in Ubuntu, of which there isn't much, but there are some things as you are discovering that have to be installed from there.

On your ubuntu desktop its in Applications --> Accessories --> Terminal

Open that up and tryout the command: cd to try and navigate your way around and it'll all start to make sense ;)

Do the command ls - first to list files or for more human readable output that would be ls -l, now for something funky, try ls -lRt small L big R.

The big R means it's recursive so it'll list all the subfolders in that directory. But the same command ls -lrt with small R is totally different, mind blowing stuff eh, to navigate it would be cd Downloads and commands get funkier as time goes by! Everything in the entire system can be controlled from that tiny window!

When you use the command sudo before another command you are telling the system you want to use FULL AUTHORITATIVE PRIVILEGES as the SU - Super User.

When doing so it will prompt you for your password, just like synaptic which executes gksudo when it opens. For a comprehensive guide check out this very informative page:  [http://spacers.lowtech.org/wiki/doku.php/shellstuff/shellstuff](http://spacers.lowtech.org/wiki/doku.php/shellstuff/shellstuff)

---

### Post by uRock on 2010-11-23
The best piece of advice I read in my Intro to Linux class was to always make a backup of a config file before making changes. This way if you mess something up you can replace the broke config with the working config file and be back up and running.

---

### Post by magnatron on 2010-11-23
True @ uRock or be very sure you know what the setting in the config file does before you change it so you know how to change it back. The GUI runs on tty7. However there are 6 other consoles open which run only a shell.   People can do this by pressing Ctrl-Alt-F2 just remember that Ctrl-Alt-F7 changes it back!

---

### Post by ByteOneZero on 2010-11-23
i am still plugging away.i didnt bare my soul completely to you guys.and magnatron you are sooo cool about this stuff.today i went whole hog to actually use terminal to encode an avi. file.i also got winff to encode a dvd.i cant seem to burn it to a dvdr yet but hey its on the hd.i am also going to do some hard drive gymnastics(see my thread if your interested),very soon.playing blu ray on xmbc player is definitely possible.you can watch a guy do it on youtube,but i cant find the plugins.thanks again for being on this forum.

---

