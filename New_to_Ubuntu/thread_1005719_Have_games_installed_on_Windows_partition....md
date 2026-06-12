---
title: "Have games installed on Windows partition..."
date: 2008-12-08
forum: New to Ubuntu
---

### Post by killermad34 on 2008-12-08
I have multiple games installed on my Windows partition on my duel boot machine, and I want to play them in Ubuntu without having to re-install all of them on my hard drive again.  I guess the only game I am really trying to get to work is World of Warcraft.  All the other games I don't mind booting into Windows for but I play this one the most.  I really don't want to install the game, all the expansions, and all the updates again on my hard drive taking up way more room than I need to.

I know wine pretty much emulates Windows folders, but I don't know if it can go into my Windows partition and play games directly from it.  Thanks for any help.

---

### Post by SuperSonic4 on 2008-12-08
No, wine doesn't work like that. It provides a layer for windows apps not directly accesses them. You'd have to install any program twice.

Check out the appDB on wine's website with your version of WoW: [http://appdb.winehq.org/](http://appdb.winehq.org/)
WoW 3.0.x has a platinum rating so it should work.

Personally, I'd boot into windows when you want to play or use the memory up since hdds are quite cheap

---

### Post by lovelyvik293 on 2008-12-08
You can not install the windows .exe's in the ubuntu,so you must have to have the linux version of that game to install them in linux.
Wine does some things for you but can't used with all the softwares.So check that it supports the Warcraft or not.
Wine can use the softwares installed in windows partition.

---

### Post by fiddler616 on 2008-12-08
Don't quote me, but I'm pretty sure this is either impossible, or waaaaaaaaaay more trouble than it's worth.
Edit: Missed it (being first). Oh well.

---

### Post by weezerisrock on 2008-12-08
from WoWWiki

> You can also just install WoW in Windows and then copy the entire World of Warcraft folder over from your Windows installation.

Or if you've already got WoW installed on your Windows partition, you can just use Wine to launch WoW directly from this installation. There is an added benefit to doing this, if you actively multiboot between Linux and Windows, because you will only need to have one copy of WoW on your hard drive for it to run in both environments. Please keep in mind that you must have both read and write access to your Windows partition for this to work, and only the most recently released GNU/Linux distributions, are currently providing write access to NTFS (Windows XP) partitions out of the box. If you do not have write access to your NTFS partition, you will need to consult with your distributions documentation for directions on enabling the NTFS-3G driver, which adds this feature.

Note: Using this method results in there being no entries for WoW in Wine's registry, but this does not cause any issues at all with running WoW.

Note 2 : Some computers might experience low FPS , while trying to run WoW in opengl mode . In that case , removing Config.wtf file ( it is localised in WTF folder ) , running WoW to generate that file again , and then making changes ( to opengl mode ) might help. Make sure , to give read/write access to WTF folder ( otherwise WoW will crash ) 

[http://www.wowwiki.com/Wine_(software](http://www.wowwiki.com/Wine_(software))

Hope this helps!

---

### Post by killermad34 on 2008-12-08
Well I appreciate your detective work weezer...but when I click on your link it says the page cannot be found on wowwiki.  I couldn't find it on the suggested pages either.  I'll keep looking on there though because obviously the answer is there somewhere.

---

### Post by weezerisrock on 2008-12-08
I clicked it to see what you meant, you are right, the reason is because the last ) didn't make it to the link for whatever reason.

Add that last ) to the end of the address bar after you click the link and it will come up.

---

### Post by killermad34 on 2008-12-08
Well I found the page you posted.  It just says that you can use it to play games already installed on windows, but I don't know how to do it.  I'll keep reading but I can only configure wine in Ubuntu to search on the Ubuntu partition, not my windows partition.  I'd just copy over the WoW folder from my Windows partition but I don't have enough space on my Ubuntu partition for that.  I think I may just end up buying another hard drive for my laptop and installed ubuntu fully on there and make things so much easier.

---

### Post by killermad34 on 2008-12-08
Good news, I kind of figured it out.  Now when I go to Configure Wine > Add Application > then select the WoW.exe from my parition (or Launcher.exe) it adds it to the list, I click ok which closes the window, but when I open the configuration menu back up again, it's not listed under the applications.  So I really don't know what to do.  Like I said this isn't a huge deal, I may just end up re-sizing my Vista partition to allow room to have two installs of the game but I really don't want to have to do that.

---

### Post by JoshuaRL on 2008-12-08
One other thing you could try is to mount your windows partition in a VM and run the game through that.  But depending on how fast your system is and how much RAM you have, that might not be feasible for gameplay.  In fact, unless you have a pretty sick rig, it probably wont.  But thought I'd suggest it.

[http://ubuntuforums.org/showthread.php?t=973756](http://ubuntuforums.org/showthread.php?t=973756)
Post #6

---

### Post by killermad34 on 2008-12-08
I'm not sure what's happening.  It launched once but is giving me some access error now.  The launcher loads, but then when the game loads it just locks up one of my desktops.  I can change cube sides and stop the program but still it's annoying.  I think I'm just going to end up installing it eventually.  I just know that it would be easier to keep addons up to date only having it installed on one system.

---

### Post by mrboojive on 2008-12-09
What is the error that you are getting? How are you launching WoW? It looks like you should just be able to navigate to the folder on your Windows partition where WoW is installed and double click on Launcher.exe.

Are you using the version of Wine from WineHQ or the version that comes with Ubuntu? You should probably install the WineHQ version since it is more up to date and probably works better with WoW: [http://www.winehq.org/site/download](http://www.winehq.org/site/download).

This page from the Wine AppDB might have some more helpful information: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154)

---

### Post by weezerisrock on 2008-12-09
I agree with Mr. Boojive.

This should be pretty easy.  Instead of running thru the wine menu, just navigate to <your windows partition>\program files\world of warcraft\Launcher.exe and run that.  This is assuming you have full read/write permissions to the windows drive.  you do right?  cause if you don't wow can't write to the WTF folder and it will lock up.

It SHOULD just work, and then you can add a link to that file on your desktop or taskbar or wherever.

P.S. on a side note if you are running an ATI graphics card, I would recommend turning off compiz before starting the game.  It will flicker something awful.

---

