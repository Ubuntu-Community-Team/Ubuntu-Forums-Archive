---
title: "Installing applications from tar.bz files.."
date: 2011-03-03
forum: New to Ubuntu
---

### Post by p1049461 on 2011-03-03
Hi, I am trying to install firefox 4.0.12 (beta) on ubuntu server 10.10. I have a .tar.bz file and once extracted it simple creates a directory structure with files in it. If I understand correctly I can just run firefox by executing the firefox binary that is part of the directory structure.

However In the interest of learning about linux I have some questions. 

1) how does one 'Install' the application. in other words make sure its accessible via the gnome gui start menu. Is it as simple as add new item to the menu and select the firefox binary or should I be doing more than that.

2) where should the firefox binaries extracted to. In other words what 'Program Files'  directory equivalent in linux / ubuntu

3) how do I make sure that I can execute the firefox binary from the shell from any directory without giving the full path to executable every time. This question is more for other applications that I may 'manually' install in the future and not so much for firefox.

Your help is appreciated !

---

### Post by PsychPop on 2011-03-03
Well any tar.bz files I've downloaded I just open up a terminal move to the extracted directory and run ./configure followed by make followed by make install, but I'd imagin there would be an install file that tells you how to install in the extracted files.. Hope this helps. :)

---

### Post by kn0w-b1nary on 2011-03-03
Once in the directory where you extracted the .bz2, type in terminal:```
./configure
```
```
make
```
```
sudo make install
```

---

### Post by mcduck on 2011-03-03
> **p1049461 said:**
> Hi, I am trying to install firefox 4.0.12 (beta) on ubuntu server 10.10. I have a .tar.bz file and once extracted it simple creates a directory structure with files in it. If I understand correctly I can just run firefox by executing the firefox binary that is part of the directory structure.

However In the interest of learning about linux I have some questions. 

1) how does one 'Install' the application. in other words make sure its accessible via the gnome gui start menu. Is it as simple as add new item to the menu and select the firefox binary or should I be doing more than that.

2) where should the firefox binaries extracted to. In other words what 'Program Files'  directory equivalent in linux / ubuntu

3) how do I make sure that I can execute the firefox binary from the shell from any directory without giving the full path to executable every time. This question is more for other applications that I may 'manually' install in the future and not so much for firefox.

Your help is appreciated !

Since it's not a program you'd have to compile yourself, but just works by extracting it somewhere, you have two options where to put it.

If you just want the program for a single user, then that suer's home directory would be just fine location. And if you want to install it for everybody, then /opt is intended for programs that come outside of the distribution's package management.

If you want the program to be executable simply by using it's name (instead of full path to the executable file) you can create a symbolic link to it's executable file, either in ~/bin (if installing for single user) or in /usr/share/bin (for all users).

What comes to a menu entry, for a single user creating the menu entry just by using the menu editor (right-click on the Applications-menu and select "Edit Menus") would be the easiest way. If you want to create a menu entry for all users you'd have to create a .desktop file for it in /usr/share/applications.

Edit: What comes to equivalent of "Program Files" in Windows, there isn't such thing. When programs are installed through package management, they don't go into any single place like in Windows, but instead all the programs files are put into different locations based on their purpose. For example the executables are put into /usr/share/bin, system-wide setting files into /etc, documentation and help files into /usr/share/doc and so on. The rest of the program's files usually end in /usr/share. While this might seem strange first, it's actually very effective way of handling files once you learn the common locations. You never need to browse around to look for some program's executable, for example, you'll know you will find it in /usr/share/bin just like pretty much every other program's executable... :)

---

### Post by peculiar penguin on 2011-03-03
> 1) how does one 'Install' the application. in other words make sure its accessible via the gnome gui start menu. Is it as simple as add new item to the menu and select the firefox binary or should I be doing more than that.It's an archive, there is nothing to install, just add a launcher where ever you want (or don't if you prefer to use the command line). 
You may also want to change the system default browser (Preferences > Preferred Applications) and create a symlink to the mozilla plugin directory, e.g.
```
 sudo ln -s /usr/lib/mozilla/plugins /opt/firefox/plugins
``` (assuming you extracted to /opt).

