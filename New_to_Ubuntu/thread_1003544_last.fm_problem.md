---
title: "last.fm problem"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by lakku on 2008-12-06
Hello, I've used search but there's no answer. So far I've only found through search was people looking for how to scrobble to one account.

Okay, there's 2 persons using this PC and Amarok, Banshee or others with built-in scrobbling doesn't support multiaccounts. There's only option for one account always. 

So I'm looking for a way how to get last.fm working like in Windows? So you use a player (player a simple as winamp) and have the last.fm on and you can switch accounts easily without typing the account info again before listening like in Amarok & Banshee.

Thanks :D

---

### Post by KIAaze on 2008-12-10
^^
Found your post on lastfm while searching for a solution: [http://www.last.fm/group/Amarok+Users/forum/18538/_/482756/1#f7975033](http://www.last.fm/group/Amarok+Users/forum/18538/_/482756/1#f7975033)

I think you should ask the amarok and banshee developers to implement this feature.

If you don't want to create another account, you could write a little script or applet to replace the amarok configuration files with your own.
They are located in:
~/.kde/share/apps/amarok

edit:
It seems there's an easier way:
>  alternateive config files
You can make alternative configuration files and make separate icons in the menu for them, Just add "--config filename" for the name of each config file in the command option. (for instance amarok --config /path/to/myconfigurationfile %U) 
[http://www.last.fm/group/Amarok+Users/forum/18538/_/482756/1#f7975033](http://www.last.fm/group/Amarok+Users/forum/18538/_/482756/1#f7975033)

---

