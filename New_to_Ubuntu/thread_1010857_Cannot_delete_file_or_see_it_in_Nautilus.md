---
title: "Cannot delete file or see it in Nautilus"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by Dynamite Jammy on 2008-12-14
Hello,

Complete newbie here - been using ubuntu for about a week.

My problem is this:

I saved my windows favourites folder to an external hard-drive then dropped it onto the Ubuntu desktop after set-up so I could import it into FireFox.

I know want to delete it but the system won't let me - the icon has one of those Xs in the corner.

When I load up nautilus with the gksudo command - I can't see the favourites folder in the window.

I have checked the tick-box for "show hidden files" but it still doesn't appear in nautilus (although it is there in the regular desktop window).

I am downloading konqueror at the moment - which is taking ages - is the right app to delete the folder?

Any help greatly appreciated - and this forum is excellently helpful by the way, so many thanks....

---

### Post by inxygnuu on 2008-12-14
wait? you want to delete it and it is on your desktop? what is the folder named?

---

### Post by Dynamite Jammy on 2008-12-14
It's called "favorites" - it's a folder with some sub-folders in it - all of which contain urls.

Any ideas?

---

### Post by inxygnuu on 2008-12-14
just give me the directory of where it is located.
example:
```
sudo rm /home/yourname/Desktop/favorites
```

that is what I need to know, and it can be removed.

---

### Post by zibi on 2008-12-14
hi,
when you launch nautilus with gksudo the the machine thinks you are the administrator (root). So the files you see are those on the root's desktop (I guess this is your problem). If you never use the root account then the desktop is empty. To look for your own desktop you have to browse around with nautilus.
Move up from the desktop twice and you will find yourself with lots of folders. Double click in /home and then into your normal user's folder. There you find all your data. Double click on Desktop and you will find your files. 

As a normal user you can't delete the files as it has diffeerent permissions (probably due to some complicated issues, like the permissions you have on the drive from which you took the file).
There are commands to change the permissions on the files but maybe it is too complicated. If you are interested into such things give a look to them on line wiki.

Hope it helps

---

### Post by Michael.Godawski on 2008-12-14
Please be cautious. Literally minutes ago I nuked my whole system while trying to remove some files from my usb stick. 

I wanted to make a back-up and landed on a fresh install. :p

---

### Post by fooman on 2008-12-14
in gksu nautilus,  go to file system > home > (user name) > desktop

---

### Post by Dynamite Jammy on 2008-12-14
Wow guys! That fixed it thanks - I didn't realize there was a different between the root desktop and the user desktop.

Have now deleted it.

Many thanks for all the quick responses!

:guitar:

---

### Post by inxygnuu on 2008-12-14
Glad you deleted it! (200th post, yay!:D)

Hope I helped,
3v4n;)

---

