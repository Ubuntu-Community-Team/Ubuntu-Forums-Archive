---
title: "my two questionss"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by kimikrishna on 2008-12-29
I am new to ubuntu [and linux os]

my knowledge on ubuntu is ZERO..

what i know is only windows..

I know with windows 95, later 98 , Me, nt then xp and now windows vista..

I have a few questions to ask :
________________________________
> 1) how to install a software ..  (i know to find a EXE file and run it..
press next > next > next >...........>finish... in windows ) 

i googled.. and learnt synaptic package manager.. I opened it and used the search box.. i downloaded a tar.gz file.. opened and extracted it to desktop.... but this is not showing in search results/// and i found no way to open that :confused: from synaptic..

________________________________
```
2) whenever i shutdown, orange colored bar fills and later a BLACK SCREEN appears with a HYPHEN in it [keeps blinking] and my cpu is not off :(

how to shutdown then ?? and switch power off then ??

I INSTALLED UBUNTU INSIDE WINDOWS !!!!!!
```

hope someone can help// I do not know where to post these questions.. so i posted here.. sorry if i made mistake..

---

### Post by taurus on 2008-12-29
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Sealbhach on 2008-12-29
If you use Synaptic Package Manager or the Add/Remove feature, you only need to select the pakages you want by ticking the box on the left of each one. 

The download and installation will all happen automatically, you don't have to do anything and you don't have to download a tar.gz unless the package is not present in Synaptic.

What are you trying to install?


.

---

### Post by northern lights on 2008-12-29
> **kimikrishna said:**
> press next > next > next >...........>finish
In GNU/Linux, there ain't no repetitive "Next". Fortunately.

Check [this tutorial for the absolute beginner]("http://www.psychocats.net/ubuntu/installingsoftware").

---

### Post by albinootje on 2008-12-29
> **kimikrishna said:**
>  i googled.. and learnt synaptic package manager.. I opened it and used the search box.. i downloaded a tar.gz file.. 

Others already gave you some webpages to read.
I'd like to add that downloading .tar.gz files is the last thing you should do right now.
First learn about using Synaptic Package Manager, and learn the basics of Ubuntu.

Have fun!

---

### Post by oldos2er on 2008-12-29
Synaptic (and every other package manager in Ubuntu) doesn't "see" files on your desktop, it only looks to Ubuntu's repositories for packages (one of which could be the Ubuntu LiveCD; see System, Administration, Software Sources).

---

### Post by kimikrishna on 2008-12-29
> **Sealbhach said:**
> If you use Synaptic Package Manager or the Add/Remove feature, you only need to select the pakages you want by ticking the box on the left of each one. 

The download and installation will all happen automatically, you don't have to do anything and you don't have to download a tar.gz unless the package is not present in Synaptic.

What are you trying to install?


.

I tried to download transconnect from a automatic bookmark  from fsf org...

its not in synaptic.. i extracted it... how do i open this with synaptic ?????
___________________________

+ no one gave me an answer for SHUTDOWN problem... I AM very new to ubuntu/// I feel like eyes tied and sent in to a dark forest..

HELP "SHUTDOWN" did anyone read this ? :confused:

---

### Post by handydan918 on 2008-12-29
> **kimikrishna said:**
> I tried to download transconnect from a automatic bookmark  from fsf org...

its not in synaptic.. i extracted it... how do i open this with synaptic ?????
___________________________

+ no one gave me an answer for SHUTDOWN problem... I AM very new to ubuntu/// I feel like eyes tied and sent in to a dark forest..

HELP "SHUTDOWN" did anyone read this ? :confused:
Installing Ubu inside windows (wubi) is the worst idea to come out of canonical. It causes more problems than...well, windows. All it is intended for is as a test platform to see if you want to install it. It is in no way the same as a "real" partitioned installation of Ubu.
Recommend you uninstall and look up your friendly neighborhood linux-geek (google for LUG -Linux user group)
or take the plunge and do a dual boot setup yourself.  Wubi doesn't rock, IMO.

