---
title: "Trouble re-installing wine"
date: 2009-12-19
forum: New to Ubuntu
---

### Post by Buuntu on 2009-12-19
I'm having trouble installing wine after deleting it and it's folders.  I've tried 'sudo apt-get update && sudo apt-get install -f' as well as 'sudo apt-get update && sudo dpkg --configure -a' since it's giving me errors about broken dependencies.  Anyways here's the error:
```
gabriel@gabriel-desktop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: wine1.2 but it is not going to be installed
E: Broken packages
```
I've added the official wine repository to my software sources and have installed wine1.2 but that still hasn't fixed the problem.  I've run out of ideas at this point so I'd appreciate any input.

---

### Post by quecoder on 2009-12-19
hope someone answers this prob.! very close to my prob. as well

---

### Post by ankspo71 on 2009-12-19
Hi,
I don't know if it will help or not, but what happens if you try to install wine from the ubuntu repositories? (I mean disable the WineHQ repo, then refresh the repositories, and then install Ubuntu's version of wine.) Or did you try that already and then added the wine repo?

If you have some experience compiling packages from source files, you might have better luck compiling wine. There are several versions to choose from.

[http://sourceforge.net/projects/wine/files/Source/](http://sourceforge.net/projects/wine/files/Source/)

Hope this helps.

---

### Post by Buuntu on 2009-12-19
Well I guess that works (removing the wine repos), though I would have liked to have that repository since it seems like they provide more recent versions of wine, or so I've heard.  Thanks though - I don't know why I didn't think of that :P

---

### Post by Buuntu on 2009-12-19
Now I have another questions though.  When I uninstalled wine I had to manually remove the entry from Applications because it didn't go away.  Now when I reinstalled it, I don't see it.  How would I go about adding the entry for wine that forked into all the applications and such?

---

### Post by Buuntu on 2009-12-23
Where could I locate the file that makes it automatically add an entry in Applications?  Sorry, I guess I don't understand exactly what goes into doing that... 
I'm just tired of adding the entries for wine in manually, it's a big pain.

---

### Post by ankspo71 on 2009-12-23
Hi,
I don't know why this is, and I was hoping someone else had the answer to this. I have this menu entry problem with uninstalling wine or wine applications too. I try not to uninstall anything from wine anymore (or remove any wine related menu entries), unless I know positively that the program will never work, or if I'll never use it again.

I think playonlinux doesn't have this problem, or at least it doesn't for me. If you don't know what playonlinux is, have a look here [http://www.playonlinux.com/en/](http://www.playonlinux.com/en/) . Current supported applications is here [http://www.playonlinux.com/repository/](http://www.playonlinux.com/repository/) .

Anways, here are some shortcut commands for Wine so you can recreate some menu entries.

"Browse C:\ Drive"
xdg-open .wine/dosdevices/c:

"Configure Wine"
winecfg              (or /usr/bin/winecfg)

"Uninstall Wine Software"
wine uninstaller    (or /usr/bin/wine uninstaller ???) 

To make a shortcut to an EXE to run under wine:
env WINEPREFIX="/home/james/.wine" wine "C:\Program Files\Folder\executable.exe" 

(note: replace my username "james" with your username.)

I'm glad I'm posting this now, because it will someday be helpful to me too. :)

Hope this helps,

---

### Post by Buuntu on 2009-12-23
Yeah I set all those commands too :D, but I don't want to set new ones for EVERY new app I install.  I'll have a look at planonlinux, if it has as much or better support for games/apps than wine then I'll definitely try it.

---

### Post by kraus3742 on 2009-12-31
> **Buuntu said:**
> Yeah I set all those commands too :D, but I don't want to set new ones for EVERY new app I install.  I'll have a look at planonlinux, if it has as much or better support for games/apps than wine then I'll definitely try it.
ankspo71 and Buuntu Thanks for the post I have been struggling with this one for over a week!

---

