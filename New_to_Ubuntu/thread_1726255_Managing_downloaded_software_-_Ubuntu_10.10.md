---
title: "Managing downloaded software - Ubuntu 10.10"
date: 2011-04-10
forum: New to Ubuntu
---

### Post by joga24 on 2011-04-10
This question is coming from a long time Windows user, where any software I downloaded off the internet would appear on my Add/Remove programs list. How do I get Ubuntu to recognize software in such a way? For example, I downloaded Eclipse and the demo for Atom Zombie Smasher off their respective websites. Both programs work fine, but I don't have the power over them that I'd like. They aren't recognized in the Ubuntu Software Center or Synaptic Package Manager, and I do not see a way to uninstall them if I chose to do so. Also I can not run either of these programs from the terminal. Currently, they are both in my /home folder.

Any help is appreciated.

---

### Post by NightwishFan on 2011-04-10
If you install .deb files they will integrate with the package manager.

---

### Post by ~Plue on 2011-04-10
well.. the package manager can't keep track of everything.. it knows only what has been done through it, 

as for running the programs from the terminal: you can use the full path to the executable.
if you dont want to use explicit path, then you'll need to add the directory to your PATH variable in .bash_profile or /etc/profile

---

### Post by indusarts on 2011-04-10
Unfortunately, this information does not help a beginner.

I have bunches of installed packages that I see in Synaptics Package Manager that are not in my menus.  Right now I am trying to demo back up programs.  DejaDup shows up as does Simple Backup, but things like Bacula and Backupninja don't (many others, as well).

Why do some show in menus and some don't?  How do I run installed packages that aren't in the menu?  How do I get them in the menu?

Thanks

Mark Springer

---

### Post by NightwishFan on 2011-04-10
Not all applications need a menu entry. You can make one if you so with, there is a program for that under System -> Preferences.

---

### Post by indusarts on 2011-04-10
Where would that be?  I just checked and don't see anything other than selecting what shows on "Main Menu", but the programs that are installed aren't there.

This has all been brought about by the fact that none of the sync or backup programs allow me to access network files or folders that are shown as mounted on the desktop.

BTW, I am using 10.4, not 10.10 if that explains the discrepancies.

Thanks

Mark Springer
industrial arts

---

### Post by NightwishFan on 2011-04-11
A good example that confused me when I first started was 7zip. I used that program back on Windows so I installed it from add/remove. I noticed it was not in the menus. I quickly learned that it was a command line program, and as such would not appear in the menu. The package just transparently added 7zip support to various archive frontends.

Any program intended to use the from the GUI that you install from the software center will have a menu. If not, then it is a bug. They may/may not have a menu entry depending on what the package is. Some do not intend to add a menu entry as they are only supporting package or command line program.

Programs you download yourself in .deb format while show up in the database to be removed later. Other programs (such as compiling your own software or other binaries such as games like Amnesia The Dark Descent) will not show up in the database and you will have to manage them yourself.

---

### Post by madjr on 2011-04-11
usually anything installed from software center should show up on the menu

also not all programs have a gui, some are command line tools, usually for administrators.

---

### Post by indusarts on 2011-04-11
*Other programs ... will not show up in the database and you will have to manage them yourself.*

Sure I understand about programs like 7zip (I use it in Windows as well, but only from the right click menu), but some of them SHOULD have GUIs or menu entries.  How do I manage them manually?

Thanks to all for your help, much appreciated!

Mark Springer
industrial arts

---

### Post by NightwishFan on 2011-04-11
> **indusarts said:**
> Sure I understand about programs like 7zip (I use it in Windows as well, but only from the right click menu), but some of them SHOULD have GUIs or menu entries.
All programs that have a GUI have a menu entry. I do not understand what you are getting at. If they do not have one it is either a bug or they are intended not to.

> How do I manage them manually?
It depends on the program. Some programs you install from source need to just have their folder deleted manually to uninstall.

> Thanks to all for your help, much appreciated!
No problems.

---

