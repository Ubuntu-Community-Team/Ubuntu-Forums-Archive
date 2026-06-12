---
title: "Software Center/Package Manager dont work+ Large System Lag"
date: 2011-05-11
forum: New to Ubuntu
---

### Post by techfighterminal on 2011-05-11
I've been using Ubuntu for maybe 1 month now, and everything was going smoothly until i came across this problem.

1. last night my system was running unusually slow (Pretty much froze and went all grey). I thought it was just running hot so i shut it off for the night. but today upon turning it on I have the same problem. once i opened my System monitor i noticed a process named "convert" using up 200% of my cpu power. figuring it was a virus or something i went to my software center to install the virus remover tool.

2. ubuntu software center says its opening in the task bar but just fails to do so. after searching this problem i came across the solution of removing it then reinstalling it in my package manager.

3.package manager loads up but give me an error then closes. 
"E: Type 'wget' is not known on line 60 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report."

[IMG]http://i180.photobucket.com/albums/x207/k-k999/Screenshot.png[/IMG]

If anyone can help it would be greatly appreciated. I just got everything including Daggerfall to work so I don't want to do another fresh install.

[EDIT]
I noticed that you sometimes need a source list so heres mine...


deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb [http://packages.dfreer.org](http://packages.dfreer.org) feisty main
wget [http://packages.dfreer.org/7572013D.gpg](http://packages.dfreer.org/7572013D.gpg) -O- | sudo apt-key add - sudo apt-get update

sudo tee -a /etc/apt/sources.list
wget [http://packages.dfreer.org/7572013D.gpg](http://packages.dfreer.org/7572013D.gpg) -O-

sudo apt-key add -
sudo apt-get update

sudo apt-get install psx32
sudo apt-get install psx32frontend

sudo apt-get install psx32

clear
deb [http://packages.dfreer.org](http://packages.dfreer.org) feisty main
wget [http://packages.dfreer.org/7572013D.gpg](http://packages.dfreer.org/7572013D.gpg) -O-sudo apt-key add -
sudo apt-get update
sudo apt-get install ia32-libs ia32-libs-sdl ia32-libs-gtk

---

### Post by ~Plue on 2011-05-11
Run* gksu gedit /etc/apt/sources.list* and remove the following from the file. They aren't valid repository lines```
[COLOR=DarkRed]
deb http://packages.dfreer.org feisty main[/COLOR]
[COLOR=DarkRed]wget http://packages.dfreer.org/7572013D.gpg -O- | sudo apt-key add - sudo apt-get update

sudo tee -a /etc/apt/sources.list[/COLOR] [COLOR=DarkRed]
wget http://packages.dfreer.org/7572013D.gpg -O-

sudo apt-key add -[/COLOR] [COLOR=DarkRed]
sudo apt-get update

sudo apt-get install psx32[/COLOR] [COLOR=DarkRed]
sudo apt-get install psx32frontend

sudo apt-get install psx32[/COLOR] [COLOR=DarkRed]

clear[/COLOR] [COLOR=DarkRed]
deb http://packages.dfreer.org feisty main
wget http://packages.dfreer.org/7572013D.gpg -O-sudo apt-key add -
sudo apt-get update
sudo apt-get install ia32-libs ia32-libs-sdl ia32-libs-gtk[/COLOR]
```Then save the file and run [I]sudo apt-get update

[/I]**Edit:**
> **techfighterminal said:**
> 
 1. last night my system was running unusually slow (Pretty much froze  and went all grey). I thought it was just running hot so i shut it off  for the night. but today upon turning it on I have the same problem.  once i opened my System monitor i noticed a process named "convert"  using up 200% of my cpu power. figuring it was a virus or something i  went to my software center to install the virus remover tool.
 
Do you have, by any chance, imagemagick installed?

---

### Post by techfighterminal on 2011-05-11
thank you! i can open my stuff again, damn that fiesyman i recognized that from when i was trying to get Epsxe to work.

is there anyway i could learn what sources belong, and what doesn't so i could handle it myself?

---

### Post by techfighterminal on 2011-05-11
> Do you have, by any change, imagemagick installed?

no i don't think so

---

### Post by ~Plue on 2011-05-11
> **techfighterminal said:**
> thank you! i can open my stuff again, damn that fiesyman i recognized that from when i was trying to get Epsxe to work.

is there anyway i could learn what sources belong, and what doesn't so i could handle it myself?
These articles may help you better understand it;
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

To keep it short, Debian repositories have format of "deb servername releasename reponame" or "deb-src" for the source code repository (only needed if you want to compile programs from source). 
If you're manually adding them to your sources, please check if the server is up and running and whether you're using the correct repository for your release - in this case, maverick

---

