---
title: "creating shortcuts"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by Archer Troy on 2008-12-24
hey guys,

So im trying to catalog my movies in mythbuntu. Problem is each movie is in its own sepearte folder, and cataloging each one i gonna take forever. So i was thinking, is there any way to create shortcuts to all the movies and put them into a seperate folder and the just catalog that one folder? is there any way to create media shortcuts? kinda like what junction links would be in windows?

---

### Post by The Cog on 2008-12-24
Get two nautilus windows - open one in the pictures and the other on the folder where you want the links. Drag the photos using the middle mouse button (if you don't have one, drag wit both the left and the right button). This will pop up a menu where you can choose to copy, move or link the photo file. Choose to link it.

---

### Post by bwallum on 2008-12-24
How about creating a folder called 'MovieCatalog' or similar, then drag and drop each movie folder into it. To create a shortcut and not move the files about you could try symbolic links. Its a bit heavyweight but once set up you could have a folder that 'pointed' to as many other folders as you wanted. 

How to Add and Remove a Symbolic Link 

To add a symbolic link (sometimes abbreviated to symlink) use the sudo ln -s command. 

The first address is the target that you wish to link to. In the example below the target is /dev/scd0. Here /dev is the directory and /scd0 is the optical cd/dvd drive.

The second address is the name and location where you want the link to appear. In this case we want a link named /dvdrw in the /dev folder.

The overall effect is if /dev/dvdrw is called by any part of the system then the system will point to /dev/scd0 instead. This can be very useful when applications use a single name to access a drive but that name may be different on different systems.

Example
(you will need to open a terminal to do this. Go to Applications>Accessories>Terminal. A terminal window will open and you can then enter code) 

sudo ln -s /dev/scd0 /dev/dvdrw 

To remove a symbolic link, use the sudo rm command followed by the name of the symlink. To remove the above symlink we would type 

sudo rm /dev/dvdrw

---

