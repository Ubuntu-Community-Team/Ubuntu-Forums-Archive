---
title: "evolution calendar"
date: 2011-01-28
forum: New to Ubuntu
---

### Post by carrarin on 2011-01-28
Hello everyone, 

Where does evolution store the information about calendar color? Try as I might, I can't find it... :(

---

### Post by philinux on 2011-01-28
> **carrarin said:**
> Hello everyone, 

Where does evolution store the information about calendar color? Try as I might, I can't find it... :(

Right click on the calendar name and choose properties.

---

### Post by carrarin on 2011-01-28
Sorry, was looking for the location where the information is stored. Not looking for a tutorial on how to change the color.

---

### Post by indium on 2011-02-17
> **carrarin said:**
> Sorry, was looking for the location where the information is stored. Not looking for a tutorial on how to change the color.

Hi,

I ran into problems with colors, calendars and their contents on ubuntu 10.10 evolution 2.30.3 because I had stored my calendars on an exchange 2003 server. I have it fixed now, and the following might help you:

Before you go and change these files: please WAIT! and read until the end...

First do: 

close evolution !!! otherwise you screw up1!!

'cp $HOME/.evolution $HOME/backup.evolution'
'cp $HOME/.gconf $HOME/backup.gconf'

WHERE THINGS ARE:

there is 1 backup file that evolution stores of the gnome registry: 

/home/myname/.evolution/backup-restore-gconf.xml

there are 2 directories where things are store + 1 live registry:
$HOME/.evolution, $HOME/.gconf

/home/myname/.evolution/exchange/
   -- this contains links so the actual calendars (do 'ls -l' to see the links)

/home/myname/.evolution/exchange/myname@myexchangeserver.com/personal/subfolders/Calendars/subfolders

   -- in this directory I have my 4 calendars as directories.

/home/myname/.gconf/apps/evolution/%gconf.xml

"IDEA":

It seems no use to change any files in the .gconf directory, since the registry is 'active' when you have Gnome running and that active registry will simply over-write your changes. So you have to search for your calendars in the program gconf-editor (that has the same structure as the directory .gconf).

In that program you go to apps>evolution>calendar. In the right pane you will find 'sources': you have to double-click on it. 
Maximize the window that pops up and select from its list the calendar 'collection' that you want to change (mine is the exchange calendars). 

Unfortunately the window that then pops up is not maximizable!! You will have to scroll through the (hardly readable) text and find you calendar. This single line of text contains XML code with the following 'hierarchy': the collect has a <source> </source> pair for each calendar. In each pair there are <property> tags that contain the properties like your color. 

If you change it INSIDE gconf-editor, it will change it automatically in the files under $HOME/.gconf.

I myself had problems with not-loaded, non-accessible or non-existing calendars (that were still displayed) This is because the are links in $HOME/.evoltion/exchange that should be removed if they don't exist anymore on the microsoft exchange server. Also the directories they point to should be removed! 

If your calendars are not accessible, it could be because <property> tags are missing. I have spotted that in the %gconf.xml files, BUT YOU HAVE TO CORRECT IT IN THE PROGRAM (gconf-editor), NOT THE FILES. In my case I've added tags that were missing for some calendars by copying from others (tags/properties like "refresh", "refresh-type", "delete", "offline_sync".
 
Start up evolution (maybe you need to do it twice) to see it this improved)

"RESCUE"

if it didn't work for you: close evolution and log out. You need to put your backup back in place (you'll have your original problem back). 
You should now have the gnome login window on your screen. Don't log in: this will start gconf registry. Instead: log in to a text console by pressing cntrl-alt-F1 (or use F2,F3,etc). You get a text prompt where you can log in, and you can type bash shell commands then.
Move back your old settings (you have done the backup, right!?):
'mv $HOME/.evolution $HOME/corrupt.evolution'
'cp $HOME/backup.evolution $HOME/.evolution'

'mv $HOME/.gconf $HOME/corrupt.gconf'
'cp $HOME/backup.gconf $HOME/.gconf'

Now that everything is as old, go back to the gnome login window by logging out from the console. 

'exit'

press cntrl-alt-F7 (or cntrl-alt-F8), so that you see the Gnome window.

Now you can log in and enjoy your original problem. You're right back where you started. Nice!

ps1.
Usually, reinstalling software doesn't work, because thing are not overwritten in either the registry (gconf-editor), the .gconf directory, or the .evolution directory.

ps2.
You will find many more settings of other programs inside gconf-editor.

---

