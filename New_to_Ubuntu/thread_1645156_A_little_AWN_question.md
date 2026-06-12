---
title: "A little AWN question"
date: 2010-12-14
forum: New to Ubuntu
---

### Post by Veren on 2010-12-14
Hello, I just starter using Linux Mint 10 after using Ubuntu 10.04 for about half a year loving it.
I didn't really like the gnome-panel at the bottom though, so I decided to replace it with a nice fitting AWN window. I actually also disabled the panel through gconf-editor. Then, my stupidity struck me :o  Is there any way how I can start the "start menu" through terminal ? I don't know how to get to all the configurations and applications through terminal alone, I need GUI. I'm sorry for a stupid question, I realize I must look like an idiot now. Is there a way to add a "start" icon to AWN ? Also, I wanted the windows like Firefor to be overlapped by AWN dock, but I can't find a way. I read there were some "trunk" option in the general tab but it must have been a few versions ago bacause all I have there is a question whether I want to start AWN on startup. Thanks

---

### Post by Simian Man on 2010-12-14
You can add a main menu applet to AWN, they actually have like 4.  Right click on the dock and select preferences, and you should be able to add applets that way.  If you don't have any menu applets, you may need to add applet packages.

BTW I'd suggest Gnome-do which is a great way to launch applications without needing to go through menus.

---

### Post by qamelian on 2010-12-14
If you launch the AWN setting, there are at least two menu plugins there, including cairo menu, that can be added to AWN.

---

### Post by rburkartjo on 2010-12-16
vern if you still want to start awn with the terminal use this command


avant-window-navigator & exit (note all the & exit does is close the terminal after awn starts)

---

### Post by migs73 on 2010-12-16
I have a feeling you mean the start-menu (run??)that would come up if you pressed Alt+F2 with the panels.

If so I have to tell you that you can't, but, as always with Linux, there is another option. 
It is called Grun and can be download from the USC, you can then add it as a launcher to your AWN dock (what I did) or you could add it to the Keyboard shortcuts (System>Preferences>Keyboard Shortcuts) and bind it to Alt+F2.

If this wasn't what you meant please ignore me!!!!!

Mike

---

### Post by migs73 on 2010-12-16
> **Veren said:**
> Also, I wanted the windows like Firefor to be overlapped by AWN dock, but I can't find a way. I read there were some "trunk" option in the general tab but it must have been a few versions ago bacause all I have there is a question whether I want to start AWN on startup. Thanks

If you right click on the dock and select Dock Preferences and select the 
Preferences tab. Then click on the 'Behaviour' dropdown box and select 'Always Visible'. 
Click close and you should have the behaviour you wish.

Mike

---

