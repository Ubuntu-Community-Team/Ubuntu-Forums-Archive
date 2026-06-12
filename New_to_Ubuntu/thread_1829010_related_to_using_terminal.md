---
title: "related to using terminal"
date: 2011-08-20
forum: New to Ubuntu
---

### Post by gr8ansh4u on 2011-08-20
every time i open terminal ...i've to  type series long commands to go to a particular directory in home folder...is ther any provision wher v can assign one command to all that so that by typing that command i'm directly in my directory?

also hw to go up in a directory tree....like v type cd..(cd dot dot) in windows to go to previous directory..in terminal how to do that?

---

### Post by Darkness Des on 2011-08-20
You can always do this for compacting a string of commands into one:
```
alias mycommand='cd ~/.whatever; string -of ~/commands; goes here'
```

As for going up a directory tree, the Windows command line is a bit loose on the spacing. In Linux, that's supposed to be
```
cd ..
```

---

### Post by sanderj on 2011-08-20
With

```
cd<ENTER>
```

you go directly to your home directory.

And you can always press <TAB> to complete a directory or file name. So type "cd mybi" and press <TAB> to complete that to "cd mybigdirectory"

HTH

---

### Post by Wim Sturkenboom on 2011-08-20
An alternative for a directory that you often work in, is to create a symlink (kind of windows shortcut). Replace **shortcut** below by a sensible name and obviously replace 'dutchies...' by the path to your directory

```

fortyfourgalena@desktop-01:~$ ln -s dutchies_travel_southafrica/Liza_homepage/capetown/winetour/ **shortcut**
fortyfourgalena@desktop-01:~$ ls -l shortcut
lrwxrwxrwx 1 fortyfourgalena fortyfourgalena 60 2011-08-20 10:17 shortcut -> dutchies_travel_southafrica/Liza_homepage/capetown/winetour/
fortyfourgalena@desktop-01:~$ cd shortcut
fortyfourgalena@desktop-01:~/shortcut$ ls
t_boschendal_cloudymountains.jpg  t_boschendal_winetasting.jpg  winetour.html  winetour.html~  winetour_nl.html
fortyfourgalena@desktop-01:~/shortcut$

```

---

### Post by gr8ansh4u on 2011-08-20
THANK you evryone... :) i find this forum very useful...i get answers to all the problems i post...:)

---

### Post by gr8ansh4u on 2011-08-20
if i use alias command...do i hav to do this evrytime i login or has it become permanent?

can i edit .bashrc file?

---

### Post by The Cog on 2011-08-20
Yes, .bashrc is the place to put the alias command if you want to keep it. I think it works as you log in, so it won't affect your current session.

---

### Post by spiky001 on 2011-08-20
As an added extra you can use the Tab button to auto fill example cd Dow then hit TAB it will finish off the word Downloads. It can be used for long paths as well. Not exactly what you asked by might be usefull.

---

### Post by Wim Sturkenboom on 2011-08-20
> **spiky001 said:**
> As an added extra you can use the Tab button to auto fill example cd Dow then hit TAB it will finish off the word Downloads. It can be used for long paths as well. Not exactly what you asked by might be usefull.

See post #3 ;)

---

### Post by aeronutt on 2011-08-20
TAB, also, let's say you have 2 directories that start with D (eg Downloads and Documents).  Type 'D', then hit tab twice quickly....it'll show all dirs that start with D.

TAB can also be used to auto complete commands and command options.
eg, type apt-g <tab>, then upg <tab>, and you'll end up with apt-get upgrade.

---

### Post by aeronutt on 2011-08-20
> **gr8ansh4u said:**
> if i use alias command...do i hav to do this evrytime i login or has it become permanent?

can i edit .bashrc file?

I prefer putting aliases in .bash_aliases, and keeping a copy of this saved as backup.  .bashrc reads .bash_aliases by default (at least in current versions of ubuntu).  This way, if you re-install ubuntu, all you have to do is copy your backup .bash_aliases to your home dir, and you have all your aliases back.

---

### Post by gr8ansh4u on 2011-08-20
but how to edit it...

---

### Post by scottstensland on 2011-08-20
sudo apt-get install gedit   # <-- to install gedit 

gedit ~/.bashrc

---

