---
title: "how well do games work on ubuntu?"
date: 2010-09-05
forum: New to Ubuntu
---

### Post by flufficus on 2010-09-05
i like to play games i find on the interent alot(mostly because i have nothing else to do) and i was wondering how well do games i download on my computer work with ubuntu?

---

### Post by Ocxic on 2010-09-05
Most likely not at all.
You can check with the WineDB to see if the games is supported with WINE.
OR your can run a virtual machine with Windows.

---

### Post by Spice Weasel on 2010-09-05
Windows Games:

[http://appdb.winehq.org/](http://appdb.winehq.org/)

Linux Games: (There are hundreds of free games ready to be played here!)

[http://www.linuxgames.com/](http://www.linuxgames.com/)
[http://www.happypenguin.org/](http://www.happypenguin.org/)
[http://www.lgdb.org/](http://www.lgdb.org/)
[http://www.playdeb.net/](http://www.playdeb.net/)

---

### Post by peptobismal on 2010-09-05
Actually, Wine's database has gotten very well done. Their site is very easy to understand. I mean I normally go for Platinum ratings so I don't see any glitches. 

If you look on their database of applications they will tell you all the games that they have tried to get running... And right there on the first page they have their top platinum (which is usually all games), gold, and bronze. So, anything you want to know go there... or you can always use a Virtual Machine of some sort and use them all! However, a virtual machine will imitate hardware and give generics for some... so, you might not get a pleasing frame rate and so forth.

---

### Post by peptobismal on 2010-09-05
> **Spice Weasel said:**
> 
[http://www.linuxgames.com/](http://www.linuxgames.com/)
[http://www.happypenguin.org/](http://www.happypenguin.org/)
[http://www.lgdb.org/](http://www.lgdb.org/)
[http://www.playdeb.net/](http://www.playdeb.net/)
None of the playdeb.net downloads are working for me...

---

### Post by Spice Weasel on 2010-09-05
> **peptobismal said:**
> None of the playdeb.net downloads are working for me...

It's much easier to install their repository, hover over the download link and apt-get the package name.

---

### Post by Elentir on 2010-09-05
I use PLayOnLinux from time to time. I had Starcraft (Classic) running, and hopefully have the money soon to try Starcraft II. I tried some other games like Heroes of Might and Magic V and Bioshock (1) but there was always something wrong (sound didn't work properly, game went too slow). I even tried Microsoft Office 2007, but no result. Best thing I got running so far was Guild Wars. 

Bottomline, getting MS games running on Linux is not guaranteed, and will ask a lot of patience, hence my dual boot Lucid/Vista.

[http://www.playonlinux.com/en/](http://www.playonlinux.com/en/) (or via Software Center)

---

### Post by Spice Weasel on 2010-09-05
Why aren't you dual booting XP or 7?

Anyway, if you're interested in Windows games then a dual boot is the best way to go for newer games, older games mostly run fine in WINE. Nevertheless, there is a great selection of free games for Linux.

---

### Post by Elentir on 2010-09-05
I have XP running in VirtualBox. Vista, well it came with my PC, didn't have too many problems, so I didn't bother. It just exists to play games.

---

### Post by HermanAB on 2010-09-05
You are approaching it all wrong.

Linux is the game.

---

### Post by Elentir on 2010-09-05
Yes, but sometimes I just like to blow someone's head off in a neat game. Unreal Tournament is a bit too old for me, too many pixels.

---

### Post by kwacka on 2010-09-05
Could you give us an example of a game you do like to play on any operating system?

---

### Post by linux18 on 2010-09-05
> **HermanAB said:**
> You are approaching it all wrong.

Linux is the game.
+1 except fallout 3 and the recently reannounced duke nukem forever

---

### Post by flufficus on 2010-09-05
the game i would like to play is called requiem momento mori(pretty sick game i tottaly recommend it) i have wine and playonlinux installed but sadly i cant play it couse it keeps on crashing:(

---

### Post by philinux on 2010-09-05
Alien Arena from the repos aint bad but PS3 is my gaming machine ;)

---

### Post by linux18 on 2010-09-05
> **philinux said:**
> Alien Arena from the repos aint bad but PS3 is my gaming machine ;)
you getting fallout new vegas?

---

### Post by Elentir on 2010-09-05
> **kwacka said:**
> Could you give us an example of a game you do like to play on any operating system?

Roller Coaster Tycoon 3 ;)

---

### Post by kaldor on 2010-09-05
Not that Linux isn't capable of playing games, it's that not many publishers make their games available for Linux.

- Under WINE, Jedi Knight: Jedi Academy works flawless; singleplayer sucks, but multiplayer is awesome.

- Quake 4 

- Doom 3 

- Unreal Tournament 2004

- Savage 1 and 2

- Urban Terror (free team-based FPS)

- Neverwinter Nights

- RuneScape (it's a browser-based MMO)

- Under WINE, World of Warcraft runs flawless so I hear

I'm sure there are more good games. These are just some popular/commercial/well-known games.

---

### Post by arvevans on 2010-09-05
While the thread originator may be a troll, his/her post would have been more definitive if the question was:

[INDENT]How Well Do Microsoft Games Run In Linux?
or
How Well Do Linux Games Run In Linux?"[/INDENT]

Then we would have a better idea of the actual question
and could provide better answers instead of speculation.

---

### Post by Elentir on 2010-09-06
Troll or not I can get some information on games on Ubuntu. In a couple of weeks I'll try to install Starcraft II, and that will be, to return to HermanAB's words, a game in itself. But games are fun and interesting, so I'm looking forward installing the game on Linux and I will definitely ask for advice here, because I know it won't run out-of-the-box.

---

### Post by peptobismal on 2010-09-11
UrbanTerror runs really well... I play it as a substitute to CS 1.6... even though it has all those weird movements like sliding and stuff that I can not for the life of me get used to...

---

### Post by sidzen on 2010-09-11
HermanAB has it right -- do this, if you can:

[PHP]sudo apt-get install -f gnome-games [/PHP]
[PHP]sudo apt-get install gnome-games-extra-data[/PHP][PHP]sudo apt-get install slingshot[/PHP]If unable, then go to [https://help.ubuntu.com]("https://help.ubuntu.com/") and look up what you need (*i.e*. "add repos to /etc/apt/sources.list")

---

