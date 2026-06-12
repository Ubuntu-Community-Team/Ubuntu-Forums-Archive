---
title: "where can I get opera?"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by fillintheblank on 2008-12-05
where can i download opera?

---

### Post by adult swim on 2008-12-05
[http://www.opera.com/browser/download/](http://www.opera.com/browser/download/)

---

### Post by sandy8925 on 2008-12-16
You could also try:

sudo apt-get install opera

---

### Post by clive littlewood on 2008-12-16
Hi

Just go to the Opera.com website.

Press the dowload button (it will detect you are using Linux)

Then choose your flavour of Ubuntu.

This will download a .deb file

Double click on the downloaded deb and it will install.

Thats It !!!!!!!!!!!!   :p

Clive

---

### Post by howefield on 2008-12-16
> **sandy8925 said:**
> You could also try:

sudo apt-get install opera

Don't think that'll do any good. :lolflag:


Opera isn't in the repository, that I can see anyway.

Dapper used to have it, but not sure when it was dropped.7



[http://www.ubuntu.com/news/opera9](http://www.ubuntu.com/news/opera9)

---

### Post by Ericthegreat on 2008-12-16
Cause Firefox > All.

---

### Post by Tatty on 2008-12-16
What... why did opera get removed from the repos?

Anyhow, i found this [https://help.ubuntu.com/community/OperaBrowser](https://help.ubuntu.com/community/OperaBrowser)

---

### Post by philinux on 2008-12-16
It's vanished from Intrepids partner repo.

---

### Post by frankleeee on 2008-12-16
Add the lenny deb to software sources and run the key add then do a sudo apt-get install opera.
[http://deb.opera.com/](http://deb.opera.com/)

---

### Post by scorp123 on 2008-12-16
You can add the Opera repository ....

[LIST]
[*]Temporarily become "root" and create a file: /etc/apt/sources.list.d/opera.list (if it asks for a password: that's your own password!):
[INDENT]Command for GNOME users (Ubuntu):
```
gksudo gedit /etc/apt/sources.list.d/opera.list
```

Command for KDE users (Kubuntu):
```
kdesu kate /etc/apt/sources.list.d/opera.list
```

Possible commands to do it right there in the terminal, e.g.:
```
sudo nano /etc/apt/sources.list.d/opera.list
sudo pico /etc/apt/sources.list.d/opera.list
sudo vim /etc/apt/sources.list.d/opera.list 
```
[/INDENT]
[*]Fill in this as content of the file (copy & paste please):
[INDENT]```
deb http://deb.opera.com/opera etch non-free
```[/INDENT]
[*]Then go to the terminal and get the key:
[INDENT]```
wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
```
[/INDENT][*]Update your software package list:
[INDENT]```
sudo apt-get update
```[/INDENT]
[*]Install Opera (current version as of this writing is: 9.63.2474):
[INDENT]```
sudo apt-get install opera
```[/INDENT]
[*]Voila, done. You should find an Opera icon here: Applications > Internet > Opera
[/LIST]

---

### Post by kansasnoob on 2008-12-16
> **adult swim said:**
> [http://www.opera.com/browser/download/](http://www.opera.com/browser/download/)

Why make it difficult? The link provided here works just fine!

If you're using Firefox with the default settings it'll use the .deb installer and it's just like falling off a log!

You can get it thru Medibuntu but it's outdated!

---

### Post by jerome1232 on 2008-12-16
> **scorp123 said:**
> You can add the Opera repository ....

[LIST]
[*]Temporarily become "root" and create a file: /etc/apt/sources.list.d/opera.list (if it asks for a password: that's your own password!):
[INDENT]Command for GNOME users (Ubuntu):
```
gksudo gedit /etc/apt/sources.list.d/opera.list
```

Command for KDE users (Kubuntu):
```
kdesu kate /etc/apt/sources.list.d/opera.list
```

Possible commands to do it right there in the terminal, e.g.:
```
sudo nano /etc/apt/sources.list.d/opera.list
sudo pico /etc/apt/sources.list.d/opera.list
sudo vim /etc/apt/sources.list.d/opera.list 
```
[/INDENT]
[*]Fill in this as content of the file (copy & paste please):
[INDENT]```
deb http://deb.opera.com/opera etch non-free
```[/INDENT]
[*]Then go to the terminal and get the key:
[INDENT]```
wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
```
[/INDENT][*]Update your software package list:
[INDENT]```
sudo apt-get update
```[/INDENT]
[*]Install Opera (current version as of this writing is: 9.63.2474):
[INDENT]```
sudo apt-get install opera
```[/INDENT]
[*]Voila, done. You should find an Opera icon here: Applications > Internet > Opera
[/LIST]

Thank you for that repo info, and actually having a repo makes it less difficult, as this helps you keep your program up to date (opera will be updated every day just like the rest of your system this way)

edit: if you go here [http://www.opera.com/support/kb/view/841/](http://www.opera.com/support/kb/view/841/) they show you how to get a gpg key as well so it's signed.

---

### Post by scorp123 on 2008-12-17
> **jerome1232 said:**
> edit: if you go here [http://www.opera.com/support/kb/view/841/](http://www.opera.com/support/kb/view/841/) they show you how to get a gpg key as well so it's signed. See my instructions again. I do the same in one single easy line of code ;)

---

### Post by scorp123 on 2008-12-19
> **kansasnoob said:**
> Why make it difficult? The link provided here works just fine!  And that link will also automatically inform you if there is a new version out? It will also automatically download the newest version for you when you update your system?

No it won't. If you just use a link and download a program manually then it is your responsibility to check for updates and to keep the software in question updated .... and that kinda sucks. The reason why package managers were created is exactly this so that we users don't have to bother about such things.

So if there is a repo I'd suggest that people make use of it. The little bit of "complication" and "difficulty" is worth it: once you have added the software repository to your system your package manager will handle the software updates, and you can use your free time for other things (instead of having to surf the web and manually find out if there are updates or not ... )

> **kansasnoob said:**
>  You can get it thru Medibuntu but it's outdated! You can get it from Opera's repos directly and it's as fresh and up-to-date as it can be. :D

---

### Post by jerome1232 on 2008-12-19
> **scorp123 said:**
> If you just use a link and download a program manually then it is your responsibility to check for updates and to keep the software in question updated .... and that kinda sucks. The reason why package managers were created is exactly this so that we users don't have to bother about such things.


+ 1, there's not a piece of software on my computer that doesn't come from a repository, I don't have to even think about updating anything.

I didn't even see the part of your post that tells you how to get the gpg key lol, selective reading is bad ;)

---

### Post by scorp123 on 2008-12-19
> **jerome1232 said:**
> I didn't even see the part of your post that tells you how to get the gpg key lol, selective reading is bad ;) Don't worry :D

What really puzzles me is why Opera's description (the one you linked to) on how to get the GPG key is so complicated? My method is one short line and it gets the job done (easy: copy & paste ...), whereas their's is like three lines and unnecessarily complicated ... oh well. :)

---

### Post by Georgia boy on 2008-12-19
Jerome1232 made the comment about not having to worry about software being updated by using the repositories. Does that include the updates for things like OpenOffice.org? 

I mean like when they come out with their security updates, not going to the 3.0. Games etc get updated too?

Got kind of confused on that comment.
Thanks
Tom

---

### Post by AlanR8 on 2008-12-19
Am running KUBUNTU 8.1 with KDE 4.2 Beta. Nice by the way.

But today, an update totally borked FireFox for some reason. As a workaround I downloaded Opera and am loving it! All my FF media plugins were automagically installed so I can view Utube, BBCi, wtc,etc.

Also like the layout and look and like the fact that it loads real fast. Haven't fount the sepell chcek yet........

---

### Post by jerome1232 on 2008-12-19
> **Georgia boy said:**
> Jerome1232 made the comment about not having to worry about software being updated by using the repositories. Does that include the updates for things like OpenOffice.org? 

I mean like when they come out with their security updates, not going to the 3.0. Games etc get updated too?

Got kind of confused on that comment.
Thanks
Tom


Using Ubuntu's repos all versions are frozen so no open office won't upgrade to 3.0 if it came out after the version freeze for whatever release your using, maybe it'll be in the backports repo. But if there's a security flaw or major bug in open office 2.4 that's fixed in version 3.0, then that fix will be patched into ubuntu's package for open office 2.4. 

I do have a small number of third-party repositories (like wine's, opera's, and like 3 or so more) for certain programs that I want the bleeding edge features on. 

I'm not really clear on what your confused about?

---

### Post by scorp123 on 2008-12-19
> **Georgia boy said:**
> Jerome1232 made the comment about not having to worry about software being updated by using the repositories. Does that include the updates for things like OpenOffice.org? Yes. Different than Windows where you at best would only get Windows updates (= for the OS itself) and maybe Microsoft Office, on Linux you'd get updates for _everything_ that was installed via a repository. The package manager automatically scans the repositories in regular intervals and if it detects a new package it will tell you.

With manually installed packages you don't get that functionality.

> **Georgia boy said:**
> I mean like when they come out with their security updates, not going to the 3.0 OpenOffice.org 3.0 supposedly will be released as update in a few weeks. And if you don't want to wait: there are various guides here that will explain how to pull OpenOffice.org 3.0 from a developer's repository (hosted at Canonical's "LaunchPad" web site) and have it installed already now.

---

### Post by Flimm on 2008-12-20
Opera will tell you itself if it needs an update.

---

### Post by scorp123 on 2008-12-20
> **Flimm said:**
> Opera will tell you itself if it needs an update. Yes, but it's confusing to the end user as it doesn't tell you how exactly that update is supposed to be done.

Repositories and the package manager are there for a reason and they are the easiest way. Period.

Installing and updating software manually is Windows thinking. This here is Ubuntu. Here we let the package manager do this job for us.

---

### Post by Georgia boy on 2008-12-21
Happy with what I have in the repositories. Was just wondering about the security updates for OpenOffice.  Not going to go for the new 3.0 until I get the new Ubuntu after 8.04 runs out in it's three years. By then there will probably be another new version out. So, I'll stick with what I have.  Don't want to mess up a good thing that is working great for me. I was just kind of wondering when I read about updates. Knew that Firefox and Thunderbird was getting their updates just wasn't sure about if OpenOffice was getting the security updates or not. Thanks for clearing that up for me. 
Have a great day.
Tom

---

