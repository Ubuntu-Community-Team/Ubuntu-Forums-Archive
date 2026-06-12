---
title: "where is the software that I installed?"
date: 2010-09-26
forum: New to Ubuntu
---

### Post by sallam on 2010-09-26
Greetings
Ubuntu software center is great. But each time I choose to install a software through it, I fail to find where it was installed, or any icon o click at to use the software. Its not anywhere in the top panel. I also use F1 to search for them.. but no trace!
For example, I just installed PowerTop, a tool to manage laptop battery life. Now I need to use it. but, there is no trace of it..!

What am I missing here?

---

### Post by spiky001 on 2010-09-26
hi some programs are run in terminal try ```
power top
```

---

### Post by endotherm on 2010-09-26
a number of programs don't try to create shortcuts/menu items, either because they are used at the terminal, or because each user may be using a differant desktop/window manager (ubuntu uses gnome, kubuntu uses KDE, etc).


powertop appears to be a command line application, so you can invoke it in a terminal by entering 
```
sudo powertop
```

 you can create a launcher for it on your desktop by right clicking and selecting "Create Launcher".
then enter this info:

Type: Application In Terminal
Name: PowerTop
Command: gksu powertop
comment: powertop

(you can change any to suit your tastes, except the type, and command).

note that the command requires admin privileges, so we have to add "gksu" to the beginning. that way, it will ask you for **your **password at launch, and thus get administrator rights. 

you can add a launcher to your menu bar, by right clicking it, and selecting "Edit Menus". then select the folder you want to put it in on the right, and click Add. use the same info as above for setting up the launcher.

---

### Post by coffeecat on 2010-09-26
> **spiky001 said:**
> hi some programs are run in terminal try ```
power top
```

Actually, it's:

```
powertop
```

No space.

@sallam, spiky001 makes a good point. Many apps are command line ones. What others have you installed which you can't find in the applications menu?

---

### Post by Paqman on 2010-09-26
> **sallam said:**
> 
What am I missing here?

Make sure you read the description before you install the app. If it's a command line app, it won't create a menu item.

---

### Post by philinux on 2010-09-26
> **Paqman said:**
> Make sure you read the description before you install the app. If it's a command line app, it won't create a menu item.

Unfortunately the description for powertop in SC or Synaptic makes no reference that is a command line tool. Neither does the website.

---

### Post by Paqman on 2010-09-26
> **philinux said:**
> Unfortunately the description for powertop in SC or Synaptic makes no reference that is a command line tool. Neither does the website.

I've always raised this as a bug whenever i've found a package with a similarly poor description.

---

### Post by sallam on 2010-09-28
What about 7zip? I just installed it from the ubuntu software center, but can't find it anywhere..
I need to extract a rar file, tried extract here, doesn' work, tried open with other software, not listed..

---

### Post by coffeecat on 2010-09-28
If you mean p7zip, that's also a command line utility. If you want to handle rar archives you need the p7zip-rar package - or get p7zip-full for everything. what you need for rar files with 
archive manager, I don't know.

---

### Post by beew on 2010-09-28
> **sallam said:**
> What about 7zip? I just installed it from the ubuntu software center, but can't find it anywhere..
I need to extract a rar file, tried extract here, doesn' work, tried open with other software, not listed..

7 zip is also a command line tool in Linux. But you can download a separate gui front end called Q7Z from source forge.
[URL="http://sourceforge.net/projects/k7z/"]
http://sourceforge.net/projects/k7z/[/URL]

I don't think Q7Z is in the repos, but you can check.

---

### Post by theozzlives on 2010-09-28
> **coffeecat said:**
> If you mean p7zip, that's also a command line utility. If you want to handle rar archives you need the p7zip-rar package - or get p7zip-full for everything. what you need for rar files with 
archive manager, I don't know.

Just install "rar" it'll work with File Roller.

---

### Post by sallam on 2010-09-28
command line again.. no thanks.
I'll use Ark then.

---

### Post by theozzlives on 2010-09-28
> **sallam said:**
> command line again.. no thanks.
I'll use Ark then.

File Roller IS NOT command line.

---

### Post by beew on 2010-09-28
Get P7zip (command line) and Q7Z (GUI for P7Zip) and install unrar (non free) from Synaptic and you are set.

File Roller is kind of garbage in my opinion. Doesn't have any option to extract to designated folder, can't handle multi-part archives and kind of sluggish. I uninstalled it long time ago.

---

### Post by sallam on 2010-09-28
Thanks theozzlives, installing rar was what I needed.
many thanks everyone for your wonderful help.

---

### Post by sallam on 2010-09-28
> **theozzlives said:**
> File Roller IS NOT command line.
Yes, I was replying to someone else. Sorry I posted before I see your reply.
Many thanks.

---

### Post by arvevans on 2010-09-28
Seems the thread got hijacked somewhere along the line.  To answer the original question "where is the app that I installed"...

In UNIX derived operating systems (Linux, BSD, OS-X, etc). there are conventional places to put things.  You can look for newly installed software in these places:

[LIST]
[*]/bin
[*]/usr/bin
[*]/usr/local/bin
[*]/$HOME/bin
[*]/sbin (system admin commands)
[*]/usr/sbin (more system admin commands)
[/LIST]

Unfortunately not all software writers follow tradition, and you occasionally find something installed in unusual places.  Fortunately this is not frequent, and software installed wrongly usually dies because it is not locatable in the standard places.

The real problem appears when someone builds an installer which changes the name of a program and installs it with a different than advertised name.

Command line type programs can still be added to the Ubuntu menu.  Go to the menu editor and add your command line program, but tell the launcher to "run in terminal" so it will have it's own screen when you launch it.
_._

---

### Post by SeijiSensei on 2010-09-28
Running 'dpkg -L packagename' will list all the files included in that package.  For instance: 

```

$dpkg -L gimp
/.
/usr
/usr/bin
/usr/bin/gimp-console-2.6
/usr/bin/gimp-2.6
/usr/share
/usr/share/python-support
/usr/share/python-support/gimp.private
/usr/share/applications
/usr/share/applications/gimp.desktop
[...]
```

Obviously GIMP didn't create the / directory, but it did "touch" it along the way.  Entries like /usr/bin/gimp-2.6 or /usr/share/python-support/gimp.private are files associated with the gimp package.

---

