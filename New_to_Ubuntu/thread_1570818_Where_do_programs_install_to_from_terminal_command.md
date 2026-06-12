---
title: "Where do programs install to from terminal command line?"
date: 2010-09-08
forum: New to Ubuntu
---

### Post by karlm on 2010-09-08
For example, I looked at the "Ubuntu Software Centre" from the Applications menu. I installed a copy of a Spectrum Emulator... It said it was installed... Could I find it anywhere? No. There were no instructions on how to access or run it. 

I checked all the menus, (Applications, Places & System) and it didn't seem to have any desktop shortcut or a taskbar icon associated either.

[offsubject]On the topic of the USC, I note Google has it's own little area... with three variations of Google Chrome. As I understand Google Earth works on Linux, why isn't it listed there? Instead I had to install it via a command line and it keeps crashing on boot, leaving me with hidden crash reports that I only recently learned how to access (CTRL+H). Surely something like that needs to be in the USC?[/offsubject]

So I read up a little on the named emulator and found others were using a command line installer, which I followed to. 

Again, no instructions on how to use it (aside from --help) were offered in any shape that I could see.

I learned from reading in this forum that to run it, I had to issue the command 'xspect' and only using that command can you access the help file.

I cannot locate the files. I do not know where the games files need to go in order to load classic 8bit games onto it. This seems to be a recurring issue with much of the software offered. I don't know how to uninstall from the command line, nor how to create a short-cut (windows speak).


I don't mean to moan, but wouldn't some sort of readme file work well for those who don't know their way around linux yet? I'm assuming some of them would have a readme.txt file, but as I have no information on where that readme file is located, I can't access it.


Am I being really stupid, thick and ignorant, or are there some basics that could perhaps do with a little more planning on the developers side of things?






*annnnnnd breathe....*

---

### Post by bodhi.zazen on 2010-09-08
Depends on the program, the linux file system is different, binaries go into */bin or /sbin and man pages all go in the man pages.

See :

[img]http://techbu.com/wp-content/uploads/2009/06/filesystemhierarchyhb8.jpg[/img]

