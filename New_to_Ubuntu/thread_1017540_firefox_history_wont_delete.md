---
title: "firefox history wont delete"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by love2learn on 2008-12-21
Problem: Firefox 3.0.5 / Hardy 8.04 the history wont delete.

Things tried: 
    Cleared private data (even went advanced and selected all boxes) , 
    Dropped down history and selected links and pressed delete button. 
    Thought it might be an add-on AKA stumble-upon etc so I un-installed all of them.
     Figured I could complete remove Firefox and re-install.... They are still there.

It is the same 6 history pages and it is driving me nuts.  any suggestions?

---

### Post by thunk77 on 2008-12-21
How about just deleting the cache folder in /home/usr/mozilla/firefox?

---

### Post by balaknair on 2008-12-21
Try History> Show all history--> In the right hand view pane select all entries(click on one entry and then press ctrl-a)-->right click on the selected entries--> choose 'Delete'.
It worked for me(just deleted my entire browsing history testing this :D

---

### Post by love2learn on 2008-12-21
> **balaknair said:**
> Try History> Show all history--> In the right hand view pane select all entries(click on one entry and then press ctrl-a)-->right click on the selected entries--> choose 'Delete'.
It worked for me(just deleted my entire browsing history testing this :D


forgot to mention that I have done that too but the weird thing about that fix is when i go into show all history it has nothing on the right pane for me to delete... 


		*How about just deleting the cache folder in /home/usr/mozilla/firefox?* 	

I am interested in this but I dont see a mozilla folder in either my /home/l2l/  or my /home/usr folder... maybe I have to be root? I will try that again brb

---

### Post by love2learn on 2008-12-21
okay, maybe i need a bit of help with this one as well. How do i root in a gui file system ?

---

### Post by .arean on 2008-12-21
alt+f2 > gksudo nautilus

---

### Post by Account1 on 2008-12-21
Wow thats a unusual problem. Try running any updates for firefox. Until its resolved try to stop the any inappropriate internet activity:---) That is why you want to delete your history so much right?

---

### Post by BDNiner on 2008-12-21
just a thought, are you talking about the websites showing up in the drop down list not in the actual history? Those are tied to your bookmarks and will always be there after you delete your history.

You don't need to be a superuser to access the firefox config files. they are under
/home/[user]/.mozilla/

you can press ctrl+h to view hidden files when in your home folder.

---

### Post by love2learn on 2008-12-21
> **BDNiner said:**
> just a thought, are you talking about the websites showing up in the drop down list not in the actual history? Those are tied to your bookmarks and will always be there after you delete your history.

You don't need to be a superuser to access the firefox config files. they are under
/home/[user]/.mozilla/

you can press ctrl+h to view hidden files when in your home folder.


This was perfect. It was the ctrl+h that worked to find the files i needed. 

The fix was 1 of 2 things. 
1. I deleted all my bookmarks in the /home/(user)/mozilla folder. (I dont think this worked but i did this first so figured i would put it in as well.)
2. I deleted the /home/(username)/mozilla/firefox/*.default  file. Then restarted FF3. 

Now to mark this as solved. Thanks for all your help!!

---

