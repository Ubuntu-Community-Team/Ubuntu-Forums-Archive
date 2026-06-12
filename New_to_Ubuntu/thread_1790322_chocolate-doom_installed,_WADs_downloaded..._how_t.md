---
title: "chocolate-doom installed, WADs downloaded... how to get it all working?"
date: 2011-06-24
forum: New to Ubuntu
---

### Post by Sablewings on 2011-06-24
I've been trying to figure this out for hours

Details:

I have Ubuntu 10.04 Lucid, and installed "chocolate-doom" using the Ubuntu Software Centre. This installed files in the following places -

 - usr/share/doc/chocolate-doom (Documents inside named: Bugs, changelog.debian.gz, changelog.gz, copyright, news.gz, README and TODO 

 - usr/share/games/doom/ (Files inside named: doom1.wad and prboom.wad)

 - usr/games/chocolate-doom (Files are all executable game files. Clicking on chocolate-doom starts up the Doom title screen with music, then the screen goes black and then the window closes again)

I managed to get hold of some actual doom wad files - for Doom 1, 2 and 3. (named Doom2.wad  etc)  At the moment these are in my home folder in a folder called "game info." (/home/game info)

All the guidelines I have read point to putting these wad files in "the same directory as the executable file" - which I assume to mean straight into the usr/games/chocolate-doom folder, or the share one...? 

Would this work?  Problem is that I can't paste them in either place because I don't have root priviliges for either folder. had a brief go at moving them with sudo mv  or gksudo command...but perhaps I was typing the filepaths incorrectly. (I used my user name instead of just "user" - would that upset it?)

I don't want to try anything more at this point til I understand what commands to use better...

As an alternative thing to try I copied all the installed files into a new folder in my home folder, then clicked on the copy of the executable file. Everything in the same folder...but of course it didn't work. ;)

Any advice would be much appreciated! I played Doom2 when it first came out... feeling nostalgic... ;)

---

### Post by spcwingo on 2011-06-24
See here:

[http://manpages.ubuntu.com/manpages/lucid/man6/chocolate-doom.6.html]("http://manpages.ubuntu.com/manpages/lucid/man6/chocolate-doom.6.html")

and here:

[http://manpages.ubuntu.com/manpages/lucid/man5/chocolate-doom.cfg.5.html]("http://manpages.ubuntu.com/manpages/lucid/man5/chocolate-doom.cfg.5.html")

---

### Post by jtarin on 2011-06-25
IMHO [this port]("http://doomlegacy.sourceforge.net/") is the best one for Doom.
Graphics are as good as they can get.
Unpack and go! I would suggest reading the docs so you know how to replace WADS and other cool things.

---

### Post by jtarin on 2011-06-25
Do you not have a menu entry under "Games"?
[User Guide]("http://www.chocolate-doom.org/wiki/index.php/User_guide")
> Chocolate doom requires a doom-wad to play. If you have a copy of the commercial games Doom or Doom 2, you can generate a doom-wad package using "game-data-packager". 
use the command ```
gksudo nautilus
```to open Nautilus with root priviliges.

---

### Post by Sablewings on 2011-06-25
So sorry, but am a little confused... I moved the wad file into the usr/share/ using gksudo nautilus, but then the game refused to run at all. I assume I broke chocolate-doom!

I have removed all traces of the programme and am going to start again from scratch.

jtarin, I downloaded Doom Legacy zip file, and it goes into my download folder, where do I need to copy it to so it will work? I unzipped it in the downloads folder, so of course the game stuff is in the same directory?  but of course when I click on the executable file it doesn't work. :(

---

### Post by Sablewings on 2011-06-25
Update - have figured out that chocolate-doom WAS working, it's just that the game intro/title screen timed out extremely fast!!

I can play the game if I'm very quick and take less than a second on selecting things on each screen ( New game - I'm too young to die ...)

Shame it's not possible to slow this down a bit...! :o

The next challenge will be to run chocolate-doom with the doom2.wad file. Can this be done in terminal - if so, which command would I use to link chocolate-doom to the wad?

Many thanks!

---

### Post by jtarin on 2011-06-25
> **Sablewings said:**
> So sorry, but am a little confused... I moved the wad file into the usr/share/ using gksudo nautilus, but then the game refused to run at all. I assume I broke chocolate-doom!

I have removed all traces of the programme and am going to start again from scratch.

jtarin, I downloaded Doom Legacy zip file, and it goes into my download folder, where do I need to copy it to so it will work? I unzipped it in the downloads folder, so of course the game stuff is in the same directory?  but of course when I click on the executable file it doesn't work. :(right-click on it, select properties,permissions tab, make executable.

---

### Post by mcellius on 2011-09-07
This is how I did it:

1.  Install Chocolate-doom. It's included in Ubuntu's Software Center, or in this repository: **ppa:mjdebruijn/chocolate-doom-release**.
2.  Without additional WADs, it'll run the first several levels of the original Doom just fine.  You can start it from the Dash: just open the Dash, type the first couple letters of "Chocolate-Doom", and then choose the icon.
3.  If you want to run other WADs, you'll need to find them on the Internet (very easy through Google) and download them. (Some sites have thousands of WADs.) Then copy the WAD you want to run to the /usr/share/games/doom directory.  

If you don't feel comfortable with the command line, or If you want to copy the WAD graphically, open a terminal and type "gksudo nautilus" which will open Nautilus with permission to move a file to the right directory.  You might find it easier at this point to hit the "F3" key to split Nautilus into two windows; in one half, go to /usr/share/games/doom, and in the other half go to wherever you downloaded the WAD you want to use, e.g. /home/yourusername/Downloads.  Copy and paste the desired WAD into the /usr/share/games/doom folder.  Make sure you know the name of the WAD correctly, including capitalization!   You can now close Nautilus.

Now, in a terminal type "chocolate-doom -iwad DoomExample.WAD" (don't type "DoomExample.WAD"; use the name of the WAD you copied, making sure to get capitalization correct) and hit "Enter."  Doom will start with the WAD you specified.

---

### Post by fragglet on 2011-09-07
Hi,

I'm the author of Chocolate Doom. I'm sorry to hear you've been having problems getting it to run. The version in the Ubuntu package repository is actually very old and I'd recommend following mcellius's instructions to get a more up-to-date version.

To make it find your IWAD file (doom.wad, doom2.wad, etc), the easiest thing to do is just place it in your home directory. You can also copy it into /usr/share/games/doom, or if you're using the terminal, cd into the directory that it's in and run chocolate-doom.

If it's quitting at the title screen, your IWAD file is probably out of date. Chocolate Doom only supports version 1.9. You might have an old version like v1.666. You can download patches [here](http://www.doomworld.com/classicdoom/info/patches.php) to upgrade to version 1.9, but they require a DOS emulator like DOSbox to run. If that sounds like too much hassle, just make sure you start a new game as soon as the title screen appears - hit enter several times and it will start a new game.

I hope this is helpful!

---

### Post by mcellius on 2011-09-07
fragglet,

You're the author of Chocolate-Doom?  Wow, I feel that I'm in the presence of greatness!  I love this program and play it often, and it is very true to the original.  It works perfectly.  Thanks for doing this!

mcellius

---

