---
title: "Firefox bookmarks disappeared into thin air"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by robot_chicken_parm on 2010-05-19
this is weird.  in the bookmarks menu all but one bookmark has been randomly erased from existance.  last night they were there, and today i started up this laptop and they are gone.  i am running ubuntu 9.10 and have been for months and firefox 3.5.9 .....   maybe its this terrible computer i am using.  i had a dell latitude d520 running karmic before someone spilled an entire cup of coffee into the keyboard..  now i am on an inspiron b120 and there is a huge difference.  the dell latitude was a million times better.  im not an expert on computers but i think the intel centrino duo, which they dont even make anymore, is just a lot better than the intel celeron M.  this computer actually lags now, while the dell latitude ran like a dream once i scrapped windows and installed ubuntu.  well they are going to call me as soon as another latitude comes in and i will likely be trading this in and paying the difference.  as for the bookmark problem as long as that is the extent of the damage that will happen i think i will manage just fine.  there are worse things than that, just wondering if anyone has an opinion on that.  when it happenned i am not suprised.  suprised was the first time this computer had frozen or a program stopped responding in ubuntu.  that was a first for me!

---

### Post by Paqman on 2010-05-19
Your bookmarks (along with the rest of your Firefox profile) lives inside the folder /home/username/.mozilla. So i'd be slightly concerned that you've lost a file from your home folder. Have you done any hard shutdowns, or suffered any other corrupt data in /home?

---

### Post by lovinglinux on 2010-05-19
Firerfox creates automatic daily backups of your bookmarks whenever you change them. To restore a backup  go to "Bookmarks >> Organize Bookmarks >> Import and Backup >> Restore" and select the last backup available.

---

### Post by Greblok on 2010-05-19
Probably wont do you any good now, but just a general tip:
I use a FireFox plugin called X-marks to keep all my website logins and bookmarks syncronised across computers.

That way, the X-marks server always keeps a backup of my bookmarks and pw, and i kan add them all to a new computer just by installing the plugin and entering my credentials.
It can also restore open tabs in FireFox across different computers and OSes.

Like I said, just a tip, but I have been using this plugin for years, and I'm often glad i do. :)
You can check it out at [http://www.xmarks.com/](http://www.xmarks.com/)

---

### Post by theozzlives on 2010-05-19
You could use xmarks in the future. It's a handy addon to FireFox. You backup your bookmarks to their server and can transfer/synchronize with other computers.

---

### Post by Paqman on 2010-05-19
> **theozzlives said:**
> You could use xmarks in the future. It's a handy addon to FireFox. You backup your bookmarks to their server and can transfer/synchronize with other computers.

It's also handy for synchronising between different browsers (eg: Chrome <> Firefox)

---

### Post by philinux on 2010-05-19
There's also bindwood in synaptic to sync via ubuntuone.

Not tried it yet though.

---

### Post by Paqman on 2010-05-20
> **philinux said:**
> There's also bindwood in synaptic to sync via ubuntuone.

Not tried it yet though.

I don't know if that's actually working yet. I tried it out on Karmic and it did nuttin.

---

