---
title: "Skype - how to REALLY shut it down"
date: 2011-04-21
forum: New to Ubuntu
---

### Post by Buster95 on 2011-04-21
Is there a way to shut down Skype other than by selecting "X"? I can't find any exit option for it and I notice that when I select "X", it closes the window, but the system monitor shows that the processes continue running.

When I first loaded Skype, there was a "green tick" icon in the Gnome panel, that seemed to shut everything down. That's no longer there, so I'm a bit lost.

Appreciate any thoughts.

---

### Post by cairnzi on 2011-04-21
hey, have you tried killing the process in the system monitor?

Here is a link i came across, not sure if it will help but it is a start Lol.

[http://ubuntuforums.org/archive/index.php/t-1634089.html](http://ubuntuforums.org/archive/index.php/t-1634089.html)

---

### Post by dasan on 2011-04-21
in terminal 
killall skype

make a link to application with this code and run it ;)

---

### Post by TheCompBoy on 2011-04-21
Hmm I've had the problem when i quit skype its still running.. But yes i found the way to close with terminal :)

---

### Post by computerandu on 2011-04-21
Use the following command:

ps aux | grep skype

this will give you the process running skype...the second column is the process id...use that to kill the process using the command :

sudo kill -9 process_id

---

### Post by kostkon on 2011-04-21
> **Buster95 said:**
> When I first loaded Skype, there was a "green tick" icon in the Gnome panel, that seemed to shut everything down. That's no longer there, so I'm a bit lost.
It seems that you have removed your notification area somehow. Right-click on your panel, click on the Add to Panel option and select it from the list of panel applets that appears to add it back.

---

### Post by Buster95 on 2011-04-21
> **cairnzi said:**
> hey, have you tried killing the process in the system monitor?

Here is a link i came across, not sure if it will help but it is a start Lol.

[http://ubuntuforums.org/archive/index.php/t-1634089.html](http://ubuntuforums.org/archive/index.php/t-1634089.html)

Currently, that's what I do. I kill the program from system monitor or use killall in a terminal. I assumed that Skype would have provided a slightly more visible method.
Unless of course, they want the user to inadvertently continue to provide bandwith for other Skype users!!

---

### Post by Buster95 on 2011-04-21
> **kostkon said:**
> It seems that you have removed your notification area somehow. Right-click on your panel, click on the Add to Panel option and select it from the list of panel applets that appears to add it back.

Correct - I removed the "green tick" applet by accident. However, I can find no panel applet for Skype. I'm looking in the right place, but can't see anything that seems relevant.

---

### Post by aeiah on 2011-04-21
> **Buster95 said:**
> Correct - I removed the "green tick" applet by accident. However, I can find no panel applet for Skype. I'm looking in the right place, but can't see anything that seems relevant.

what is suggested is that you add the notification applet, if it is missing. do other notification icons show up? if so, you it might be that you've turned off the system tray icon for skype in skype's preferences.

incidentally, i just quit skype by selecting 'quit' from the skype menu. shortcut key is Ctrl+q

---

### Post by yetiman64 on 2011-04-21
> **Buster95 said:**
> Correct - I removed the "green tick" applet by accident. However, I can find no panel applet for Skype. I'm looking in the right place, but can't see anything that seems relevant.

You need to put the Notification Area applet back. Skype doesn't have its own applet, it just puts an icon in the Notification Area. To shut it down fully right click on the icon in the Notification area and select "Quit".

---

### Post by Buster95 on 2011-04-21
> **aeiah said:**
> what is suggested is that you add the notification applet, if it is missing. do other notification icons show up? if so, you it might be that you've turned off the system tray icon for skype in skype's preferences.

incidentally, i just quit skype by selecting 'quit' from the skype menu. shortcut key is Ctrl+q

Couldn't find a system tray icon in Skype preferences. However, I did not have the notification area enabled on the panel. On enabling it, the green tick returned. Tried it and confirmed that Skype can be fully terminated from that icon.

I was under the impression that the Ctrl+q did not remove the active processes. However, I just rechecked it and discovered that it does the job.

This problem is solved. Thanks to all contributors.
Cheers

---

### Post by drewesq on 2011-04-21
> **Buster95 said:**
> Correct - I removed the "green tick" applet by accident. However, I can find no panel applet for Skype. I'm looking in the right place, but can't see anything that seems relevant.
 
 
It is just the notification applet, I think..... There is no applet just for Skype.

---

### Post by mikewhatever on 2011-04-21
_ctrl+q_
;)

---