---

### Post by igknighted on 2008-12-29
.tar.gz files are like zip files... they are compressed archives.  You should right click -> extract to extract the file, then read the instructions in the INSTALL file.  You need to compile it yourself, but its just two simple commands (see the install file).  The CONFIGURE file will tell you how to use it.  This is a CLI program, you won't have a GUI to use.

---

### Post by cabbiinc on 2008-12-29
>  2) whenever i shutdown, orange colored bar fills and later a BLACK SCREEN appears with a HYPHEN in it [keeps blinking] and my cpu is not off :(

how to shutdown then ?? and switch power off then ??

I INSTALLED UBUNTU INSIDE WINDOWS !!!!!!

hope someone can help// I do not know where to post these questions.. so i posted here.. sorry if i made mistake..

I'm pretty new to this myself, but if your Wubi is installed within Windows, then wouldn't you need to shut down Windows from the Windows interface?

Win key to get the start menu then shut down from there.

Just a thought.

---

### Post by antmenj on 2008-12-29
Don't throw away windows straight off but I would recommend doing a proper install to get used to it for starters.

I don't know about wubi but in real ubuntu you just click the red power icon and select shutdown.  There is a shutdown bug in hardy but its easy fixed with one line of text in 1 file.  If you choose not to fix it all it means is you have to push the power button at the end.

Shut down is as easy as ---> see attached screen shot.

---

### Post by hyper_ch on 2008-12-30
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by kimikrishna on 2008-12-30
> **igknighted said:**
> .tar.gz files are like zip files... they are compressed archives.  You should right click -> extract to extract the file, then read the instructions in the INSTALL file.  You need to compile it yourself, but its just two simple commands (see the install file).  The CONFIGURE file will tell you how to use it.  This is a CLI program, you won't have a GUI to use.


well, teach me how to install that..

i double clicked install file... It opened..

i didnt install anything ?????????

teach me how to install that ???????

and do not give any links

---

### Post by kimikrishna on 2008-12-30
> **antmenj said:**
> Don't throw away windows straight off but I would recommend doing a proper install to get used to it for starters.

I don't know about wubi but in real ubuntu you just click the red power icon and select shutdown.  There is a shutdown bug in hardy but its easy fixed with one line of text in 1 file.  If you choose not to fix it all it means is you have to push the power button at the end.

Shut down is as easy as ---> see attached screen shot.


I know to shutdown..........

:X :X :X x-( 

when i shutdown a  black screen appears with a blinking hypen...

do not teach me how to shutdown with screen shots

---

### Post by ubersolid on 2008-12-30
Installing software:

First search for it, it is probably in the repositories:
```
aptitude search *programname*
```

Installation:

```
sudo aptitude install *packagename*
```


Removing software:

```
sudo aptitude remove *packagename*
```

Shutting down:

```
sudo shutdown -h now
```
this will power off immediately!

Rebooting:

```
sudo reboot
```

These should all be entered in the Terminal, which you will find in the *Applications -> Accessories menu.*

Hope this is some help to you, best would be if you read the links you were pointed to.

---

### Post by albinootje on 2008-12-30
> **kimikrishna said:**
> I tried to download transconnect from a automatic bookmark  from fsf org...

its not in synaptic.. i extracted it... how do i open this with synaptic ?????


You mean this one :
[http://directory.fsf.org/search/?query=transconnect](http://directory.fsf.org/search/?query=transconnect)

I just looked at the tar.gz ; it's from 2002, that means it's unlikely that you will manage to compile and install it.
Try to find an application through add/remove or Synaptic package manager which is alike.

---

### Post by BatsotO on 2008-12-30
One thing to clarify this install  issue, while windows use exe, ubuntu preferably use deb. When there's deb version of an application, there's no need to use tar.gz or anything else. 
As with tar.gz you can read the readme file.

---

