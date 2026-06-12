---
title: "Crontab out of the box in 9.04"
date: 2009-10-16
forum: New to Ubuntu
---

### Post by smileyguy on 2009-10-16
I'm having trouble getting a crontab to run. Been reading around so have this question:

Do any permissions need to be set in a newly installed 9.04 OS and Gnome-Schedule has been installed for a regular user to be able to have crontabs & "at" run?

---

### Post by Vermind on 2009-10-16
So, you did ```
crontab -e
``` and added a task, for example
```
* * * * * echo "hello" >> /home/user/Desktop/crontest.txt
```
saved it,
and nothing happens after a minute?

---

### Post by smileyguy on 2009-10-16
Did something like that from [http://gaute.vetsj.com/2009/02/20/how-to-figure-out-if-crontab-and-at-is-correctly-set-up/](http://gaute.vetsj.com/2009/02/20/how-to-figure-out-if-crontab-and-at-is-correctly-set-up/)

and it output the correct text file to my home directory.

Somebody said something about full paths so I am now using as the code:
/usr/bin/btdownloadgui.bittornado /home/username/torrents/movie.torrent (replacing "username" with correct one)

Still same - runs OK manually but nought happens except 'at' task disappears from GUI.

if I do it as recurrent nothing at all happens

Even managed to enter it through Terminal (the crontab) but nothing happened (recurrent task shows up in Gnome-Schedule GUI but doesn't run)

Trying to work out how to enter an AT task through terminal manually for troubleshooting

---

### Post by Vermind on 2009-10-16
Hi.
cron runs in the background. It doesn't know about your X session.
You need to do certain things to make this work with GUI apps.
to start with, you need to set the DISPLAY variable:
DISPLAY=:0 btdownloadgui /home/user/torrents/and-so-on.torrent

---

### Post by smileyguy on 2009-10-16
Thanks Vermind - worked a treat.

I also found this code ***env DISPLAY=:0*** with just the **env** bit added on the front of what you suggested. Do I not need that "env" bit?

Problem is solved now but I am still just curious about how it works:)

---

### Post by mocoloco on 2009-10-16
An easier way is to edit the crontab manually once an put in DISPLAY=:0 at the top of the file, then  you don't need it on each line.  Honestly that should be included by default now that I think about it, maybe I'll push for that.

---

### Post by smileyguy on 2009-10-17
Makes sense. I've suggested is as a tick box option for Gnome-Schedule (like the null display option). Since I imagine it will be those who can't use code using the GUI.

Not sure if I suggested it in the right place though at [http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/) as I think I might need to go to the app's site itself?

---

