---
title: "Where do files go once you install them ?"
date: 2010-08-17
forum: New to Ubuntu
---

### Post by AfrikaDietmar on 2010-08-17
Its another novice question of me, please don't beat if its really stupid what i am asking - but i really have always been wondering where files go, once you install them in case you want to get rid of them afterwards...

I have been using ubuntu for a few months now, did a lot of installs, uninstalls, and figured out its always best to use the software centre but still there are programs that you cannot get or install from the software centre. 

So i use commands mentioned on websites to install their packed programs. 
It looks like that it usually creates a hidden file in my home folder.
I won't find those programs on my computer with the synaptic manager.

If i just delete that hidden folder, would it then mean the program is gone ? And i would have to simply remove its associated link that i created on the desktop tab ?
Do packed programs all write their files structured in the same places, so i would only need to look in those places and remove them there ? Is there a list or technique for this ? Or a search method ? How do you guys uninstall programs ?

---

### Post by earthpigg on 2010-08-17
> **AfrikaDietmar said:**
> 
If i just delete that hidden folder, would it then mean the program is gone ? 

no, it will mean the ***settings*** for that program are gone. software center does not do this by default because those hidden files (also called 'dotfiles') take up such a microscopic amount of space. and, since they are kept by default, the settings will be there waiting if you decide to reinstall the software.

if you want to restore some program to it's default settings, deleting it's dotfiles and dotfolders will do that for you. anything in your home folder, you can delete and rename and do whatever you want to do with it all day long... it may break that particular software for you, but the system will still boot and other users will be completely unaffected.

having to type 'sudo' or enter your password after logging in is your hint that what you are doing may affect other users or break the system.

> And i would have to simply remove its associated link that i created on the desktop tab ?

right click -> move to trash.

> Do packed programs all write their files structured in the same places, so i would only need to look in those places and remove them there ? 

no, they write them all over. the package manager (software center or synaptic or the command line) does this for you. software center is the only one that doesn't give you the option of removing the dotfiles as well. this is because software center is designed to be easy for novices to use. in synaptic, you can select '***completely*** remove' to remove the dotfiles. in the command-line tool apt-get, you can add the --purge flag. both will remove the dotfiles.

> Is there a list or technique for this ? Or a search method ? How do you guys uninstall programs ?

let's use tuxtype as our example.

```
sudo apt-get remove tuxtype
```

or, if i want the dotfiles to go away too:

```
sudo apt-get remove --purge tuxtype
```

in synaptic, you purge it by right clicking on the package and selecting 'completely remove'. synaptic is found in system -> administration.


aside from deleting dotfiles and dotfolders, you ought _never_ _*never*_ ***_never_*** manually try to uninstall a program by deleting it's files and folders. decades (literally) of work have gone into the package management software we have in ubuntu, and it would be silly for a non-guru (myself included) to attempt to outdo those efforts.

---

### Post by mapes12 on 2010-08-17
[http://amitech.50webs.com/installing/index.php.html](http://amitech.50webs.com/installing/index.php.html)

---

### Post by NikoC on 2010-08-17
You can use the following command for a list of all installed packages (downloaded and software center or synaptic):
dpkg -l

You can remove a package with:
sudo dpkg -r package_name

---

