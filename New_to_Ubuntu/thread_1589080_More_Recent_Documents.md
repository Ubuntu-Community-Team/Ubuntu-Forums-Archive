---
title: "More Recent Documents"
date: 2010-10-05
forum: New to Ubuntu
---

### Post by skattorshot on 2010-10-05
Is there any way to list more than 10 "Recent Documents"?  I found some people having success limiting the list with:

```
gtk-recent-files-limit=3
```

in the .gtkrc-2.0 file, but when I try to go above 10 it seems to have no effect.  Does anyone know of something else I could put in that file to list more recent documents, or perhaps another way to do it entirely?

---

### Post by hhh on 2010-10-06
I have no idea how to get the Recent Documents list to display more than 10 entries, but if you open the hidden file ~/.recently-used.xbel you'll see more than 10, mine currently has 16 (look at each href= entry). I don't know how many it holds as I don't usually check it.

HTH

---

### Post by skattorshot on 2010-10-06
Yeah, I noticed that, seems like there should be a way for more than 10 items to show up since the system is keeping track of more.  I think I have the same number you do in ~/.recently-used.xbel, and in ~/.recently-used there appears to be many more.  I figure there has to be a number somewhere I can change, I just can't find it.

---

### Post by hhh on 2010-10-06
I did some Googling and it seems the number of max entries is hard coded into Gnome, so it can't be done. However, screenshots of Gnome 3 (due out in 6 months) show that the number has been greatly increased. (You can do a search for Gnome 3 review, I don't want to hotlink to someone's image.)

---

### Post by skattorshot on 2010-10-06
That is interesting.  Makes me curious as to why it allows you to show less than 10 documents and not more than 10.  I would have figured if it was hardcoded that it wouldn't allow you to show less.  Thanks for the info though, Gnome 3 is looking pretty awesome.  Still wish I could change it on my own, but waiting a few months for it to be officially implemented isn't bad.

---

### Post by Meneer Jansen on 2011-06-26
Sorry to reply to an old thread. But I hate 10.000 forum topics about the exactly same thing. That's even worse! You don't know where to start then. ;)

Anyway, it's 2011 now and still I cannot find *anywhere* on the internet how to bloody get Ubuntu/Gnome to show more than 10 recent documents. Only chips can be "hard coded" imho. There must be a setting. 

Tried *gconf-editor*, but no luck there (did manage to get al longer recent file list in gedit though! :))

No ideas what so ever? And still no word from Gnome developers or experts that can give a decisive answer after all this time?? Come on....

---

### Post by trickish on 2011-07-12
> **Meneer Jansen said:**
> Sorry to reply to an old thread. But I hate 10.000 forum topics about the exactly same thing. That's even worse! You don't know where to start then. ;)

Anyway, it's 2011 now and still I cannot find *anywhere* on the internet how to bloody get Ubuntu/Gnome to show more than 10 recent documents. Only chips can be "hard coded" imho. There must be a setting. 

Tried *gconf-editor*, but no luck there (did manage to get al longer recent file list in gedit though! :))

No ideas what so ever? And still no word from Gnome developers or experts that can give a decisive answer after all this time?? Come on....

Looking for a longer recent documents list in gedit led me to this post and reading through it I was not so happy until I read your post. Therefore can you tell me how you got the longer recent file list in gedit?

---

### Post by Meneer Jansen on 2011-07-12
@Trickish the recent file list in Gedit is: gconf-editor > apps > gedit-2 > preferences > recents > max_recents = 20

:)

---

### Post by nocnokneo on 2011-08-05
On my machine it is:

gconf-editor > apps > gedit-2 > preferences > ui > recents > max_recents

but it only affects the Recent files list in gedit, not the system-wide recent files list.

This is a classic example GNOME not exposing a configuration option for the sake of usability (a good thing, imo) but then failing to provide an under-the-hood option (e.g. gconf-editor) for advanced users.

---

