---
title: "[SOLVED] too much manual package management on reinstall..."
date: 2008-12-28
forum: New to Ubuntu
---

### Post by mrowth on 2008-12-28
How can I reinstall the exact same packages I have now on a future installation or on another computer? 

It seems I can get a list of installed packages through **dpkg -l | grep ii**, but I don't know how to proceed from there to a script (or single command). 

Fortunately there're some metapackages like Ubuntustudio's, but then again they pull in a lot of stuff I don't actually want. So I'd also like to know how to prepare the removal of  packages that are part of a standard installation but that I don't want to keep.

Basically I just want to recreate (on a standard installation) the same "package situation" I have now on my painstakingly configured Hardy.

---

### Post by cariboo on 2008-12-28
You can store your archived packages using apton-cd, it is available in the repositories.

If you don't need some parts of UbuntuStudio, you can use Synaptic-->Edit-->Mark Packages by Task and just select the UbuntuStudio desktop, if you need more of the multimedia packages you can install them using the menu.

To remove packages you don't want use Synaptic to mark them for complete removal.

Jim

---

### Post by mrowth on 2008-12-28
> **cariboo907 said:**
> You can store your archived packages using apton-cd, it is available in the repositories..

Sounds promising -- though redownloading isn't the problem -- I think what I'm looking for is really a simple list of just the package names, something I could script a "go through this list of names and apt-get install each of them" kinda loop around that would pull in the current versions. Fine, I realize now that I should be able to do that. But I was wondering if there's a "built-in" way to do achieve the same result. 

And then remove packages that have been installed by default that aren't in the list.

> If you don't need some parts of UbuntuStudio, you can use Synaptic-->Edit-->Mark Packages by Task and just select the UbuntuStudio desktop, 
Much too coarse -- I never need all of those, nor ever none ;)

> if you need more of the multimedia packages you can install them using the menu.

To remove packages you don't want use Synaptic to mark them for complete removal.

Jim

Thanks... I do know how to install/uninstall things manually, though... just looking for a simple way to automate the process. Ubuntustudio was just an example of where it's actually relatively *easy* thanks to the metapackages.

---

### Post by drs305 on 2008-12-28
Run this to create a list of your installed apps:
```
aptitude --display-format '%p' search '?installed!?automatic' > ~/Desktop/packages.txt 

```

Copy the file ~/Desktop/packages.txt to the new computer. Then run this to install the same packages on the new machine:
```

sudo xargs aptitude --schedule-only install < ~/Desktop/packages.txt
sudo aptitude install  

```

---

### Post by handydan918 on 2008-12-28
Okay, this should be in the wiki, or something. It's so simple, yet so powerful.


```
sudo dpkg --get-selections
```


```
sudo dpkg --get-selections > softwarelist
```
At this point in the proceedings, you hose your system and reinstall, and then...

```
dpkg --set-selections < softwarelist
```


```
apt-get dselect-upgrade
```

Enjoy.

---

### Post by mrowth on 2008-12-29
> **drs305 said:**
> Run this to create a list of your installed apps:
```
aptitude --display-format '%p' search '?installed!?automatic' > ~/Desktop/packages.txt 

```

E: Regex compilation error: Invalid preceding regular expression

Thanks, though

PS: Also, and unrelatedly, aptitude decided I had 134 unused packages, which it promptly started deleting (some orphaned dependencies, but **useful** stuff, too, like kuser-kde4, dkms, tango-icon-theme, rosegarden-data, AND MAH-JONG!!! :P:lol:); why...?

---

### Post by mrowth on 2008-12-29
> **handydan918 said:**
> Okay, this should be in the wiki, or something. It's so simple, yet so powerful.


```
sudo dpkg --get-selections
```


```
sudo dpkg --get-selections > softwarelist
```
At this point in the proceedings, you hose your system and reinstall, and then...

```
dpkg --set-selections < softwarelist
```


```
apt-get dselect-upgrade
```

Enjoy.

That looks like it's exactly what I was looking for. Even contains "deinstalls".

---

### Post by drs305 on 2008-12-29
> **mrowth said:**
> E: Regex compilation error: Invalid preceding regular expression

I ran the code and it worked fine for me. Having said that, the commands given by handydan918 are ones I've successfully used and repeated here many times. Sometimes you just can't build a better mousetrap.

I cannot tell you why aptitude was trying to remove some packages unless they were marked for deinstallation at some point. You could check the "softwarelist" file to see if any of the packages aptitude tried to remove are listed as 'deinstall'. The command I presented doesn't list 'deinstall' status, which would actually be a good thing for replicating a system (provided it is correct!).

*Edited after next post: Since apt found **automatically** installed packages, these were packages that you did not install, and were no longer needed by other apps, even though 'useful,  they were uninstalled. This is normal behavior.*

---

### Post by mrowth on 2008-12-30
> **drs305 said:**
> I ran the code and it worked fine for me. Having said that, the commands given by handydan918 are ones I've successfully used and repeated here many times. Sometimes you just can't build a better mousetrap.

I cannot tell you why aptitude was trying to remove some packages unless they were marked for deinstallation at some point. You could check the "softwarelist" file to see if any of the packages aptitude tried to remove are listed as 'deinstall'. 
No, I think it's (largely or exclusively?) the same packages that apt-get lists like so:

[b]The following packages were automatically installed and are no longer required:
  kdeartwork-emoticons-kde4 sweeper-kde4 kstars-kde4 parley-data-kde4 ...etc. for a at least hundred more[/b]

I think those would be packages that were installed to meet the dependencies of packages that have in the meantime been removed. So from that point of view there's no reason to keep them around anymore. 

Except I'd rather not have that be done automatically.

When I try to install them (although they are, already, installed) they are taken off that list.

---

### Post by drs305 on 2008-12-31
One more thought on this thread. Regarding post #5, there is an additional command which would be helpful in what you are trying to do.

Prior to running the "sudo dkpg --set-selections" command on your *install* computer, you may want to run this:
```

sudo dpkg --clear-selections

```

This command will clear the dpkg list of all non-essential apps before you begin the import. Otherwise, the --set-selections command will *add* your new list to the existing list. It depends on what your goals are, but to get the new computer's list to most closely match the old computer, you would want to run this command.

---

