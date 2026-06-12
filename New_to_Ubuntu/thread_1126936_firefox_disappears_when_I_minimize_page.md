---
title: "firefox disappears when I minimize page"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by fredfelter on 2009-04-15
I just did an upgrade from Ubuntu 8.04 to 8.10. Now when I open Firefox (3.08) then minimize the page, all evidence of that browser page disappears, so I have no way to reopen it. The same occurs when I open Skype, for example; the formerly opened FF page disappears. If I try to open a new page I get the ¨already opened¨ warning preventing a new browser page from being viewed.

I´ve searched and googled this and although there is a many mentioned FF bug described it involves missing buttons, the use of visual effects like Compiz or the use of certain extensions, none of which seem to apply to me.

Now I´m sorry I did this upgrade since my use of FF was more important than having the upgraded Ubuntu.

Thanks for any help.

---

### Post by sylvainrb on 2009-04-16
Can you find FF's PID, in htop for example, or not to see if it is at least still active when you minimize the window?

---

### Post by Yashiro on 2009-04-16
Do any programs you run appear as buttons on your taskbar? (like in WindowsXP)

---

### Post by fredfelter on 2009-04-16
Thanks for the replies:
   
Yashiro; No, the minimized window does not appear on the task bar like it used to in Ubuntu Hardy. If it did I could just click on it to reopen it.

Sylvainrb: I don´t know what a PID is nor what htop is so I can´t attempt to answer your question. I hope you´ll elaborate.

---

### Post by sylvainrb on 2009-04-16
Regarding the task bar, I might be wrong but I don't think 8.10 lists open windows on the panel by default. Right click on the task bar/panel, select add to panel and then choose to add Window List. See if this solve the problem? (Or you can toggle windows with Alt+tab also!)

As to install htop:
```
$ sudo apt-get install htop
```

And to run:
```
$ htop
```

And it'll give you a list of all the processes and see if you can find firefox (should be within the first on the list).

Hope this helps!

---

### Post by fredfelter on 2009-04-16
Here´s another clue. I was reviewing a list of FF tips from PC World magazine and saw that Alt + Tab will toggle between open pages so I tried it and lo and behold up pops the minimized page. I already knew that the brower was still open even though I couldn´t see any evidence of it so now I just need to figure out how to have it minimize to a task bar (windows list) item that is still visible. It may be that the bar is off the screen and all I need to do is resize the browser window but I can´t just do it by dragging that edge as it won´t grab. And. by the way, I tried the FF Safe Mode to reset the toolbars but that did nothing.

---

### Post by Yashiro on 2009-04-16
On a bar on your desktop (a gnome panel), right click it and select add to panel.
Scroll down the list off applets and select Window List.
Add it.

---

### Post by Sunon on 2009-04-16
If all else fails you can run 'killall firefox' in the console and then re-run firefox.  It will ask you to start a new session or use the old one.

---

### Post by fredfelter on 2009-04-16
You all nailed it! Thanks a million! 

Looks like Intrepid does the FF windows a bit differently than Hardy and it will take me  while to get used to it.

---

### Post by fredfelter on 2009-04-16
Sylvainrb; can´t I just go to System/Admin/System Moniter to see all the running processes?

---

### Post by lindsay7 on 2009-04-16
click on alt, ctrl,tab, all at once and this will bring back what you can not find.  Also get the add-on to ff called tab mix plus. When you get it click on the the tabs you want to open up in the settings.

---

### Post by fredfelter on 2009-04-16
Thanks Lindsay7. I´ll check out the TabMixPlus.

---

### Post by sylvainrb on 2009-04-16
> **fredfelter said:**
> Sylvainrb; can´t I just go to System/Admin/System Moniter to see all the running processes?

Or you can do that too hehe. I'm still learning too. Glad I could help a little...

---

### Post by jhchadwell on 2009-04-26
you could also run pidof appname from the terminal and it will give you the pid...  I had the same problem, although it was normal yesterday.  Somehow my window chooser disappeared or maybe i removed it on accident.  thanks for the fix

---