> 2) where should the firefox binaries extracted to. In other words what 'Program Files' directory equivalent in linux / ubuntuThere is no such thing in Linux. Extract it to a subdirectory of your home directory (if you're the only user) or to /opt (if other users are going to use it as well).

> 3) how do I make sure that I can execute the firefox binary from the shell from any directory without giving the full path to executable every time. This question is more for other applications that I may 'manually' install in the future and not so much for firefox.```
sudo ln -s /opt/firefox/firefox /usr/local/bin/firefox
```(again assuming you extracted to /opt).

---

### Post by p1049461 on 2011-03-03
@mcduck

Thanks for the explanation and the insight. As a new user, I find it hard to understand how spraying files all different locations is more efficient than putting all files in 1 dedicated folder is more efficient. I guess what I am not clear on is the fact that wouldnt spraying files all over the places make uninstall difficult..and eventually the file system would end up looking like a windows registry! when I see files being put all over the place I find it analogous to a windows registry and hence think its a mess. May be I need to understand the file system directory structure a little bit better. I'd appreciate it if you or someone else reading this post can point me to good article explaining it.

Thanks

---

### Post by p1049461 on 2011-03-03
@peculiar penguin

thanks for the preferred applications tip.

Also since you mentioned the /usr/local directory .. I decided to see whats already in there and what I found was that /usr and /usr/local have almost the same sub directories. why is that ? can you tell me what is the purpose of having almost identical directory structures in this fashion. 

Thanks,

---

### Post by mcduck on 2011-03-03
> **p1049461 said:**
> @mcduck

Thanks for the explanation and the insight. As a new user, I find it hard to understand how spraying files all different locations is more efficient than putting all files in 1 dedicated folder is more efficient. I guess what I am not clear on is the fact that wouldnt spraying files all over the places make uninstall difficult..and eventually the file system would end up looking like a windows registry! when I see files being put all over the place I find it analogous to a windows registry and hence think its a mess. May be I need to understand the file system directory structure a little bit better. I'd appreciate it if you or someone else reading this post can point me to good article explaining it.

Thanks

No, it doesn't make uninstalling difficult or create a mess in any other way, simply because all this is handled automatically by the package management. :)

Things are only different with programs you install outside of the package mangement, which is why you'd usually put such programs into /opt, where you can easily find them yourself. If you install some additional software from source code, you might want to use *checkinstall* which will create a .deb package out of the complied program and then install it through the package management, making clean uninstall very easy.

So, it's not a problem from the system's point of view, the only issue would be new users who might have troubles figuring out where all the files went. But you'll son learn the locations that matter most from user's perspective (/usr/share/bin for executables, /etc for config files and /usr/share/doc for documentation. The rest you'll rarely need). After that things really are much easier than in Windows, where programs actually may end in folders named by the company which created that program, using their own non-standard folder structures for additional files and so on... Instead of having to figure out the specific structures and locations for every program you have, you only need to learn the generic locations and those will pretty much apply to every program you'll ever install (and same of course works from system's point of view, making the use of shared libraries and such very easy without having to maintain a registry like Windows does).

---

### Post by peculiar penguin on 2011-03-03
> As a new user, I find it hard to understand how spraying files all different locations is more efficient than putting all files in 1 dedicated folder is more efficient.Historic reasons/define "efficient".

> I guess what I am not clear on is the fact that wouldnt spraying files all over the places make uninstall difficultYou're supposed to use packages (released specifically for your distribution and release) and the system's package management tools whenever possible, which will keep track of everything automagically. 

Once you start downloading stuff manually and sticking it into your system behind the back of the package management system, there is a certain risk of clogging/damaging/breaking your system. That's why you should stick with Ubuntu's official repositories and package management system unless you have a good reason not to. And if you do, this stuff goes to special locations (e.g. an application specific subdirectory in /opt, sort of like what you do in Windows) where it won't conflict with the rest of the system.

> May be I need to understand the file system directory structure a little bit better. I'd appreciate it if you or someone else reading this post can point me to good article explaining it.> Also since you mentioned the /usr/local directory .. I decided to see whats already in there and what I found was that /usr and /usr/local have almost the same sub directories. why is that ? can you tell me what is the purpose of having almost identical directory structures in this fashion. Short answer: That's the way it is, deal with it :P
Long answer: [LinuxFilesystemTreeOverview]("https://help.ubuntu.com/community/LinuxFilesystemTreeOverview"), [Filesystem Hierarchy Standard]("https://secure.wikimedia.org/wikipedia/en/wiki/Filesystem_Hierarchy_Standard")

---

