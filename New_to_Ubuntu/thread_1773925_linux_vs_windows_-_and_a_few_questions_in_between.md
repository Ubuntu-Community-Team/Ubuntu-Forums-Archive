---
title: "linux vs windows - and a few questions in between"
date: 2011-06-02
forum: New to Ubuntu
---

### Post by -Outlaw- on 2011-06-02
Hey again peeps, 
 
Right, I love linux and what it stands for but I'm having trouble making the FULL change to linux being my main system. 
 
A few questions. 
 
1.  What is linux's equivalent to windows "Programs Files" directory? In my  experience it seems to change? Is that true? or is it me compiling  source in the wrong folders? Having said that I've installed .deb files  that don't seem to be in the "Start" menu afterwards? 
 
2. Why don't all programs I install from .deb's end up in the "Start" menu? 
 
3.  I get that most linux distro's are "find out for yourself" albeit with  tremendous documentation on the web but what is the best  Windows>Linux starter OS for beginners? 
 
 
4. I myself am  fairly good with computers but I struggle reading the documentation  because of dyslexia but learn extremely fast whilst watching  someone/YouTube when I understand WHY I'm doing it. Is there a forum  that caters for people like me? even if its just the basics? 
 
 
I'm  really sorry for bombarding you with N00B questions but I really want  to go Linux all the way but my knowledge inhibits me :(

---

### Post by lykwydchykyn on 2011-06-02
> **-Outlaw- said:**
> Hey again peeps, 
 
Right, I love linux and what it stands for but I'm having trouble making the FULL change to linux being my main system. 
 
A few questions. 
 
1.  What is linux's equivalent to windows "Programs Files" directory? In my  experience it seems to change? Is that true? or is it me compiling  source in the wrong folders? Having said that I've installed .deb files  that don't seem to be in the "Start" menu afterwards? 

There isn't one.  Basically, stuff installed from the repos will most likely put its executable in /usr/bin and a shortcut in /usr/share/applications.

If you compile something, it usually ends up under /usr/local somewhere.

There *is* a logic and a pattern to it, but it's not done the way Windows does it.  For the complete story, see this: [http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)
> 

 
2. Why don't all programs I install from .deb's end up in the "Start" menu? 
 

Not a Gnome/unity user, but AFAIK if it puts a shortcut in /usr/share/applications, it should show up in the menus.  If it doesn't, that's either by design (non-GUI apps, for instance), or bad packaging.  If it's the latter, someone probably needs to submit a bug.

---

### Post by silex89 on 2011-06-02
Hi there! :D


[LIST=1]
[*]Usually, all the programs are installed in your home directory (/home/yournickname) and /usr/bin, but the folders are hidden, you can view them if you press Ctrl+H while you are in your home directory. If you wanna manage the programs you have installed, I would recommend you to use Synaptic, the package manager of Debian/Ubuntu. You can uninstall and upgrade your software from there.
[*]Some .deb's don't end up in your start menu because some of them are libraries (also called dependencies) or scripts programs (applications that you run by typing in the console)
[*] Hmmm, what helped me to figure out my way in Linux was googleing every doubt, problem or issue I had, almost everything has already been posted here or some other ubuntu forum.
[*]I don't know, maybe this forum could help, but in my experience, is not necessary to know why something has to be made that way, I just accepted that and moved on to learn more things about the system. Maybe is important to know why in a basic context, but any further from there, I get no point of doing that.
[/LIST]

Best luck and regards :D

---

### Post by dFlyer on 2011-06-02
Can't answer for windows as I haven't use it in years. As far as linux it's not windows, nor would I want to compare it with windows. Ubuntu menu's mainly depend on what desktop environment your using. Remember an OS is a personal choice. If you like windows, use it. If you like linux, use it. But please don't, don't try and compare them, as they are not the same. If your looking for the program directory you have /usr/ and /opt/.

---

### Post by iansane on 2011-06-02
I think lykwydchykyn did a pretty good job answering your questions and better than what my answers were going to be so I won't mess with that.

I did want to say that there's nothing wrong with wanting to know why and how rather than just accepting it. The people who fix things when they don't work right are the ones who actually know the why's and how's.

I also think comparing Linux to Windows is a good thing in the sense of learning "this is how linux does it" and "this is how windows does it" and why they don't do it the same way. But at the same time have to agree that they are not the same. It's comparing apples to oranges.

Similarities they do have is that each one has a place for executables, a place for system wide config files, and a place for user specific files.

Compare Documents and settings/yourname/application settings (hidden in windows) to /home/yourname/.someprogram . They both contain user specific application settings.

---

### Post by dniMretsaM on 2011-06-02
Your best bet for a Windows-like experience on Linux is Kubuntu (KDE). It has a panel on the bottom (like the Windows task bar) and the Kickoff menu (like the Start menu), and it has the close/minimise/maximise buttons on the right (Unlike Ubuntu/GNOME/Unity). The biggest difference is that it is a single-click environment. Meaning you only click on icons, folders, documents, etc. once to open it. It's more efficient than double clicking, but it takes a little getting used to. Any of the above can be changed to suit your preference (including the single-click setting). A lot of the other DEs can be changed to look a lot like Windows, but KDE is the best out-of-the-box.

---

### Post by frogo on 2011-06-02
> **-Outlaw- said:**
> 
3.  I get that most linux distro's are "find out for yourself" albeit with  tremendous documentation on the web but what is the best  Windows>Linux starter OS for beginners? 
 

Have a look here: 
[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)

Perhaps, in particular this:
[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows/Configuring](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows/Configuring)
 
> **-Outlaw- said:**
> 
4. I myself am  fairly good with computers but I struggle reading the documentation  because of dyslexia but learn extremely fast whilst watching  someone/YouTube when I understand WHY I'm doing it. Is there a forum  that caters for people like me? even if its just the basics? 
 
 
I don't know. I struggle with most documentation myself. I usually can't understand things written like bug reports. There are a few very well written HowTos on this forum, and more less accessible or less well written ones:
[http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100)

In my experience, I've regularly accessed pages from one and the same resource, either via Google searches or by stumbling upon links on this forum. That resource is: 
[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/) (where the first two links above come from). 

However, I have to admit that I find the navigation of these web pages rather difficult and not particularly intuitive. It's not easy to see where to go next nor what it is all about nor even manage recognise what you may be looking for. 

So best may be to do google searches on that site. For example, something like:
site:help.ubuntu.com/community/  windows

hope this helps, 
cheers

---

### Post by -Outlaw- on 2011-06-03
Firstly I'd like to thank you all for your input.
It looks like I have a quite a bit of reading to do today.

---

### Post by ivanovnegro on 2011-06-03
The internet is your biggest friend here, when I was a noob :P, I learned almost everything googling it out, that is normal as you can just load a whole Linux system from the net. There is enough information to learn about Linux/Ubuntu and of course this community and forum. Of course not every site is perfect or "serious" enough but there are tons of web sites and good documentations for Ubuntu, I have in my mind the outstanding documentation IMHO of OpenSuse, Debian and especially Arch Linux.

---

