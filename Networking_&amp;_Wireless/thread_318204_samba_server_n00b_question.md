---
title: "samba server n00b question"
date: 2006-12-13
forum: Networking &amp; Wireless
---

### Post by foxxx on 2006-12-13
sorry, but i´m going nuts here...
i tried to follow this thread: [http://www.ubuntuforums.org/showthread.php?p=571908&mode=threaded#post571908](http://www.ubuntuforums.org/showthread.php?p=571908&mode=threaded#post571908)
but i´m stuck at step 2, point 8.
i´d REALLY like to click on my OK button, but it´s greyed out!
i also tried to stop the samba server and installed smbfs, swat and so on
any hints? because i cant find a howto about "greyed out buttons"

thx

---

### Post by koenn on 2006-12-13
wild guess:
- you did not fill in all required information
- you don't have sufficient rights to share that folder (check who owns the folder, who you are,and what permissions you have)

---

### Post by linuchsan on 2006-12-13
try testparm in the console, to see if you get any errors.

---

### Post by dmizer on 2006-12-13
actually, i'd suggest using a different howto.  the howto you linked is lacking in many ways, and may be why you are having a problem.

the first link in my sig is the howto i refer to constantly when i need to set up a samba server.

---

### Post by foxxx on 2006-12-14
hi! thx for your replies!

well... i´m terribly sorry for this but... i found out that this how to is missing one important part: naming your share!!!
of course it´s not possible for samba to activate a share without naming it.

i seems i followed this guide too blindly and oversaw that tiny mistake.
so, thx for your help and understanding
](*,)

---

