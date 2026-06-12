---
title: "How-To add parameter to start-up for wireless"
date: 2008-02-15
forum: Networking &amp; Wireless
---

### Post by NuxIT on 2008-02-15
Hi, can someone help me with this issue. Everytime I start ubuntu 7.10 I don't get a valid IP address. It give me the generic 169.x.x address for my ATH0 interface. So, to get online I have to type sudo ifdown ath0 and then sudo ifup ath0. After this it gets a valid IP address from my router and I'm online wireless. How do I add this command to a script or something so It will do it for me? TBH, Chris

---

### Post by NuxIT on 2008-02-15
Nevermind, I figured it out. Guess they don't have advanced linux users around here. :confused:

---

### Post by kevdog on 2008-02-15
Here ya go:
[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

Why don't you do a search before making claims against the lack of experience of the ubuntu community.

---

### Post by NuxIT on 2008-02-15
> **kevdog said:**
> Here ya go:
[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

Why don't you do a search before making claims against the lack of experience of the ubuntu community.

Hi kevdog. Sorry about that. I'm just a little on-edge recently and have a cold. I did see your guide. Nice job!

---

### Post by kevdog on 2008-02-15
No problem -- let me know if the method works for you!

---

### Post by NuxIT on 2008-02-15
> **kevdog said:**
> No problem -- let me know if the method works for you!

Yeah, I didn't notice in your guide initially but I found this in another thread. I also see it in yours. 
> the commands may be placed inside the /etc/rc.local 

I added this to rc.local. 

/etc/init.d/networking restart

Thanks, Chris

---

### Post by kevdog on 2008-02-15
That guide stole some of the methods from me (who I lifted off another user -- at least I gave the user credit however).

---

