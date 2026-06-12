---
title: "Easy to follow &quot;Wine&quot; Set up"
date: 2009-03-30
forum: New to Ubuntu
---

### Post by old_dope on 2009-03-30
I would like to install WINE on my pc so i can play a Windows base game. Does anyone know of a really easy set up guide please. Many thanks.

---

### Post by LowSky on 2009-03-30
go to add/remove

search for Wine

install



as for games, check Winehq, here a link to see if the game in question will run and how to do that
[http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true](http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true)

---

### Post by hyper_ch on 2009-03-30
what do you need wine for?

---

### Post by old_dope on 2009-03-30
Have installed Wine via Add/Remove but can't figure out where to go from there? Thought i could have just run the game by inserting the Football Manager cd into the drive and that Wine would have took over from there?

How do i install the game into Wine?

---

### Post by ajgreeny on 2009-03-30
Not all games will work with wine, but if that one does, you need to find the setup.exe file on the CD and then use the terminal with the command ```
wine /media/cdrom/path/to/setup.exe
``` which should install the game in your hidden **home/.wine** folder

---

### Post by aktiwers on 2009-03-30
[Wine-doors ]("http://wddb.wine-doors.org/downloads")is pretty easy

---

### Post by hyper_ch on 2009-03-30
well, check wine appdb for game support.

---

### Post by Chemical Imbalance on 2009-03-30
First check compatibility with your game in WINE on the wineapps site mentioned above.

With CD's or DVD installers, opening up the mounted disk on your desktop and navigating to the setup.exe or similar .exe  will usually suffice.

It most likely will not autostart on a linux system like on windows.

---

### Post by LowSky on 2009-03-30
> **hyper_ch said:**
> well, check wine appdb for game support.

I gave you the link above to check the game to see if others have used wine to get it to run


here is is again, note I added the search for football, there is like 5 version of that game based on each year
[http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=application&sTitle=Browse+Applications&iItemsPerPage=25&iPage=1&sOrderBy=appName&bAscending=true](http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=application&sTitle=Browse+Applications&iItemsPerPage=25&iPage=1&sOrderBy=appName&bAscending=true)

---

### Post by SunnyRabbiera on 2009-03-30
If you installed wine via the repo's then there should be a menu for wine in your main menu (applications places system) under applications.
If wine isnt in your menu log out and log back in (some apps need this)
afterwords there should be a entry in the wine menu called "configure wine"
You may need to change the version of wine from windows 2000 to XP if XP isnt the default.
You will see a pulldown menu for this in your first tab.

afterwords its more of a shot in the dark, you can try to go to the directory of your .exe and see if it works.
Wine is not perfect though, it wont solve all windows application issues.

---

