---
title: "Yahoo messanger"
date: 2009-09-29
forum: New to Ubuntu
---

### Post by vipulkelkar on 2009-09-29
I am not able to install GYachi from the command

sudo apt-get install gyachi

it is unable to find the package

Suggest me a good Yahoo msngr apart from Kopete.

---

### Post by zeroseven0183 on 2009-09-29
Empathy or Pidgin (default Instant Messenger for GNOME)

```
sudo apt-get install empathy
```

Both works good in Yahoo!

---

### Post by mathay on 2009-09-29
To extend what zeroseven said: Pidgin(GNOME), Kopete (KDE), Empathy (GNOME), etc. All are very good alternatives for Yahoo Messenger. You shouldn't have any real issues with any of the mentioned clients.

---

### Post by vipulkelkar on 2009-09-29
i tried to configure pidgin but unable to do it for my yahoo id..m using 8.04
i'll try empathy

---

### Post by mathay on 2009-09-29
What seems to be the issue with Pidgin? Any prompts or anything out of the ordinary?

---

### Post by vipulkelkar on 2009-09-29
when i add an acoount..it doesnt show the contacts in the buddy list

---

### Post by mathay on 2009-09-29
Did you happen to enable the account from 'Accounts->' and then the specific account name?

---

### Post by zeroseven0183 on 2009-09-29
I assume you have the older version. You can get the latest version of Pidgin at [http://www.getdeb.net]("http://www.getdeb.net/release.php?id=4743").

Download all the four files (including the dependencies):
 pidgin (560.8 KB)
 libpurple0 (1.7 MB)
 libpurple-bin (105.2 kB)
 pidgin-data (7.3 MB)

then install them, pidgin is last.

---

### Post by vipulkelkar on 2009-09-29
when i start pidgin for the first time it asked me to add an account
I selected yahoo,gave my id in the screen name and my password..
The next window i got was the buddy list..but it doesnt show any of the buddies

---

### Post by 50chevy on 2009-09-29
> **vipulkelkar said:**
> when i start pidgin for the first time it asked me to add an account
I selected yahoo,gave my id in the screen name and my password..
The next window i got was the buddy list..but it doesnt show any of the buddies
Maybe this is why.
By default pidgin did not show any buddies that were offline. 
To change it.
GO to Buddies > Show > Offline Buddies.

---

### Post by humphreybc on 2009-09-29
Pidgin's pretty cool, I use it and it works well enough, does what I need!

---

### Post by vipulkelkar on 2009-09-29
no dude...obviously i tried that..
this is may be cos i have an old version of pidgin..i'll try out the above given version
thanks

---

### Post by random turnip on 2009-09-29
Download the latest Pidgin then, it works well.

---

### Post by 3rdalbum on 2009-09-29
> **vipulkelkar said:**
> I am not able to install GYachi from the command

sudo apt-get install gyachi

it is unable to find the package

Correct. Gyachi is not available in the Ubuntu repositories. It's old and unmaintained.

Why not use [www.meebo.com?](www.meebo.com?)

---

### Post by zeroseven0183 on 2009-09-29
> **3rdalbum said:**
> Correct. Gyachi is not available in the Ubuntu repositories. It's old and unmaintained.

Why not use [www.meebo.com?]("http://www.meebo.com?")

Meebo is also cool but that's web-based, right?
I believe it doesn't store message logs (I'm not sure).

I hope vipulkelkar was able to set up any of the two.

Anyone here using Empathy?

---

### Post by 3rdalbum on 2009-09-29
> **zeroseven0183 said:**
> Meebo is also cool but that's web-based, right?
I believe it doesn't store message logs (I'm not sure).

Yes it's web-based, and it doesn't allow you to save message logs AFAIK, but it does keep a cache of your last conversation so you can flick back through.

---

