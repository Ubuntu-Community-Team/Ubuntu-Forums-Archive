---
title: "GIMP Fail to start"
date: 2010-01-20
forum: New to Ubuntu
---

### Post by PTSWhite on 2010-01-20
**BLUF**: GIMP now fails to run.  Shows "starting GIMP" in status bar, but then nothing happens and that message disappears.
 
**The machine in question**:
Gateway 4100 w/ Hyperthreading P4 2.6 Ghz, 4 GB RAM, 120GB HD, SB Audigy 2ZS Soundcard, 256MB NVidia vido card.  
 
I'm about as newbie as they get.  Been in the MS world since DoS 2.0.  Spent a weekend building two machines from City Surplus and installing different distros.  Ubuntu 9.10 seemed the most trouble free so I've stuck with it for the past two weeks.  So far I REALLY like it.  What took me so freakin' long?  Oh yeah, total cost for the machine built from a $35 dollar surplus box is $60.  Gotta love the way Linux breathes new life into old 'puters.
 
Alas, #1 daughter (who uses PhotoShop at school) wasn't comfortable with GIMP, so I thought I'd try to install GIMPShop.  I downloaded the .deb package and double clicked.  All seemed okay, but I couldn't find the application in the Application menu, nor was I able to figure out where to browse to so I could add it to the menu/
 
Decided to uninstall it and reinstall GIMP 2.6.  Uninstalled GIMPShop and Ubuntu Software Center said all went well.  Reinstalled GIMP and USC said that went well too.  However, GIMP did not reappear on the menu.  I edited the menu and GIMP appeared there.  I hit Apply and voila GIMP reappeared on the menu.  However, now when I click on the GIMP icon I get a "starting GIMP" message in the lower status bar, but then it disappears and nothing happens.
 
I uninstalled and completely removed GIMP and then reinstalled it.  Same problem.  I noticed that in my "usr" folder that some GIMPShop folders and documents are still there.  I thought maybe I could do an uninstall and completely remove, but GIMPShop does not appear as installed in USC.
 
Hmmmm . . . it just struck me that maybe my next step should be to uninstall and remove GIMP, reinstall GIMPShop, then unitstall and remove GIMPShop to clear out its last vestiges.  Then maybe a clean install if GIMP will work.
 
Or am I making this waaaaaaay too complicated?

---

### Post by Hospadar on 2010-01-20
Most applications store their configuration files in hidden directories (in linux a hidden directory is any directory whose name begins with a '.').

It seems possible that gimpshop, being a modified version of gimp, uses some incompatible configurations.   It may be that if you just get rid of that config directory it will solve you problems.

Try deleting the .gimp-2.6 folder in your home directory (it might be named a little different on your system, look for any folders with gimp in the name).  To show hidden directories in the file browser you can check that option in the view menu, or just hit Ctrl-H

---

### Post by PTSWhite on 2010-01-20
> **Hospadar said:**
> Most applications store their configuration files in hidden directories (in linux a hidden directory is any directory whose name begins with a '.').

It seems possible that gimpshop, being a modified version of gimp, uses some incompatible configurations.   It may be that if you just get rid of that config directory it will solve you problems.

Try deleting the .gimp-2.6 folder in your home directory (it might be named a little different on your system, look for any folders with gimp in the name).  To show hidden directories in the file browser you can check that option in the view menu, or just hit Ctrl-H
Thanks Hospadar, I'll give that a shot when I get home.  Might the "reinstall then uninstall and revove-all" of GIMPShop accomplish the same thing?  I ask because at my current skill level I trust USC to find more GIMPShop remnants than I can.

---

### Post by PTSWhite on 2010-01-21
> **PTSWhite said:**
> 
Hmmmm . . . it just struck me that maybe my next step should be to uninstall and remove GIMP, reinstall GIMPShop, then unitstall and remove GIMPShop to clear out its last vestiges.  Then maybe a clean install if GIMP will work.
 


That did it.  Works like a charm now.  Woohoo!  Thanks for the help.

Now if only I could get Screenlets Manger to show up in the Preferences menu like Compiz says it's supposed to.  <sigh>

---

### Post by staple on 2011-03-07
I have a similar thing - installed standard Gimp through the Ubuntu Software Centre (three times now) and when trying to start from the application menu it looks like it is trying then nothing.

However if I start from the shell with command "gimp" it is all sweet...strange....

---

### Post by Chen78 on 2013-02-16
worked for me too. cheers !

---