### Post by indusarts on 2011-04-11
OK

I went back to really research some of the programs I am having trouble getting to work and I think I have it a little more sorted.  One of the programs - Bacula - still doesn't show, but I believe it's due to an earlier install problem and I can't fully uninstall it.

Thanks again for your help.  I have spent hours and hours trying to figure out various aspects of both Ubuntu and Mint distros and most of the "help" I get is not really helpful. A large part of the posts and tutorials contain errors and misinformation.  You've actually provided me with usable information.

Mark Springer
industrial arts

---

### Post by QLee on 2011-04-11
[QUOTE=indusarts]
I went back to really research some of the programs I am having trouble getting to work and I think I have it a little more sorted.  One of the programs - Bacula - still doesn't show, but I believe it's due to an earlier install problem and I can't fully uninstall it.[/QUOTE]

This is a good way to describe things, using the actual name of the program you mean to discuss, using general terms like "some" of the programs don't show, is not. It would be possible to work with you and sort that out. However, the truth is you hijacked the thread of jaga24 and that is usually considered rude, it's usually considered appropriate to post your own question because questions that come after the original poster's question often tend to take over and make the original question be forgotten. No foul, but as a new user you probably did not realise it.

[QUOTE=indusarts]Thanks again for your help.  I have spent hours and hours trying to figure out various aspects of both Ubuntu and Mint distros and most of the "help" I get is not really helpful. A large part of the posts and tutorials contain errors and misinformation.  You've actually provided me with usable information.
...[/QUOTE]

Many of the users here, especially in the Absolute Beginners Topics, don't know much more than you do, some of them probably less but they still try to help. People's skills vary widely and this distribution (Ubuntu) changes rapidly (new release every 6 months), that accounts for some of the "errors" that you have noticed and poor troubleshooting skills and logic account for most of the rest. It's a fact of life with peer support done by volunteers and that is only about the good-hearted volunteers. Because we are a sub-population of the real world there are even a handful of people who post with malicious intent or just to play. With a paid staff of troubleshooters much of what you describe could be fixed but then you'd have to pay for help. All in all, the system works fairly well and I imagine you will find that over time you will learn enough to evaluate the advice given. If you become proficient in forum search, you will find that most of your inexperienced user questions have been answered many times. The community help wiki has a lot of good stuff too. For example, the page about backup.
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
There are links on that page for wiki pages of documentation for some of the utilities you've mentioned.

Try to avoid the error of wanting to know all the answers soon after starting to use a system that is very different from what you are already familiar with.

