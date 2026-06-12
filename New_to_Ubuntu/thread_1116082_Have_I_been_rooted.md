---
title: "Have I been rooted??"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by GeordieJedi on 2009-04-04
Hi all. Hope your all well. 

I've just done a scan with hard-info (to resolve another question that I've posted)

However when I gave it a cursory glance, I noticed something a little bit strange.

```


Users
-----

-Human Users-
**** 		: **** (I've blanked out my name)
-System Users-
root		: root
daemon		: daemon
bin		: bin
sys		: sys
sync		: sync
games		: games
man		: man
lp		: lp
mail		: mail
news		: news
uucp		: uucp
proxy		: proxy
www-data	: www-data
backup		: backup
list		: Mailing List Manager
irc		: ircd
gnats		: Gnats Bug-Reporting System (admin)

nobody	        : nobody <<< (This was the worrying item)

```

Is this normal or have I been rooted?

Any thoughts/help or advice would be appreciated

Cheers.

---

### Post by GreyGeek on 2009-04-04
> **GeordieJedi said:**
> Hi all. Hope your all well. 

I've just done a scan with hard-info (to resolve another question that I've posted)

However when I gave it a cursory glance, I noticed something a little bit strange.

```


Users
-----

-Human Users-
**** 		: **** (I've blanked out my name)
-System Users-
root		: root
...

nobody	        : nobody <<< (This was the worrying item)

```

Is this normal or have I been rooted?

Any thoughts/help or advice would be appreciated

Cheers.

"nobody" is a non-privileged user the system uses to run services like FTP and others so that they do not have root permission.  Ignore it.

---

### Post by mali2297 on 2009-04-04
It is normal to have a user 'nobody'. I don't recall its use though.

---

### Post by t0p on 2009-04-04
It's perfectly normal to have user "nobody".  So don't sweat!

---

### Post by Didius Falco on 2009-04-04
From the Ubuntu Wiki: [https://wiki.ubuntu.com/nobody](https://wiki.ubuntu.com/nobody)

*nobody is a user on unix systems. *
*you can switch user to nobody thus sudo su nobody *
*Note that nobody's default shell is sh, so you may want to run bash bash *
*Nobody has minimal permissions, so this is a safer user to execute code you do not know, particularly obfuscated code. *

Thanks for asking the question. As a noob myself, it's stuff like this that makes me dig for info and learn more.

---

### Post by GeordieJedi on 2009-04-04
Thanks very much lads, its much appreciated!!

Didius Falco
t0p  	
mali2297 	
GreyGeek


Cheers to all who responded :D

---

