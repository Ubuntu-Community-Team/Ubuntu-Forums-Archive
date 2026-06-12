---
title: "downloading full albums from picasa"
date: 2011-07-12
forum: New to Ubuntu
---

### Post by constellanation on 2011-07-12
I am trying to download some albums shared with me via picasa and having a bit of difficulty.   I am able to download individual photos (however I need to download around 400+) but when I attempt to download full albums in chrome I get no response, in firefox I recieve the message "Firefox doesn't know how to open this address, because the protocol (picasa) isn't associated with any program."

after a bit of searching I found this link [http://www.google.es/support/forum/p/Picasa/thread?tid=4bda38f0fd25661b&hl=en](http://www.google.es/support/forum/p/Picasa/thread?tid=4bda38f0fd25661b&hl=en) specifically

> Under the gnome desktop, find the following file and edit by hand. I did not find the correct way to do this with gconf-editor.

File name and path:
~/.local/share/applications/mimeapps.list

1. make a copy of the file in case you need to replace it.
2. add the following line at the end of [Added Associations]:
    x-scheme-handler/picasa=picasa.desktop
3. save the file

After doing this, both chrome and firefox will launch the desktop version of picasa on my computer (running 11.04 ubuntu), but nothing happens further with the download. 

I've also tried uninstalling and reinstalling picasa, but that made no difference.  


Finally as another note, in picasa (desktop version) I tried to change the destination folder for downloads in tools>options>general, it lists "My Pictures" as the destination folder, which does not (and to my knowledge, has never) exist(ed) on my computer, when clicking browse to change the folder it opens to "pictures" which does exist however I can not change the destination nor create a new folder for the download destination.


Any help with this would be appreciated.

---

