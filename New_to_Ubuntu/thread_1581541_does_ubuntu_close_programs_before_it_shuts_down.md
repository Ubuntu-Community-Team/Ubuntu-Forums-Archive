---
title: "does ubuntu close programs before it shuts down?"
date: 2010-09-25
forum: New to Ubuntu
---

### Post by sallam on 2010-09-25
Greetings
I noticed that each time I shutdown my laptop, and restart later, Firefox says it didn't close properly. Must I close all programs before shutting down Ubuntu?
I'm asking because I'm used to windows7, where we can just shutdown and the OS takes care of properly closing all opened programs.

---

### Post by drpjkurian on 2010-09-25
Hi
No need. It closes all the programme by itself when you click shutdown. I close my computer throuh keyboard and i dont care any programme which is running except software downloads and software installation.

Ignore the message of firefox. Nothing has happened to me yet

---

### Post by sallam on 2010-09-25
Thats great. Many thanks.

---

### Post by jtarin on 2010-09-25
It will have negligible effect on Firefox but.....You can go to Menu>System>Preferences>Startup Applications>Options (tab).
Uncheck>Automatically remember running applications when logging out.

---

### Post by iiiears on 2010-09-25
It is more involved but you can add applications/actions to the /etc/init.d shutdown script also.

Cheers.

---

### Post by sallam on 2010-09-25
Thanks.

---

### Post by sallam on 2010-09-26
I've found a nice solution for firefox. We can disable firefox's offer to restore session after crashes. In case anyone is searching for this, here are the simple steps:
   1.  In the Location bar, type about:config and press Enter.
          * The about:config "This might void your warranty!" warning page may appear. Click I'll be careful, I promise!, to continue to the about:config page. 
   2. Find [COLOR="SeaGreen"]browser.sessionstore.resume_from_crash[/COLOR] in the list
   3. Double-click on [COLOR="SeaGreen"]browser.sessionstore.resume_from_crash[/COLOR] to set it to false.

This is helpful if your ubuntu is set to start firefox on startup, and your home pages are too many to wait for loading.

---

