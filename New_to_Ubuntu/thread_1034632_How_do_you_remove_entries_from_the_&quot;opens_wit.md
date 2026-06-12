---
title: "How do you remove entries from the &quot;opens with&quot; menu?"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by kbekward on 2009-01-08
I have photoshop cs2 referenced three times under my "opens with" right-click menu(running intrepid). None of these work yet (something to do with how wine is dealing with file associations). Anyways, I would like to able to remove these duplicate entries - I found this solution but I have no clue what to make of it since I am new to ubuntu, really new - 
 

"Edit Open With menu?
How would I go about editing this?

I have Nvu listed twice and it's bugging me.

Edit: never mind just found out how! Nautilus -> Select .html File -> File -> Preferences -> Open With -> Select -> Remove."


I have been stumped on what exactly these directions mean. Am I supposed to find an .html file with nautilus and edit its preferences? I don't really know what to look for. Thanks ahead of time for bearing with my ignorance haha.

---

### Post by jken146 on 2009-01-08
Just right click on the file you're interested in, then click on Properties in the menu that appears.  Go to the Open With tab and make your changes.

---

### Post by kbekward on 2009-01-08
alright that helped because when I now right click on a psd or image file it no longer says open with photoshop twice at the top - they are now gone - however, when I select the "Open with other application.." , in the long list of various programs that pop up, photoshop.exe is still on there three times(I added it too many times with no success). Is there anyway to remove these? thanks for the help

---

### Post by mc4man on 2009-01-09
> Is there anyway to remove these
It's actually very simple, but because your new to linux it will be safer and possibly be more informative to you if you were to post a screenshot for me.

Where you want to go is into your home folder and use ctrl+h or view -> show hidden files.

Then open .local -> share -> applications

Resize the window so it's just big enough to show all the contents and press alt+Prnt Scrn

When you reply to a thread there is a 'manage attachments' button, use that to browse to the screenshot, open and upload.

Also in the applications folder should be a file named mimeapps.list (it doesn't exist by default but is created from using, among other things, the r.click in certain ways. If it's not there don't worry. If it is post the contents along with the screenshot.

The r. click in linux is a very useful tool and much, much  'deeper' than it is in windows.

---

### Post by kbekward on 2009-01-09
here is the screenshot you requested - I see there are one too many photoshop.exe's, (I still use cs2 but don't need any references in the 'open with other application' menu). I also have uninstalled the duplicate image finder windows app and thats there as well, digikam works nice (can I remove that while I am at it?)

---

### Post by mc4man on 2009-01-09
Yes, in this case you can delete the all photoshop.exe ones and the duplicate image finder.
Ones with app specific icons or with blue diamonds shouldn't be deleted unless you open them up first to see the specific exec=. (they may be something you are using.

Those are all .desktops, so for example

If you could find a command that would open a file in photoshop rather than just open p.s., than a .desktop could be created with that command as the exec=. and obviously you wouldn't want to delete it.

---

