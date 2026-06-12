---
title: "Change target folder Places&gt;Music"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by AlucardArg on 2009-01-29
The things goes like this:
I have two HD's. The primary, is of course, the OS, and the usual. And in the secondary, there are some backed-up stuff from my old Winbugs install, and all my music.
What I'd like to do, if possible, is to make the link in Places > Music (from the top panel) go to "/media/secdisk/My Music" instead of "/home/nicolas/Music"
I checked in gconf-editor, but no avail. Does anyone know a way to do this?

Thanks!

---

### Post by roquefilipe on 2009-01-29
I believe what you need is to play with Nautilus (file explorer) bookmarks. Open the folder you want and then choose Bookmarks - Add bookmark (Ctrl + D).

If you don't need the old music folder remove it from the bookmarks list by going to Bookmarks - Edit Bookmarks.

---

### Post by mcduck on 2009-01-29
The easiest way is to remove the current Music directory, and then link your own into your home:
```

ln -s /media/secdisk/My\ Music /home/nicolas/Music
```
Now your musics are in the separate drive, but still accessible as if they were inside your home directory. (of course you can also access them by browsing to the actual mountpoint)

Anyway, the locations shown in the Places-menu are the same as bookmarks in Nautilus. You can add any bookmark simply by browsing to that directory and then Bookmarks/Add Bookmark from file browser's menu.

To edit your bookmarks just select Bookmarks/Edit Bookmarks in the file browser.

---

### Post by AlucardArg on 2009-01-29
A big thanks for both of you guys!
As you said, those links are just Nautilus' bookmarks. So I just edited the link from nautilus, and it's done.

Again, thank you for your time.

---

