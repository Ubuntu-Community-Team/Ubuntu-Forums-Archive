---
title: "how can I move my musics to another partition without loosing Rhythmbox rates ?"
date: 2011-03-18
forum: New to Ubuntu
---

### Post by shevin on 2011-03-18
Guys I bought a new hard disk, I wanna move my musics to another partition , is there any way that I could keep my ratings, Logs, and Statistics of Rhythmbox ?


my ratings are so important to me.
I use ubuntu 10.10

---

### Post by quirks on 2011-03-18
1. Close Rhythmbox.
2. Make a backup copy of the directory /home/<your username>/.local/share/rhythmbox. This is where Rhythmbox saves your ratings etc. In case you mess up, you can always restore your settings.
3. Move all your music to the new hard disk.
4. Right-click on the relocated directory containing your music and choose "Make Link". A new link should be created, pointing to the music directory. Cut this link and place it, where your music directory used to be. Also, rename it to have exactly the same name that the old directory has (i.e., remove the "Link to " at the beginning).
5. Open Rhythmbox. It should not have noticed that you moved the actual data, because it is still accessible via the old path. In fact, you can access the music via the file browser (or any other application for that matter) via the same old path.

Alternatively, you could also adjust all the paths in the .xml files in the Rhythmbox settings directory. But this is not as easy as creating a symbolic link. Let me know, if my suggested solution is ok for you.

---

### Post by shevin on 2011-03-18
thanks those are smart ideas...I think editing the xml file is better idea , making symbolic links always makes file management slower  ...plus I can make a Replace All in a text editor in a few second . I will let you guys know if it works out for me .

---

