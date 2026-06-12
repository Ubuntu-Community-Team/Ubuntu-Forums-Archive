---
title: "firefox doesn't keep bookmarks"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by klein de usa on 2009-01-11
hi 
i have installed ubuntu 8.10 64bit,with Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.5) Gecko/2008121623 Ubuntu/8.10 (intrepid) Firefox/3.0.5

the problem is when i book mark something, and then close fire fox and reopen it the book marks i maid my self are gone i even created a folder and put the book marks in a folder and when i shut down fire fox and then restart it they are gone, i can't figure it out has anyone else had this problm?

---

### Post by tuxxy on 2009-01-11
In the edit > prefs > privacy menu have you got it set to delete your session data at application exit?

---

### Post by stumbleUpon on 2009-01-11
Use foxmarks ([http://www.foxmarks.com/](http://www.foxmarks.com/)). It is excellent for maintaining bookmarks across many computers as well.

---

### Post by hivelocitydd on 2009-01-12
Try the following steps

Launch Firefox from the icon on your desktop or through your "Start"(Explorer) menu by finding Mozilla Firefox in your "Programs" or "All Programs" section.

Click on "Bookmarks" in the top toolbar (in between "History" and "Tools"). Under this menu, click "Organize Bookmarks". Another browser window will pop up listing all your bookmarks. In this new window, there is a list of icons at the top.

Select "Bookmarks" from the far left pane, then click on "New Folder", which is the second icon button at the top. A new folder will appear at the bottom of your 
list in the far left pane, and a dialog window will appear.


Rename the folder to something appropriate, then click "Ok".

Scroll through your bookmarks in the right pane to find the ones you want to move to this folder.

   1. Click on the first one you'd like to move.
   2.
      Hold down the "Ctrl" key and continue to click on others to move. This will highlight only the bookmarks you select.


# Click and drag your selections to the new folder you have created in the far left pane.
# Repeat these steps to create additional folders and organize related bookmarks.

---

### Post by klein de usa on 2009-01-12
hi 
tuxxy is in the right ball park, and i checked the box it isn't selected, when it is selected  firefox comes up to a blank page when i de select it, i get the file:///usr/share/ubuntu-artwork/home/index.html page, 

i'm not trying to save bookmarks,or move book marks i just would like it to save them, maybe i need to reinstall firefox ?

---

### Post by josephpmh on 2009-01-16
I just had the same problem.  What I had to do was close out of firefox,  delete the hidden file, /home/[mycomputersname]/.mozilla (goto home/[yourcomputersname]; (it's hidden, so, if you can't see it in nautilus, hit Ctrl-H and all your hidden files should appear).  Then restart firefox.  You'll have lost all settings, extensions, etc. (a clean firefox), but you'll have backed those up already with FEBE or CLEO or just by copying the data.  Right?  

Hope this works for you too.

---

### Post by TechBeastie on 2009-01-16
Actually, though the suggestion to delete your profile directory and start from scratch is a good one, you may not have to delete anything at all.  

I'm thinking that it's possible that the permissions on your ~/.mozilla/firefox directory (or perhaps just the bookmarks file itself) might be incorrect - because the behavior you've described is entirely consistent with you having read-only access to that file.  If you'd like to check this, open up a terminal window, navigate to your profile directory(~/.mozilla/firefox/<your profile directory/), and then run ls -l.

---

### Post by klein de usa on 2009-01-22
hi 
i checked the permissions , and it seemed fine i had read/write permission, so i deleted /.mozilla and reinstalled fire fox and everything is working now thank you for all the help!

---

