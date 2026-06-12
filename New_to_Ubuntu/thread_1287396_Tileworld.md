---
title: "Tileworld"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by gspawn69 on 2009-10-10
I have Tile World installed from the repo's, but I'm trying to find where I need to save new level sets so I can access them in the game. I tried searching for the the two intro .dac files but I can't seem to find them anywhere. Can anyone help?

---

### Post by RichardLinx on 2009-10-10
Not sure about the games you mentioned (never heard of them) but you can download a bunch of games for Ubuntu from here: [http://www.playdeb.net/updates/](http://www.playdeb.net/updates/)
You might find something you like.

Edit: Nevermind, this thread is from March..

---

### Post by gspawn69 on 2009-10-10
Lol, well except for my question. :)

This is the one thing I've never liked about installing software from the repositories. If there's additional content that can be added to a game, but requires it to be in a specific directory, it's very difficult to find where that directory is.

---

### Post by ibuclaw on 2009-10-10
If you are trying to search for them in your home directory
```
find ~ -type f -iname "*.dac" 2>/dev/null
```

If you are trying to search for them in the installed package:
```
dpkg -L tworld
```
or
```
dpkg -L tworld-data
```
Regards
Iain

---

### Post by gspawn69 on 2009-10-10
That doesn't turn anything up. According to the instructions for compiling the game yourself, the game should be installed to /usr/local/games - but it's not there.

I guess I could just remove it and compile the game myself and put everything where it's supposed to go, but I was hoping to avoid doing that.

---

### Post by ibuclaw on 2009-10-10
dpkg -L will tell you where the files for that package are located.
If you can't see it, you aren't looking hard enough, or haven't tried.

Games are usually put in /usr/games

---

### Post by gspawn69 on 2009-10-10
I found the game binary in /usr/games, but for some reason it wasn't showing up when I used the "Search for files" option under the Places menu. I still can't figure out where to put the levelsets though.

I would run dpkg -L but I added the game from the Add/Remove option under the Applications menu, and any searches I've done to try and find the .deb file have turned up zilch so far. I'm assuming I need the .deb file in order to use the dpkg -L command, right?

*EDIT* Ok, apparently I can just run the command if I specify the name of the package. That's neat. :) I found the folders I was looking for now. For some reason, they just weren't turning up with my searches. Thanks for the tip, as this should help with any other programs I install by package.

---

### Post by ibuclaw on 2009-10-10
> **gspawn69 said:**
> I would run dpkg -L but I added the game from the Add/Remove option under the Applications menu, and any searches I've done to try and find the .deb file have turned up zilch so far. I'm assuming I need the .deb file in order to use the dpkg -L command, right?

No, you don't need the .deb file to use dpkg -L.

When you install packages, all data is kept internally in a database, some data in files, others in scripts.

---