As to putting things in the menu maybe have a look at this:
[http://www.ubuntugeek.com/howto-add-entries-in-gnome-menu.html](http://www.ubuntugeek.com/howto-add-entries-in-gnome-menu.html)

Often a program can be run from a terminal window or a Alt+F2 dialogue by entering the program's name (if the executable binary has the same name). 

If you have installed a program you can read the manual page for the program by entering the command, man program_name. (i.e. man bacula)

If you are using the synaptic GUI for installing you can see where it has put all the files installed with the package under the properties of the package. (This might help you with paths for your menu entries.)

It will take time and probably be frustrating for a portion of that time as does learning any worthwhile thing.

---

### Post by QLee on 2011-04-11
blanked a dup

---

### Post by QLee on 2011-04-11
[QUOTE=joga24]This question is coming from a long time Windows user, where any software I downloaded off the internet would appear on my Add/Remove programs list. How do I get Ubuntu to recognize software in such a way? For example, I downloaded Eclipse and the demo for Atom Zombie Smasher off their respective websites. Both programs work fine, but I don't have the power over them that I'd like. They aren't recognized in the Ubuntu Software Center or Synaptic Package Manager, and I do not see a way to uninstall them if I chose to do so. Also I can not run either of these programs from the terminal. Currently, they are both in my /home folder.

Any help is appreciated.[/QUOTE]
First, I'd like to caution you about downloading programs from the Internet. If you stick to the official Ubuntu repositories the programs have been checked and verified as safe, if you get something somewhere else it may or may not be safe to use.

See if this helps you create menu items.
[http://www.ubuntugeek.com/howto-add-entries-in-gnome-menu.html](http://www.ubuntugeek.com/howto-add-entries-in-gnome-menu.html)

Those programs are probably not in your path, so you would have to include the complete path for the command in order to run them. If you make a folder in your home called /bin and put those executable binaries in there you could just enter the command for the binary without the path string after your next login because they would then be in your path. That being said, I want to repeat the caution about using files you get from places unless you can trust the source.

---

### Post by Locke_99GS on 2011-04-11
@indusarts
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by indusarts on 2011-04-12
Once again, thank you very much to all who have posted replies.

Firstly - sorry for hijacking a thread.  I finally found relevant info and jumped right in :#

What I do for a living is fix and troubleshoot Audio/Video/Small Network installations as well as repair audio equipment, so finding solutions is what I do.  I just want to point out that it's pretty difficult to find straight forward answers to problems that I am having with Linux.  Generally before I post I will devote as much as several hours searching everywhere for answers to my problems.  Often I can find no clear resolution.

Which is too bad because I would love to be a Linux fanboy.  But - from my experience - it's way too difficult for anyone who's not seriously technically inclined.  

So once again - thanks.  Your posts have pointed me in directions that have helped me understand Linux, though maybe still not solved my problems.  But I'm still not ready to give up ;)

Mark Springer
industrial arts

---

### Post by NightwishFan on 2011-04-12
> **indusarts said:**
> from my experience - it's way too difficult for anyone who's not seriously technically inclined.

I think this depends on the hardware in most cases. I am not technically inclined, just curious and like freedom, and I managed to make over 4000 support posts. It takes time, patience and working hardware to get started with Linux. As time goes by, hardware will be less and less of a problem.

---

### Post by QLee on 2011-04-12
[QUOTE=indusarts3]...
Firstly - sorry for hijacking a thread.  I finally found relevant info and jumped right in :# [/QUOTE]

Yes, that is a normal and common response, especially after searching a long time for relevance. 

[QUOTE=indusarts3]What I do for a living is fix and troubleshoot Audio/Video/Small Network installations as well as repair audio equipment, so finding solutions is what I do.  I just want to point out that it's pretty difficult to find straight forward answers to problems that I am having with Linux.  Generally before I post I will devote as much as several hours searching everywhere for answers to my problems.  Often I can find no clear resolution.[/QUOTE]

A good troubleshooter has a distinct advantage for the task of learning GNU/Linux, approaching a problem logically (after a certain amount of learning) works for fixing cars or audio equipment or system analysis. Just so you know, I too can often find no clear solution written down somewhere.

[QUOTE=indusarts3]Which is too bad because I would love to be a Linux fanboy.  But - from my experience - it's way too difficult for anyone who's not seriously technically inclined.  [/QUOTE] 

How long have you been using Ubuntu? (no need to answer, just think about other worthwhile things in your life and if they took time to learn)

Incidentally, "Linux fanboy" isn't a compliment.

[QUOTE=indusarts3]So once again - thanks.  Your posts have pointed me in directions that have helped me understand Linux, though maybe still not solved my problems.  But I'm still not ready to give up ;)
...[/QUOTE]

Yes, well in a reply above I mentioned that we (someone here) would be able to help you with the problem of not being able to uninstall bacula if you would post a thread regarding that problem. I see you haven't done that. Also, if after 24 hours, or so, no one has replied to a post you've made, it's considered acceptable to "bump" (add a post to your thread to bring your question back to the top of the list). Sometimes you need to be in a different timeslice to find the person with the answer you need.

Being "not ready to give up" is a good sign.

---

### Post by indusarts on 2011-04-12
> **QLee said:**
> Being "not ready to give up" is a good sign.

However, after finding that my smb.conf has somehow changed again over night, I am closer to giving up.  But that's a different post.

Mark Springer
industrial arts

---

