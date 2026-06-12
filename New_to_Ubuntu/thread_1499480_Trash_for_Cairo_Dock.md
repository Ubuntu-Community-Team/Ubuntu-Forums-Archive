---
title: "Trash for Cairo Dock?"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by TriBlox6432 on 2010-06-01
How can I put trash on Cairo Dock?

---

### Post by nhasian on 2010-06-02
i dont have cairo-dock installed at the moment but i remember there was a setting to add the trashcan as well as other applets.

---

### Post by TriBlox6432 on 2010-06-02
I've found it.  Thank you!!

---

### Post by elliotn on 2010-06-02
Whenever i put trash in Cairo it wont find the icon

---

### Post by fabounet on 2010-06-02
there is an applet to activate, you can't just drag and drop the trash icon from the desktop

---

### Post by TheRacerX on 2011-11-03
i got the trashcan working on the dock but the Icon itself wont display on the dock its just an empty space with the word "Trash" when i run my cursor over it. How do i fix that?

---

### Post by Cpierce on 2011-11-03
Go to your startup applications and edit your Cairo dock command. I assume you created one so Cairo will start on boot up. After the command, put a -o. Note this is an "o" not a zero. It should look like this:

/usr/bin/Cairo-dock -o


This will start the version with advanced graphics. However your graphics card may not be good enough to run it. Check to see if you have extra graphics installed.

---

### Post by TheRacerX on 2011-11-03
i havent set it up to start up when i log in cause i 1) i dont know how too ( still new to this) and 2) i havent turned my computer off in like a week

---

### Post by Cpierce on 2011-11-06
go to system>preferences>startup applications. Click add, For the title put "Cairo Dock" without the quotations. For command, put "/usr/bin/cairo-dock -o" then hit save and reboot. For the lower graphic cairo, the command would be "/usr/bin/cairo-dock -c".

If for some reason later you don't want cairo to start at bootup, then just go back to startup applications and uncheck the cairo box.

 A little hint, while you are in startup, uncheck and boxes of programs you don't use,(remote desktop, Ubuntu One ?) This will free up some processor and RAM.

---

### Post by Cavsfan on 2012-03-05
For some odd reason when I add dustbin (Trash) to Cairo Dock and click on it. Just a glimpse of something appears
at the top left of the screen down a couple of inches.
It looks like few icons but, it disappears too quick to tell for sure. But, it will not open the trash folder.
I have added Trash to the panel at the top and that works fine. I have checked in Configure Cairo Dock and that is where I added the check mark by trash 
to get it to appear in the dock in the first place. I have checked the settings there about trash and everything appears correct.
But, it just does not work as expected from the dock. 
Any help would be appreciated.

---

### Post by Cavsfan on 2012-03-07
Does anybody have an idea why when I add Trash to Cairo Dock and click on it, it does not open trash?

---

### Post by Cavsfan on 2012-04-01
Never mind. Upon booting into Ubuntu today, Cairo-Dock got and error about trash and asked if I wanted to delete it or keep it.
I deleted it and trash was still there. It now opens like it should when clicked on.

Must have been a glitch that ironed itself out.

---

