---
title: "what is the &quot;zeitgeist-daemon&quot; process for?"
date: 2011-07-25
forum: New to Ubuntu
---

### Post by werty2010 on 2011-07-25
i'm curious...i keep seeing that that all the time in system monitor

---

### Post by melrokz on 2011-07-25
> zeitgeist-daemon  is  a  daemon which keeps track of activities on your
       system (file usage, browser history, calendar events, etc.)   and  logs
       them  into  a  central  database. It does not only create a chronologic
       register, but also supports tagging  and  can  establish  relationships
       between activities.

No need to worry, it's a normal system process. Here's the link if you need more info

[http://manpages.ubuntu.com/manpages/karmic/man1/zeitgeist-daemon.1.html](http://manpages.ubuntu.com/manpages/karmic/man1/zeitgeist-daemon.1.html)

---

### Post by werty2010 on 2011-07-25
thanks, 
is there any software installed by default giving me access to this database with a gui?
if not could you recommend me one?

---

### Post by werty2010 on 2011-07-25
...besides unity?

---

### Post by melrokz on 2011-07-26
You may be looking for this:

[http://live.gnome.org/GnomeActivityJournal](http://live.gnome.org/GnomeActivityJournal)

[or]

System > Administration > Log file viewer

---

### Post by XubuRoxMySox on 2011-07-26
When I first read the description of it, I thought for a split second, "Omygosh, spyware in Ubuntu!?" :o

Not at all. It shares information between *applications*, not between users and some "mother ship" or master spy network.

Xubuntu doesn't ship with it like Ubu does (I looked for it on my Xubu).

-Robin

---

### Post by amjjawad on 2011-07-26
> **werty2010 said:**
> i'm curious...i keep seeing that that all the time in system monitor

[http://manpages.ubuntu.com/manpages/karmic/man1/zeitgeist-daemon.1.html](http://manpages.ubuntu.com/manpages/karmic/man1/zeitgeist-daemon.1.html)

Which is already posted I guess.

Please make sure to use [http://www.googlubuntu.com/](http://www.googlubuntu.com/) OR [www.google.com](www.google.com) for such question because that will save **your **time ;)

---

### Post by alina.bolero on 2011-08-25
I tripped over "Zeitgeist" while trying to figure out why my firewall box was running so slow.  You can surely imagine the chills I got when I read the description of the process!  ... followed shortly thereafter by the utter disappointment that the Ubuntu team has allowed this.

I've tried Unity and hated it for the same reason I hate Vista and over-engineered vehicles that do things like lock the doors when you didn't request it.  Sorry, but many of us ran to Linux years ago because we were control freaks.  ... and now the default in Ubuntu is to change the interface based on what it thinks I want to do!  gggrrrrrrrrrrrrr

"Anybody that would give up liberty (read: PERSONAL CONTROL) for the sake of security, deserves neither."  ... but in this case, with Unity and Zeitgeist, it seems we are giving up BOTH at the same time.

I tried to use the "Activity Journal" to see what it was collecting.  It didn't work.  I tried to use sqlite to look at the logs in ~/.local/share/zeitgeist.  It told me the db was locked.  So, I uninstalled Zeitgeist, rebooted, and tried again. No, sorry, "database disk image is malformed".  <eye-roll/> ... DELETE!

This just seems like a script kiddie's wet dream to me!  Knowing what websites and applications the user has credentials on is half the battle.

Can you say "p0wn3d"?

---

### Post by fdrake on 2011-08-25
> what is the "zeitgeist-daemon" process for?
ehh?.. :confused: isn't that....i tought.....  	#-o

ahhhh i have to stop watching Conspiracy Theory movies !

---

### Post by fractalman on 2011-08-25
"Anybody that would give up liberty  for the sake of security, deserves neither. and will lose both"

---

