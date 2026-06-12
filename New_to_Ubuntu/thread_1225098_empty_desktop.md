---
title: "empty desktop?"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by joris1977 on 2009-07-28
As the title is saying: I cannot see the documents that i placed on the desktop. I know they are there  because i can see them when i browse to Desktop in Nautilus or on the panel Places -> Desktop.

After some googling I found out that the documents become visible after i do alt-F2 and type nautilus

But they are gone after I restart again. 

Also I checked gconf-editor but under apps -> nautilus -> preferences -> show desktop items is checked. 

After installing ubuntu netbook remix i switched to the classic view with the desktop switcher. Everything else is running really well. 

Does somebody know how to fix this, because it is slightly annoying.

---

### Post by Giant Speck on 2009-07-28
You could try adding Nautilus to the list of startup applications.

Press Alt+F2 and enter "gnome-session-properties".   When the Startup Applications Preferences window pops up, click Add and enter the following:

Name:  Nautilus
Command: nautilus

---

### Post by joris1977 on 2009-07-28
Thanks for the suggestion giant speck. It is a work around, but I rather have a solution. With a netbook I like to keep start-up time, as short as possible.  Maybe I will do a reinstall and see if it happens again, if so than I might make a bug report. I am just thinking there is something wrong in my settings that can easily be fixed, I just can't figure out how and why this happens...

	](*,)

---

### Post by joris1977 on 2009-08-07
Ok fixed it!

If you have the same problem. Here's how i did it
Press alt-f2
type gconf-editor
Go to Desktop -> gnome -> session 

make sure that the required_components_list has the value filemanager if not, as was in my case and probably is a bug in the netbook-remix. than click on it and add the value filemanager.

so it will look like this

[windowmanager,panel,filemanager]

:smile:

---

