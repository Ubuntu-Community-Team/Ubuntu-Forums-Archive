---
title: "Copying Launchers"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by Kissell on 2009-01-20
I created a bunch of scripts to do common command-line stuff I do, and created nice icons/shortcuts/laucnhers for them in folders under the SYSTEM menu...  

Now I want to share them with someone new to linux, so that they don't have to learn the command line at all, because they're just going to do some minor tasks while I'm away.  

How do I copy my menu lauchers to another user?  I think they should be located in each users home folder somewhere, but I can't seem to find them...

---

### Post by SteveDee on 2009-01-20
> **Kissell said:**
> I created a bunch of scripts to do common command-line stuff I do, and created nice icons/shortcuts/laucnhers for them in folders under the SYSTEM menu...  

Now I want to share them with someone new to linux, so that they don't have to learn the command line at all, because they're just going to do some minor tasks while I'm away.  

How do I copy my menu lauchers to another user?  I think they should be located in each users home folder somewhere, but I can't seem to find them...

I think Launchers are saved by user, e.g.; /home/steve/.gnome2/panel2.d/default/launchers

But I don't see how you can effectively copy these, as each users Home probably requires appropriate application config files.

If there is a clean way of doing this I'd expect it to be supported via gconf-editor, but having had a quick look I couldn't see anything promising.

---

### Post by Kissell on 2009-01-20
> /home/USERNAME/.gnome2/panel2.d/default/launchers

This path contains some launchers, but it appears to only contain the launchers I added to the application bar (top)...  not any of the launchers I added to the menus in the application bar...  like if I created folders under SYSTEM and then put launchers in there, they don't show up in this location.

I don't mind installing all the scripts and applications on the other computer, that's not a big deal, but I created several dozen launchers that I don't want to manually re-create on the other computer, or every time I reformat...  so I'd like to know where these files are stored...  but I just can't find them anywhere in my home folder.

---

### Post by Kissell on 2009-01-20
Ah, I finally found the little buggers...  they're hiding in the .local folder.

> 
/home/USERNAME/.local/share/applications
/home/USERNAME/.local/share/desktop-directories


---

