---
title: "arranging favorites in launcher"
date: 2009-12-24
forum: New to Ubuntu
---

### Post by rolando.m on 2009-12-24
I can't seem to figure out how to rearrange the order of apps in the launcher (main GUI interface). My favs are in the order I added them and I want to rearrange them to be in the order I use them most often...

---

### Post by Brandon Williams on 2009-12-25
Go to Preferences->Main Menu (or Alt+F2 and run alacarte). You should be able to reorder the menu items there, including the ones in your Favorites menu.

---

### Post by rolando.m on 2009-12-26
I don't see favorites in there.. I see the other tabs, but not favorites.

---

### Post by jonest1 on 2009-12-26
Can you please be more specific about what is a favorite as I cannot find a reference to favorites?  A little clarification and I'll be happy to give pointed assistance.

I've had a look around and I'm going to take a guess that you may be talking about the Places menu?

From my testing, the places menu is only slightly customizable from common utilities.  The 'Home Folder' and Desktop items appear to be there by default, but I'm not 100% on that one.  Everything else which is a place can be organized by opening nautilus the file manager and editing Bookmarks.  The items may be dragged up and down the list.

I hope this helps.

---

### Post by jonest1 on 2009-12-26
I'm sorry about my earlier reply as I did not see this was a netbook remix post. I've got a remix box and will take a look.

---

### Post by jonest1 on 2009-12-26
I've just tested out the following solution for you.  

1.  Open up 'System Tools' -> 'Configuration Editor'
If it's not there, open alacarte as in a previous reply on this topic and add it in.

2.  Open the configuration editor (aka gconf editor) and use with care.  Navigate to apps -> netbook-launcher -> favorites and click on favorites.

3.  In the right-side pane, double-click on the favorites_list item.  You will then be able to move individual items up and down the list.

4.  Close out of the configuration editor.  You will need to logoff and log back in to see the changes.  There is no need for a full restart.

I hope this works for you.

---

### Post by Brandon Williams on 2009-12-26
> **rolando.m said:**
> I don't see favorites in there.. I see the other tabs, but not favorites.

I can recall the developer telling me that favorites would no longer be a true menu category with the new version of UNR. I guess you must be running karmic. In earlier versions (through jaunty), the favorites showed up in the alacarte menu and could be edited/managed from there. The method described above should work for karmic.

---

### Post by Justin C. on 2010-01-06
I'm running Karmic UNR and jonest1's steps worked perfectly for me. Thanks man.

---

### Post by kalos on 2010-09-17
I just posted [here]("http://ubuntuforums.org/showthread.php?p=9855822#post9855822") about my simple app to arrange favorites, but on a [related Idea]("http://brainstorm.ubuntu.com/idea/22652/") someone named Artanis wrote a much nicer version.

You should be able to run it with:
```

sudo apt-get install git-core
git clone http://github.com/Artanis/UNRFavorites.git
python UNRFavorites

```

Drag and drop the icons and click save. You can then run this from a terminal to see your changes (it restarts netbook-launcher):
```
killall netbook-launcher
netbook-launcher &

```

---

