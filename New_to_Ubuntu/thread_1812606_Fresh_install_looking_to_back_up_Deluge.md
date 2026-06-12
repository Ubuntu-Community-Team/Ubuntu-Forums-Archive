---
title: "Fresh install looking to back up Deluge"
date: 2011-07-26
forum: New to Ubuntu
---

### Post by osc1882 on 2011-07-26
I'm planning on doing a fresh install of Ubuntu and was wondering what folders do I need to back up to make a back of of Deluge so that I don't have to lose my torrents?

I"m also looking to do a back up of firefox and mumble if anyone knows anything about those.

---

### Post by amjjawad on 2011-07-26
> **osc1882 said:**
> I'm planning on doing a fresh install of Ubuntu and was wondering what folders do I need to back up to make a back of of Deluge so that I don't have to lose my torrents?

You mean the torrents that in progress? or those you already downloaded? 

> 
I"m also looking to do a back up of firefox and mumble if anyone knows anything about those.
What exactly you want to backup? bookmarks?

---

### Post by osc1882 on 2011-07-26
The torrents are already fully downloaded but I plan to keep on seeding them and don't want to have to go thru the work of adding them again one by one. I'm assuming that I can just copy over some settings folders or something. 

As with Firefox I'm looking for back up.. everything. As in everything everything. All of my history and so on.

---

### Post by amjjawad on 2011-07-26
> **osc1882 said:**
> The torrents are already fully downloaded but I plan to keep on seeding them and don't want to have to go thru the work of adding them again one by one. I'm assuming that I can just copy over some settings folders or something. 

As with Firefox I'm looking for back up.. everything. As in everything everything. All of my history and so on.

I'm not on my Ubuntu machine right now to check but will try to post back when I'll be there.

I think it's a matter of copying some folders, that's all. I haven't done that before because I wouldn't care much about that.
All what I care about is anything inside my /home and the bookmarks, that's all :)

---

### Post by Cas07 on 2011-08-05
Visiting the Deluge [website]("http://deluge-torrent.org/") and [forums]("http://forum.deluge-torrent.org/") is a quicker way to get the answer.

[FAQ: Where does Deluge store its settings/config?]("http://dev.deluge-torrent.org/wiki/Faq#WheredoesDelugestoreitssettingsconfig")
```
~/.config/deluge/
```

The state folder within that directory stores all the torrent details.

---

