---
title: "Things I should consider before reinstalling my root partition"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by diablo75 on 2009-06-07
I'm running 9.04 with separate partitions for my root and my home.  I did this so that in the event I'd ever want to do a fresh install I wouldn't have to back anything up (or at least very little might have to be backed up).  Well the system has been buggy ever since I upgraded from 8.10 and I'd like to reinstall the root partition from an alternate disc to see if a fresh install will fix these glitches.

I really only have one app I'm concerned about:  I have some torrents seeding in Transmission that I'd rather want to keep there so I don't have to go dig their respective torrent files up to add them back into the seed queue.  If I reinstall, and then start Transmission up for the first time, will everything be just as I left it before the reinstall?  Stuff like Evolution I'll backup in advanced just to be certain all that stuff is in tact (I rely greatly on my address book).

Anything else I should consider?

---

### Post by philinux on 2009-06-07
As long as you dont format the /home partition all your settings etc. for apps will be preserved. I've reinstalled this way for 2 years now. When I say install thunderbird or deluge following reinstall it's like the same as before. The apps just pick up their settings and data.

---

### Post by yoda2031 on 2009-06-07
There is either much else to consider, or nothing, depending on how you use your system.

If you are a programmer, /usr/local, /opt and /etc probably have files in that you'll want to backup.

If your system runs any servers, particularly web, news or email; then you'll want /var/www/, /var/spool/ and some subdirectories of /etc/ (/etc/apache2, /etc/postfix, /etc/inn spring to mind).

If you are a desktop user who doesn't really tinker much with the environment, you should be ok with just /home but I'd check that there's nothing in /usr/share that's important (eg customised themes).  

As for your torrent, I should imagine the session data is stored in ~/.config/transmission and therefore part of the backup you mentioned.  As long as the files you are seeding are also backed up, you should be ok.

Disclaimer: I probably haven't covered all the bases here, there's a science to backing things up and I'm not an expert.  Just a few suggestions of things you might not have thought of.

---

### Post by diablo75 on 2009-06-07
There only one other thing I don't want to bother setting back up after a reinstall and that's my public SSH key settings.  I'm assuming that since that's stored in ~/.ssh/ all I'll have to do after a reinstall is apt-get install openssh-server and it'll see the key in the folder already and I won't have to create a new one from scratch.  Is that right?

---

