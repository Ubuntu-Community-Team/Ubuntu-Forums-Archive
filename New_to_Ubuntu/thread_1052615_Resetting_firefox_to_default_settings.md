---
title: "Resetting firefox to default settings"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by Sentoguy on 2009-01-27
I need to reset firefox to it's default settings, and I know there is a way to simply delete the "~/.mozilla/firefox folder" but I don't know where to find that folder. Can anyone direct me where to find it?

---

### Post by emarkd on 2009-01-27
I think you're probably missing it because it's hidden.  Linux denotes hidden files and folders by starting them with a '.', as in '.mozilla'.  If you're using Nautilus, click the view menu and select 'show hidden files'  It'll be right there under your home directory.

And a bit of advice - try renaming it something first instead of just deleting it, in case something goes badly wrong and you need to recover it.  It could save you a lot of trouble.

---

### Post by Sentoguy on 2009-01-27
> **emarkd said:**
> I think you're probably missing it because it's hidden.  Linux denotes hidden files and folders by starting them with a '.', as in '.mozilla'.  If you're using Nautilus, click the view menu and select 'show hidden files'  It'll be right there under your home directory.

And a bit of advice - try renaming it something first instead of just deleting it, in case something goes badly wrong and you need to recover it.  It could save you a lot of trouble.

Thanks man, I'll try that. :)

---

### Post by Sentoguy on 2009-01-27
Hmmm, maybe I'm not using Nautilus (don't really know what program that is), but I don't see a "show hidden files" option under the "view menu".

Are you talking about the "view" drop down menu that appears at the top of the screen while you are running firefox?

---

### Post by emarkd on 2009-01-27
No.  Nautilus is the file browser.  It's under Accessories on the main ubuntu menu.

---

### Post by Sentoguy on 2009-01-28
I don't see an option to "show hidden files". 

I see:
Calculator
Character Map
Dictionary
Disk Usage Analyzer
Manage Print Jobs
Password and Encryption Keys
Take Screenshot
Terminal
Tomboy Notes
Tracker Search Tool

---

### Post by emarkd on 2009-01-28
hmmm.. not sure why the file browser is not on your menu.  you can use the run dialog.  press <alt>F2 and type 'nautilus'.

also, you can go under Preferences > Main Menu and see if the File Browser shortcut under Accessories is disabled.

---

### Post by Sentoguy on 2009-01-28
Yeah, it was disabled.

Ok, so now before I go screwing things up any further, let me get this straight. I should now:
-click on the "accessories" menu
-select "show hidden files"
-find the 'mozilla' folder and rename it?

Will that still reset firefox as if it was the first time it had been run?

---

### Post by emarkd on 2009-01-28
Not quite.  You'll click on Accessories and run the File Browser.  Once the browser is up, click the view menu and select 'show hidden files'.  Then find your .mozilla folder and rename it to .mozilla-old or something.  Then start Firefox and see what you've got.  I've never had to do this so I don't know how much will be reset, but I'd expect it to be pretty much back to the original state.  If something goes wrong, though, you can just undo the rename and be back where you started.

---

### Post by Sentoguy on 2009-01-28
Cool, thanks I'll try it.

---

### Post by Sentoguy on 2009-01-28
Sweet, it worked. Thanks emarkd.

So, now, could I rename it ".mozilla" and still have it be ok? Or will it go back to where it previously was?

---

### Post by emarkd on 2009-01-28
You should now have a new .mozilla folder that was created automatically for your new settings, so you can't rename the old one back to that.  But you shouldn't need to because you've got all new settings now.  

If you're happy with the changes and you're sure everything's like you want it to be, you can safely delete the .mozilla-old folder or whatever you called it.  You only kept it around as a safety net anyway.

---

### Post by Sentoguy on 2009-01-28
Nice. Thanks again.

---

### Post by emarkd on 2009-01-28
Welcome.  Glad we got it worked out for you.

---

