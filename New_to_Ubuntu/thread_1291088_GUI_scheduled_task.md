---
title: "GUI scheduled task?"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by smileyguy on 2009-10-14
Is there a simple GUI way to add a scheduled task without having to type ANY commands?

I sued it in Windows to start a pre-downloaded bit torrent file, which would open with the default bit-torrent app,  after my "Off Peak" ISP download time started (e.g., 2:30am) so as not to use all my "peak" time downloads.

I have had advice about the command line way of doing it, but frankly - I don't think I'll ever understand it!

The Windows version let me enter a password to use if logged on etc etc. I only needed to browse to the file to be run and select it.

I have Gnome-schedule 2.02 but it still requires me to enter the command to run the file AND I am not sure what will happen when it asks for a password.

Any pointers? Does anyone know when it will ask me for the password (i.e., if it's at 2:30am - that's no use for me!)

---

### Post by MrWES on 2009-10-14
> **smileyguy said:**
> Is there a simple GUI way to add a scheduled task without having to type ANY commands?

I sued it in Windows to start a pre-downloaded bit torrent file, which would open with the default bit-torrent app,  after my "Off Peak" ISP download time started (e.g., 2:30am) so as not to use all my "peak" time downloads.

I have had advice about the command line way of doing it, but frankly - I don't think I'll ever understand it!

The Windows version let me enter a password to use if logged on etc etc. I only needed to browse to the file to be run and select it.

I have Gnome-schedule 2.02 but it still requires me to enter the command to run the file AND I am not sure what will happen when it asks for a password.

Any pointers? Does anyone know when it will ask me for the password (i.e., if it's at 2:30am - that's no use for me!)


[http://www.ubuntugeek.com/schedule-tasks-using-gnome-schedule-a-cron-at-gui-in-ubuntu.html]("http://www.ubuntugeek.com/schedule-tasks-using-gnome-schedule-a-cron-at-gui-in-ubuntu.html")

---

### Post by smileyguy on 2009-10-14
Installed that - now what would be the command to run the file** /home/username/torrents/movie.torrent** ?

I'm also hoping it would open automatically in my chosen/default program - as it would if I opened the file via Naultilis, but I am getting the felling it doesn't happen that way via the command line right?

I am assuming that's the bit I enter in the **Task** pane of Gnome-Schedule. Is that right?

---

### Post by smileyguy on 2009-10-16
Thanks all - and been reading around. Problem solved and for those interested:

I discovered a bit of code missing off the front of my command in crontab which tells the GUI to run in the desktop. The little bit of code is **env DISPLAY=:0**

So my full command reads
[B]env DISPLAY=:0 /usr/bin/btdownloadgui.bittornado /home/user/torrents/filename.torrent
[/B]replacing **user **and **filename** with the correct variable

Funnily though, the BitTornado GUI would run if I just entered the code WITHOUT **env DISPLAY=:0** from terminal but it never ran from crontab (terminal or Gnome-Schedule GUI).

I know the "env" bit of code tells the app GUI to run on the desktop, but if somebody can explain why this needs to be done in crontab and not elsewhere, I'd love to hear the explanation with the hope of maybe, possibly, with a tuny chance - understanding it!

---

