---
title: "World Of Warcraft Permissions Problem"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by jwright70 on 2009-11-11
Hi guys,

I'm new to Linux and have really no idea how to do anything. I somehow managed to use wine and install my favorite game "World of Warcraft" and its 2 expansions. The last expansion " Wrath of the Lich King" has an incripted dvd or something, so I just downloaded the installer off the website. Everything went surprisingly smooth. The problem is, now that the last expansion is installed wine will not run the program. It says permissions denied and I noticed the folder has a padlock and a X on it. How do I fix this? Sorry if there is another thread about this but i was unable to find one.

---

### Post by 0cton on 2009-11-11
either you installed it with root and you are trying to run it without it.
Either it does not have executable permission
chmod +x yourfile
or right click and check give permission to execute (or something like that)

---

### Post by ubuser76 on 2009-11-11
This problem actually started with the latest patch that Blizzard tried to push out. Fix your folder permissions with chmod 
chmod 755 "/home/<user>/.wine/drive_c/Program Files/World of Warcraft"


After you have done that don't use the Launcher.exe app to start Warcraft, instead launch it with the Wow.exe file
wine "/home/<user>/.wine/drive_c/Program Files/World of Warcraft/Wow.exe"

---

### Post by jwright70 on 2009-11-11
Thanks alot. Chmod did the trick. It's crashing when I first start it but it'll let me run it on a second try. So I'll have to figure that out but at least I can run it now. Thanks again

---

### Post by Rayve on 2009-11-11
If you run it from the terminal via command line, the output there may tell you some interesting things about what could be causing it to crash.

I had similar issues and changing permissions did the trick.  It runs fine on the first try.

---

### Post by Rrasyrogenees on 2009-11-11
i am curious to know why Blizzard thinks they need to cut permissions for Linux users like this... first it was the WotLK expansion and now this recent patch (tuesday, 11-10-09) that they make it difficult for linux users.. but some companies seem to be afraid of linux and the implications that they will not make as much money by limiting what is available... oh well... linux will get the majority market share in the future... :D

---

### Post by jwright70 on 2009-11-12
I don't know why it crashed that first time. I added the line for opengl in the config file and everything is working flawlessly. Now I can say goodbye to windows for good.

---

### Post by dardack on 2009-11-12
Yea i noticed the most recent tiny patch made the launcher chance the folder permissions (which sux), but not the group/user owner (which is good). So after a patch the launcher usually auto runs, just once you close the launcher you have to go back and chmod u+xrw the wow folder again.

---

### Post by arkanabar on 2009-11-12
So the launcher is going to re-wreck the WoW folder permissions each and every time I run it?  If so, blech.

---

### Post by Rayve on 2009-11-13
> **arkanabar said:**
> So the launcher is going to re-wreck the WoW folder permissions each and every time I run it?  If so, blech.

I don't use the launcher, personally, so I can't say if it will change the WoW folder permissions every time it runs or only after an update.

---

### Post by toupeiro on 2009-11-13
Second latest patch does the same thing.  I renamed the Launcher.exe file and the game still runs fine without it launching wow.exe directly.

-1 Blizzard...

---

### Post by Iksf on 2009-11-13
Change the file permissions, as has been mentioned several times already. I personally use the main WoW.exe, i have 

env WINE_CURSOR=1
wine c:/Program\ Files/World\ of\ Warcraft/WoW.exe -opengl

in a shell script as my launcher

---

### Post by toupeiro on 2009-11-14
> **Iksf said:**
> Change the file permissions, as has been mentioned several times already. I personally use the main WoW.exe, i have 

env WINE_CURSOR=1
wine c:/Program\ Files/World\ of\ Warcraft/WoW.exe -opengl

in a shell script as my launcher

The problem is that a post patch operation calls launcher automatically, so it doesn't matter that you call wow.exe directly.  Thats all I've ever done since playing wow in 2004, but I was still impacted.  So far, renaming launcher.exe seems to have stopped the incidents.

---

### Post by Rrasyrogenees on 2009-11-20
i have setup on my desktop a launcher for wow and another for a file that holds several sets of passwords (which are made up of random numbers and letters that are small and large case) because i actually had a hacker take my account for a short time. but i used the properties of the World of Warcraft folder to change permissions... easy like windows but NOT windows... yippee.  i had to change it a few times but now i haven't had to go back there for a while either... and this is on karmic koala

oh... and fyi... i have several passwords in that file but only one is the one i use.  copy then ctrl+v to put it in the password section of the sign in page.  that way it is totally random and not easy to get.  :D

---

### Post by DedMoroz on 2009-12-07
> **ubuser76 said:**
> This problem actually started with the latest patch that Blizzard tried to push out. Fix your folder permissions with chmod 
chmod 755 "/home/<user>/.wine/drive_c/Program Files/World of Warcraft"


After you have done that don't use the Launcher.exe app to start Warcraft, instead launch it with the Wow.exe file
wine "/home/<user>/.wine/drive_c/Program Files/World of Warcraft/Wow.exe"

If you do it this way to play the game, how will you ever do the updates?

---

### Post by polpak on 2009-12-08
> **DedMoroz said:**
> If you do it this way to play the game, how will you ever do the updates?

Simple. Run the BackgroundDownloader.exe file in that same directory.

I have a small shell script that starts one after the other, and I added a menu item to my applications menu that runs the script. If there are no updates the downloader just gives an error about not finding patch information, then proceeds to launch WoW.

---

