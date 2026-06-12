---
title: "Where is &quot;getid/plugins&quot; folder in xubuntu"
date: 2011-01-09
forum: New to Ubuntu
---

### Post by Add-Aware on 2011-01-09
Hello!

(please, excuse me for mistakes in english text - I am russian)

I've installed gedit on my new Xubuntu (because this is robustest editor for plain text - imho :) ) and want add encoding plugin to it.

But where is "~/.gnome2/gedit/plugins/" folder in Xubuntu? Where gedit stores it's plugins? Where I need to copy files?

Thank you for answer!

---

### Post by mcduck on 2011-01-09
In the same place, ~/.gnome2/gedit/plugins/. :D

(In case you didn't know, "~" is your home directory, so .gnome2 is a hidden directory inside your home.)

If it doesn't exist, you can just create it.

---

### Post by Add-Aware on 2011-01-09
To my regret, it has no effect :( I've created directory, but gedit not interested in files in this folder :) It saves that config, but plugins stores in another place.

---

### Post by mcduck on 2011-01-09
I just tried it and it works fine for me. Make sure that you put the plugin files *directly in to the plugins dir*, not in subdirecotires inside it. And of course remember to enable the plugin from Gedit's preferences as well... ;)

---

### Post by Add-Aware on 2011-01-09
Oh, thank you very much! Now it really works :) 

I owe you... emm.. popcorn. Here it is :)
:popcorn:

---

