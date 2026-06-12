---
title: "Make Link For Network Shares"
date: 2007-10-08
forum: Networking &amp; Wireless
---

### Post by AgentZ86 on 2007-10-08
Hi all

I'm using Ubunu 7.10 beta

The short Version :
I am trying to create desktop shortcuts to the server shares.


The Long Version
The shares are on a SME contrib box AKA linux and has been working perfectly for all computers on the network for about 2 years.

The Ubuntu install has the Gnome, I'm more use to KDE, however I cannot seem to figure out how to make link or create a desktop shortcut that will link to my Network shares.

I can access all the files by browsing to the network and selecting login info /pass etc,  but I'm a bit confused.

I've googed and search the forums on this subject and don't understand the Gnome interface.

With KDE it was a snap just drag and drop the folder to the desktop and it would ask you if you want to copy/move or create link and it work perfectly.

I'm sure there must be something similar in Gnome but I don't know what or where

Please advise 
Thanks

---

### Post by spd106 on 2007-10-08
I believe in Gnome the idea is to promote a cleaner desktop by putting such links in the Places menu as a bookmark.

You can add a remote share icon to the desktop by going through the Connect to Server... dialog in the Places menu. Alternatively you can create a symlink to the share in Nautilus (right-click -> Make Link) and drag that to the desktop. This doesn't work on file system that don't support symlinks though (FAT32).

---

### Post by AgentZ86 on 2007-10-09
Thanks for the reply,


First:
I did figure out that I could select from the menu places and browse to the network and then from there I can select connect to server and it will create a desktop icon for me.

Second:
As far as keeping the desktop neat, the only real problem with this is:

When you use other programs lets say Lphoto or some other program like KompoZer or something, then it does not allow you to browse easily or quickly to that location. for saving/importing/exporting etc. For example: you can browse to lets say the desktop and if you had a shortcut then you could easily save/import/export to those locations etc.
Basically at this point you have to either save locally or browse the network, and in some cases it could be some deep browsing as files may be deeper in the directories depending on your filing methods of how deep you go for folders.

Example: lets say on the server i have my image file in a location on the server Auction/Steve/selfhost/images/dells/c840s/ref1

If I am selling a few dell C840's computer and make a folder called ref1 for my own refernces and put my current dell which I"m selling in there, then as you can see the directory is already deep enough, but to add to this I also half to browse thru the whole network/ thru the network shares to that location then to that folder instead of simply browsing to that desktop/link which could be at that network location etc.

Anyhow I do get the point about the neat desktop it's a nice idea and I did find out how to make the connect to server links so that worked fine.


Last:
I did not however, get the make link to work for any locations, I get a error message that says:

Ahhh I'm on my windows box now I can't remember what it said, but I'll post back on that later.

Anyhow the links I'm trying to create are on a SME linux server, but I believe perhaps they are using a windows share method perhaps samba or something cause the error message i get says something like error???%%%smb/file name etc.  or something to that effect I'll post the actual message once I reboot back to Ubuntu

But other then that it appears to work perfectly for my needs and took me some getting use to the Gnome desktop which I prefer the KDE method, but I must say it does work well.

Thanks again for the reponse

---

### Post by dmizer on 2007-10-09
try the second link in my sig.  when complete (with the permanent mount method) you will end up with a link on your desktop.

---

### Post by AgentZ86 on 2007-10-10
Uhhhh What ?

Which button do I click again ? LOL

Sorry thats a bit too much information for me.
I have the desktop folder created using a clickety method of browsing thru the network and opening the folder I wish to make a shortcut to. Then I use the menu at the top to create a connect to server file on the desktop, and select connect permanantly.

So it's working fine, but the make link did not appear to allow it.

Anyhow thanks for the response If I run into a problem I'll try the konsole method etc.

Thanks

---

