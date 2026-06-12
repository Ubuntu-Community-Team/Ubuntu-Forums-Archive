---
title: "video playing issues"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by clt on 2009-05-12
Hey,

I've recently been using VLC in windows to play avi files from our server, but whenever there is network activity my connection would drop out.

So I installed kubuntu 9.04, but am still having issues...

In VLC, because it's not a native KDE app, I can't find, or browse to, our network drive on the server. Is there any way to locate this? And when I browse to the server in dolphin, and open a file in VLC, it downloads the file to its cache, then plays it. Is there a way to make VLC stream the video instead?

The default video player, dragon, and also kmplayer can find the network drives, and will stream the videos, but can only play one file at a time. Is there any way to play all the files from a specific folder?

Thanks

---

### Post by gn2 on 2009-05-12
Have you tried Kaffeine yet?

---

### Post by clt on 2009-05-12
In kaffeine I can't browse to or locate the network drive (smb://10.1.1.2), like VLC. Mplayer's the same.

---

### Post by gn2 on 2009-05-12
Can you browse to the network drive with Dolphin or Konqueror, then multiple select the files you want to play, then right-click and choose "open with"?

---

### Post by clt on 2009-05-12
The files I want to play are contained within many folders, and when I right-click a folder in dolphin there is no 'open with' option.

---

### Post by gn2 on 2009-05-12
You would have to right-click on the files within the folders.

---

### Post by clt on 2009-05-12
The files I want to play are contained within many folders. I want a playlist of many files.

---

### Post by gn2 on 2009-05-12
Right click on them, select "open with" and they should queue up in the player.

---

### Post by clt on 2009-05-12
But I want many files from many folders in the playlist, I don't want to do it manually.

---

### Post by gn2 on 2009-05-12
I'm confused, you want to play the files but don't want to select them?
How are you going to make them play? By mind control? :P

---

### Post by clt on 2009-05-12
You obviously don't understand what I'm saying, maybe read my posts again because I've explained it fairly well.

---

### Post by gn2 on 2009-05-12
> **clt said:**
> Is there any way to play all the files from a specific folder?

Yes. Browse to them in a file browser such as Dolphin or Konqueror and multiple select the files you want and right-click on them and select "open with".

---

### Post by clt on 2009-05-12
> **clt said:**
> The files I want to play are contained within many folders. I want a playlist of many files.


> **clt said:**
> But I want many files from many folders in the playlist, I don't want to do it manually.

.

---

### Post by gn2 on 2009-05-12
> **clt said:**
> The files I want to play are contained within many folders. I want a playlist of many files.


As I said before, they'll queue up in the Player. (i.e. added to the playlist)

> **clt said:**
> But I want many files from many folders in the playlist, I don't want to do it manually.

Whether you select them from the Player's browser, or using a file browser application, you'll still have to select them "manually".

Once the remote location is mounted, does it not show up in the player's browser?
It does in Totem.

---

### Post by clt on 2009-05-12
> **gn2 said:**
> As I said before, they'll queue up in the Player. (i.e. added to the playlist)



Whether you select them from the Player's browser, or using a file browser application, you'll still have to select them "manually".

Once the remote location is mounted, does it not show up in the player's browser?
It does in Totem.

But I don't want to manually go into every folder that contains videos and select them all and add them to the playlist, I want to go into the application, and "add directory" containing all the videos.

The remote location is not mounted, and I couldn't get smb4k working properly.

---

### Post by clt on 2009-05-13
Well I installed opensuse (just because I prefer it), and I read up how to mount my network drive.

So now I'm using kaffeine, I can locate the files, and add the entire folder to the playlist!

Thanks

---

### Post by gn2 on 2009-05-13
I did suggest Kaffeine and mounting the network drive earlier.....

Glad you have a working solution at last :)

---

