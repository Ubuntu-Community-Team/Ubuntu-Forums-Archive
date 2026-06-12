---
title: "Reset Download Directory Action"
date: 2010-12-14
forum: New to Ubuntu
---

### Post by expatCM on 2010-12-14
Something I have done but I do not know what ......

If I go to Places / Downloads I do not get the directory view, SMPlayer opens instead.  The same directory viewed from Nautilus gives the directory view.  Whilst Downloads is given as an example it happens to all directories accessed from Places.

Any idea what I have done wrong since I would like to fix it?

---

### Post by expatCM on 2010-12-14
If it helps .....  I just uninstalled smplayer and was able to access all of the directories in the Places menu.

I then reinstalled smplayer and find that I am back to launching the program by clicking to open any directory under Places.

Does anyone know where are the settings found for the directories listed under Places?

---

### Post by QLee on 2010-12-14
This is one way.

When you have accessed(clicked on) "Computer" from the Places menu in the top panel, you are looking at a file browser window which shows whatever partitions are on your hard disk (shown as drive icons), a cdrom if you have one and "Filesystem" (also shown as a drive icon), is that correct?

If so. right click on the "Filesystem", and select "Properties" from the context menu (should be down at the bottom). After the properties sheet opens, select the "Open With" tab to see what the system thinks it should do. (Note: That Open With tab on the properties sheet has a reset button) You probably want to choose, Open Folder.

---

### Post by expatCM on 2010-12-15
ok so I uninstalled smplayer again in order to  do this.   Yes, Computer opens up as you suggest and in the right pane I can right click and select Properties for all items except File System.

For File System the Properties tab is present but it cannot be selected.  Other items such as Photographs show that the Open With action is Open Folder.

I left the window open and then reinstalled smplayer.  I checked the Open With action again and a smplayer item had appeared and had been selected.  So I deselected and then deleted the entry.

This appears to have fixed the problem since I just tested opening the Downloads directory from the Places menu and it opens in directory view rather than launching smplayer ... 

So thank you for your suggestions ..... :)

---

