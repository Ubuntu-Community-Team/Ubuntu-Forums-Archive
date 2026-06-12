---
title: "Login just to use Seamonkey?"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by ricardisimo on 2010-05-03
Why does Ubuntu 10.04 ask me for my password every time I launch Seamonkey? I've checked the launcher properties, and it's not a superuser session that I'm launching, so... ?

P.S. - I'm attaching the password prompt image, which doesn't look like the sudo or gksudo prompt anyway.

---

### Post by ricardisimo on 2010-05-03
Hmmm... typing "about:config" in the address bar gave me Seamonkey's configuration page, and there I found a line that says
```
mail.server.server2.login_at_startup     user set     boolean     true
```
Would it be safe to change this to "false"?

---

### Post by ricardisimo on 2010-05-03
It did nothing. Does everyone else log in to use Seamonkey? It just seems odd to me.

---

### Post by chriswyatt on 2010-05-03
I Googled and found this:

[http://www.smartcomputing.com/TECHSUPPORT/detail.aspx?guid=&ErrorID=29874](http://www.smartcomputing.com/TECHSUPPORT/detail.aspx?guid=&ErrorID=29874)

---

### Post by ricardisimo on 2010-05-03
I'd rather not delete all of my stored passwords. Is there another way?

The comp on which I simply upgraded to 10.04 is fine... no password necessary. It's the fresh install that has caused all of the problems.

---

### Post by batharoy on 2010-05-03
> I actually managed to figure out how to get around my issue with the master password. The about:config method didn't work. I renamed the key key3.db to key3.old and let SeaMonkey recreate a new one. When I started up SeaMonkey I wasn't prompted for a master password and all my passwords were saved. I had to re-input only the mail passwords but those were easy. Now everything works like it's supposed to.

[http://forums.mozillazine.org/viewtopic.php?f=40&t=1586055&sid=698631ae82fe82237d908facc28e7aa5&start=15]("http://forums.mozillazine.org/viewtopic.php?f=40&t=1586055&sid=698631ae82fe82237d908facc28e7aa5&start=15")

---

### Post by ricardisimo on 2010-05-03
Oops!... I finally gave up and reset the Master, which seems to be working so far. I did have to access my passwords in Preferences and take a few screenshots so as to have them on hand, but... as long as it works out in the end, I'm cool.

Thanks for the link.

---

### Post by ricardisimo on 2010-05-04
It worked. Now I just have to figure out why I have basically the opposite problem with Firefox... it won't save - or even ask to save - any passwords at all.

---

