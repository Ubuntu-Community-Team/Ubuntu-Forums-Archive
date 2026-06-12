---
title: "How do I install a &quot;sound theme?&quot;"
date: 2010-10-25
forum: New to Ubuntu
---

### Post by Iniquit-e on 2010-10-25
Very newish to Linux, be aware.

Using 10.10 right now, I believe it is a Gnome desktop too. Whatever it is by default, that is what I have.

Anyway, I'm trying to install a "sound theme" and looking for guidance. Thanks all.

---

### Post by Megaptera on 2010-10-25
I've not tried it but have a look at this:
[http://ubuntu-art.org/index.php?xcontentmode=25&PHPSESSID=bbce70b8289bc6fbc743d788fd09461e](http://ubuntu-art.org/index.php?xcontentmode=25&PHPSESSID=bbce70b8289bc6fbc743d788fd09461e)

[http://ubuntu-art.org/content/show.php/TalkingCat?content=133795](http://ubuntu-art.org/content/show.php/TalkingCat?content=133795)
one example with this instruction:
"Extract the archive into ~/.local/share/sounds.
If the directory doesn\'t exist, make one.
Then open System> Settings> Sounds and select \'TalkingCat\'. "

I went to Control Centre > sounds and it looks possible?

---

### Post by armoftheland on 2010-11-28
Looks like megaptera has it right. You'll want to download a sound theme from gnome-look.org or the like and ensure it's a file with an index for the sounds. Then log in as root (you can hit alt+f2 and type "gksudo nautilus" and enter your password. it should bring up a folder view to navigate through. be careful you have privileges here to mess things up so dont play too much in this mode) navigate to "usr/share/sounds" and drag your theme into the sounds folder. Close your root navigator and then in your menu go to preferences/sound. On that screen there should be a drop down box. As long as your theme has an index for the sounds it should appear there. Apply and restart as required. Good luck! :)

---

