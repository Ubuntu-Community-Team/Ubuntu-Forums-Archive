---
title: "Considering moving to Ubuntu"
date: 2010-02-19
forum: New to Ubuntu
---

### Post by TurnOfTide on 2010-02-19
So... What I do know is that I am making a switch to a linux distro from being a windows user with a decent working familiarity with linux.

What I don't know is if I'm going to use Ubuntu or any of its variants.


Questions about Ubuntu/linux in general (these are nooby questions):

I like command prompts. Can I easily access bash shell from Ubuntu? Like with a simple default key? Is this functionality out of box or is it something you configure? It is important that I can access this anytime/fast/easily.

If you like to develop/program, what language and how has Ubuntu treated you versus other distros?

What do you all do for gaming (to play tf2 for example)
Finally, 
There are various applications that I have found on win32 that I just well, am really used to... I will list each, and hopefully there is a linux version that works just as well.

I will name a win32 app, please tell me if it is available in Linux or name various apps which can replace the win32 one (as I don't intend to use WINE forever)


[LIST=1]
[*] Fiddler2 (HTTP Debugger, works by running a local proxy server to capture http traffic, it **is NOT for IE only**) (Also, ethereal/wireshark isn't as good for http debugging!)
[*] FreeCap (freecap.ru, forces any process's sockets to use SOCKS4/5)
[*] µTorrent - This program is just awsome
[*] Integrated SVN client (Like Tortoise SVN) (For GNOME obviously... unless switching to Kubuntu is the way to go?)
[*] Toad for MySQ (very nice/feature rich GUI program for MySQL)
[/LIST]
     
(I will probably update this list/make a new thread)

---

### Post by chaanakya_chiraag on 2010-02-19
1) It's fairly easy to set up a keybinding for Gnome-terminal (System->Preferences->Keyboard Shortcuts or something like that should do the trick).
2) I use Eclipse and Java.  After I installed sun's official version and set it as default using update-alternatives, it's pretty smooth.  If you use Eclipse, I would recommend manually downloading it, as I'm not sure how often the version in the repos is updated.  Last time I checked (around Hardy/Intrepid I believe), it was at version 2.something where the current version was 3.something.  Yeah, very old :D
uTorrent: An alternative for Gnome is Transmission, but I'm not very familiar with uTorrent and all of its features.
I'm not really sure about the rest, but I'll post a link in my next post for alternatives to Windows programs.

---

### Post by chaanakya_chiraag on 2010-02-19
[http://osalt.com]("http://osalt.com")
[http://www.linuxalt.com/]("http://www.linuxalt.com/")
[http://linuxappfinder.com/alternatives]("http://linuxappfinder.com/alternatives")

---

### Post by Nebelhom on 2010-02-19
I can't answer all your questions, but I'll give it a try for the rest ;)

BASH Shell:

Can be accessed via a terminal in the gui very quickly (like a start menu), you can also assign a hotkey load up the terminal (I assigned it to Ctrl+Alt+X for example). think of that option like 'cmd' in windows

Another option is to switch to a virtual terminal away from the Gui and do your work there (via Ctrl+Alt+F[2-6]; to get back you use Ctrl+Alt+F7)

Programming:
I'm only a beginner (Python), but the switch to ubuntu was pretty much simultanous. Using python is good. you got NetBeans as a development program and it is automatically installed on ubuntu so no extra work to get to a starting point.

Games:
hmm... yes games... ;) I'm keeping a dual-boot because of that reason. (and one or two others) Some people swear by WINE but my experiences with it are really bad. So I guess it dependent on the PC. For me games that should've run with no problems, didn't even get past the load up screen.

If you wanna play games, I'd suggest to use a dual boot ubuntu/windows.

The rest, I can't help you with unfortunately. Sorry. Hope the rest helped.

---

### Post by chaanakya_chiraag on 2010-02-19
Just to clarify: **Python** is installed by default.  **NetBeans** is not.

---

### Post by Nebelhom on 2010-02-19
oh. thanks for the clarification ;)

---

### Post by chaanakya_chiraag on 2010-02-19
No problem :D

---

### Post by amauk on 2010-02-19
> **TurnOfTide said:**
> FreeCap (freecap.ru, forces any process's sockets to use SOCKS4/5)tsocks> **TurnOfTide said:**
> Toad for MySQ (very nice/feature rich GUI program for MySQL)mysql-admin
(assuming you meant a GUI for DB admin)

---

### Post by TurnOfTide on 2010-02-19
Those websites don't have results for things like fiddler2 :O

---

### Post by hortstu on 2010-02-19
I am definitely not the guy to answer this question but maybe this link will help you...

[http://www.zegeniestudios.net/ldc/index.php?select_lang=true](http://www.zegeniestudios.net/ldc/index.php?select_lang=true)

answer the questions and it will make suggestions as to what distro is best for you.  I'm curious as to what it suggests for you so post back.

---

### Post by TurnOfTide on 2010-02-19
> **amauk said:**
> tsocksmysql-admin
(assuming you meant a GUI for DB admin)

Any program that is good for performing select queries, then saving the results to spreadsheets/csv files. Basically I just like toad because it has these features + many more.

---

### Post by lavinog on 2010-02-19
Wine has come very far in the past couple of years.
Some users swear that there is no replacement for utorrent, but they also claim it works great in wine. [http://appdb.winehq.org/objectManager.php?sClass=application&iId=6824](http://appdb.winehq.org/objectManager.php?sClass=application&iId=6824)

I am not familiar with the other apps, but the nice thing about linux is that it doesn't cost anything to give it a try.  If you can't find an alternative for those apps, see if they would work in wine.

---

### Post by TurnOfTide on 2010-02-19
My results for the distro test (all 100%):

**OpenSuSE**


**Mandriva**


**Ubuntu**


**Kubuntu**


**Linux Mint**


90%:
**Fedora**

---

### Post by TurnOfTide on 2010-02-19
Another question:

Should I go for Ubuntu or Kubuntu if I want to primarily use linux for development in Ruby and Java using SVN for revision control.

---

### Post by ajgreeny on 2010-02-19
> **TurnOfTide said:**
> Another question:

Should I go for Ubuntu or Kubuntu if I want to primarily use linux for development in Ruby and Java using SVN for revision control.
It will not matter in any way which you choose of those, both are basically the same system with a different DE pasted on top.  Gnome or straight Ubuntu is probably best served by these forums, but kde or kubuntu is many users preferred DE.

---

### Post by TurnOfTide on 2010-02-19
Also, will the latest stable version of Ubuntu come with default codecs for flash/mp3s/avi/etc.

---

### Post by qyot27 on 2010-02-19
> **TurnOfTide said:**
> Also, will the latest stable version of Ubuntu come with default codecs for flash/mp3s/avi/etc.
Codecs/media in general are often restricted by patents, so you'll need to enable the Universe and Multiverse repositories and/or add Medibuntu to the repo list.  The support does not come by default, but can be easily grabbed with apt-get or Synaptic.


As for uTorrent, I switched to Halite on Windows after uTorrent got bought out.  On Ubuntu, Deluge is a very close fit to either of them.

---

### Post by da burger on 2010-02-19
Regarding programming I program at a VERY low level in ruby. I didn't have any problems moving my programs across from windows to ubuntu apart from one which was my own fault (I deleted a file with about a million numbers generated by one of my programs). I use geany to program in because I don't like how more complex IDEs force you to make projects and develop their way.
So yes there are lots of good IDEs available.
Angus

---