[http://techbu.com/2009/06/28/linux-file-system-explained-for-beginers/](http://techbu.com/2009/06/28/linux-file-system-explained-for-beginers/)

---

### Post by Jesus_Valdez on 2010-09-08
Some software is meant to be used from the Terminal, so it's only accesable trhou it.

I didn't understood the issue with Google Earth.

---

### Post by karlm on 2010-09-08
> **bodhi.zazen said:**
> Depends on the program, the linux file system is different, binaries go into */bin or /sbin and man pages all go in the man pages.

See :

[img]http://techbu.com/wp-content/uploads/2009/06/filesystemhierarchyhb8.jpg[/iimg]

[http://techbu.com/2009/06/28/linux-file-system-explained-for-beginers/](http://techbu.com/2009/06/28/linux-file-system-explained-for-beginers/)Thanks!!! I'll check that lot out!

> **Jesus_Valdez said:**
> Some software is meant to be used from the Terminal, so it's only accesable trhou it.Right... that seems a bit odd. But then, I'm a windoze user so I guess I'll adjust sooner or later. It also begs the question, if it's command line only - how am I supposed to uninstall without a script or at least a note to tell me the instructions I need to issue?

> **Jesus_Valdez said:**
> I didn't understood the issue with Google Earth.
[http://ubuntuforums.org/showthread.php?p=9818194#post9818194](http://ubuntuforums.org/showthread.php?p=9818194#post9818194) <---explained in full.

---

### Post by 0N3 on 2010-09-08
Ubuntu tweak is a very good tool for installing and enabling repositories and keeping your system up to date available here
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by Jesus_Valdez on 2010-09-08
You can make an App launcher, just right click on the Desktop and "add a launcher", If its a "terminal thing" like seems to be the case, just choose the correct setting on the little window, then choose a pretty icon and enjoy.

---

### Post by bodhi.zazen on 2010-09-08
You can locate / find things on the command line with 

locate
find
which

Try it 

which firefox
locate firefox

After installing a new application, you will need to update the database with locate (it is automatically updated at midnight I think)

```
sudo updatedb
```

For use of find, read a tutorial

[http://content.hccfl.edu/pollock/unix/findcmd.htm](http://content.hccfl.edu/pollock/unix/findcmd.htm)

[http://www.linux.com/archive/feed/55377](http://www.linux.com/archive/feed/55377)

---

### Post by beew on 2010-09-08
> Right... that seems a bit odd. But then, I'm a windoze user so I guess I'll adjust sooner or later.


Or you can create desktop launchers for your apps. :)
[http://www.liberiangeek.net/2010/09/create-desktop-launchersshortcuts-ubuntu-10-0410-10-maverick-meerkat/]("http://www.liberiangeek.net/2010/09/create-desktop-launchersshortcuts-ubuntu-10-0410-10-maverick-meerkat/")

If you want the launchers to be in the drop down menus(the way I prefer) instead of cluttering the desktop, you can go to the top panel then then go to System > Preference > Main Menu. Open it, choose from the left panel where you want your launcher to appear (Accessories, Graphics, Internet etc) Then click  "new item" in the right panel and proceed as the link describes. 

If you want the launcher to have a special appearance you can download an icon and when you create the launcher, click on the little box on the upper right hand corner in the launcher creation dialogue box and point it to the icon. Sometimes programs may come with default .desktop files and you can click the little box and find them in /usr/share/applications or /usr/local/share/applications (if the program is installed locally, usually things you download and install yourself instead of through the program manager)

---

### Post by karlm on 2010-09-08
> **0N3 said:**
> Ubuntu tweak is a very good tool for installing and enabling repositories and keeping your system up to date available here
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)Thank you - I shall check that out too.

> **Jesus_Valdez said:**
> You can make an App launcher, just right click on the Desktop and "add a launcher", If its a "terminal thing" like seems to be the case, just choose the correct setting on the little window, then choose a pretty icon and enjoy.

That's great to hear, thank you! However, just to add... Just because I'm well versed in Windows doesn't mean I am seeking 'pretty icons'. I'm simply after the knowledge to understand the system here better. The lack of information on installation is a little discombobulating for me.

Hopefully, I'll start making better sense of it as I become more acclimated with it.

---

### Post by gnicko on 2010-09-08
Hey! Here's something you might find interesting too....

Try not to use the Software Center to do any installing if you can help it. Its fine (even useful) to browse around and see what's available in there, but try to do the installation/un-installation from the command line using apt-get when possible--especially when you're just starting out. Do it "manually" for a while to develop some "intuition" about what you're doing and you'll be amazed at how quickly it becomes second nature.

e.g 
```
sudo apt-get install *someprogram*           (<-- to install...)
sudo apt-get remove (or purge) *someprogram*       (<-- to uninstall
(apt-get --help for the complete run-down, etc.)
```

It won't tell you exactly where the program is going (installed to) but it does let you see what's going on "behind the scenes" to get a better feel for the installation process...and hopefully a couple of things to guess at to get what you want. As a rule of thumb, most applications will install to /usr/bin, and some (usually, but not always,) "smaller", "wiget-y" programs go into /etc/bin--but there are, as always, exceptions to this principle. Start by looking in /usr/bin, then /etc/bin and you'll find maybe 90% of what you are looking for.

I know its not very "Windows-like," but try to use the command line when you can (really, it won't hurt!) so that you can see what's going on inside your computer. That, in my opinion, is one of the tragic flaws of Windows...you never really know what it's doing when you click on an icon or something...you just have to sit back and trust that you're going to get what you want.

Another thing, once you know how to launch a specific program from the command line, it's relatively easy to make a "short-cut" for your desktop or in the menu by setting the target of the "short-cut" or menu item to be the same thing you type on the command line to launch your program.

If you understand Windows well, Linux will be very easy for you, too--once you get over the differences. To be sure, there's a learning curve and all, but it's not as steep as it looks. The really cool thing, at least in my opinion, is that as you go, you'll learn a lot about how your computer actually works instead of just how to work an operating system.

Another point: Sometimes when you install a program, it just doesn't work. Not often, but it happens. Nice thing about Linux is that there are usually a dozen alternatives that you can try instead...or a different version that will work. "If at first you don't succeed, try something else!"

Stay close to the forums you'll be OK!

---

### Post by karlm on 2010-09-08
> **gnicko said:**
> Hey! Here's something you might find interesting too....

Try not to use the Software Center to do any installing if you can help it. Its fine (even useful) to browse around and see what's available in there, but try to do the installation/un-installation from the command line using apt-get when possible--especially when you're just starting out. Do it "manually" for a while to develop some "intuition" about what you're doing and you'll be amazed at how quickly it becomes second nature.

e.g 
```
sudo apt-get install *someprogram*           (<-- to install...)
sudo apt-get remove (or purge) *someprogram*       (<-- to uninstall
(apt-get --help for the complete run-down, etc.)
```

It won't tell you exactly where the program is going (installed to) but it does let you see what's going on "behind the scenes" to get a better feel for the installation process...and hopefully a couple of things to guess at to get what you want. As a rule of thumb, most applications will install to /usr/bin, and some (usually, but not always,) "smaller", "wiget-y" programs go into /etc/bin--but there are, as always, exceptions to this principle. Start by looking in /usr/bin, then /etc/bin and you'll find maybe 90% of what you are looking for.

I know its not very "Windows-like," but try to use the command line when you can (really, it won't hurt!) so that you can see what's going on inside your computer. That, in my opinion, is one of the tragic flaws of Windows...you never really know what it's doing when you click on an icon or something...you just have to sit back and trust that you're going to get what you want.

Another thing, once you know how to launch a specific program from the command line, it's relatively easy to make a "short-cut" for your desktop or in the menu by setting the target of the "short-cut" or menu item to be the same thing you type on the command line to launch your program.

If you understand Windows well, Linux will be very easy for you, too--once you get over the differences. To be sure, there's a learning curve and all, but it's not as steep as it looks. The really cool thing, at least in my opinion, is that as you go, you'll learn a lot about how your computer actually works instead of just how to work an operating system.

Another point: Sometimes when you install a program, it just doesn't work. Not often, but it happens. Nice thing about Linux is that there are usually a dozen alternatives that you can try instead...or a different version that will work. "If at first you don't succeed, try something else!"

Stay close to the forums you'll be OK!

Now THAT'S the kinda stuff I'm talking about!!!! Nice once. Is there a rep function on this site or a 'thanks'?

See, I [strike]do[/strike] did use the command line a lot and SSH (putty) for using my linux webserver VPS, so I do have a 'general' idea. I also have inspected window shortcuts before and examined the keys within to see how different commands work to make programs behave slightly differently (e.g. starting firefox in safe mode, shutting down with a timer etc.)

I have, just for sh*ts n' giggles, installed my XP pro CD into a virtual box on my ubuntu... just so I can reminisce :P

This forum HAS already proved invaluable to me. You guys (the members) have helped me get my quickcam 9000 pro working, shown me how to view hidden files, helped me get flash content working (youtube) in firefox and much more. 

I've got the 'gist' of the command line, but it's all new for me and I'm no spring chicken any more. Years ago, I began programming my humble Spectrum 128k as a young teenage, I caught on quick with that. Now in my mid 30s, things ain't so easy to retain in my dusty brain.

---

### Post by anewguy on 2010-09-08
You can do the same thing in Synaptic Package Manager.  Just click the "terminal" (maybe it's "show termina"?) button in the box when the first download is getting ready to run.

As bodhi.zazen mentioned, there is a structure to the file system and where things would "normally" get installed to.  However, there's also the freedom for an installer to put things pretty much where ever it wants to some degree.  If you're used to looking a \Program Files and finding apps in Windows, it's not the same in Linux.  Things like libs will go one place, executables another, documentation (man pages) in another, etc..  It would be best if you could follow some of bodhi's links and get familiar with the defaults for the file system and what they are meant to be used for.

Best of luck, and welcome to Ubuntu!

Dave ;)

BTW - in your 30's??  Try being in your 50's or later - things just get worse.  I came from a mainframe programmer,programmer/analyst, system administrator, systems programmer environment.  When mini's came out we had to adjust to also having those in our mix.  Then micros (what everyone thinks of as a PC now).  But a Spectrum 128k?  I go a little further back in that line - back to the original kit form ZX81.  Had to build all my interfaces (disk, printer, etc.) from scratch.  Forget the stupid Basic on the thing - I only used Basic to create a jump into machine code.  Wrote everything in machine code - gave much better control of the little bugger.  But before all of that, how about back to some of the original "PC"'s - Intel 8080 based (then Zilog Z80, etc.) kits that you used the front panel to toggle in each bit in each byte?  If you were lucky you figured out how to use a teletype or even a simple terminal with it, and store/read programs, etc., via punched tape.  Those were the days when things were fun, when hacking and being a hacker had a completely different (and at the time, enviable) meaning.

---

### Post by oldos2er on 2010-09-08
You can see where each file in a package is installed to using ```
dpkg -L <package name
``` or using Synaptic Package Manager, right-click on an installed package, Properties, Installed Files.

---

### Post by Miljet on 2010-09-09
A couple more tips for getting used to using the terminal that you seldom see mentioned is user guides. Almost all commands and package names are in lower case. Even if you are installing DeVeDe, the actual package will be named devede. And if you are having trouble remembering specific command names, most four letter commands will use the first and third letter. mv for move, ls for list, cp for copy, and so forth.

---

### Post by karlm on 2010-09-09
Hmm, well I tried:

```
 sudo apt-get install fuse
[sudo] password for xyz: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package fuse

```


So... that one didn't work :)


How exactly does this one install, please?
[http://people.igalia.com/berto/](http://people.igalia.com/berto/)

---

### Post by bodhi.zazen on 2010-09-09
> **karlm said:**
> Hmm, well I tried:

```
 sudo apt-get install fuse
[sudo] password for xyz: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package fuse

```
So... that one didn't work :)


How exactly does this one install, please?
[http://people.igalia.com/berto/](http://people.igalia.com/berto/)

There are links to .deb on that site.

Download the .deb and install with:

```
sudo dpkg -i name_of_deb.deb
```

If they do not work, contact the developer or try the source code.

---

### Post by karlm on 2010-09-09
> **bodhi.zazen said:**
> ```
sudo dpkg -i name_of_deb.deb
```

OKies, it works from command line. Nice! Thank you.

Now.. a question (yeah, another)... What is the dpkg? I gather the -i is 'ignore case', right? 

How come some things require me to cd to the directory where the files are downloaded in order to run (i.e. the above post you made), while other commands can be from anywhere..?

---

### Post by bodhi.zazen on 2010-09-09
> **karlm said:**
> OKies, it works from command line. Nice! Thank you.

Now.. a question (yeah, another)... What is the dpkg? I gather the -i is 'ignore case', right? 

How come some things require me to cd to the directory where the files are downloaded in order to run (i.e. the above post you made), while other commands can be from anywhere..?

Close / good guess

-i = install

[http://manpages.ubuntu.com/manpages/lucid/en/man1/dpkg.1.html](http://manpages.ubuntu.com/manpages/lucid/en/man1/dpkg.1.html)

---

### Post by Rubi1200 on 2010-09-09
Dpkg: [http://www.debian.org/doc/FAQ/ch-pkgtools.en.html](http://www.debian.org/doc/FAQ/ch-pkgtools.en.html)

> dpkg -i | --install package_file...
          Install the package. If --recursive or -R option    is  specified,
          package_file must refer to a directory instead.

          Installation consists of the following steps:

          1. Extract the control files of the new package.

          2.  If  another version of the same package was installed before
          the new installation, execute prerm script of the old package.

          3. Run preinst script, if provided by the package.

          4. Unpack the new files, and at the same time back  up  the  old
          files, so that if something goes wrong, they can be restored.

          5.  If  another version of the same package was installed before
          the new installation, execute the postrm script of the old pack-
          age.  Note that this script is executed after the preinst script
          of the new package, because new files are written  at  the  same
          time old files are removed.

          6.  Configure the package. See --configure for detailed informa-
          tion about how this is done.source: 
[http://unixhelp.ed.ac.uk/CGI/man-cgi?dpkg](http://unixhelp.ed.ac.uk/CGI/man-cgi?dpkg)

EDIT: bodhi's link is nicer :-)

---

### Post by karlm on 2010-09-09
Thanks for the info... I read something about -i being ignore case somewhere, i'm sure...

Anyway, thanks!

Now I'm stuck with a command line operated emulator that doesn't appear to have any menus to it or instruction on how to use it. I read the --help but it is only vague information and I can't find any help files in the documents folder for it.


ETA:-
Ahhar - seems the F1 keys answers a lot of the issues... Now then... Screen size, how the devil do we increase that? O_o
Been a while since I had to look at real 256x192 display lol

---

### Post by bodhi.zazen on 2010-09-09
> **karlm said:**
> Thanks for the info... I read something about -i being ignore case somewhere, i'm sure...

Aye, depends on the command

grep -i for example ...

[http://manpages.ubuntu.com/manpages/lucid/en/man1/grep.1.html](http://manpages.ubuntu.com/manpages/lucid/en/man1/grep.1.html)

---

### Post by bredman on 2010-09-10
You can't just guess your way through the parameters, -i could mean ignore case in one program, and mean install in another.

To be exact, the safe way to find out is to read the manual. To read the manual for dpkg, type in
man dpkg

Use the key 'q' to quit the manual reader, arrow keys and page up/down keys to move around.

In general, if you are using a new command for the first time, READ THE MANUAL!

If somebody suggests a command on a fourm like this, read the manual, for two reasons
1. Just in case a typo could change a safe command into something dangerous
2. You learn something new every day if you read the man pages

By the way, dpkg is the Debian package manager. Ubuntu is built on the Debian flavour of GNU/Linux.

---

