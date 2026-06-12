---
title: "Firefox transition problem, xp to ubuntu"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by sisyphusdvm on 2009-02-04
As the name of the forum implies...I am definitely an absolute beginner.  I had tinkered a little in the past with some other linux versions, but will slowly transition to ubuntu in order to avoid vista.

Anyway...here is the problem.  I very simply wanted to transfer all my firefox settings (bookmarks mostly) to ubuntu firefox.  Instead of researching, I copied the .default folder from xp to ubuntu directly (using flash memory) and renamed the original ubuntu firefox .default folder to something else.  Well...it didn't work.  Now, when I try to open firefox I get the message:

Firefox is already running but is not responding.  To open a new window you must close the existing process or restart system.

Of course, restarting didn't do anything.  I also tried to uninstall and reinstall using synaptics package manager.

So how do I get firefox back.

Also...I will perform a search after posting this, but any links on transitioning firefox and thunderbird stuff to ubuntu would be GREATLY appreciated.

Thanks in advance and I am really happy to be using 8.10...looks great!

---

### Post by Andy06 on 2009-02-04
Start firefox profile manager.


Alt+F2, then firefox -p. The same command will also be accepted in the terminal, Gnome Do and Launchy if you have them.

Delete all profiles, in fact manually goto your profile folder (~/.mozilla/firefox/xxxxxxxx.default ) in ubuntu and delete everything there. Now you will have a clean firefox.

You can now create a new profile in the profile manager or you can directly copy the entire folder of your windows profile into the ubuntu profile folder and that will work too IF you start up profile manager and then in the folder location select THIS newly copied folder as your location.

What happened right now was you deleted your profile folder that firefox used and subsequently copied an unrecognisable folder. Firefox uses random strings to identify the various folders and these are not the same.

Be very very careful with selecting profile folder location since there is a very very serious bug with firefox on all platforms where it can delete files it did not create (upto and including your root folder, documents or everything). Make sure you choose the folder exactly which you want and don't expect it firefox to create a folder FOR you. example: selecting F:/Documents as your profile location folder will start using the F:/Documents as the profile instead of F:/Documents/h17rh.default and when you delete the profile, the whole of F:/Documents will disappear.

---

### Post by theApokalypsis on 2009-02-04
Do you still have your XP or did u write over it with Ubuntu?

Because you can export your firefox book marks in a HTML format and then import them easily. You can find this in Organize Booksmarks in the Bookmarks menu/

Also for future check out the Foxmarks add on. It lets you sync your books marks, settings and even saved password if you want etc between different installations.

Not too sure about Thunderbird hopefully someone mentions something.

Regarding getting firefox back, when using the Synaptic Package Manager did you select Removal? or Complete Removal? complete removal will remove any configurations for firefox (in your case im guessing the files you copied over from your XP. so make sure to make a copy of them before you remove them if you still want to keep that folder).

best of luck!

EDIT: Andy06 beat me to the initial punch. :)

---

### Post by Dougie187 on 2009-02-04
If you just want to get your bookmarks why not just export them in xp firefox and then reimport them in ubuntu firefox. Also, to clean your firefox you can simply open a terminal and type
```
rm -rf ~/.mozilla
```
Keep in mind, if this is your only copy of your bookmarks you will lose them. But you can always browse through and save your bookmarks too.

---

### Post by sisyphusdvm on 2009-02-04
> **Andy06 said:**
> Start firefox profile manager.


Alt+F2, then firefox -p. The same command will also be accepted in the terminal, Gnome Do and Launchy if you have them.

Delete all profiles, in fact manually goto your profile folder (~/.mozilla/firefox/xxxxxxxx.default ) in ubuntu and delete everything there. Now you will have a clean firefox.

You can now create a new profile in the profile manager or you can directly copy the entire folder of your windows profile into the ubuntu profile folder and that will work too IF you start up profile manager and then in the folder location select THIS newly copied folder as your location.

So incredibly simple, yet worked perfectly.  Thanks!

> **theApokalypsis said:**
> Do you still have your XP or did u write over it with Ubuntu?

Because you can export your firefox book marks in a HTML format and then import them easily. You can find this in Organize Booksmarks in the Bookmarks menu/

Yes, this was a much, much simpler and smarter way to do this.  I have used mozbackup in windows, and totally forgot about exporting.  Thanks also!

This has solved the problem unless someone would like to comment on Thunderbird.

---

### Post by lazyart on 2009-02-04
+1 to Foxmarks.  Keep your bookmarks synced up on multiple machines.

---

### Post by lajevardi on 2009-10-23
Mozilla official sync platform is out now, [Weave]("http://labs.mozilla.com/weave") it!

---

