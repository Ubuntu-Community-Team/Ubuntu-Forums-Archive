---
title: "Editing Menus and Desktop Icons"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by gRnt on 2009-03-18
Hi all I have recently swapped to Ubuntu 8.10 Desktop as my main Operating System and for the most part I am loving it, I have learnt to master google and found that I picked up terminal fairly easily. I've got all the apps I've wanted installed and configured but there are just two things left that aren't functioning exactly as I would like them.

The first being the "Places" menu, it's pretty messy in there at the moment and there is no option in edit menus to change this. Is there a reason for that, and if you can't change it is there a simple way to hide the menu from my options I rarely use it and it's just annoying me at the moment.

Secondly I currently have an NTFS drive (that with the help of a member in the ubuntu irc channel) helped me mount on boot. I currently have some folders within that drive placed on my desktop. It works great BUT I have this obsession about having a clean desktop (save the icons I want). Is there a way (either in the fstab or the icon itself) to have a command that when the partition is mounted the icon for it doesn't sit on my desktop (if that makes any sense).

The partition itself is of no use to me just the three folders I have a "shortcut" to on my desktop.

Any help would be greatly appreciated!

---

### Post by Bölvaður on 2009-03-18
in fstab mount the partition to something like /mnt/data
you have to make that directory and change the permissions according to your needs (probably set you as owner and chmod 744 [which stand for 7&#8594;give user all rights  4&#8594; give group/all others read permissions])

---

### Post by mcduck on 2009-03-18
For the menu, just right-click the menu applet and select "Edit Menus" to open the menu editor.

Most of the things in the Places-menu can't be edited, but you can edit the bookmarks in Nautilus (Bookmarks/Edit Bookmarks from the menu) for your own bookmarked locations. I rmemeber there should be a way to disable file search & recent documents but can't right now find the gconf keys for those..

For the NTFS drive, everything mounted in to /media will appear as icons on desktop, so if you change your /etc/fstab to moiunt the partition to any other place, for example into /mnt, it won't show on desktop any more. Apart from this there's no way to disable a single partition from showing on the desktop, it's either all of them or none at all. (to disable all drive icons on the desktop, ibncluding removable dives, USB sticks and CD's open gconf-editor, browse to apps/nautilus/desktop and disable "volumes_visible".)

---

### Post by D3ath on 2009-03-18
> **mcduck said:**
> For the menu, just right-click the menu applet and select "Edit Menus" to open the menu editor.

For the NTFS drive, everything mounted in to /media will appear as icons on desktop, so if you change your /etc/fstab to moiunt the partition to any other place, for example into /mnt, it won't show on desktop any more. Apart from this there's no way to disable a single partition from showing on the desktop, it's either all of them or none at all. (to disable all drive icons on the desktop, ibncluding removable dives, USB sticks and CD's open gconf-editor, browse to apps/nautilus/desktop and disable "volumes_visible".)
Thats the only way that i know, but i like having icons.  there is nothing wrong with having stuff on your desktop that's like me sitting here at work and putting my coffee in the drawer becasue I like a clean desktop! lol

---

### Post by rburkartjo on 2009-03-18
gnrt as to the first question you cant remove the places menu. as you get more experienced with ubuntu you can bookmark directories to appear in it. you could if you want to open your home folder go to bookmarks and delete all of them. but the places would still show on the main menu just with nothing in them. and in answer to you second question i dont think so. but you could rights click on the ntfs then right click on the properties button on the botton then left click on the icon when the file opens and you could change the icon. good luck have fun with ubuntu!

---

### Post by gRnt on 2009-03-18
Thanks guys I will try mounting it in a different location now. As for right clicking on the menu that doesn't give me access to change the places pane only applications and system.

This is also a bit off topic but I don't want to start two threads so if someone stumbles across it this would help. I just fully updated my system, ever since if I use a p2p app my network completely disconnects, I must say it's a pain it was working fine before I did this, could I just try re-installing my old network drivers as a fix? How can I diagnose why this is happening...

---

### Post by leonardo_neo on 2009-03-18
Let me try to answer your problem, if I have understood it correctly.

1. You don't want the 'places' icon on your panel? : If this is the problem if I understand, then you can simply remove that from panel by clicking right and then remove. You can chose to replace 'menu bar' with 'main menu'. main menu has single icon which has every options in it.

2. If you don't want see the mounted volumes then you can press Alt+F2---> type gconf-editor---->apps--->nautilus--->desktop----> Uncheck volumes visible.

But that will hide all the mounted volumes. I don't know how to hide a single volume from desktop. But thought to tell you whatever I know. :)

P.S. Appears many people have already answered the questions before my answer become visible..... :)

---

### Post by gRnt on 2009-03-18
Thanks everyone, mounting the folder in /mnt worked for me which is great, I reinstalled my wireless drivers and I have not timed out yet (which it would have done by now normally) and the places tab I may just have to live with, and yes I know having a desktop with almost nothing on it seems silly I just seem to like it better that way haha.

Anyway I might just leave the places tab for now, I don't use it so if I don't open it the unorganisation that is won't annoy me :)

---

