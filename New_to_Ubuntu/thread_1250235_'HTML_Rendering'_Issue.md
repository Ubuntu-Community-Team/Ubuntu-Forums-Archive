---
title: "'HTML Rendering' Issue"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by embiggened.badger on 2009-08-26
Good morning, everyone!

Last night, I continued my misadventures in the long and contrived process of installing 'World of Warcraft' to work within the Wine environment. I can't seem to get the files copied from my CDs to install properly, so at the moment, I'm relying on the Blizzard Downloader.

The Installer downloads successfully. However, once the Installer is running within Wine, and the window that normally displays the End User License Agreement is loaded, I see the following error message:

> [FONT=Book Antiqua][SIZE=5]**HTML Rendering is current disabled.**[/SIZE][/FONT]I [did some research]("http://forum.winehq.org/viewtopic.php?p=9188") and [found some advice ]("http://forum.winehq.org/viewtopic.php?t=1520&highlight=html+rendering")about resolving this issue using the available Gecko library. I installed this library directly using the appropriate Terminal commands (see second URL), and this seemed to alleviate the issue ... partly.

Now, instead of no Agreement at all, I'm faced with an EULA window that never activates its 'Agree' button. Meanwhile, the 'Disagree' button just sits there ... watching me ... *mocking me*. (That smug *********.)

I also [found an alternative]("http://ubuntuforums.org/showthread.php?t=718912") involving something called 'Wine Doors.' I'm thinking about trying this when I get home, but if Wine Doors is identical to Wine, I don't feel particularly compelled to install a redundant program. Is this the same thing?

Does anyone have any other ideas as to how I can try to solve this issue? Any help would be greatly appreciated!

**Edit:** I just remembered that I also installed something called 'IEs4Linux' as recommended on another thread. (I can't find the link at the moment, unfortunately.) This installed Linux-compatible versions of Microsoft (*gag!*) Internet Explorer v5.0 and v6.0 within my file system, and as far as I can tell, the Blizzard Downloader and the Installer are trying to access MSIE rather than Firefox to display text and navigation. Could 'IEs4Linux' be another part of the problem?

---

### Post by NoaHall on 2009-08-26
Wine Doors is a just a extra toolset - not an entire program. If that fails, use winetricks to install extra fonts.

Also, you could try running it in a virtual desktop, not just a virtual application.

---

### Post by embiggened.badger on 2009-08-26
Thanks for your quick response, **NoaHall**. When you refer to 'winetricks,' are you referring to a Terminal command, or another application? I'm not familiar with either.

Also, when you suggest running a 'virtual desktop' ... Actually, I'm not even 100% sure what that means. I recognize the term from old Windows networking apps, but beyond that, I'm clueless. Could you elaborate?

( Side note: Mmmm. French Vanilla coffee creamer. Praise [insert deity here] for such divine chemistry. )

---

### Post by NoaHall on 2009-08-26
Winetricks is a script for installing extra things in Wine - see here -http://wiki.winehq.org/winetricks

Virtual desktop =

Applications -> Wine -> Configure Wine -> Graphics -> Emulate a Virtual Desktop

---

### Post by embiggened.badger on 2009-08-26
Thank you! I'll have to try this after I get home tonight.

One question: The Wine Wiki page to which you linked prominently features both the Terminal command and an extremely detailed 'Help Text' (under 'Options'). is this because the Terminal command automatically downloads and installs *all *of the files mentioned under 'Options,' or are the command listed under 'Options' actually Terminal commands that I may have to enter one-by-one?

---

### Post by NoaHall on 2009-08-26
You can run it with a GUI, and select multiple options at once, and it will download and install all you select.

---

### Post by embiggened.badger on 2009-08-26
Are you a man? 'Cause I don't want to say 'You Da Man' if you're a woman. That would just be awkward.

Thanks, regardless.

Also, definitely let me know about that 'Virtual Desktop' thing.

---

### Post by LowSky on 2009-08-26
instal the windows version  of firefox if you "need" a internet browser for a wine install

---

### Post by NoaHall on 2009-08-26
I am a man, I guess. 

Virtual Desktop will run the application like it's being run on a Virtual Machine, and it resolves some issues that Wine has.

---

### Post by embiggened.badger on 2009-08-26
**LowSky:** Would that still work if the Blizzard Downloader and Installer apps are designed to assume that Internet Explorer is integrated as my default browser? Blizzard programs have a nasty tendency to make that assumption, I've found.

**NoaHall:** How do I activate the 'Virtual Desktop' to which you're referring?

---

### Post by NoaHall on 2009-08-26
Like so.... Applications -> Wine -> Configure Wine -> Graphics -> Emulate a Virtual Desktop
then choose the desktop size that you wish to emulate. Simple.

---

### Post by embiggened.badger on 2009-08-26
**NoaHall:** +1, Insightful. Thanks for your help!

---

