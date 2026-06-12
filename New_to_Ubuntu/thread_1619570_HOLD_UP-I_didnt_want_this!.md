---
title: "HOLD UP-I didnt want this!"
date: 2010-11-11
forum: New to Ubuntu
---

### Post by Grey Aspire on 2010-11-11
[I]I did the following command to download a program called "conky" to my computer, to allow for system monitoring.

sudo apt-get install conky

I then hit "y" (yes) to allow...All of a sudden I have programs like:
Konsole
Kwalletmanager
Amarok 
Kaddressbook

As well as other programs starting with a large K.

I simply wanted a ****ing system monitor, why in hell did this download? And how can I get it the hell off!
[/I]

---

### Post by c2tarun on 2010-11-11
> **Grey Aspire said:**
> [I]I did the following command to download a program called "conky" to my computer, to allow for system monitoring.

sudo apt-get install conky

I then hit "y" (yes) to allow...All of a sudden I have programs like:
Konsole
Kwalletmanager
Amarok 
Kaddressbook

As well as other programs starting with a large K.

I simply wanted a ****ing system monitor, why in hell did this download? And how can I get it the hell off!
[/I]

bad things first: nobody here forced u to install conky so please stop using foul language here.

if apt-get is installing those packages they must be the dependencies for conky, dont worry go to the terminal and type conky ur application will start.

---

### Post by Grey Aspire on 2010-11-11
Editing- Because people **** me off.

---

### Post by DangerOnTheRanger on 2010-11-12
*cough* one little problem - He's the guy who can give you the answer.
Since he is, you should respect him, and every one else, or he might not give you an answer...

And I personally agree with him - no situation is bad enough for foul language.

---

### Post by Grey Aspire on 2010-11-12
You've never been in detroit then. :)
I'll just google it.

---

### Post by wirelessmonkey on 2010-11-12
I use aptitude instead of apt-get, but 

```
 sudo aptitude purge conky 
``` 
should work.

---

### Post by endotherm on 2010-11-12
well, if conky refered to the kde libraries, then all you need to do is remove conky, and then run
```

sudo apt-get purge conky
sudo apt-get autoremove
```

autoremove uninstalls any packages not explicitly installed and no longer depended on by any other installed package.

conky did not have any KDE dependencies on my system, per synaptic, and when I installed it just a second ago, it required only libiml2 or some such. if apt-get autoremove does not get rid of the offending packages, then they came with another app. I usually get them on any system on which I install stellarium (or was it celestia? one of them...).

---

### Post by Grey Aspire on 2010-11-12
> **endotherm said:**
> well, if conky refered to the kde libraries, then all you need to do is remove conky, and then run
```

sudo apt-get purge conky
sudo apt-get autoremove
```autoremove uninstalls any packages not explicitly installed and no longer depended on by any other installed package.

conky did not have any KDE dependencies on my system, per synaptic, and when I installed it just a second ago, it required only libiml2 or some such. if apt-get autoremove does not get rid of the offending packages, then they came with another app. I usually get them on any system on which I install stellarium (or was it celestia? one of them...).
I'm getting programs like:
Konsole
Kpakagekit
Krfb
Ksystemlog
Konqeror
Kopete
Kppp
Krdc
Ktorrent

I didnt want these! Among many other programs!
All of a sudden I have programs I -did not want-, and this is the very same reason I left Windows, I dont want that again.


Ran autoremove, and got nothin'.

---

### Post by endotherm on 2010-11-12
> **Grey Aspire said:**
> I'm getting programs like:
Konsole
Kpakagekit
Krfb
Ksystemlog
Konqeror
Kopete
Kppp
Krdc
Ktorrent

I didnt want these! Among many other programs!
All of a sudden I have programs I -did not want-, and this is the very same reason I left Windows, I dont want that again.

if you removed conky, and then ran autoremove, then conky wasn't the application that installed all those extra components. what else have you installed recently? anythign that starts with a 'K'?

those programs are all part of the KDE desktop environment. somthing you installed was designed to be run on a KDE system like Kubuntu, rather than a GNOME system like ubuntu. the program you installed, required a KDE library, so it installed it. that KDE library required other KDE packages, so in the end, you end up with all those extra components. as I said, there are a couple apps I've tried that do the same. you have a simple choice; uninstall the offending app, or just ignore it. they won;t hurt anything, and you could probably remove a lot of them via synaptic or whatever if you want.

---

### Post by Grey Aspire on 2010-11-12
> **endotherm said:**
> [SIZE=7][COLOR=black]Kubuntu[/COLOR][/SIZE]



Oh for the love of-
I completely forgot I installed that thing.
-face to palm-
Alright...whats the sudo command to uninstall anything Kubuntu...?
Anyways, I thought when I downloaded that thing, it'd act like a second OS, at least that was my thought on download, not download a bunch of stuff into my Ubuntu setup.

---

### Post by endotherm on 2010-11-12
just to clarify, you are running ubuntu, and the kde libraries got accidentally installed, right? these instructions will be diasterous if you are actually running kubuntu.  

it kinda depends on how you installed it, but if you installed the top level metapackage, it would be:
```

sudo apt-get purge kubuntu-desktop 
sudo apt-get autoremove

```if it says that kubuntu-desktop is not installed, then I would go through software-center or synaptic, and filter on installed packages, and try to sort out what you explicitly installed. if you remove whatever you told it to install, and then autoremove, you should be good.

---

### Post by Grey Aspire on 2010-11-12
> **endotherm said:**
> it kinda depends on how you installed it, but if you installed the top level metapackage, it would be:
```

sudo apt-get purge kubuntu-desktop 
sudo apt-get autoremove

```if it says that kubuntu-desktop is not installed, then I would go through software-center or synaptic, and filter on installed packages, and try to sort out what you explicitly installed. if you remove whatever you told it to install, and then autoremove, you should be good.
And this is why I ****ing love forums.
Thank you.
Jeez, I really need to examine what I download sometimes. I had installed Kubuntu at night and went to bed right after not thinking about it.
Then you say KDE and it hits me.
Thanks mate.

---

### Post by Grey Aspire on 2010-11-12
To clarify, my apologies to anyone insulted by my language. Yet again I must say..words only hold as much power as they are given by the listener. If you find my language insulting, then simply PM me. Don't make it a public deal.
My computer is the one place I get angry at most. Why? I've dealt with a shoddy windows OS that I recently completely ditched, and moved to Linux. To find something going wrong on day two makes me panic, and when I panic I get angry, when I'm angry, I swear. My apologies.
Grey.

---

### Post by ndefontenay on 2010-11-12
Just in case you end up with a black screen with a flashing cursor by removing this,

you can always re install kde or gnome by typing 

sudo apt-get install gnome

if gnome does not exists for ubuntu,

do sudo apt-get install gnome*
you'll have a huge list, review it, find the relevant package (could be gnome-ubuntu or something like that)

then ctrl + c to stop the command

then sudo apt-get install gnome-whateveryou'vefound

or go on internet, find the proper package to install before you do something dangerous.

Apologies accepted. It takes courage too.

---

### Post by ndefontenay on 2010-11-12
oh yeah if you get the back screen with just a command line

log in with your username password

then 
sudo apt-get install ubuntu-desktop

that should fix it.

---

