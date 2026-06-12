---
title: "Help with rtorrent - samba share as watch folder"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by randalotto on 2009-09-20
I'm hoping someone can give me a hand here.

I'm trying to set up rtorrent on a headless box. What I want to do, (and what I've heard of others doing, though haven't seen their rtorrent config files,) is to have a folder on my desktop computer, shared via samba, which functions as the watch folder for rtorrent running on the headless box. The headless box would then look at the folder on the desktop.

Essentially, I need help configuring this line:

schedule = watch_directory,5,5,load_start=<PUT SAMBA FOLDER HERE>

When I navigate to the network folder in nautilus, the address bar shows "smb://xxxx-desktop/torrents/"

I've tried it several ways, and I just can't figure it out. How should this look, (if it's even possible...)?

---

### Post by erilidon on 2009-09-20
I'm not sure about the exacts of this setup, as I have never tried anything like that. But I do know what I have had problems with pointing to directories and it is usually that it does like the trailing "/"

SO I would suggest "smb://xxxx-desktop/torrents"

---

### Post by scrooge_74 on 2009-09-20
Why you need samba in the first place ? You using a Windows computer?

For using rtorrent

I open a ssh session to my box, then I use screen, then rtorrent what ever I want to download, I detach from the screen session and I let rtorrent do my bidding

---

