---
title: "How do I remove &quot;Set up mail...&quot;, &quot;Set up chat...&quot; and &quot;Broadcast&quot;"
date: 2010-06-14
forum: New to Ubuntu
---

### Post by Momotombo on 2010-06-14
Can anyone tell me how to remove "Set up chat...", "Set up mail..." and "Broadcast" from the messages indicator so that I can just leave it with pidgin and gmail notifier? That and the thing next to the shutdown icon with my name and status, I don't need any of these things.

Thanks

---

### Post by ubunterooster on 2010-06-14
I do not think the me-menu is easily configured.

You can remove the me-menu and add a quicklauncher for pidgin but I am not sure about the gmail notifier

---

### Post by Deadite81 on 2010-06-14
The files that tell the Indicator Applet what things to display in the messaging menu are located here:

/usr/share/indicators/messages/applications

Removing the file associated with a app will remove it's menu entry.  You can also add new items, like Thunderbird for example.  If the programs get updated the removed files may be replaced.  You have to log in and out to see the changes, and this obviously has to be done with administrated privileges.  You may just want to move the files in case you want to put them back later.

---

### Post by Deadite81 on 2010-06-14
And to remove the Indicator Applet Session simply right click it and choose remove from panel.

If you would still like a shutdown button, just right click the panel, choose add to panel, and select the "Shutdown..." button.

---

### Post by CO_Shifty on 2010-09-07
> **Deadite81 said:**
> The files that tell the Indicator Applet what things to display in the messaging menu are located here:

/usr/share/indicators/messages/applications

Removing the file associated with a app will remove it's menu entry.  You can also add new items, like Thunderbird for example.  If the programs get updated the removed files may be replaced.  You have to log in and out to see the changes, and this obviously has to be done with administrated privileges.  You may just want to move the files in case you want to put them back later.

This is close, but I don't have the broadcast app in that folder; I like to remove Broadcast from the menu since I have two of them there for some reason (I installed a workaround a while back for some issue I forgot about).
[I]
Edit[/I]: Nevermind I got it. The reason I had 2 of Broadcast menus is because I trashed a cache gwibber file as part of a work around, but since the file still existed in the trash folder the indicator picked up and created two entries. Deleting my trash can solved my problems. I still will thank you, got me started here lol.

*Edit*: Spoke to soon, it wasn't that file after all, it had to do with another config file in .local/share/applications. I deleted the gwibber .desktop file and fixed it, unless some thing else that I deleted fixed it. Cool either way :)

---

### Post by Deadite81 on 2010-09-07
Yes, I have noticed the problem with .desktop files.  If the program is in the messaging menu and you create a .desktop file in .local/share/applications to override the .desktop file in /usr/share/applications you will get multiple message menu entries.  You can also add information to a .desktop file that will qualify how it appears in the messaging menu, as in the Evolution .desktop file, which could cause problems elsewhere if you don't keep up with what you change.  It sucks that they don't make this more easily configurable and apparently don't plan to.

---

### Post by wanchai on 2010-11-14
I uninstalled the package *indicator-me* and this cleaned up the Indicator Applet Session. It now shows only the power switch icon which has options to log off, change session, power off, reboot, etc.

Deleting the files from */usr/share/indicators/messages/applications* or even removing the whole directory only empties out the envelope icon. In order to completely remove it you need to uninstall the package *indicator-messages*.

---

