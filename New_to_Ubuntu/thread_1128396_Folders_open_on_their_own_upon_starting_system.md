---
title: "Folders open on their own upon starting system"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by aml1648 on 2009-04-17
Every time I start Ubuntu, the desktop folder and the Firefox folder automatically open and display their contents. This seems to be rather harmless but is really annoying.

The problem seemed to have started after I edited the "profile.ini" file inside the firefox folder.

Does anyone know how can I solve this problem? 

Many Thanks!

---

### Post by LowSky on 2009-04-17
dont edit the profile.ini file.... lol

in all seriousness, what/why did you edit the file for?

---

### Post by aml1648 on 2009-04-18
I edited  the profile.ini file so that the path described there would match the name of the .default file for firefox. 

Does anyone know how do prevent the folders from automatically opening?

---

### Post by Yashiro on 2009-04-18
Close any programs you don't want open when you log in.
Goto system > preferences > sessions (or startup programs if it's been renamed).
In session options click the big button that saves the currently running programs. Untick the 'save sessions automatically' too.
Log out.
Log in.

Might be fixed.

---

### Post by aml1648 on 2009-04-18
Hi Yashiro,

Thanks for your help.

I am using Jaunty Beta right now. The option tab under Startup Applications only has one option "automatically remember running applications when logging out". I unchecked this box and logged in again but the folders once again opened automatically.

Perhaps the folders were always running in the background somehow?

---

### Post by aml1648 on 2009-04-18
I found a solution to the problem.

It is just as  Yashiro said, except that for Jaunty the option of saving current session is not in the option tab of startup applications.

Instead I had to edit gconf and uncheck this option from the gnome session tab there.

---

### Post by CatKiller on 2009-04-18
Autostarted applications are kept as .desktop files in ~/.config/autostart. I don't know for sure that the "saved session" applications are also kept there, but it might be worth a look.

---

