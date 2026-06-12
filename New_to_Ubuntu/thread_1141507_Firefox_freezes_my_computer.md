---
title: "Firefox freezes my computer"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by cybertoon on 2009-04-28
everytime i load firefox my computer slow down - almost stuck
and the only way to save it is to kill firefox ...
i've tired removing it complely and reinstalling and nothing
im useing 9.04 but it happend on 8.10 and the upgrade didnt help 

any ideas?
maybe i should load it on  "Safe mode" and remove all the plugins? 
but how do i do it?

Thanks

---

### Post by MightySeb on 2009-04-28
Try moving Firefox's configuration files somewhere else. This way FF will run with the default settings (with no plugins).

To move the config. files :

[LIST=1]
[*]Make sure Firefox is closed.
[*]Open your home folder ( /home/yourUserName )
[*]Press CTRL + H to display hidden files
[*]Find the ".mozilla" Folder ( the config files are in there )
[*]Rename this folder to something else ( like .mozilla-backup )
[*]Start Firefox
[/LIST]

(Another ".mozilla" folder should be created with the default settings.)

---

### Post by NightwishFan on 2009-04-28
What are your system specs?

Also, do other web browsers, such as Epiphany or Kazehakaze do this?

---

### Post by cybertoon on 2009-04-28
it worked! thanks alot [MightySeb]("http://ubuntuforums.org/member.php?u=700374")! 
thats the folder with the Firefox confs? 

thanks anyway

---

### Post by MightySeb on 2009-04-28
You're welcome. ;)

Yes, the ".mozilla" folder contains everything : options, installed plugins, bookmarks, etc.

It probably was a plugin or an error in a configuration file that was making Firefox act strange.

---

### Post by Wbie on 2010-03-19
Thanks x2 MightSeb

---

