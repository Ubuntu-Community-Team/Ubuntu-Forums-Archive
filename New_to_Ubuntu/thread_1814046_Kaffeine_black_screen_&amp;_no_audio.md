---
title: "Kaffeine black screen &amp; no audio"
date: 2011-07-28
forum: New to Ubuntu
---

### Post by gigenieks on 2011-07-28
Hi guys,
really need your help! :sad:

Kubuntu 11.04 64bit. In order to do some "advanced" stuff (like make playlists; default Video player (Dragon player) doesn't have that..) had to install other video player.

I found Kaffeine. So, **KPackageKit** > "kaffeine" Enter > Install
Everything went as it should (no errors).

[COLOR="DarkRed"]**But it doesn't have sound AND picture. NOTHING.**[/COLOR] Just black screen..

[CENTER][SIZE="3"]What I Noticed[/SIZE][/CENTER]

[LIST]
[*]It doesn't matter what kind of file I open ==> screen is black.
[*]Something isn't right with [COLOR="Navy"]**Settings tab!**[/COLOR]
I have only 2 options:
[LIST]
[*]Configure Shortcuts
[*]Configure Kaffeine
[/LIST]
[*]When I open something lower panel (where you can forward video) is going in some random increments. And it is [COLOR="DimGray"]**greyed out!**[/COLOR] (See attachment)
[*]Technical:
[LIST]
[*]When I open DVDRip type movie process: **kaffeine-xbu** uses 20-40% (while slider in lower screen grey are is moving toward end; when it finishes process: kaffeine-xbu, just disappears (meaning - it dont use even 0%)
[*]If I watch on widget called [CPU and System Viewer]("http://www.incunabulum.de/blog-archive/kde-plasma-hacking-the-cpu-and-system-viewer") it graphically "says" that my PC utilizes 50-60%
[/LIST]
[/LIST]

I have Intel Pentium D 820 2.8GHz. So, 40% is too much for DVDRip quality movie..

[SIZE="3"][CENTER]What I have done?[/CENTER][/SIZE]

I searched in:
[LIST]
[*]Ubuntu Forums
[*]Kubuntu Forums
[*]Kaffeine forums
[/LIST]
not much topics or posts about Kaffeine in either of those forums. 

Found some kinda related posts --->


> **Temüjin said:**
> 
It looks like you're using kaffeine in gnome? I'm guessing you don't have phonon configured correctly. Do you know what phonon backend you have installed? Do you have the systemsettings package installed? systemsettings is the KDE configuration GUI that allows one to configure phonon (unfortunately, it can drag a lot of KDE dependencies in with it).


> **James78 said:**
> You can find the deb for 10.10 here. Note: Make SURE you get the dependencies for it too; I tried installing it on my computer to see if it tried for dependencies, it didn't install any, but this may not be the case for you either.
[http://packages.ubuntu.com/maverick/kaffeine](http://packages.ubuntu.com/maverick/kaffeine)

> **jbhtexas said:**
> Hello!

According to the Kaffeine website, there is supposed to be an **xine configuration menu in Kaffeine**, but for the life of me, I cannot find it.

Me too! Moreover I have NO settings at all. Just Configure Kaffeine and 2 options (see attachment)

> 
I found the Kaffeine xine-config file...


In Kaffeine forums:

[Link 1:]("http://hftom.free.fr/phpBB2/viewtopic.php?t=605")
> 
Everything works except one thing. 
After clicking on settings, all i have are 2 choices: 
- configure shortcuts 
- configure caffeine 

which is fine, but.. after clicking "configure caffeine" i'm having only this: 

See attachment for what I see clicking "configure kaffeine"!


I don't have A CLUE how to fix this or what to google or where to ask help... 

I could probably try to launch Kaffeine in Terminal - maybe some useful errors come? (how one launch x program in terminal?)


If someone needs more info just ask.
REALLY need to fix Kaffeine.

---

### Post by PaulW2U on 2011-07-28
I've answered you more fully over on the Kubuntu forums but does this thread - [http://ubuntuforums.org/showthread.php?t=1482558](http://ubuntuforums.org/showthread.php?t=1482558) - help?

It worked for me. :D

---

### Post by gigenieks on 2011-07-28
Yes, I had found that thread before I posted in forums, but when I executed:
```

sudo apt-get install libxine1-all-plugins

```
And instantly tried Kaffeine (I did restart it) - all the same (black screen)..
But then I was tired and decided to watch 2 TV series of 43min each, after that I tried last time Kaffeine, and what do you think?

It worked like charm. :)

Wierd...
(this reminds me Windows - when you try almost everything that one can imagine to fix something and nothing changes, BUT when you don't try to fix it, it fixes magically!! :D :biggrin:

---

