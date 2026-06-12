---
title: "Eve, Wine, and Shader 2.0"
date: 2010-04-19
forum: New to Ubuntu
---

### Post by Madstan23 on 2010-04-19
OK be nice to me this is my first post here and I have only been using Linux for a few weeks.

So my first attempt at loading a game from windows is EVE.  They used to have a client for Linux but discontinued it after releasing  a new version.  After looking around on-line it seems alot of people have got it to work using Wine.  It installs cleanly for me and shows the starting splash screen, but then throws up an error message that it needs shader 2.0 to work.  I am duel booting and I have it installed and working on the XP side, but my goal is the live as Microsoft free as possible.  Is this an issue with the defualt graphics driver that installed? If so how do I update it?

Thanks,
MadStan

[COLOR=Black]*"Well I don't think there is any question about it. It can only be attributable to human error. This sort of thing has cropped up before, and it has always been due to human error."*[/COLOR] - Hal 9000

---

### Post by scottiw2000 on 2010-04-19
I'm not sure about this game (since I haven't played it), but in general I've found good advice on the WineHQ database ([www.winehq.org](www.winehq.org)). Most games have a page there (in the AppDB) where other people have posted their experiences and at the bottom of the page for each program there are often good tips for getting a program to work.

In general, you will want to have the proprietary (binary-only) driver installed for your video card. This is a lot simpler to do than it used to be since "jockey" does most of the heavy-lifting automatically. Sometimes you do need to play around a bit with your /etc/X11/xorg.conf file, but only do that if you have advice you trust. And always make a backup first.

In any case, if opengl is working running native linux apps, then the problem is probably with getting the right settings and dll files in wine, not with your driver. In general, an excellent resource here is the "winetricks" script which will automatically install all kinds of windows resources into your wine installation. You can get it here: [http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

Finally, there are always the commercial forks of Wine called CrossOver and Cedega. For many games, they do a lot of the fiddling for you. Be careful before you buy, though, since for some games it's actually easier with the open-source version of Wine.

---

### Post by e4uforums on 2010-04-19
Here is the WINE page for EVE:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=15922](http://appdb.winehq.org/objectManager.php?sClass=version&iId=15922)

Also, take a look at PlayOnLinux ([http://playonlinux.com](http://playonlinux.com)).  POL is a front end to WINE - it gives you a nice GUI to manage your programs and WINE versions.  One thing I've learned recently is that the newest version of WINE isn't always the most compatible with the program you're running.  POL gives you an easy way to manage your versions of WINE and assign programs to use certain versions.  It's helped me get a few games running.

I usually use the WINE appdb to find the best settings for a game, then use POL to actually set the WINE version and options.

---

